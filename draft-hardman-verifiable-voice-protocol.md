---
title: "Verifiable Voice Protocol"
abbrev: "VVP"
category: std

docname: draft-hardman-verifiable-voice-protocol-latest
submissiontype: IETF
number:
date:
consensus: true
v: 3
keyword:
 - voip
 - telecom
 - telco
 - telephone number
 - vetting
 - KYC
venue:
  github: "dhh1128/vvp"
  latest: "https://dhh1128.github.io/vvp/draft-hardman-verifiable-voice-protocol.html"

author:
 -
    fullname: "Daniel Hardman"
    organization: Provenant, Inc
    email: "daniel.hardman@gmail.com"

normative:
  RFC3261:
  RFC7519:
  RFC8032:
  RFC8224:
  RFC8225:
  RFC8588:
  RFC8866:
  OVC:
    target: https://trustoverip.github.io/kswg-ovc-specification/
    title: "Open Verifiable Communications (OVC)"
    author:
      -
        name: Daniel Hardman
      -
        org: Trust Over IP Foundation
    date: 2025
  TOIP-DOSSIER:
    target: https://trustoverip.github.io/kswg-dossier-specification/
    title: "Verifiable Dossiers"
    author:
      -
        name: Daniel Hardman
    date: 22 Sep 2025
  TOIP-KERI:
    target: https://trustoverip.github.io/tswg-keri-specification/
    title: "Key Event Receipt Infrastructure (KERI)"
    author:
      -
        name: Sam Smith
      -
        name: Kevin Griffin
        role: editor
      -
        org: Trust Over IP Foundation
    date: 5 Jan 2024
  TOIP-ACDC:
    target: https://trustoverip.github.io/tswg-acdc-specification/
    title: "Authentic Chained Data Containers (ACDC)"
    author:
      -
        name: Sam Smith
      -
        name: Phil Feairheller
      -
        name: Kevin Griffin
        role: editor
      -
        org: Trust Over IP Foundation
    date: 6 Nov 2023
  TOIP-CESR:
    target: https://trustoverip.github.io/tswg-cesr-specification/
    title: "Composable Event Streaming Representation (CESR)"
    author:
      -
        name: Sam Smith
      -
        name: Kevin Griffin
        role: editor
      -
        org: Trust Over IP Foundation
    date: 7 Nov 2023

informative:
  FN-DSA:
    target: https://csrc.nist.gov/presentations/2025/fips-206-fn-dsa-falcon
    title: "FIPS 206: FN-DSA (Falcon)"
    author:
      org: NIST
    date: Sep 2025
  RFC4353:
  RFC4575:
  RFC5626:
  RFC6350:
  RFC9796:
  ARIES-RFC-0519:
    target: https://github.com/hyperledger/aries-rfcs/blob/main/concepts/0519-goal-codes/README.md
    title: "Aries RFC 0519: Goal Codes"
    author:
      name: Daniel Hardman
    date: Apr 2021
  CTIA-BCID:
    target: https://api.ctia.org/wp-content/uploads/2022/11/Branded-Calling-Best-Practices.pdf
    title: "Branded Calling ID Best Practices"
    author:
      org: CTIA
    date: Nov 2022

--- abstract

The Verifiable Voice Protocol (VVP) is a profile of the Open Verifiable Communications (OVC) framework {{OVC}} for voice calls carried over SIP {{RFC3261}}. VVP encodes OVC citations as STIR PASSporTs {{RFC8225}} in SIP signaling, binding rich, independently verifiable identity evidence to individual calls. Evidence about callers travels in the SIP `Identity` header of an INVITE; evidence about callees travels in an SDP attribute of the response. VVP interoperates with SHAKEN {{RFC8588}}, RCD {{RFC9796}}, and vCon, and can justify SHAKEN A attestations for calls originating outside SHAKEN ecosystems. This document defines the voice-specific transport binding, PASSporT encoding, channel-binding fields, replay mitigation, and security considerations. Transport-agnostic concerns — citation data model, verification algorithm, dossier structure, evidence theory — are defined in {{OVC}} and {{TOIP-DOSSIER}}.

