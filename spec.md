---
title: "Verifiable Voice Protocol"
abbrev: "VVP"
category: std

docname: draft-hardman-verifiable-voice-protocol-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
# area: AREA
# workgroup: WG Working Group
keyword:
 - voip
 - telecom
 - telco
 - telephone number
 - vetting
 - KYC
venue:
#  group: WG
#  type: Working Group
#  mail: WG@example.com
#  arch: https://example.com/WG
  github: "dhh1128/vvp"
  latest: "https://dhh1128.github.io/vvp/draft-hardman-verifiable-voice-protocol.html"

author:
 -
    fullname: "Daniel Hardman"
    organization: Provenant, Inc
    email: "daniel.hardman@gmail.com"

normative:
  RFC3261:
  RFC4353:
  RFC4575:
  RFC4648:
  RFC5626:
  RFC5280:
  RFC8032:
  RFC8224:
  RFC8225:
  RFC8866:
  FIPS186-4:
    target: https://doi.org/10.6028/NIST.FIPS.186-4
    title: Digital Signature Standard (DSS)
    author:
      org: National Institute of Standards and Technology (NIST)
    date: July 2013
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
  ISO-17442-1:
    target: https://www.iso.org/standard/78829.html
    title: "Financial services – Legal entity identifier (LEI) – Part 1: Assignment"
    author:
      org: International Organization for Standardization
    date: 2020
  ISO-17442-3:
    target: https://www.iso.org/standard/85628.html
    title: "inancial services – Legal entity identifier (LEI) – Part 3: Verifiable LEIs (vLEIs)"
    author:
      org: International Organization for Standardization
    date: 2024
  ATIS-1000074:
    target: https://atis.org/resources/signature-based-handling-of-asserted-information-using-tokens-shaken-atis-1000074-e/
    title: "Signature-Based Handling of Asserted Information Using toKENs (SHAKEN)"
    author:
      org: Alliance for Telecommunications Industry Solutions
    date: Feb 2019

informative:
  RFC3262:
  RFC3986:
  RFC6350:
  RFC7095:
  RFC7519:
  RFC8226:
  RFC8588:
  VCON-DRAFT: I-D.ietf-vcon-vcon-container
  GSMA-RCS:
    target: https://www.gsma.com/solutions-and-impact/technologies/networks/wp-content/uploads/2019/10/RCC.07-v11.0.pdf
    title: "Rich Communication Suite - Advanced Communications
Services and Client Specification, version 11.0"
    author:
      org: GSMA
    date: 16 Oct 2019
  RCD-DRAFT: I-D.ietf-sipcore-callinfo-rcd
  RCD-PASSPORT: I-D.ietf-stir-passport-rcd
  SD-JWT-DRAFT: I-D.ietf-oauth-selective-disclosure-jwt
  CTIA-BCID:
    target: https://api.ctia.org/wp-content/uploads/2022/11/Branded-Calling-Best-Practices.pdf
    title: "Branded Calling ID Best Practices"
    author:
      org: CTIA
    date: Nov 2022
  W3C-DID: W3C.REC-did-core-20220719
  W3C-VC: W3C.REC-vc-data-model-20220303
  ARIES-RFC-0519:
    target: https://github.com/hyperledger/aries-rfcs/blob/main/concepts/0519-goal-codes/README.md
    title: "Aries RFC 0519: Goal Codes"
    author:
      name: Daniel Hardman
    date: Apr 2021
  JSON-SCHEMA:
    target: https://json-schema.org/specification
    title: "JSON Schema Specification 2020-12"
    author:
      org: JSON Schema Community
    date: 16 June 2022
  LE-VLEI-SCHEMA:
    target: https://github.com/GLEIF-IT/vLEI-schema/blob/main/legal-entity-vLEI-credential.json
    title: "Legal Entity vLEI Credential"
    author:
      org: GLEIF
    date: 20 Nov 2023
  TN-ALLOC-SCHEMA:
    target: https://github.com/provenant-dev/public-schema/blob/main/tn-alloc/tn-alloc.schema.json
    title: "TN Allocation Credential"
    author:
      org: Provenant
    date: 20 Dec 2024
  BRAND-SCHEMA:
    target: https://github.com/provenant-dev/public-schema/blob/brand-owner/brand-owner/brand-owner.schema.json
    title: "Brand Credential"
    author:
      name: Daniel Hardman
    date: 31 Dec 2024
  PERSONHOOD-CRED:
    target: https://arxiv.org/pdf/2408.07892
    title: "Personhood credentials:
Artificial intelligence and the value of
privacy-preserving tools to distinguish who is real online"
    author:
      -
        name: Steven Adler
      -
        name: Zoë Hitzig
      -
        name: Shrey Jain
      -
        name: Catherine Brewer
      -
        name: Wayne Chang
      -
        name: Renée DiResta
      -
        name: Eddy Lazzarin
      -
        name: Sean McGregor
      -
        name: Wendy Seltzer
      -
        name: Divya Siddarth
      -
        name: Nouran Soliman
      -
        name: Tobin South
      -
        name: Connor Spelliscy
      -
        name: Manu Sporny
      -
        name: Varya Srivastava
      -
        name: John Bailey
      -
        name: Brian Christian
      -
        name: Andrew Critch
      -
        name: Ronnie Falcon
      -
        name: Heather Flanagan
      -
        name: Kim Hamilton Duffy
      -
        name: Eric Ho
      -
        name: Claire R. Leibowicz
      -
        name: Srikanth Nadhamuni
      -
        name: Alan Z. Rozenshtein
      -
        name: David Schnurr
      -
        name: Evan Shapiro
      -
        name: Lacey Strahm
      -
        name: Andrew Trask
      -
        name: Zoe Weinberg
      -
        name: Cedric Whitney
      -
        name: Tom Zick
    date: Aug 2024
  F2F-SCHEMA:
    target: https://github.com/provenant-dev/public-schema/blob/main/face-to-face/index.md
    title: "Face-to-Face Credentials"
    author:
      name: Daniel Hardman
    date: 13 Dec 2023
  CITATION-SCHEMA:
    target: https://github.com/provenant-dev/public-schema/blob/main/citation/index.md
    title: "Citation Schema"
    author:
      name: Daniel Hardman
    date: 2 Apr 2025
  GCD-SCHEMA:
    target: https://github.com/provenant-dev/public-schema/blob/main/gcd/index.md
    title: "Generalized Cooperative Delegation (GCD) Credentials"
    author:
      name: Daniel Hardman
    date: 18 Dec 2023
  DOSSIER-SCHEMA:
    target: https://github.com/provenant-dev/public-schema/blob/main/vvp-dossier/vvp-dossier.schema.json
    title: "Verifiable Voice Dossier"
    author:
      name: Arshdeep Singh
    date: 2 Jan 2025
  ORG-VET-SCHEMA:
    target: https://github.com/provenant-dev/public-schema/blob/main/org-vet/index.md
    title: "Org Vet Credentials"
    author:
      name: Daniel Hardman
    date: 17 June 2025

--- abstract

Verifiable Voice Protocol (VVP) authenticates and authorizes organizations and individuals making and/or receiving telephone calls. This eliminates trust gaps that malicious parties exploit. Like related technolgies such as SHAKEN, RCD, and BCID, VVP uses STIR to bind cryptographic evidence to a SIP INVITE, and verify this evidence downstream. VVP can also let evidence flow the other way, proving things about the callee. VVP builds from different technical and governance assumptions than alternatives, and uses stronger, richer evidence. This allows VVP to cross jurisdictional boundaries easily and robustly. It also makes VVP simpler, more decentralized, cheaper to deploy and maintain, more private, more scalable, and higher assurance. Because it is easier to adopt, VVP can plug gaps or build bridges between other approaches, functioning as glue in hybrid ecosystems. For example, it may justify an A attestation in SHAKEN, or an RCD passport for branded calling, when a call originates outside SHAKEN or RCD ecosystems. VVP also works well as a standalone mechanism, independent of other solutions. An extra benefit is that VVP enables two-way evidence sharing with verifiable text and chat (e.g., RCS and vCon), as well as with other industry verticals that need verifiability in non-telco contexts.

--- middle

# Introduction
When we get phone calls, we want to know who's calling, and why. Often, we want similar information when we *make* calls as well, to confirm that we've truly reached who we intend. Strangers abuse expectations in either direction, far too often.

Regulators have mandated protections, and industry has responded. However, existing solutions have several drawbacks:

* Assurance of callers derives only from the signatures of originating service providers, with no independently verifiable proof of what they assert.
* Proving the identity of the callee is not supported.
* Each jurisdiction has its own governance and its own set of signers. Sharing information across boundaries is fraught with logistical and regulatory problems.
* Deployment and maintenance costs are high.
* Market complexities such as the presence of aggregators, wholesalers, and call centers that proxy a brand are difficult to model safely.
* What might work for enterprises offers few benefits and many drawbacks for individual callers.

