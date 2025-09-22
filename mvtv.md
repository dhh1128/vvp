# Making Voice Traffic Verifiable

This document provides supporting theory, rationale, and implementation guidance for the Verifiable Voice Protocol (VVP). The formal protocol specification is defined in a separate document.

## Introduction
VVP solves problems with existing mechanisms by applying three crucial innovations in evidence.

### Evidence scope
Existing solutions aim to assert variable levels of confidence about a caller's identity, plus possibly some brand attributes. These assertions rest entirely on a service provider's judgment and are testable only in the moment a call is initiated; later, they become repudiable.

VVP proves more. It always proves the legal identity of whoever presents evidence, plus any authority that they have delegated to staff and service providers. It typically also proves brand attributes and right to use a phone number. If a call center and/or an AI is involved, it proves the constraints under which that entity operates as a representative. Depending on how it is used, VVP can thus achieve very high levels of assurance about a broad range of facts related to callers, callees, or both.

All VVP proof is traceable back to justifying evidence and can be evaluated in the present or the past. This guarantees accountability for all parties with a permanent, non-repudiable audit trail.

### Evidence format
VVP is rooted in an evidence format called *authentic chained data containers* (*ACDC*s) -- see the [Authentic Chained Data Containers (ACDC) specification](https://trustoverip.github.io/tswg-acdc-specification/). Other forms of evidence (e.g., JWTs/STIR PASSporTs, digital signatures, and optional interoperable inputs from W3C [verifiable credentials](W3C.REC-vc-data-model-20220303) and [SD-JWTs](I-D.ietf-oauth-selective-disclosure-jwt)) also contribute. However, the foundation that VVP places beneath them is unique. For a discussion of the theory behind VVP evidence, see [Appendix A: Evidence theory](#appendix-a-evidence-theory).

Because of innovations in format, VVP evidence is easier to create and maintain, safer, and more flexible than alternative approaches. It also lasts much longer. This drastically lowers the costs of adoption.

### Vetting refinements
Although VVP interoperates with governance frameworks such as SHAKEN ([ATIS-1000074](https://atis.org/resources/signature-based-handling-of-asserted-information-using-tokens-shaken-atis-1000074-e/)), it allows for a dramatic upgrade of at least one core component: the foundational vetting mechanism. The evidence format used by VVP is also the format used by the Verifiable Legal Entity Identifier (vLEI) standardized in [ISO-17442-3](https://www.iso.org/standard/85628.html). vLEIs implement a KYC approach advocated by the G20's Financial Stability Board, and overseen by the G20's Regulatory Oversight Committee. This approach follows LEI rules for KYC ([ISO-17442-1](https://www.iso.org/standard/78829.html)), and today it's globally required in high-security, high-regulation, cross-border banking.

Millions of institutions have already undergone LEI vetting, and they already use the resulting evidence of their organizational identity in day-to-day behaviors all over the world. By adopting tooling that's compatible with the vLEI ecosystem, VVP gives adopters an intriguing option: *just skip the task of inventing a whole new vetting regime unique to telco, with its corresponding learning curve, costs, and legal and business adoption challenges.*

To be clear, VVP does not *require* that vLEIs be used for vetting. However, by choosing an evidence format that is high-precision and lossless enough to accommodate vLEIs, VVP lets telco ecosystems opt in, either wholly or partially, to trust bases that are already adopted, and that are not limited to any particular jurisdiction or to the telco industry. It thus offers two-way, easy bridges between identity in phone calls and identity in financial, legal, technical, logistic, regulatory, web, email, and social media contexts.

# Curating
The evidence that's available in today's telco ecosystems resembles some of the evidence described here, in concept. However, existing evidence has gaps, and its format is fragile. It is controlled by keys having a short lifespan, and thus churns steadily. It requires direct trust in the proximate issuer, and it typically needs to be organized for discovery; both characteristics lead to large, centralized registries at a regional or national level. These registries become a trusted third party, which defeats some of the purpose of creating decentralized and independently verifiable evidence in the first place. Sharing such evidence across jurisdiction boundaries requires regulatory compatibility and bilateral agreements. Sharing at scale is impractical at best, if not illegal.

How evidence is issued, propagated, quality-controlled, and referenced is therefore an important concern for this specification.

## Activities

The following curation activities guarantee the evidence upon which a VVP ecosystem depends.

### Witnessing and watching
In an ACDC-based ecosystem, issuers issue and revoke their own evidence without any calls to a centralized registry or authority. However, KERI's decentralized witness feature MUST be active. This provides an official, uniform, and high-security methodology for curating the relationship between keys and identifiers, and between identifiers and non-repudiable actions like issuing and revoking credentials. In addition, watchers MAY be used by given verifiers, to provide efficient caching, pub-sub notifications of state changes, and duplicity detection. For more about these topics, see {{<appendix-b}}.

### Vetting identity
Entities that SHOULD be vetted in a VVP ecosystem include APs {{<AP}}, but also OPs {{<OP}} and callees {{<TP}}, depending on which identities need to be verified. The job of vetting legal entities and issuing vetting credentials ({{<vetting-credential}}) is performed by a *legal entity vetter*. VVP MUST have evidence of vetted identity. It places few requirements on such vetters, other than the ones already listed for vetting credentials themselves. Vetting credentials MAY expire, but this is not particularly desirable and might actually be an antipattern. ACDCs and AIDs facilitate much longer lifecycles than certificates; proactive key rotation is recommended but creates no reason to rotate evidence. However, a legal entity vetter MUST agree to revoke vetting credentials in a timely manner if the legal status of an entity changes, or if data in a vetting credential becomes invalid.

### Vetting brand
At the option of the verified entities, VVP MAY prove brand attributes. When this feature is active, the job of analyzing the brand assets of a legal entity and issuing brand credentials ({{<brand-credential}}) is performed by a *brand vetter*. A brand vetter MAY be a legal entity vetter, and MAY issue both types of credentials after a composite analysis. However, the credentials themselves MUST NOT use a combined schema, the credentials SHOULD have independent lifecycles. This allows the assurances associated with each credential type to remain independent.

A brand vetter MUST verify the canonical properties of a brand, but it MUST do more than this: it MUST issue the brand credential to the AID {{<aid}} of an issuee that is also the issuee of a vetting credential that already exists, and it MUST verify that the legal entity in the vetting credential has a right to use the brand in question. This link MUST NOT be based on mere weak evidence such as an observation that the legal entity's name and the brand name have some or all words in common, or the fact that a single person requested both credentials. Further, the brand vetter MUST agree to revoke brand credentials in a timely manner if the associated vetting credential is revoked, if the legal entity's right to use the brand changes, or if characteristics of the brand evolve.

### Allocating TNs
At the option of the AP and OP, VVP SHOULD prove the right to use the originating phone number. At the option of the callee, VVP MAY prove the right to use the terminating phone number. When this feature is active, regulators MUST issue TNAlloc credentials ({{<tnalloc-credential}}) to range holders, and range holders MUST issue them to downstream AHs in an unbroken chain that reaches telephone number users (TNUs; see {{<allocation-holder}}). TNUs MAY in turn issue them to a delegate such as a call center. If aggregators or other intemediaries hold an RTU in the eyes of a regulator, then intermediate TNAlloc credentials MUST be created to track that RTU as part of the chain. On the other hand, if TNUs acquire phone numbers through aggregators, but regulators do not consider aggregators to hold allocations, then aggregators MUST work with range holders to assure that the appropriate TNAlloc credentials are issued to the TNUs.

### Authorizing brand proxy
When VVP is used to prove brand, VPs ({{<VP}}) MAY issue brand proxy credentials ({{<brand-proxy-credential}}) to delegates, giving them the right to use the VP's brand. Without this credential, the delegate has the right to use the phone number, not the brand.

Decisions about whether to issue vetting and brand credentials might be driven by large databases of metadata about organizations and brands, but how such systems work is out of scope. The credentials themselves contain all necessary information, and once credentials are issued, they constitute an independent source of truth as far as VVP is concerned. No party has to return to the operators of such databases to validate anything.

### Delegating signing authority
A VP ({{<VP}}) MUST prove, by issuing a delegated signer credential ({{<delegated-signer-credential}}), that the signer of its VVP passports does so with its explicit authorization. Normally the signer is automation under the control of the delegate, but the issuee of the credential MAY vary at the VP's discretion.

Since this credential merely documents the issuer's intent to be accountable for the actions of the signer, the VP MAY choose whatever process it likes to issue it.

### Revoking
Revoking an ACDC is as simple as the issuer signing a revocation event and distributing it to witnesses (see {{<appendix-b}}). Parties that perform a full validation of a given ACDC (see {{<verifying}}) will automatically detect the revocation event in realtime, because they will contact one or more of these witnesses. Parties that are caching their validations MAY poll witnesses very efficiently to discover revocation events. Some witnesses may choose to offer the option of registering a callback, allowing interested parties to learn about revocations even more efficiently.