--- middle

# Introduction

When we get phone calls, we want to know who is calling and why. Existing solutions — SHAKEN, RCD, branded calling — address parts of this problem. Their common limitation is shallow evidence: assurance derives from a service provider's signature alone, without independently verifiable proof of what that signature asserts. They are jurisdiction-specific. They do not prove things about callees. They are expensive to deploy.

VVP addresses these limitations by applying the OVC framework to voice. OVC's curate-once-cite-ephemerally architecture means that the deep evidence work — acquiring vetting credentials, number allocation proofs, brand rights, and delegation chains — is done once and amortized across every subsequent call. The per-call artifact is a compact PASSporT {{RFC8225}} that references the evidence rather than containing it. Any verifier anywhere along the call route can independently fetch and validate the full evidence graph.

This document defines VVP as a conformant OVC profile. It satisfies the eleven profile requirements in {{OVC}} Section 10 ("Writing an OVC Profile"). Transport-agnostic concerns are not repeated here; they are defined in {{OVC}} and {{TOIP-DOSSIER}} and incorporated by reference.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

The terms "citation", "dossier", "profile", "Accountable Party (AP)", "Citing Party (CP)", "Verified Party (VP)", "Verifier", "AID", "KEL", "OOBI", "SAID", "ACDC", "CESR", "witness", and "watcher" are as defined in {{OVC}} and the specifications it references.

The following additional terms are used in this document:

Originating Party (OP):
: The VVP-specific instantiation of the OVC Citing Party (CP). The OP controls the session border controller (SBC) that generates the VVP passport in the SIP INVITE. See {{roles}}.

Accountable Party (AP):
: As defined in {{OVC}}. In voice contexts, the AP holds the right to use the originating telephone number. The callee and any regulator hold the AP accountable for the call.

Originating Service Provider (OSP):
: The service provider associated with the OP.

Terminating Service Provider (TSP):
: The service provider of the callee.

# Overview {#overview}

VVP requires identified parties — callers and optionally callees — to curate a dossier ({{TOIP-DOSSIER}}) of stable evidence in advance. For each call, they issue an ephemeral VVP passport: a JWT {{RFC7519}} in JWS Compact Serialization, encoded as a STIR PASSporT {{RFC8225}}, that cites their dossier. A caller's passport travels as an `Identity` header in a SIP INVITE {{RFC3261}}. A callee's passport travels as an `a=callee-passport:` attribute in the SDP {{RFC8866}} body of the response. Verifiers anywhere along the route — TSPs, regulatory monitors, analytics engines, the recipient — extract and verify the passport(s) per the algorithm in {{OVC}} Section 5.

VVP inherits all transport-agnostic properties of OVC: independent verifiability, cross-jurisdictional operation, historical auditability, privacy-preserving graduated disclosure, and the ability to bridge certificate-based ecosystems such as SHAKEN.

## Role Mapping {#roles}

OVC defines generic roles. The following table maps them to VVP and SIP entities.

| OVC Role | VVP Role | SIP Entity |
|---|---|---|
| Citing Party (CP) | Originating Party (OP) | Entity controlling the originating SBC |
| Accountable Party (AP) | Accountable Party (AP) | The legal entity accountable for the call |
| Verified Party (VP) | AP (caller direction); callee (callee direction) | — |
| Verifier | Verifier | TSP, regulatory monitor, analytics engine, caller or callee |

The OP is the entity that builds and signs the VVP passport. The AP is the entity accountable for the call, whose rights are proved by the dossier. In many deployments these are the same entity. Where they differ — for example, when a call center acts on behalf of an enterprise — the delegation MUST be proved by a delegation credential in the dossier per {{OVC}} Section 3.