VVP solves these problems by applying crucial innovations in evidence scope, evidence format, and vetting mechanisms. These innovations profoundly upgrade what is provable in an ecosystem, as well as what is cacheable and what must be centralized. However, they have only subtle effects on the content of a STIR PASSporT, so they are explored outside this spec. 

# Conventions and Definitions

{::boilerplate bcp14-tagged}

# Overview

Fundamentally, VVP requires identified parties (callers and/or callees) to curate ({{<curating}}) a dossier ({{<dossier}}) of stable evidence that proves things about them. This is done once or occasionally, in advance, as a configuration precondition. Then, for each call, participants decide whether to share this evidence. Callers share evidence by creating an ephemeral STIR-compatible VVP PASSporT ({{<passport}}) that cites ({{<citing}}) their preconfigured dossier. This passport travels along the delivery route as an `Identity` header in a SIP INVITE. Callees share evidence by adding an analogous passport to an attribute line in the SDP {{RFC8866}} body of their SIP response. This passes a signed citation to their dossier in the other direction. Verifiers anywhere along the route check the citation(s) and corresponding dossier(s), including realtime revocation status, to make decisions ({{<verifying}}).

A VVP call may carry assurance in either or both directions. Compliant implementations may choose to support only assurance about the caller, only assurance about the callee, or both.

## Roles

Understanding the workflow in VVP requires a careful definition of roles related to the protocol. The terms that follow have deep implications for the mental model, and their meaning in VVP may not match casual usage.

### Allocation Holder
An *allocation holder* controls how a phone number is used, in the eyes of a regulator. Enterprises and consumers that make and receive calls with phone numbers they legitimately control are the most obvious category of allocation holders, and are called direct *telephone number users* (*TNUs*). Range holders hold allocations for numbers that have not yet been assigned; they don't make or receive calls with these numbers, and are therefore not TNUs, but they are still allocation holders.

It is possible for an ecosystem to include other parties as allocation holders (e.g., wholesalers, aggregators). However, many regulators dislike this outcome, and prefer that such parties broker allocations without actually holding the allocations directly.

### Callee {#TP}
For a given phone call, a *callee* (also referred to as a *terminating party* or *TP*) receives the call. Typically one callee is targeted, but multiparty SIP flows allow INVITEs to multiple callees, either directly or via a conference server (see {{RFC4353}} and {{RFC4575}}). A callee can be an individual consumer or an organization. The direct service provider of the callee is the *terminating service provider* (*TSP*). In many use cases for VVP, callers attempt to prove things to callees, and callees and their service providers use VVP primarily with a verifier mindset. However, enterprises or call centers that accept inbound calls from individuals may want assurance to flow the other direction; hence, VVP supports optional evidence about callees as well.

### Originating Party {#OP}
An *originating party* (*OP*) controls the first *session border controller* (*SBC*) that processes an outbound call, and therefore builds the VVP passport ({{<passport}}) that cites evidence about the caller.

It may be tempting to equate the OP with "the caller", and in some perspectives this could be true. However, this simple equivalence lacks nuance and doesn't always hold. In a VVP context, it is more accurate to say that the OP creates a SIP INVITE {{RFC3261}} with explicit, provable authorization from the party accountable for calls on the originating phone number. The OP originates the VVP protocol, but not always the call on the handset.

It may also be tempting to associate the OP with an organizational identity like "Company X". While this is not wrong, and is in fact used in high-level descriptions in this specification, in its most careful definition, the cryptographic identity of an OP should be more narrow. It typically corresponds to a single service operated by an IT department within (or outsourced but operating at the behest of) Company X, rather than to Company X generically. This narrowness limits cybersecurity risk, because a single service operated by Company X needs far fewer privileges than the company as a whole. Failing to narrow identity appropriately creates vulnerabilities in some alternative approaches. The evidence securing VVP MUST therefore prove a valid relationship between the OP's narrow identity and the broader legal entities that stakeholders more naturally assume and understand (see {{<DE}}).

The service provider associated with an OP is called the *originating service provider* (*OSP*). For a given phone call, there may be complexity between the hardware that begins a call and the SBC of the OP -- and there may also be many layers, boundaries, and transitions between OSP and TSP.

### Accountable Party {#AP}
For a given call, the *accountable party* (*AP*) is the organization or individual (the TNU) that has the right to use the originating phone number, according to the regulator of that number. When a callee asks, "Who's calling?", they have little interest in the technicalities of the OP, and it is almost always the AP that they want to identify. The AP is accountable for the call, and thus "the caller", as far as the regulator and the callee are concerned.

APs can operate their own SBCs and therefore be their own OPs. However, APs can also use a UCaaS provider that makes the AP-OP relationship indirect. Going further, a business can hire a call center, and delegate to the call center the right to use its phone number. In such a case, the business is the AP, but the call center is the OP that makes calls on its behalf. None of these complexities alter the fact that, from the callee's perspective, the AP is "the caller". The callee chooses to answer or not, based on their desire to interact with the AP. If the callee's trust is abused, the regulator and the callee both want to hold the AP accountable.

In order to verify a caller, VVP requires an AP to prepare a dossier ({{<dossier}}) of evidence that documents a basis for imposing this accountability on them. Only the owner of a given dossier can prove they intend to initiate a VVP call that cites their dossier (see {{<delegating-signing-authority}}). Therefore, if a verifier confirms that a particular call properly matches its dossier, the verifier is justified in considering the owner of that dossier the AP for the call. Otherwise, someone is committing fraud. Accountability, and the basis for it, are both unambiguous.

### Verified Party {#VP}
A *verified party* (*VP*) is a party that uses VVP to prove assertions about itself and its delegation decisions. When VVP provides assurance about callers, the AP is a VP. When VVP provides assurance about callees, the callee is a VP. Some characteristics of proxies, delegates, and service providers may be proved by a dossier, but these parties are not VPs. They don't create dossiers, and dossiers are not focused on them.

### Verifier
A *verifier* is a party that wants to know who's calling or being called, and maybe why -- and that evaluates the answers to these questions by examining formal evidence. Callees, callers, TSPs, OSPs, government regulators, law enforcement doing lawful intercept, auditors, and even APs or OPs can be verifiers. Each may need to see different views of the evidence about a particular phone call, and it may be impossible to comply with various regulations unless these views are kept distinct -- yet each wants similar and compatible assurance.

In addition to checking the validity of cryptographic evidence, the verifier role in VVP MAY also consider how that evidence matches business rules and external conditions. For example, a verifier can begin its analysis by deciding whether Call Center Y has the right, in the abstract, to make or receive calls on behalf of Organization X using a given phone number. However, VVP evidence allows a verifier to go further: it can also consider whether Y is allowed to exercise this right at the particular time of day when a call occurs, or in a particular jurisdiction, given the business purpose asserted in a particular call.

## Lifecycle
VVP depends on three interrelated activities with evidence:

* Curating
* Citing
* Verifying

Chronologically, evidence must be curated before it can be cited or verified. In addition, some vulnerabilities in existing approaches occur because evidence requirements are too loose. Therefore, understanding the nature of backing evidence, and how that evidence is created and maintained, is a crucial consideration for VVP.

However, curating does not occur in realtime during phone calls, and is out of scope for a network protocol specification. Citing and verifying are the heart of VVP, and implementers will approach VVP from the standpoint of SIP flows {{RFC3261}}, {{RFC5626}}. Therefore, we leave the question of curation to a separate document. Where not-yet-explained evidence concepts are used, inline references allow easy cross-reference to formal definitions that come later.

# Citing

## Citing the AP's dossier
A VVP call that makes the caller verifiable begins when the OP ({{<OP}}) generates a new VVP passport ({{<passport}}) that complies with STIR {{RFC8224}} requirements. In its compact-serialized JWT {{RFC7519}} form, this passport is then passed as an `Identity` header in a SIP INVITE {{RFC3261}}. The passport *constitutes* lightweight, direct, and ephemeral evidence; it *cites* and therefore depends upon comprehensive, indirect, and long-lived evidence (the AP's dossier; see {{<dossier}}). Safely and efficiently citing stronger evidence in a dossier is one way that VVP differs from alternatives.

### Questions answered by an AP's passport
The passport directly answers at least the following questions:

* What is the cryptographic identity of the OP?
* How can a verifier determine the OP's key state at the time the passport was created?
* How can a verifier identify and fetch more evidence that connects the OP to the asserted AP?
* What brand attributes are asserted to accompany the call?

The first two answers come from the `kid` header. The third answer is communicated in the required `evd` claim. The fourth answer is communicated in the optional `card` and `goal` claims.

More evidence can then be fetched to indirectly answer the following additional questions:

* What is the legal identity of the AP?
* Does the AP have the right to use the originating phone number?
* Does the AP intend the OP to sign passports on its behalf?
* Does the AP have the right to use the brand attributes asserted for the call?

Dossiers can be further expanded to answer even more questions; such dynamic expansion of the scope of proof is compatible with but not specified by VVP.

### Sample passport
An example will help. In its JSON-serialized form, a typical VVP passport for an AP (with some long CESR-encoded hashes shortened by ellipsis for readability) might look like this:

~~~ json
{
  "header": {
    "alg": "EdDSA",
    "typ": "JWT",
    "ppt": "vvp",
    "kid": "https://agentsrus.net/oobi/EMC.../agent/EAx..."
  },
  "payload": {
    "orig": {"tn": ["+33612345678"]},
    "dest": {"tn": ["+33765432109"]},
    "card": ["NICKNAME:Monde d'Exemples",
      "CHATBOT:https://example.com/chatwithus",
      "LOGO;HASH=EK2...;VALUE=URI:https://example.com/ico64x48.png"],
    "goal": "negotiate.schedule",
    "call-reason": "planifier le prochain rendez-vous",
    "evd": "https://fr.example.com/dossiers/E0F....cesr",
    "origId": "e0ac7b44-1fc3-4794-8edd-34b83c018fe9",
    "iat": 1699840000,
    "exp": 1699840030,
    "jti": "70664125-c88d-49d6-b66f-0510c20fc3a6"
  }
}
~~~

The semantics of the fields are:

* `alg` *(required)* MUST be "EdDSA". Standardizing on one scheme prevents jurisdictions with incompatible or weaker cryptography. The RSA, HMAC, and ES256 algorithms MUST NOT be used. (This choice is motivated by compatibility with the vLEI and its associated ACDC ecosystem, which depends on the Montgomery-to-Edwards transformation.)
* `typ` *(required)* Per {{RFC8225}}, MUST be "passport".
* `ppt` *(required)* Per {{RFC8225}}, MUST identify the specific PASSporT type -- in this case, "vvp".
* `kid` *(required)* MUST be the OOBI of an AID ({{<aid}}) controlled by the OP ({{<OP}}). An OOBI is a special URL that facilitates ACDC's viral discoverability goals. It returns IANA content-type `application/json+cesr`, which provides some important security guarantees. The content for this particular OOBI MUST be a KEL ({{<KEL}}). Typically the AID in question does not identify the OP as a legal entity, but rather software running on or invoked by the SBC operated by the OP. (The AID that identifies the OP as a legal entity may be controlled by a multisig scheme and thus require multiple humans to create a signature. The AID for `kid` MUST be singlesig and, in the common case where it is not the legal entity AID, MUST have a delegate relationship with the legal entity AID, proved through Delegate Evidence {{<DE}}.)
* `orig` *(required)* Although VVP does not depend on SHAKEN, the format of this field MUST conform to SHAKEN requirements ({{ATIS-1000074}}), for interoperability reasons (see {{<interoperability}}). It MUST also satisfy one additional constraint, which is that only one phone number is allowed. Depite the fact that a containing SIP INVITE may allow multiple originating phone numbers, only one can be tied to evidence evaluated by verifiers.
* `dest` *(required)* For interoperability reasons, MUST conform to SHAKEN requirements.
* `card` *(optional)* Contains one or more brand attributes. These are analogous to {{RCD-DRAFT}} or {{CTIA-BCID}} data, but differ in that they MUST be justified by evidence in the dossier. Because of this strong foundation that interconnects with formal legal identity, they can be used to derive other brand evidence (e.g., an RCD passport) as needed. Individual attributes MUST conform to the VCard standard {{RFC6350}}.
* `goal` *(optional)* A machine-readable, localizable goal code, as described informally by {{ARIES-RFC-0519}}. If present, the dossier MUST prove that the OP is authorized by the AP to initiate calls with this particular goal.
* `call-reason` *(optional)* A human-readable, arbitrary phrase that describes the self-asserted intent of the caller. This claim is largely redundant with `goal`; most calls will either omit both, or choose one or the other. Since `call-reason` cannot be analyzed or verified in any way, and since it may communicate in a human language that is not meaningful to the callee, use of this field is discouraged. However it is not formally deprecated. It is included in VVP to facilitate the construction of derivative RCD passports which have the property (see {{<interoperability}}).
* `evd` *(required)* MUST be the OOBI of a bespoke ACDC (the dossier, {{<dossier}}) that constitutes a verifiable data graph of all evidence justifying belief in the identity and authorization of the AP, the OP, and any relevant delegations. This URL can be hosted on any convenient web server, and is somewhat analogous to the `x5u` header in X509 contexts. See below for details.
* `origId` *(optional)* Follows SHAKEN semantics.
* `iat` *(required)* Follows standard JWT semantics (see {{RFC7519}}).
* `exp` *(required)* Follows standard JWT semantics. As this sets a window for potential replay attacks between the same two phone numbers, a recommended expiration should be 30 seconds, with a minimum of 10 seconds and a maximum of 300 seconds.
* `jti` *(optional)* Follows standard JWT semantics.

For information about the signature over a passport, see {{<pss}}.

## Citing a callee's dossier
Optionally, evidence in VVP can also flow from callee to caller. For privacy reasons, individuals who receive phone calls may choose not to use VVP in this way. However, enterprises and call centers may find it useful as a reassurance to their customers about who they've reached.

In such cases, the callee must have curated a dossier. The format of the callee dossier is identical in schema to that used by a caller. It may therefore introduce evidence of the callee's legal identity, right to use a brand, right to use a TN, delegated authority to a call center proxy or an AI, and so forth. (A callee's dossier might differ in one minor way that doesn't affect the schema: it could prove the right to use a TN that has a DNO flag.)

A reference to the callee's dossier is conveyed by adding a special `a=callee-passport:X` attribute line to the SDP {{RFC8866}} body of the callee's `200 OK` response. (Optionally, the lines MAY also be added to a `180 Ringing` response, to make the callee verifiable earlier, but it MUST appear on the `200 OK` response.) The value of this line is a JWT in compact form, with the `;type=vvp` suffix. This is exactly compliant with the format used by callers to convey VVP passports in `Identity` headers. However, `Identity` headers are not used for callees because existing SIP tooling does not expect or preserve `Identity` headers on responses. Furthermore, the identity of a callee is primarily of interest to the caller, who is willing to parse the SDP body; it does not need the same full-route auditability as the identity of a caller.

Although dossiers are identical in either direction, the callee JWT has a slightly different schema than a caller's VVP passport. The headers of the JWT match, but `kid` contains the OOBI of the callee, not of the OP. Two new claims are added to the JWT payload: `call-id` and `cseq`. These MUST contain the values of the `Call-ID` and `CSeq` values on the preceding SIP INVITE. The `iat` claim MUST also be present and MUST contain a value from the system clock of the callee. The `exp` field MAY also be present and use a value chosen by the callee; if it is missing, this communicates the callee's intention to impose no new timeout logic on the call. The `evd` field MUST also be present, and MUST contain the OOBI of the callee's dossier. The `card` and `goal` claims are also allowed. Other claims MAY be present, but MUST be ignored by compliant implementations that do not understand them. (Because the callee references the specific SIP dialog via `call-id` and `cseq`, there is no point in repeating fields that describe the dialog, like `orig`, `dest`, and so forth.)

# Verifying

## Verifying the caller

### Algorithm
When a verifier encounters a VVP passport, they SHOULD verify by using an algorithm similar to the following. Optimizations may combine or reorder operations, but MUST achieve all of the same guarantees, in order to be compliant implementations.

1. Analyze the `iat` and `exp` claims to evaluate timing. Confirm that `exp` is greater than `iat` and also greater than the reference time for analysis (e.g., *now*), and that `iat` is close enough to the reference time to satisfy the verifier's tolerance for replays. (A replay attack would have to call from the same `orig` to the same `dest` with the same `iat`, within whatever window the verifier accepts. Thirty seconds is a recommended default value.)
1. Confirm that the `orig`, `dest`, and `iat` claims match contextual observations and other SIP metadata. That is, the passport appears aligned with what is known about the call from external sources.
1. Extract the `kid` header.
1. Fetch the key state for the OP at the reference time from the OOBI in `kid`. Caches may be used to optimize this, as long as they meet the freshness requirements of the verifier.
1. Use the public key of the OP to verify that the signature on the passport is valid for that key state. On success, the verifier knows that the OP is at least making an assertion about the identity and authorizations of the AP. (When reference time is now, this is approximately the level of assurance provided by existing alternatives to VVP.)
1. Extract the `evd` field, which references the dossier ({{<dossier}}) that constitutes backing evidence.
1. Use the SAID ({{<said}}) of the dossier as a lookup key to see whether the dossier has already been fully validated. Since dossiers are highly stable, caching dossier validations is recommended.
1. If the dossier requires full validation, perform it. Validation includes checking the signature on each ACDC in the dossier's data graph against the key state of its respective issuer at the time the issuance occurred. Key state is proved by the KEL ({{<KEL}}), and checked against independent witnesses.

    Issuance is recorded explicitly in the KEL's overall event sequence, so this check does not require guesses about how to map issuance timestamps to key state events. Subsequent key rotations do not invalidate this analysis.

    Validation also includes comparing data structure and values against the declared schema, plus a full traversal of all chained CVD ({{<cvd}}), back to the root of trust for each artifact. The verifier MUST accept the root of trust as a valid authority on the vital question answered by each credential that depends upon it. The correct relationships among evidence artifacts MUST also be checked (e.g., proving that the issuer of one piece is the issuee of another piece).

1. Check to see whether the revocation status of the dossier and each item it depends on has been tested recently enough, at the reference time, to satisfy the verifier's freshness requirements. If no, check for revocations anywhere in the data graph of the dossier. Revocations are not the same as key rotations. They can be checked much more quickly than doing a full validation. Revocation checks can also be cached, possibly with a different freshness threshold than the main evidence.
1. Assuming that the dossier is valid and has no breakages due to revocation, confirm that the OP is authorized to sign the passport. If there is no delegation evidence ({{<DE}}), the AP and the OP MUST be identical, and the OP MUST be the issuee of the identity credential; otherwise, the OP MUST be the issuee of a delegated signing credential for which the issuer is the AP.
1. Extract the `orig` field and compare it to the TNAlloc credential ({{<tnalloc-credential}}) cited in the dossier ({{<dossier}}) to confirm that the AP ({{<AP}}) -- or, if OP is not equal to AP and OP is using their own number, the OP ({{<OP}}) -- has the right to originate calls with this number.
1. If the passport includes non-null values for the optional `card` claim, extract that information and check that the brand attributes claimed for the call are justified by a brand credential ({{<brand-credential}}) in the dossier.
1. Check any business logic. For example, if the passport includes a non-null value for the optional `goal` claim, confirm that the verifier is willing to accept a call with that goal. Or, if the delegated signer credential says that the OP can only call on behalf of the AP during certain hours, or in certain geos, check those attributes of the call.

## Verifying the callee

The callee is verified with an algorithm that MAY be optimized but MUST achieve the same security guarantees as this:

1. Confirm that the `call-id` and `cseq` claims match the values of `Call-ID` and `CSeq` from the preceding SIP INVITE.
1. Confirm that the `iat` claim matches contextual observations and other SIP metadata. That is, the timing described by the callee appears aligned with what is known about the call from external sources.
1. If the `exp` claim is present, analyze the `iat` and `exp` claims to evaluate timeout.
1. Extract the `kid` header.
1. Fetch the key state for the callee at the reference time from the OOBI in `kid`. Caches may be used to optimize this, as long as they meet the freshness requirements of the verifier.
1. Use the public key of the callee to verify that the signature on the passport is valid for that key state.
1. Extract the `evd` field, which references the dossier ({{<dossier}}) that constitutes backing evidence.
1. Use the SAID ({{<said}}) of the dossier as a lookup key to see whether the dossier has already been fully validated. Since dossiers are highly stable, caching dossier validations is recommended.
1. Confirm that the dossier was signed (issued) by the same AID that appears in the `kid` header.
1. If the dossier requires full validation, perform it.
1. Check to see whether the revocation status of the dossier and each item it depends on has been tested recently enough, at the reference time, to satisfy the verifier's freshness requirements.
1. Compare the callee's TN to the TNAlloc credential ({{<tnalloc-credential}}) cited in the dossier ({{<dossier}}) to confirm that the callee has the right to accept calls at this number.
1. If the passport includes non-null values for the optional `card` claim, extract that information and check that the brand attributes claimed for the call are justified by a brand credential ({{<brand-credential}}) in the dossier.
1. Check any business logic. For example, if the passport includes a non-null value for the optional `goal` claim, and the preceding INVITE included a VVP passport that also declared a goal, confirm that the callee's and caller's goals overlap (one must be a subset of the other). Or, if the delegated signer credential says that a call center or an AI can accept calls during certain hours, or in certain geos, check those attributes of the call.

## Planning for efficiency
A complete verficiation of either caller or callee passport, from scratch, is quite rigorous. With no caches, it may take several seconds, much like a thorough validation of a certificate chain. However, much VVP evidence is stable for long periods of time and lends itself to caching, subject to the proviso that revocation freshness must be managed wisely. Since the same dossier is used to add assurance to many calls -- perhaps thousands or millions of calls, for busy call centers -- and many dossiers will reference the same issuers and issuees and their associated key states and KELs ({{<KEL}}), caching will produce huge benefits.

Furthermore, because SAIDs and their associated data (including links to other nodes in a data graph) have a tamper-evident relationship, any party can perform validation and compile their results, then share the data with verifiers that want to do less work. Validators like this are not oracles, because consumers of such data need not trust shared results blindly. They can always directly recompute some or all of it from a passport, to catch deception. However, they can do this lazily or occasionally, per their preferred balance of risk/effort.

*In toto*, these characteristics mean that no centralized registry is required in any given ecosystem. Data can be fetched directly from its source, across jurisdictional boundaries. Because it is fetched from its source, it comes with consent. Privacy can be tuned (see {{<privacy}}). Simple opportunistic, uncoordinated reuse (e.g., in or across the datacenters of TSPs) will arise spontaneously and will dramatically improve the scale and efficiency of the system.

## Historical analysis
Normally, a verification algorithm determines whether the passport verifies *now*. (This is the only evaluation that's valid for most JWTs, because they depend on ephemeral key state fetched just in time from `x5u`). However, a VVP passport can do more. Its `kid` header references a KEL for the signer's AID, and its `evd` header references a dossier issued by either the AID of the AP or the AID of the callee. Thence it connects to a KEL (see {{<KEL}}). These data structures provide key state transitions that are timestamped -- both by the controllers of the AIDs, and by their independent witnesses. Although the timestamps are not guaranteed to be perfectly synchronized, they can be compared to establish rough transition times and to detect duplicity.

Using this historical information, it becomes possible to ask whether a VVP passport would have verified at an arbitrary moment in the past. In such framings, the reference time from the verification algorithm is *then*, not *now*. In the normal case where *then* falls outside a fuzzy range, answers about key state are clear to all observers. In the rare cases where *then* falls inside a fuzzy range, a state transition was underway but not yet universally known, and a verifier can compute the key state (and thence, the outcome of the verification algorithm) according to their preferred interpretation.

# Security Considerations
Complying with a specification may forestall certain easy-to-anticipate attacks. However, *it does not mean that vulnerabilities don't exist, or that they won't be exploited*. The overall assurance of VVP requires reasonable vigilance. Given that a major objective of VVP is to ensure security, implementers are strongly counseled to understand the underlying principles, the assumptions, and the ways that choices by their own or other implementations could introduce risk.

Like most cryptographic mechanisms, VVP depends on the foundational assumption that human stakeholders will manage cryptographic keys carefully. VVP enforces this assumption more thoroughly than many existing solutions:

* Parties that issue credentials MUST be identified with AIDs ({{<aid}}) that use witnesses ({{<appendix-b}}). This guarantees a non-repudiable, publicly accessible audit log of how their key state evolves, and it makes key rotation easy. It also offers compromise and duplicity detection. Via prerotation, it enables recovery from key compromise. AIDs can be upgraded to use quantum-proof signing algorithms without changing the identifier.
* Parties that issue credentials MUST do so using ACDCs ({{<acdcs}}) signed by their AID rather than a raw key. This makes evidence revocable. It also makes it stable across key rotation, and prevents retrograde attacks by allowing verifiers to map an issuance or revocation event to an unambiguous key state in the KEL ({{<KEL}}).
* Parties that issue credentials SHOULD employ threshold-based multi-signature schemes. This enhances security by distributing signing authority across multiple key holders, reducing the risk of single-point compromise. Threshold-based signatures ensure that no single key compromise undermines the system’s integrity while enabling controlled key recovery and rotation without disrupting credential validity.

Nonetheless, it is still possible to make choices that weaken the security posture of the ecosystem, including at least the following:

* Sharing keys or controlling access to them carelessly
* Issuing credentials with a flimsy basis for trust
* Delegating authority to untrustworthy parties
* Delegating authority without adequate constraints
* Failing to fully verify evidence

Generally understood best practices in cybersecurity will avoid many of these problems. In addition, the following policies that are specific to VVP are strongly recommended:

1. Passports SHOULD have an aggressive timeout (e.g., 30 seconds). Signatures on passports are not anchored in a KEL, and must therefore be evaluated for age with respect to the time they were received. Overly old passports could be a replay attack (a purported second call with the same orig and dest numbers, using the same backing evidence, soon after the first.)

2. Witnesses (which MUST be used) SHOULD be used in such a way that high availability is guaranteed, and in such a way that duplicity by the controller of an AID is detected. See {{<appendix-b}}. (Verifiers will be able to see the witness policy of each AID controller, and SHOULD decide for themselves whether the party is reliable, depending on what they observe.)

3. Revocations SHOULD be timely, and the timeliness guarantees of issuers SHOULD be published.

4. Watchers SHOULD propagate events to local caches with a low latency, and MUST provide information that allows verifiers to decide whether that latency meets their freshness requirements.

# Privacy

Institutions and individuals that make or receive phone calls as verified parties may have privacy goals. Although their goals might differ in some ways, both will wish to disclose some attributes to the counter party, and both may wish to suppress some of that same information from intermediaries. Both will want control over how this disclosure works.

## Graduated Disclosure
ACDCs support a technique called *graduated disclosure* that enables this.

The hashing algorithm for ACDCs resembles the hashing algorithm for a merkle tree. An ACDC is a hierarchical data structure that can be modeled with nested JSON. Any given layer of the structure may consist of a mixture of simple scalar values and child objects. The input to the hashing function for a layer of content equals the content of scalar fields and the *hashes* of child objects.

<figure>
<name>ACDC hashes like a Merkle tree</name>
<artset>
  <artwork type="svg" name="fig4.svg">
<svg xmlns="http://www.w3.org/2000/svg" version="1.1" height="432" width="408" viewBox="0 0 408 432" class="diagram" text-anchor="middle" font-family="monospace" font-size="13px" stroke-linecap="round">
<path d="M 8,48 L 8,272" fill="none" stroke="black"/>
<path d="M 72,320 L 72,328" fill="none" stroke="black"/>
<path d="M 72,368 L 72,376" fill="none" stroke="black"/>
<path d="M 112,48 L 112,272" fill="none" stroke="black"/>
<path d="M 152,48 L 152,160" fill="none" stroke="black"/>
<path d="M 216,320 L 216,328" fill="none" stroke="black"/>
<path d="M 216,344 L 216,360" fill="none" stroke="black"/>
<path d="M 224,80 L 224,88" fill="none" stroke="black"/>
<path d="M 224,104 L 224,120" fill="none" stroke="black"/>
<path d="M 256,48 L 256,160" fill="none" stroke="black"/>
<path d="M 296,48 L 296,80" fill="none" stroke="black"/>
<path d="M 400,48 L 400,80" fill="none" stroke="black"/>
<path d="M 8,48 L 112,48" fill="none" stroke="black"/>
<path d="M 152,48 L 256,48" fill="none" stroke="black"/>
<path d="M 296,48 L 400,48" fill="none" stroke="black"/>
<path d="M 296,80 L 400,80" fill="none" stroke="black"/>
<path d="M 152,160 L 256,160" fill="none" stroke="black"/>
<path d="M 8,272 L 112,272" fill="none" stroke="black"/>
<path d="M 240,96 C 248.83064,96 256,103.16936 256,112" fill="none" stroke="black"/>
<path class="jump" d="M 224,104 C 218,104 218,88 224,88" fill="none" stroke="black"/><path class="jump" d="M 216,344 C 210,344 210,328 216,328" fill="none" stroke="black"/><g class="text">
<text x="56" y="20">Fully</text>
<text x="208" y="20">Partially</text>
<text x="344" y="20">Fully</text>
<text x="56" y="36">Expanded ACDC</text>
<text x="204" y="36">Compact ACDC</text>
<text x="348" y="36">Compact ACDC</text>
<text x="40" y="68">a = {</text>
<text x="184" y="68">a = {</text>
<text x="348" y="68">a = H(...)</text>
<text x="60" y="84">b = N,</text>
<text x="200" y="84">b = N</text>
<text x="56" y="100">C = {</text>
<text x="200" y="100">c = H</text>
<text x="232" y="100">c</text>
<text x="76" y="116">d = M,</text>
<text x="200" y="116">g = Q</text>
<text x="76" y="132">e = O,</text>
<text x="212" y="132">i = H(i)</text>
<text x="72" y="148">f = P</text>
<text x="168" y="148">}</text>
<text x="44" y="164">},</text>
<text x="60" y="180">g = Q,</text>
<text x="56" y="196">i = {</text>
<text x="76" y="212">j = R,</text>
<text x="72" y="228">k = S</text>
<text x="40" y="244">}</text>
<text x="24" y="260">}</text>
<text x="48" y="308">H(a) = H(</text>
<text x="192" y="308">H(a) = H(</text>
<text x="344" y="308">H(a) = SAID</text>
<text x="48" y="324">b = N</text>
<text x="192" y="324">b = N</text>
<text x="64" y="340">c = H(c),</text>
<text x="192" y="340">c = H</text>
<text x="232" y="340">c),</text>
<text x="72" y="356">recurse</text>
<text x="192" y="356">g = Q</text>
<text x="48" y="372">g = Q</text>
<text x="204" y="372">i = H(i)</text>
<text x="60" y="388">i = H(i)</text>
<text x="188" y="388">) = SAID</text>
<text x="72" y="404">recurse</text>
<text x="44" y="420">) = SAID</text>
</g>
</svg>
  </artwork>
  <artwork type="ascii-art" name="fig4.txt">
<![CDATA[
    Fully            Partially          Fully
Expanded ACDC      Compact ACDC      Compact ACDC
+------------+    +------------+    +------------+
| a = {      |    | a = {      |    | a = H(...) |
|   b = N,   |    |   b = N,   |    +------------+
|   C = {    |    |   c = H(c),|
|     d = M, |    |   g = Q,   |
|     e = O, |    |   i = H(i) |
|     f = P  |    | }          |
|   },       |    +------------+
|   g = Q,   |
|   i = {    |
|     j = R, |
|     k = S  |
|   }        |
| }          |
+------------+

 H(a) = H(         H(a) = H(         H(a) = SAID
   b = N,            b = N,
   c = H(c),         c = H(c),
     recurse         g = Q,
   g = Q,            i = H(i)
   i = H(i)        ) = SAID
     recurse
 ) = SAID
]]>
    </artwork>
  </artset>
</figure>

This means is that any given child JSON object in an ACDC can be replaced with its hash, *without altering the hash of the parent data*. Thus, there can be expanded ACDCs (where all data inside child objects is visible) or compacted ACDCs (where some or all of the child objects are opaquely represented by their equivalent hashes). A signature over an expanded ACDC is also a signature over any of the compacted versions of the same ACDC, and a revocation event over any of the versions is guaranteed to mean the same thing.

In combination with the `evd` claim in a passport, graduated disclosure can be used to achieve privacy goals, because different verifiers can see different variations on an ACDC, each of which is guaranteed to pass the same verification tests and has the same revocation status.

For example, suppose that company X wants to make a call to an individual in jurisdiction Y, and further suppose that auditor Z requires proof that X is operating lawfully, without knowing the name of X as a legal entity. In other words, the auditor needs to *qualify* X but not necessarily *identify* X. Company X can serve the KEL for its dossier from a web server that knows to return the expanded form of the identity credential in the dossier to the individual or the individual's TSP in Y, but a compacted form of the identity credential (revealing just the vetter's identity and their signature, but not the legal identity of the issuee, X) to auditor Z. Later, if law enforcement sees the work of the auditor and demands to know the legal identity of X, discovery of the expanded form can be compelled. When the expanded form is disclosed, it will demonstrably be associated with the compact form that Z recorded, since the qualifying and identifying forms of the ACDC have the same hash.