The callee role in VVP is both a potential VP (when providing a callee passport) and a potential Verifier (when checking the caller's passport). Enterprises running inbound call centers commonly occupy both roles simultaneously.

A full description of OVC roles, the delegation model, and the dossier evidence graph is in {{OVC}} Sections 3 and 4. Credential type definitions — vetting credentials, TNAlloc credentials, brand credentials, brand proxy credentials, and delegated signer credentials — are defined in {{TOIP-DOSSIER}}.

# Transport Identification

VVP operates over SIP {{RFC3261}}, including deployments using SIP outbound {{RFC5626}} and conference-extended SIP ({{RFC4353}}, {{RFC4575}}). The transport carries OVC citations as STIR PASSporTs per {{RFC8224}} and {{RFC8225}}.

VVP is a PASSporT extension type. The `ppt` header value "vvp" identifies a VVP passport in any STIR-aware infrastructure.

# Serialization Format

VVP uses JWT {{RFC7519}} in JWS Compact Serialization (header.payload.signature, Base64url-encoded). No alternative serialization is defined for this profile; the full OOBI URLs in `kid` and `evd` are sufficient for the bandwidth of SIP signaling.

## Mapping of OVC Abstract Fields to JWT Structure

The mapping from the OVC abstract citation data model ({{OVC}} Section 4.1) to JWT structure is:

**JWT header:**

* `alg` — MUST be "EdDSA" ({{RFC8032}}) or "FN-DSA-512" ({{FN-DSA}}). RSA, HMAC, and ES256 MUST NOT be used. This restriction is inherited from OVC and MUST NOT be weakened.
* `typ` — MUST be "passport" per {{RFC8225}}.
* `ppt` — MUST be "vvp".
* `kid` — MUST be the OOBI of an AID ({{TOIP-KERI}}) controlled by the OP. The OOBI resolves to the OP's KEL ({{TOIP-KERI}}), which provides key state at any reference time. Typically the AID identifies a single SBC service rather than the OP as a legal entity. When the signing AID is not the AP's legal-entity AID, a delegated signer credential in the dossier MUST prove the relationship.

**JWT payload:**

* `evd` — MUST be the OOBI of the dossier ACDC ({{TOIP-ACDC}}) for the AP. Resolves to an HTTP resource serving `application/cesr`. Analogous to `x5u` in X.509 contexts but with tamper-evident SAID-keyed caching.
* `orig` — Required channel-binding field; see {{channel-binding}}.
* `dest` — Required channel-binding field; see {{channel-binding}}.
* `iat` — Required. Seconds since the Unix epoch.
* `exp` — Required in VVP; see {{replay}}.
* `card` — Optional. Brand attributes in VCard format {{RFC6350}}. If present, MUST be justified by a brand credential in the dossier.
* `goal` — Optional. Machine-readable goal code per {{ARIES-RFC-0519}}. If present, the dossier MUST prove CP authorization for calls with this goal.
* `jti` — Optional. Unique identifier for the citation. MAY be used for deduplication.
* `call-reason` — Optional. Human-readable description of call intent. This field is largely redundant with `goal`. Use is discouraged; it is retained for RCD interoperability. It cannot be verified.
* `origId` — Optional. Follows SHAKEN semantics per {{RFC8588}}.

For callee-direction passports only:

* `call-id` — Required. MUST equal the value of the `Call-ID` header in the preceding SIP INVITE.
* `cseq` — Required. MUST equal the value of the `CSeq` header in the preceding SIP INVITE.

Fields defined in the OVC abstract model that appear in the JWT payload of callee passports are otherwise identical to those of caller passports, subject to the callee-specific channel-binding rules in {{channel-binding}}.

### Sample Passport

An example caller VVP passport (long CESR-encoded hashes shortened by ellipsis):

~~~ json
{
  "header": {
    "alg": "EdDSA",
    "typ": "passport",
    "ppt": "vvp",
    "kid": "https://agentsrus.net/oobi/EMC.../agent/EAx..."
  },
  "payload": {
    "orig": {"tn": ["+33612345678"]},
    "dest": {"tn": ["+33765432109"]},
    "card": ["NICKNAME:Monde d'Exemples",
      "LOGO;HASH=EK2...;VALUE=URI:https://example.com/ico64x48.png"],
    "goal": "negotiate.schedule",
    "call-reason": "planifier le prochain rendez-vous",
    "evd": "https://fr.example.com/dossiers/E0F....cesr",
    "origId": "e0ac7b44-1fc3-4794-8edd-34b83c018fe9",
    "iat": 1699840000,
    "exp": 1699840015,
    "jti": "70664125-c88d-49d6-b66f-0510c20fc3a6"
  }
}
~~~

# Channel-Binding Fields {#channel-binding}

VVP defines the following channel-binding fields per {{OVC}} Section 4.2.

## Caller-Direction Binding

`orig` (required):
: The originating telephone number. Format MUST conform to SHAKEN requirements ({{RFC8588}}). Only one telephone number is permitted, even when the SIP INVITE specifies multiple originating numbers. The single number is the one whose authorization is proved by the dossier.

`dest` (required):
: The destination telephone number. Format MUST conform to SHAKEN requirements ({{RFC8588}}).

The verifier confirms that `orig` and `dest` match the corresponding values in the SIP INVITE.

## Callee-Direction Binding

`call-id` (required):
: MUST equal the `Call-ID` value from the preceding SIP INVITE.

`cseq` (required):
: MUST equal the `CSeq` value from the preceding SIP INVITE.

`iat` (required):
: MUST be present and MUST contain a value from the callee's system clock.

The `call-id` and `cseq` fields bind the callee's passport to the specific SIP dialog. The verifier confirms that these values match the INVITE. The callee omits `orig` and `dest` because those are already established by the caller's passport and the dialog context.

# Replay Mitigation {#replay}

`exp` is REQUIRED in VVP for both caller and callee passports. The same two telephone numbers may have many calls; timing plus channel binding alone is insufficient to prevent replay.

The recommended value for `exp` is `iat` + 15 seconds. This is long enough for an INVITE to be routed and trigger ringing on a handset. The maximum permitted value is `iat` + 60 seconds. Values greater than 60 seconds MUST NOT be used.

For callee passports, `exp` is permitted but not required. A callee that omits `exp` signals no additional timeout constraint beyond what the caller's passport implies. If present, the same 60-second maximum applies.

The verifier MUST confirm that `exp` is greater than `iat` and greater than the reference time. The verifier MUST also confirm that `iat` is close enough to the reference time to satisfy its replay tolerance. Thirty seconds is a recommended default tolerance for caller passports.

Detailed generic replay mitigation guidance is in {{OVC}} Section 7.2.

# Citation Encoding

## Caller Direction

The JWT compact form (base64url(header).base64url(payload).base64url(signature)) is placed in the `Identity` header of the SIP INVITE per {{RFC8224}}:

~~~
Identity: <compact-jwt>;info=<oobi-url>;alg=es256
~~~

The `alg` parameter in the `Identity` header indicates the signing algorithm per {{RFC8224}}. For EdDSA, use "es256" for SHAKEN compatibility — TODO: confirm whether SHAKEN's `alg` parameter registry accepts "EdDSA" or whether a bridging convention is needed here.

The `info` parameter SHOULD be set to the OOBI URL from the `kid` header, giving SHAKEN-aware intermediaries a familiar resolution path.

## Callee Direction

The JWT compact form is placed as an `a=callee-passport:` attribute in the SDP {{RFC8866}} body of the callee's `200 OK` response. The value is the compact JWT followed by the suffix `;type=vvp`:

~~~
a=callee-passport:<compact-jwt>;type=vvp
~~~

The attribute MAY also appear in a `180 Ringing` response to make the callee verifiable earlier, but MUST appear in the `200 OK` response.

`Identity` headers are not used for callee passports. Existing SIP tooling does not preserve `Identity` headers on responses. The callee's identity is primarily of interest to the caller, who reads the SDP body.

# Directionality

VVP supports evidence in both directions of a voice call. Compliant implementations MAY support caller-direction only, callee-direction only, or both. The supported direction(s) SHOULD be documented in deployment configuration.

**Caller direction:** Supported when the OP generates a VVP passport and places it in the SIP INVITE `Identity` header as specified in {{citation-encoding}}.

**Callee direction:** Supported when the callee generates a VVP passport and places it in the SDP body of the `200 OK` response as specified in {{citation-encoding}}.

The two passports are independently constructed and independently verified. They reference the same dossier structure but typically different dossiers (each party proves things about itself). The callee's channel-binding fields reference the dialog established by the caller's INVITE.

For callee-direction passports that include `card` and `goal` claims: if the preceding INVITE also declared a `goal`, the callee's goal MUST be a subset of the caller's goal, or the caller's goal MUST be a subset of the callee's goal. This ensures that the two parties are aligned on the communication purpose.

Generic directionality requirements are in {{OVC}} Section 3.4.

# Additional Voice-Specific Fields {#additional-fields}

The fields `typ`, `ppt`, `orig`, `dest`, `call-id`, `cseq`, `call-reason`, and `origId` are defined in {{serialization-format}}. No additional fields beyond those defined in this document and in {{OVC}} Section 4.1 are defined by this profile.

Implementations that encounter unknown fields in a VVP passport MUST ignore them, per {{OVC}} Section 4.1.

# OOBI Resolution

`kid` and `evd` carry full OOBI URLs. No resolver infrastructure is required. A verifier dereferences each URL directly. The OOBI for `kid` returns the OP's KEL in `application/cesr` format. The OOBI for `evd` returns the dossier ACDC in `application/cesr` format.

Because the dossier SAID is globally unique and the dossier is highly stable, verifiers SHOULD cache dossier validations keyed by the SAID. Verifiers MAY cache key state keyed by the AID. Freshness requirements for revocation checking MUST be respected in both cases. See {{OVC}} Section 5.2.

# Verification

VVP verification follows the generic algorithm in {{OVC}} Section 5.1. The following steps are VVP-specific instantiations of the steps that OVC delegates to profiles:

**Step 2 (timing):** Use the replay tolerance and `exp` rules in {{replay}}.

**Step 3 (channel binding):** For caller passports, confirm that `orig` matches the originating telephone number in the SIP INVITE and that `dest` matches the destination number. For callee passports, confirm that `call-id` and `cseq` match the corresponding values from the preceding SIP INVITE and that `iat` is consistent with the timing of the call.

**Step 10 (resource authorization):** Confirm that the dossier contains a TNAlloc credential ({{TOIP-DOSSIER}}) that covers the originating telephone number in `orig`. For callee passports, confirm that the dossier contains a TNAlloc credential for the destination telephone number. If the TNAlloc credential covers a number with a Do Not Originate (DNO) flag, the credential MAY be used in callee-direction passports but MUST NOT be cited in caller-direction passports.

All other steps proceed as defined in {{OVC}} Section 5.1. VVP implementations SHOULD implement caching as described in {{OVC}} Section 5.2. VVP implementations MAY perform historical analysis as described in {{OVC}} Section 5.3.

# Relationship to Existing Trust Mechanisms {#interop}

## SHAKEN

VVP and SHAKEN both use STIR PASSporTs in SIP signaling. They address different problems. SHAKEN attests a service provider's confidence level (A/B/C) in the caller's identity. VVP provides independently verifiable evidence that lets any party — including parties outside SHAKEN's governance — draw their own conclusions.

The two mechanisms interoperate in two modes per {{OVC}} Section 9.2.

**Cascaded mode:** An OSP that has verified a VVP caller passport may issue a SHAKEN passport with an A attestation. The OSP's SHAKEN certificate is referenced via `x5u` in the SHAKEN passport. The OVC evidence underlies the A attestation — the OSP's assertion that the caller controls the number is now backed by a verifiable dossier rather than unilateral judgment. This is the primary deployment model for VVP in SHAKEN ecosystems: VVP provides upstream assurance; SHAKEN carries the result downstream in a form that existing infrastructure understands.

**Foundation mode:** A VVP passport MAY include an `x5u` header pointing to an X.509 certificate for the OP. The `x5u` header does not change OVC verification — key state from the AID's KEL is still required. However, if the certificate is issued to the public key of the OP's AID, the certificate-aware downstream ecosystem receives the full weight of OVC evidence. Foundation mode is useful when a transit provider or analytics engine requires a certificate but the evidence backing it should be OVC-grade.

**Scope:** SHAKEN is deployed primarily in North America. VVP operates without jurisdictional boundary. The cascaded and foundation modes allow VVP evidence originating anywhere in the world to be translated into SHAKEN-compatible form at whatever ingress point SHAKEN governance covers. The reverse — SHAKEN evidence flowing into VVP — is accomplished by incorporating a SHAKEN attestation credential into the dossier via the foreign artifact bridge mechanism in {{TOIP-DOSSIER}}.

## RCD and Branded Calling

The `card` field in a VVP passport carries brand attributes in VCard {{RFC6350}} format. These attributes are analogous to data in RCD {{RFC9796}} and CTIA Branded Calling {{CTIA-BCID}} passports.

The difference is the evidence basis. Brand attributes in a VVP passport MUST be justified by a brand credential in the dossier. They are not self-asserted and not solely dependent on a platform's internal vetting. A verifier that checks the dossier can trace the brand right back to an authoritative registrar.

This creates a bridge to RCD. An OSP or analytics engine that has validated a VVP caller passport — including the brand credential in the dossier — may issue a derivative RCD passport using the validated brand data. The VVP dossier provides the evidentiary foundation for the RCD assertion. Conversely, an RCD or CTIA-BCID vetting credential may be incorporated into the dossier via the foreign artifact wrapper mechanism in {{TOIP-DOSSIER}}, providing additional corroboration.

The `call-reason` field is included in VVP for RCD interoperability. RCD passports include a call reason field; including the same data in the VVP passport allows derivative RCD passports to preserve it. Because `call-reason` is self-asserted and unverifiable, its use is discouraged in VVP contexts where `goal` (which is verifiable) serves the same purpose.

## vCon

VVP passports MAY be attached to vCon conversation records to provide permanent evidence of the identity assertions made during a recorded call. A vCon `stir` party attachment field is the natural location for a caller passport. Callee passports MAY be attached similarly.

As long as signatures over the vCon container assert truthfully that the passport was verified at the time of attachment, all OVC guarantees transfer without replay risk. The dossier's SAID-keyed stability means that validators examining the vCon record months or years later can re-verify the full evidence graph as it existed at the time of the call.

Generic guidance on vCon integration is in {{OVC}} Section 9.4. Voice-specific integration details — the `stir` vCon field semantics, attachment format, and verification lifecycle — are TODO: reference the vCon specification or define here once the relevant vCon extension is stable.

# Security Considerations

This section addresses attack surfaces specific to voice over SIP. Generic security considerations for OVC citations — key management, replay mitigation, delegation constraints, algorithm agility, and quantum readiness — are in {{OVC}} Section 7.

## SIP B2BUA Intermediaries

Session border controllers and back-to-back user agents (B2BUAs) along the call route may strip, replace, or fail to forward the `Identity` header. An attacker controlling a B2BUA can suppress a VVP passport entirely, downgrading the call to unverified.

VVP cannot prevent stripping, but it limits the damage. If a downstream verifier requires VVP verification and the passport is absent, it can apply a configured policy — accept at reduced assurance, challenge, or reject. Verifiers SHOULD distinguish between calls with no VVP passport and calls with an invalid VVP passport. The absence of a passport is a policy question; an invalid passport is an integrity failure.

Deployments that require end-to-end VVP assurance SHOULD negotiate passport preservation as a condition of peering agreements with intermediaries.

## TN Spoofing in SIP

VVP binds the originating telephone number `orig` to the OP's key state and dossier. A forger cannot produce a valid VVP passport for a number they do not control without also controlling the AID in `kid` and a dossier that proves authorization for that number. This is a substantially higher bar than SIP header manipulation alone.

However, VVP does not prevent an OP from constructing a valid passport for a number they legitimately control while using a SIP FROM header that contains a different number. Verifiers MUST check that the `orig` value in the passport matches the actual SIP FROM and P-Asserted-Identity headers, not only that the passport is cryptographically valid.

## SRTP and Media Integrity

VVP secures SIP signaling. It makes no assertions about the media stream. An attacker who hijacks the media path after INVITE acceptance cannot be detected by VVP. Media integrity, if required, depends on SRTP or similar mechanisms outside the scope of this specification.

## Robocall Threat Model

VVP is designed to raise the cost of caller fraud. A caller who curates a dossier — acquiring vetting credentials from identity vetters, TNAlloc credentials from number allocators, and brand credentials from brand registrars — must interact with authoritative parties that can report or revoke abusive actors. The AID and KEL create a non-repudiable, auditable record of the caller's actions. Revocations propagate quickly and are detectable by watchers.

However, VVP does not prevent a legitimately vetted party from misusing their authority (e.g., a vetted organization that subsequently engages in fraud). Revocation of the dossier or individual credentials terminates the VVP assurance for future calls. For ongoing monitoring, verifiers SHOULD configure freshness thresholds for revocation checking that are appropriate to the risk profile of the call population.

## Key Compromise

OVC's use of AIDs with witnesses and prerotation makes VVP more resilient to key compromise than certificate-based approaches. A compromised signing key can be rotated without replacing the AID or the dossier. Compromises are detectable via witness queries. The damage from a compromise is bounded to calls signed between compromise and detection; historical calls are not retroactively invalidated.

For the signing AID in `kid`, which is typically a delegated automation key (not the AP's legal-entity AID), compromise is further bounded: only calls from that specific SBC are affected, not calls from other delegated parties of the same AP.

# IANA Considerations

## PASSporT Type Registration

This document requests IANA registration of the "vvp" PASSporT type per {{RFC8225}}:

~~~
Type: vvp
Description: Verifiable Voice Protocol PASSporT
Specification: [this document]
~~~

## SDP Attribute Registration

This document defines a new SDP {{RFC8866}} session-level attribute per the registry in {{RFC8866}}:

~~~
Attribute name:      callee-passport
Long-form description: A STIR-compatible VVP passport citing a
  dossier of evidence about the callee's identity, brand, and
  related attributes. Placed in 200 OK (and optionally 180
  Ringing) responses to a SIP INVITE.
Type of attribute:   session-level
Subject to charset:  No
Syntax:              callee-passport: <compact-jwt>;type=vvp
Reference:           [this document]
~~~

## Content Type

This specification depends on OOBIs ({{TOIP-KERI}}) being served as web resources with IANA content type `application/cesr`.

--- back

# Acknowledgments
{:numbered="false"}

Much of the cybersecurity infrastructure used by VVP depends on KERI, which was invented by Sam Smith, and first implemented by Sam plus Phil Feairheller, Kevin Griffin, and other technical staff at GLEIF. Thanks to logistical support from Trust Over IP and the Linux Foundation, and to a diverse community of technical experts in those communities and in the Web of Trust group.

Techniques that apply KERI to telco use cases were developed by Daniel Hardman, Randy Warshaw, and Ruth Choueka, with additional contributions from Dmitrii Tychinin, Yaroslav Lazarev, Arshdeep Singh, and many other staff members at Provenant, Inc. Thanks as well to Ed Eykholt for multiple editorial improvements, and to Sam Smith and Kevin Griffin for ongoing collaboration on the OVC framework.