Company X doesn't have to engage in sophisticated sniffing of traffic by geography to achieve goals like this. It can simply say that anonymous and unsigned HTTP requests for the dossier return the compact form; anyone who wants the expanded form must make an HTTP request that includes in its body a signature over terms and conditions that enforce privacy and make the recipient legally accountable not to reshare.

Importantly, transformations from expanded to compact versions of an ACDC can be performed by anyone, not just the issuer or holder. This means that a verifier can achieve trust on the basis of expanded data, and then cache or share a compacted version of the data, meaning that any subsequent or downstream verifications can have equal assurance but higher privacy. The same policy can be applied to data any time it crosses a regulatory, jurisdictional boundary where terms and conditions for disclosure have weaker enforcement. It can also be used when business relationships should be redacted outside of a privileged context.

Schemas for credentials should be designed to allow graduated disclosure in increments that match likely privacy goals of stakeholders. ACDC schema design typically includes a salty nonce in each increment, avoiding rainbow attacks on the hashed data. VVP encourages but does not require this.

## Correlation
Privacy theorists will note that, even with contractually protected graduated disclosure and maximally compact ACDCs, verifiers can still correlate by using some fields in ephemeral passports or long-lived ACDCs, and that this may undermine some privacy goals.

There are three correlators in each passport:

1. Any brand information in `card` (may strongly identify a VP)
2. the `kid` header (identifies the signer of the passport -- the OP for verified callers, or perhaps a call center or TSP automation for verified callees)
3. the `evd` claim (uniquely identifies a dossier used by a VP)

We discount the first correlator, because if it is present, the VP is explicitly associating its correlated reputation with a call. It has asserted this brand publicly, to every stakeholder in the SIP pipeline. In such cases, any question of the VP's privacy is off the table, and no privacy protections on the other two correlators will be effective. However, if the first correlator is missing, the other two correlators become more interesting.

### kid
In VVP, the passport signer role that's identified by `kid` is played by automation. Automation is unlikely to have any direct privacy goal. Automation is assumed to be operated by a company, and that company is likely to be either a service provider, or a large corporation capable of significant IT investments. Either way, the signer is in the business of servicing phone calls, and is likely to be content for its traffic to be correlated publicly. Therefore, the fact that `kid` correlates the signer is not particularly interesting.

However, could the signer be used as an indirect correlator for the VP?

The signer's SBC can service calls for many thousands or millions of clients, providing a some herd privacy. This is not a perfect protection, but it is a beginning. We add to this the crucial observation that *the signer doesn't need to have a stable reputation to support VVP goals*. Trust in the signer comes from the existence of a delegated signer credential (see {{<delegated-signer-credential}}), not from a certificate or any other long-term identity. Therefore, the AID that provides cryptographic identity for a signer MAY be rotated often (as often as VPs are willing to delegate to a new one). Further, even without rotation, a signing organization MAY provide multiple instances of its automation, each using a different AID. Also, a VP MAY delegate signing authority to multiple signing organizations, each of which is using various strategies to mitigate correlation. Taken together, these measures offers reasonable protection -- protection that a VP can tune -- against correlating a VP via `kid`.

### evd
The other correlator, `evd`, tracks a VP more directly, because a dossier is uniquely identified by its SAID, and can only be used by a single VP. Furthermore, if someone resolves `evd` to an actual dossier (something that might be avoidable with judicious use of graduated disclosure), the dossier will at a minimum have an issuer field that ties it to the VP as a perfect correlator.

One answer here is to introduce a *VP blinding service*. This service creates *derived dossiers* on a schedule or by policy. Each derivation includes the hash of the original dossier, in a field that is hidden but available (along with a salty nonce) via graduated disclosure. The derived dossier is signed by the blinding service rather than the original VP. It embodies an assertion, by the blinding service, that it has verified the original dossier according to published rules, and that it will revoke the derivative if the original is revoked. VP blinding services would have to be trusted by verifiers, much like root CAs in SHAKEN. However, unlike CAs, their actions could be trivially audited for correctness, since every derivation would have to be backed by a dossier that has the associated hash. Such a mechanism is probably unnecessary for b2c calling, but may be justified when VVP is used by individual VPs if they wish to merely qualify without identifying themselves to some intermediaries or callees.

# Appendix A: Evidence theory
{:appendix #appendix-a}

Most existing approaches to secure telephony uses X509 certificates {{RFC5280}} for foundational identity. Certificates have great virtues. Notably, they are well understood, and their tooling is ubiquitous and mature. However, they also have some serious drawbacks. They are protected by a single key whose compromise is difficult to detect. Recovery is cumbersome and slow. As a result, *certificates are far more temporary than the identities they attest*.

This has numerous downstream consequences. When foundational evidence of identity has to be replaced constantly, the resulting ecosystem is fragile, complex, and expensive for all stakeholders. Vulnerabilities abound. Authorizations can only be analyzed in a narrow *now window*, never at arbitrary moments in time. This creates enormous pressure to build a centralized registry, where evidence can be curated once, and where the cost of reacting to revocations is amortized. The entire fabric of evidence has to be rebuilt from scratch if quantum security becomes a requirement.

In contrast, the issuers and holders of ACDCs -- and thus, the stakeholders in VVP passports -- are identified by autonomic identifiers, not raw keys. This introduces numerous security benefits. Keys, key types, and signing algorithms can all change (even for post-quantum upgrades) without invalidating evidence. Signing and rotation operations are sequenced deterministically, making historical audits possible. Key compromises are detected as soon as an attacker attempts consequential actions. Recovery from compromise is trivial. Multisig signing policies allow diffuse, nuanced control.

The result is that *identities in ACDCs are as stable as identities in real organizations*. This makes delegations and chaining mechanisms far more robust than their analogs in certificates, and this in turn makes the whole ecosystem safer, more powerful, and easier to maintain. Revocations are cheap and fast. No central registries are needed, which eliminates privacy concerns and regulatory hurdles. Adoption can be opportunistic; it doesn't require a central mandate or carefully orchestrated consensus throughout a jurisdiction before it can deliver value.

ACDCs make it practical to model nuanced, dynamic delegations such as the one between Organization X and Call Center Y. This eliminates the gap that alternative approaches leave between accountable party and the provider of call evidence. Given X's formal approval, Y can sign a call on behalf of X, using a number allocated to X, and using X's brand, without impersonating X. They can also prove to any OSP or any other party, in any jurisdiction, that they have the right to do so. Furthermore, the evidence that Y cites can be built and maintained by X and Y, doesn't get stale or require periodic reissuance, and doesn't need to be published in a central registry.

Even better, when such evidence is filtered through suballocations or crosses jurisdictional boundaries, it can be reused, or linked and transformed, without altering its robustness or efficiency. Unlike W3C verifiable credentials and SD-JWTs, which require direct trust in the proximate issuer, ACDCs and the JWTs that reference them verify data back to a root through arbitrarily long and complex chains of issuers, with only the root needing to be known and trusted by the verifier.

The synergies of these properties mean that ACDCs can be permanent, flexible, robust, and low-maintenance. In VVP, no third party has to guess who's accountable for an outbound call or who's answering an inbound call; that party is transparently and provably accountable, period. (Yet notwithstanding this transparency, ACDCs support a form of pseudonymity and graduated disclosure that satisfies vital privacy and data processing constraints. See {{<privacy}}.)

# Appendix B: Witnesses and Watchers
{:appendix #appendix-b}

A full description of witnesses and watchers is available in {{TOIP-KERI}}. Here, we merely summarize.

A KERI *witness* is a lightweight server that acts as a notary. It exposes a standard interface. It receives signed events from the controller of an identifier that it services. If these events are properly sequenced and aligned with the identifier's signing policy and key state, they are recorded and become queryable, typically by the public. KERI allows the controller of an autonomic identifier to choose zero or more witnesses. The witnesses can change over the lifecycle of the identifier. However, the relationship between an identifier and its witnesses cannot be changed arbitrarily; the controller of the identifier makes a cryptographic commitment to its witnesses, and can only change that commitment by satisfying the signing policy of the identifier. In VVP, identifiers used by issuers MUST have at least one witness, because this guarantees viral discoverability, and SHOULD have at least 3 witnesses, because this guarantees both high availability and the detection of duplicity by the controller of the identifier.

Witnesses provide, for VVP, many of the security guarantees that alternate designs seek from blockchains. However, witnesses are far more lightweight than blockchains. They can be run by anyone, without coordination or approval, and can be located in any jurisdiction that the owner of the identifier prefers, satisfying regulatory requirements about data locality. Although a single witness may service mulptiple identifiers, the records related to any single identifier are independent, and no consensus algorithm is required to order them relative to others. Thus, every identifier's data evolves in parallel, without bottlenecks, and any identifier can be deleted without affecting the integrity of other identifiers' records, satisfying regulatory requirements about erasure. Witnesses only store (and thus, can only expose to the public) what a given data controller has instructed them to retain and publish. Thus, witnesses do not create difficulties with consent or privacy.

In VVP, when a party shares an identifier or a piece of evidence, they do so via a special URL called an OOBI (out of band invitation). The OOBI serves a tamper-evident KEL ({{<KEL}}) that reveals the full, provable history of the key state and other witnesses for the identifier, and even includes a forward reference to new witnesses, if they have changed. It also allows the discovery of issuance and revocation events, and their sequence relative to one another and to key state changes.

An additional and optional feature in KERI is enabled by adding *watchers*. Watchers are lightweight services that synthesize witness data. They MAY monitor multiple witnesses and enable hyper-efficient caching. They SHOULD also compare what multiple witnesses for a given identifier are saying, which prevents controllers of an identifier from forking reality in a duplicitous way, and which can detect malicious attempts to use stolen keys.

Witnesses are chosen according to the preference of each party that controls an identifier, and a mature ecosystem could have dozens, hundreds, or thousands. Watchers, on the other hand, address the needs of verifiers, because they distill some or all of the complexity in an ecosystem down to a single endpoint that verifiers can query. Any verifier can operate a watcher at any time, without any coordination or approval. Viral discoverability can automatically populate the watcher's cache, and keep it up-to-date as witness data evolves.

Verifiers can share watchers if they prefer. Anything that watchers assert must be independently verified by consulting witnesses, so watchers need not have a complete picture of the world, and they are a convenience rather than an oracle that must be trusted. The data that watchers synthesize is deliberately published by witnesses for public consumption, at the request of each data stream's associated data controllers, and does not represent surveillance ({{<privacy}}). If a watcher can no longer find witness data to back one of its assertions, it MUST delete the data to satisfy its contract. This means that acts of erasure on witnesses propagate to watchers, again satisfying regulatory erasure requirements.

# Appendix C: Sample Credentials
{:appendix #appendix-c}

## Common fields
Some structure is common to all ACDCs. For details, consult {{TOIP-ACDC}}. Here, we provide a short summary.

* `v` *(required)* Contains a version statement.
* `d` *(required)* Contains the SAID ({{<said}}) of the ACDC. (Nested `d` fields contain SAIDs of nested JSON objects, as discussed in {{<graduated-disclosure}}.)
* `i` *(required)* In the outermost structure, contains the AID ({{<aid}}) of an issuer. Inside `a`, contains the AID of the issuee.
* `ri` *(optional)* Identifies a registry that tracks revocations that might include one for this credential.
* `s` *(required)* Contains the SAID of a schema to which the associated ACDC conforms.
* `a` *(required)* Contains additional attributes for this specific ACDC, as allowed by its schema.
* `dt` *(optional)* Contains the date when the issuer claims to have issued the ACDC. This data will correspond closely with a timestamp saved in the issuer's KEL, at the point where the signature on the ACDC was signed and anchored there. The ordering of the signature in the KEL, relative to other key state events, is what is definitive here; the timestamp itself should be viewed more as a hint.
* `e` *(optional)* Contains edges that connect this ACDC to other data upon which it depends.
* `r` *(optional)* Contains one or more rules that govern the use of the ACDC. Holding the credential requires a cryptographically nonrepudiable `admit` action with a wallet, and therefore proves that the holder agreed to these terms and conditions.

All ACDCs are validated against a schema that conforms to {{JSON-SCHEMA}}. Below we show some sample credentials and their corresponding schemas. VVP does not require these specific schemas, but rather is compatible with any that have roughly the same information content.

## Identity credential {#id-cred-sample}
The schema of a identity credential ({{<identity-credential}}) can be very simple; it needs to identify the issuer and issuee by AID, and it needs to identify the vetted legal entity in at least one way that is unambiguous. Here is a sample LE vLEI that meets these requirements. The issuer's AID appears in the first `i` field, the issuee in the second `i` field, and the connection to a vetted legal entity in the `LEI` field. (The validity of this credential depends on its issuer having a valid, unrevoked QVI credential; the specifc credential it links to is conveyed in `e`. The full text of rules has been elided to keep the example short.)

~~~json
{
  "v":"ACDC10JSON0005c8_",
  "d":"Ebyg1epjv7D4-6mvl44Nlde1hTyL8413LZbY-mz60yI9",
  "i":"Ed88Jn6CnWpNbSYz6vp9DOSpJH2_Di5MSwWTf1l34JJm",
  "ri":"Ekfi58Jiv-NVqr6GOrxgxzhrE5RsDaH4QNwv9rCyZCwZ",
  "s":"ENPXp1vQzRF6JwIuS-mp2U8Uf1MoADoP_GqQ62VsDZWY",
  "a":{
    "d":"EdjPlxlRyujxarfXHCwFAqSV-yr0XrTE3m3XdFaS6U3K",
    "i":"Eeu5zT9ChsawBt2UXdU3kPIf9_lFqT5S9Q3yLZvKVfN6",
    "dt":"2024-09-19T13:48:21.779000+00:00",
    "LEI":"9845006A4378DFB4ED29"
  },
  "e":{
    "d":"EeyVJC9yZKpbIC-LcDhmlS8YhrjD4VIUBZUOibohGXit",
    "qvi":{
      "n":"EmatUqz_u9BizxwOc3JishC4MyXfiWzQadDpgCBA6X9n",
      "s":"EBfdlu8R27Fbx-ehrqwImnK-8Cm79sqbAQ4MmvEAYqao"
    }
  },
  "r":{
    "d":"EgZ97EjPSINR-O-KHDN_uw4fdrTxeuRXrqT5ZHHQJujQ",
    "usageDisclaimer":{
      "l":"Usage of a valid...fulfilled."
    },
    "issuanceDisclaimer":{
      "l":"All information...Governance Framework."
    }
  }
}
~~~

The schema that governs this credential, `ENPX...DZWY`, is shown in the `s` field. LE vLEI credential schemas are managed by GLEIF and published at {{LE-VLEI-SCHEMA}}.

An alternate schema for vetting credentials -- one that incurs less effort to perform vetting and achieve quality goals, and that offers correspondingly lower levels of assurance, is published at {{ORG-VET-SCHEMA}}.

As fundamentally public artifacts that are issued only to organizations, most vetting credentials will not be designed for graduated disclosure ({{<graduated-disclosure}}). Vetting credentials for individuals would require a different schema -- perhaps one that documents their full legal name but allows disclosure strategies such as first name + last initial, or first initial plus last name.

## TNAlloc credential {#tn-cred-sample}
A TNAlloc credential needs to identify its issuer and issuee. If and only if it isn't issued by a national regulator that acts as a root of trust on allocation questions, it also needs to cite an upstream allocation that justifies the issuer's right to pass along a subset of the numbers it controls.

Here is a sample TNAlloc credential that meets these requirements.

~~~json
{
  "v": "ACDC10JSON0003cd_",
  "d": "EEeg55Yr01gDyCScFUaE2QgzC7IOjQRpX2sTckFZp1RP",
  "u": "0AC8kpfo-uHQvxkuGZdlSjGy",
  "i": "EANghOmfYKURt3rufd9JNzQDw_7sQFxnDlIew4C3YCnM",
  "ri": "EDoSO5PEPLsstDr_XXa8aHAf0YKfPlJQcxZvkpMSzQDB",
  "s": "EFvnoHDY7I-kaBBeKlbDbkjG4BaI0nKLGadxBdjMGgSQ",
  "a": {
      "d": "ECFFejktQA0ThTqLtAUTmW46unVGf28I_arbBFnIwnWB",
      "u": "0ADSLntzn8x8eNU6PhUF26hk",
      "i": "EERawEn-XgvmDR_-2ESVUVC6pW-rkqBkxMTsL36HosAz",
      "dt": "2024-12-20T20:40:57.888000+00:00",
      "numbers": {
          "rangeStart": "+33801361002",
          "rangeEnd": "+33801361009"
      },
      "channel": "voice",
      "doNotOriginate": false
  },
  "e": {
      "d": "EI9qlgiDbMeJ7JTZTJfVanUFAoa0TMz281loi63nCSAH",
      "tnalloc": {
          "n": "EG16t8CpJROovnGpgEW1_pLxH5nSBs1xQCbRexINYJgz",
          "s": "EFvnoHDY7I-kaBBeKlbDbkjG4BaI0nKLGadxBdjMGgSQ",
          "o": "I2I"
      }
  },
  "r": {
      "d": "EJFhpp0uU7D7PKooYM5QIO1hhPKTjHE18sR4Dn0GFscR",
      "perBrand": "Issuees agree not to share..."
  }
}
~~~

The schema used by this particular credential, `EFvn...GgSQ`, is published at {{TN-ALLOC-SCHEMA}}.

## Brand credential {#bcred-sample}
A brand credential ({{<brand-credential}}) is essentially a signed attestation of properties that are otherwise communicated without proof in a VCard ({{RFC6350}}). These characteristics, such as a brand name and a logo, MUST be ones that the issuee of the credential -- the VP (see {{<VP}}) -- is legally entitled to use, either because they are the legal entity that owns the relevant trademarks or associated IP, or because they have licensed them from the legal owner.

An example schema is published at {{BRAND-SCHEMA}}. It is simple; besides some boilerplate, the core is an array of items in the `vcard` field, each of which represents one entry from a VCard. The `goal` field is also notable, in that it constrains the activities that the issuee can engage in while using the brand. A sample is: TODO

~~~json
~~~

## Brand proxy credential {#bprox-cred-sample}
A brand proxy credential ({{<brand-proxy-credential}}) is very similar to a delegated signer credential, in that it proves carefully constrained delegated authority. The difference lies in what authority is delegated (proxy a brand vs. sign passports).

A Generalized Cooperative Delegation (GCD) credential embodies delegated but constrained authority in exactly this way. A GCD credential suitable for use as a brand proxy in VVP might look like this:

~~~json
{
    "v": "ACDC10JSON00096c_",
    "d": "EWQpU3nrKyJBgUJGw5461CbWcug9BZj7WXUkKbNOlnFx",
    "u": "0ADE6oAxBl4E7uKeGUb7BEYi",
    "i": "EC4SuEyzrRwu3FWFrK0Ubd9xejlo5bUwAtGcbBGUk2nL",
    "ri": "EM2YZ78SKE8eO4W1lQOJeer5xKZqLmJV7SPr3Ji5DMBZ",
    "s": "EL7irIKYJL9Io0hhKSGWI4OznhwC7qgJG5Qf4aEs6j0o",
    "a": {
        "d": "EPQhEk5tfXvxyKe5Hk4DG63dSgoP-F2VZrxuIeIKrT9B",
        "u": "0AC9kH8q99PTCQNteGyI-F4g",
        "i": "EIkxoE8eYnPLCydPcyc_lhQgwOdBHwzkSe36e2gqEH-5",
        "dt": "2024-12-27T13:11:29.062000+00:00",
        "c_goal": ["ops.telco.*.proxybrand"],
        "c_proto": ["VVP:OP,callee"]
    },
    "r": {
        "d": "EFthNcTE20MLMaCOoXlSmNtdooGEbZF8uGmO5G85eMSF",
        "noRoleSemanticsWithoutGfw": "All parties agree...",
        "issuerNotResponsibleOutsideConstraints": "Although verifiers...",
        "noConstraintSansPrefix": "Issuers agree...",
        "useStdIfPossible": "Issuers agree...",
        "onlyDelegateHeldAuthority": "Issuers agree..."
    }
}
~~~

Note the `c_goal` field that limits goals that can be justified with this credential, and the `c_proto` field that says the delegate can only exercise this authority in the context of the "VVP" protocol with the "OP" or "callee" role. The wildcard in `c_goal` and the addition of the "callee" role in `c_proto` are complementary changes that allow this credential to justify proxying the brand on both outbound and inbound calls. (To convert this credential to a purely outbound authorization, replace the wildcard with `send`, and limit the roles in `VVP` to `OP`.)

The schema for GCD credentials, and an explanation how to add additional constraints, is documented at {{GCD-SCHEMA}}.

## Delegated signer credential {#dsig-cred-sample}
A delegated signer credential ({{<delegated-signer-credential}}) must prove that the issuer is giving authority to the issuee. This authority should be carefully constrained so that it applies only to outbound voice calls, not to signing invoices or legal contracts. It can also be constrained so it only applies on a particular schedule, or when the call originates or terminates in a particular geo or jurisdiction.

A Generalized Cooperative Delegation (GCD) credential embodies delegated but constrained authority in exactly this way. A GCD credential suitable for use as a delegated signer credential in VVP might look like this:

~~~json
{
    "v": "ACDC10JSON00096c_",
    "d": "EDQpU3nrKyJBgUJGw5461CbWcug9BZj7WXUkKbNOlnFR",
    "u": "0ADE6oAxBl4E7uKeGUb7BEYi",
    "i": "EC4SuEyzrRwu3FWFrK0Ubd9xejlo5bUwAtGcbBGUk2nL",
    "ri": "EM2YZ78SKE8eO4W1lQOJeer5xKZqLmJV7SPr3Ji5DMBZ",
    "s": "EL7irIKYJL9Io0hhKSGWI4OznhwC7qgJG5Qf4aEs6j0o",
    "a": {
        "d": "EPQhEk5tfXvxyKe5Hk4DG63dSgoP-F2VZrxuIeIKrT9B",
        "u": "0AC9kH8q99PTCQNteGyI-F4g",
        "i": "EIkxoE8eYnPLCydPcyc_lhQgwOdBHwzkSe36e2gqEH-5",
        "dt": "2024-12-27T13:11:29.062000+00:00",
        "c_goal": ["ops.telco.send.sign"],
        "c_proto": ["VVP:OP"]
    },
    "r": {
        "d": "EFthNcTE20MLMaCOoXlSmNtdooGEbZF8uGmO5G85eMSF",
        "noRoleSemanticsWithoutGfw": "All parties agree...",
        "issuerNotResponsibleOutsideConstraints": "Although verifiers...",
        "noConstraintSansPrefix": "Issuers agree...",
        "useStdIfPossible": "Issuers agree...",
        "onlyDelegateHeldAuthority": "Issuers agree..."
    }
}
~~~

Note the `c_goal` field that limits goals that can be justified with this credential, and the `c_proto` field that says the delegate can only exercise this authority in the context of the "VVP" protocol with the "OP" role.

The schema for GCD credentials, and an explanation how to add additional constraints, is documented at {{GCD-SCHEMA}}.

## Dossier
A dossier ({{<dossier}}) contains little direct data of its own. It consists almost entirely of edges -- that is, links to other credentials. Here's what one might look like:

~~~json
{
  "v": "ACDC10JSON00036f_",
  "d": "EKvpcshjgjzdCWwR4q9VnlsUwPgfWzmy9ojMpTSzNcEr",
  "i": "EIkxoE8eYnPLCydPcyc_lhQgwOdBHwzkSe36e2gqEH-5",
  "ri": "EMU5wN33VsrJKlGCwk2ts_IJi67IXE6vrYV3v9Xdxw3p",
  "s": "EFv3_L64_xNhOGQkaAHQTI-lzQYDvlaHcuZbuOTuDBXj",
  "a": {
    "d": "EJnMhz8MJxmI0epkq7D1zzP5pGTbSb2YxkSdczNfcHQM",
    "dt": "2024-12-27T13:11:41.865000+00:00"
  },
  "e": {
    "d": "EPVc2ktYnZQOwNs34lO1YXFOkT51lzaILFEMXNfZbGrh",
    "vetting": {
      "n": "EIpaOx1NJc0N_Oj5xzWhFQp6EpB847yTex62xQ7uuSQL",
      "s": "ENPXp1vQzRF6JwIuS-mp2U8Uf1MoADoP_GqQ62VsDZWY",
      "o": "NI2I"
    },
    "alloc": {
      "n": "EEeg55Yr01gDyCScFUaE2QgzC7IOjQRpX2sTckFZp1RP",
      "s": "EFvnoHDY7I-kaBBeKlbDbkjG4BaI0nKLGadxBdjMGgSQ",
      "o": "I2I"
    },
    "brand": {
      "n": "EKSZT4yTtsZ2AqriNKBvS7GjmsU3X1t-S3c69pHceIXW",
      "s": "EaWmoHDYbkjG4BaI0nK7I-kaBBeKlbDLGadxBdSQjMGg",
      "o": "I2I"
    },
    "bproxy": {
      "n": "EWQpU3nrKyJBgUJGw5461CbWcug9BZj7WXUkKbNOlnFx",
      "s": "EL7irIKYJL9Io0hhKSGWI4OznhwC7qgJG5Qf4aEs6j0o",
      "o": "I2I"
    },
    "delsig": {
      "n": "EMKcp1-AvpW0PZdThjK3JCbMsXAmrqB9ONa1vZyTppQE",
      "s": "EL7irIKYJL9Io0hhKSGWI4OznhwC7qgJG5Qf4aEs6j0o",
      "o": "NI2I"
    }
  }
}
~~~

Notice how each named edge references one of the previous sample credentials in its `n` field, and that other credential's associated schema in the `s` field.

The schema for this credential is documented at {{DOSSIER-SCHEMA}}.

# IANA Considerations

This document defines a new SDP {{RFC8866}} session-level attribute:

   Attribute name:      callee-passport
   Long-form description: Contains a STIR-compatible passport that references a dossier of evidence about the callee's identity, brand, and related attributes. Used in 200 OK and/or 180 Ringing responses.
   Type of attribute:   session-level
   Subject to charset:  No
   Reference:           This document

This specification also depends on OOBIs (see {{<aid}}) being served as web resources with IANA content type `application/json+cesr`.

--- back

# Acknowledgments
{:numbered="false"}

Much of the cybersecurity infrastructure used by VVP depends on KERI, which was invented by Sam Smith, and first implemented by Sam plus Phil Fairheller, Kevin Griffin, and other technical staff at GLEIF. Thanks to logistical support from Trust Over IP and the Linux Foundation, and to a diverse community of technical experts in those communities and in the Web of Trust group.

Techniques that apply KERI to telco use cases were developed by Daniel Hardman, Randy Warshaw, and Ruth Choueka, with additional contributions from Dmitrii Tychinin, Yaroslav Lazarev, Arshdeep Singh, and many other staff members at Provenant, Inc. Thanks as well to Ed Eykholt for multiple editorial improvements.
