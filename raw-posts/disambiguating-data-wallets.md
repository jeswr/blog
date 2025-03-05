---
title: "Disambiguating Data Wallets"
date: 2025-02-14
permalink: /2025/02/14/data-wallets/
status: Draft
---

Data wallets are becoming popular, as this happens the term is becoming increasingly *overloaded* and *confused*. This post is a digestable disambgiuation :ramen: of the standards :card_index:, regulation :black_nib:, implementors :screwdriver:, and other players :raising_hand: in the space.

## The Standards

As an engineer, I like to start by talking about the technology and standards behind data wallets. From there, we can point to which standards that regulators do - or don't - choose.

Don't worry - the tech is *not hard to understand*. As you'll soon see the confusion comes from having many players who want **their solution** to win out.

### The goal

![](../static/vc.webp)
*Credit: [dock.io](https://www.dock.io/post/verifiable-credentials)*

The common goal of data wallets is to allow you to prove that a *someone* said *something* - for instance that the *University of Oxford* says that you earned a DPhil in Computer Science, or that *TicketMaster* says they issued you with a valid ticked for tonights Taylor Swift concert. 

To do this the *someone* (which we will now call an *issuer*) gives you, or more specifically an application on your device like Google Wallet (which we will call the *holder*) a digital Verifiable Credential. Examples include the [UK digital drivers license](https://www.gov.uk/government/news/digital-driving-licence-coming-this-year) :credit_card: and [Digital Student Certificates](https://athumi.be/en/blog/news/athumi-and-itsme-launch-groundbreaking-digital-student-certificate-first-implemented-by-dibbs-en-be).

This digital credential can then be forwarded to someone else (which we call a *verifier*) - such as an employer who wants to confirm that you have a valid Doctorate. Et. :sparkles:voila:sparkles: you now have that dream job [growing cherry tomatoes](https://engineerdog.com/2023/05/29/why-do-so-many-programmers-want-to-be-farmers-how-to-build-a-corrugated-steel-garden-box/)[^1].

### The tech

<!-- TODO: Insert the diagram -->

Now I said the tech wasn't that hard - so let's take a look at what is going on under the hood of these credentials.

Here is an example using *one* of the credential standards, specifically [W3C Verifiable Credentials](https://www.w3.org/TR/vc-data-model-2.0/) - we'll come to the rest later. In this example, I have been issued with a "DPhil in Computer Science" from the University of Oxford.

```json
{
  "@context": "https://www.w3.org/ns/credentials/v2",
  "id": "http://www.ox.ac.uk/credentials/58473",
  "type": ["VerifiableCredential", "DPhilAwardCredential"],
  "issuer": "http://www.ox.ac.uk/",
  "credentialSubject": {
    "id": "https://www.jeswr.org/#me",
    "awarded": {
      "id": "http://www.cs.ox.ac.uk/awards/DPhil",
      "name": "DPhil in Computer Science"
    }
  }
}
```
*A [JSON-LD](https://json-ld.org) representation of a [W3C Verifiable Credential](https://www.w3.org/TR/vc-data-model-2.0/) for a DPhil Award*

But there is one problem, *I just made this up*. So how is this supposed to be useful in my job application to become a farm hand.[^2]

<!-- TODO: Survey whether this section helps or adds confusion -->

Well, what would help is for Oxford to *digitally sign* this credential.

The concept of digital signatures has existed for *decades* and whether you're aware of it or not - is already in many parts of your digital life, including being the backbone of the HTTPS security. More recently, if you've found yourself using passkeys to log into websites lately - then you've been using digital signatures to *sign* a message saying "I own this account", please let me in!

![](../static/passkey.jpg)

#### Signatures

So how do these signatures actually work? 

First, a *hash* of the the digital credential document is created - and is a unique fingerprint :feet: for the document. For the DPhil Award Credential, this is what the hash looks like:

```
4sSXDN7iEw2niW96vPWNPJVeiwWe6VR77jl+wRnA6bk=
```

You can try generating it for yourself [here](https://emn178.github.io/online-tools/sha256.html?input=%7B%0A%20%20%22%40context%22%3A%20%22https%3A%2F%2Fwww.w3.org%2Fns%2Fcredentials%2Fv2%22%2C%0A%20%20%22id%22%3A%20%22http%3A%2F%2Fwww.ox.ac.uk%2Fcredentials%2F58473%22%2C%0A%20%20%22type%22%3A%20%5B%22VerifiableCredential%22%2C%20%22DPhilAwardCredential%22%5D%2C%0A%20%20%22issuer%22%3A%20%22http%3A%2F%2Fwww.ox.ac.uk%2F%22%2C%0A%20%20%22credentialSubject%22%3A%20%7B%0A%20%20%20%20%22id%22%3A%20%22https%3A%2F%2Fwww.jeswr.org%2F%23me%22%2C%0A%20%20%20%20%22awarded%22%3A%20%7B%0A%20%20%20%20%20%20%22id%22%3A%20%22http%3A%2F%2Fwww.cs.ox.ac.uk%2Fawards%2FDPhil%22%2C%0A%20%20%20%20%20%20%22name%22%3A%20%22DPhil%20in%20Computer%20Science%22%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D&input_type=utf-8&output_type=base64&hmac_enabled=0&hmac_input_type=utf-8). It is not important for this article to understand *how* this hash is generated, but if you're curious - [look here](https://blog.boot.dev/cryptography/how-sha-2-works-step-by-step-sha-256/#how-does-the-sha-256-algorithm-work).

The *issuer* (i.e. Oxford) then *signs* this hash using something called public-private key cryptography. The way this works is that the *issuer* uses some [mathemagic](https://en.wikipedia.org/wiki/Public-key_cryptography) to generate a pair of files - one of which is called a **public key**, and the other which is called a **private key**. Below are real examples of these files:
```
-----BEGIN RSA PRIVATE KEY-----
MIIBOgIBAAJBAKj34GkxFhD90vcNLYLInFEX6Ppy1tPf9Cnzj4p4WGeKLs1Pt8Qu
KUpRKfFLfRYC9AIKjbJTWit+CqvjWYzvQwECAwEAAQJAIJLixBy2qpFoS4DSmoEm
o3qGy0t6z09AIJtH+5OeRV1be+N4cDYJKffGzDa88vQENZiRm0GRq6a+HPGQMd2k
TQIhAKMSvzIBnni7ot/OSie2TmJLY4SwTQAevXysE2RbFDYdAiEBCUEaRQnMnbp7
9mxDXDf6AU0cN/RPBjb9qSHDcWZHGzUCIG2Es59z8ugGrDY+pxLQnwfotadxd+Uy
v/Ow5T0q5gIJAiEAyS4RaI9YG8EWx/2w0T67ZUVAw8eOMB6BIUg0Xcu+3okCIBOs
/5OiPgoTdSy7bcF9IGpSE8ZgGKzgYQVZeN97YE00
-----END RSA PRIVATE KEY-----
```

```
-----BEGIN RSA PUBLIC KEY-----
MEgCQQCo9+BpMRYQ/dL3DS2CyJxRF+j6ctbT3/Qp84+KeFhnii7NT7fELilKUSnx
S30WAvQCCo2yU1orfgqr41mM70MBAgMBAAE=
-----END RSA PUBLIC KEY-----
```

What is special about the letters and numbers in these two files, is that a [mathematical function](https://cryptobook.nakov.com/digital-signatures/rsa-signatures) can be used to combine the private key and the hash to generate a *signature* like this one:

```
z58DAdFfa9SkqZMVPxAQp...jQCrfFPP2oumHKtz
```

The *issuer* keeps the private key a secret so that no-one can forge the signature. The *issuer* (Oxford) also tells *everyone* about their public key, for instance, by putting it on their website. Putting this all together, we add the following information to the DPhil Award Credential:

```json
{
  ...
  "proof": {
    ...
    "verificationMethod": "http://www.ox.ac.uk/pubkey",
    "proofValue": "z58DAdFfa9SkqZMVPxAQp...jQCrfFPP2oumHKtz"
  }
}
```

How does this help the *verifier* (my prospective farming employer) confirm that my DPhil Award Credential was *actually* stated by the *issuer* (Oxford)?

The *verifier* can use different mathematical function to convert a signature and public key into a hash. If that hash, is the same as the hash of my DPhil Award Credential, then they know that the award *must* have been signed by the private key that the *issuer* (Oxford) created.

#### Selective disclosure

![](../static/document.svg)

Many headlines surrounding digital credentials - such as [this UK press release](https://www.gov.uk/government/news/pubgoers-given-choice-to-prove-age-with-phones-next-year-in-boost-for-high-street-and-hospitality-sectors) - promise the ability to "prove your age without revealing any other information."

To enable this, some Verifiable Credentials are built with the capacity to perform Selective Disclosure. In short, this allows you to take a Verifiable Credential containing lots of information, such as [this Resident Card credential](https://www.w3.org/TR/vc-data-model-2.0/#example-verifiable-credential-using-the-data-integrity-bbs-cryptosuite-with-a-base-proof) - and forward only part of the information, such as your `birthDate` to the *verifier*, whilst enabling the *verifier* to confirm that the date of birth was contained in a validly signed Verifiable Credential.

### Standards Wars

Well that all makes sense ... so what on earth is there to dispute? Quite a bit as it turns out!

Broadly speaking the debate is around:
 - What the *format* of the information inside the digital credential should be
 - How the *hash* of the digital credential should be created, and
 - What mathematical function should be used for creatiing the signature


Include discussion fo JSON-LD vs. CBOR


These are the kinds of battles that that we have seen played out *many* time historically. Past [format wars](https://en.wikipedia.org/wiki/Format_war#:~:text=A%20format%20war%20is%20a,recording%20formats%20for%20electronic%20media.) include [VHS vs. BetaMax](https://en.wikipedia.org/wiki/Videotape_format_war), [Blu-Ray vs. HD DVD](https://en.wikipedia.org/wiki/HD_DVD#:~:text=Much%20like%20the%20videotape%20format,format%2C%20Blu%2Dray%20Disc.), and, if we dare venture back to the 1800's - wars over the [size of the rail gauge](https://en.wikipedia.org/wiki/Track_gauge) and [type of electrical current](https://en.wikipedia.org/wiki/War_of_the_currents) we should use.

So - what different formats are there? How do they compare?

W3C Timeline:
```mermaid
timeline
  %% Aug 
  2014: [__W3C__<br/> Credentials Community Group](https://www.w3.org/community/credentials/) is chartered
  %% Apr 
  2017: [__W3C__<br/> Verifiable Credentials Working Group](https://www.w3.org/2017/vc/WG/charter.html#history) is chartered
  %% May 2017
  : [__W3C__<br/> Credentials Community Group](https://www.w3.org/community/credentials/) creates the final [Verifiable Claims Data Model and Representations 1.0](https://www.w3.org/2017/05/vc-data-model/CGFR/2017-05-01/) report
  %% Jan 
  %% 2020: [__W3C__<br/> Verifiable Credentials Working Group](https://www.w3.org/2020/01/vc-wg-charter.html) is renewed
  2019: [__W3C__<br/> Verifiable Credentials Working Group](https://www.w3.org/2020/01/vc-wg-charter.html) publishes [Verifiable Credentials Data Model 1.0](https://www.w3.org/TR/2019/REC-vc-data-model-20191119/)
  %% Sep 
  2021: [__ISO__<br/> Mobile driving licence (mDL)](https://www.iso.org/standard/69084.html) standard published
  : [__OPENID__<br/> produces the first working group draft of OpenID Connect for Verifiable Presentations (OIDC4VP)](https://openid.net/specs/openid-4-verifiable-presentations-1_0.html)
  %% Feb 
  2023: [__ISO__<br/> Cards and security devices for personal identification ](https://www.iso.org/standard/74910.html) standard published
  %% Oct 2023
  : [__IETF__<br/> Web Authorization Protocol Working Group](https://datatracker.ietf.org/wg/oauth/about/) publishes [SD-JWT-based Verifiable Credentials](https://www.ietf.org/archive/id/draft-ietf-oauth-sd-jwt-vc-01.html)
  %% Feb 
  2024: [__W3C__<br/> Verifiable Credentials Working Group](https://www.w3.org/2020/01/vc-wg-charter.html) creates [Verifiable Credentials Data Model v2.0 candidate recommendation](https://www.w3.org/TR/2024/CR-vc-data-model-2.0-20240201/)
  %% Oct 2024
  : [__W3C__<br/> Verifiable Credentials Working Group](https://www.w3.org/2020/01/vc-wg-charter.html) creates new charter
  %% Jan 
  2025: [__W3C__<br/> Verifiable Credentials for Education Task Force](https://w3c-ccg.github.io/vc-ed/charter/) begins to create charter
```

"Late 2022: International adoption plans emerge. The European Digital Identity Wallet Architecture and Reference Framework (ARF) draft (by the EU’s eIDAS expert group) lists OID4VP, OID4VCI, and SIOPv2 as required protocols for certain digital identity use cases ￼."


Cards and security devices for personal
identification — Building blocks for identity
management via mobile devices

ISO Timeline:
 - 

Note the following from the 2020 WG Charter

Internet Engineering Task Force
The Working Group will seek security review from the IETF, coordinated through the Liaison.

Decentralized Identity Foundation Interoperability Working Group
To coordinate on broad horizontal review and integration of the specifications developed by the Working Group into the Decentralized Identity Foundation's ecosystem.

European Telecommunications Standards Institute - Electronic Signatures and Infrastructure Technical Committee
To coordinate in ensuring that eIDAS-compliant systems can be built on top of the specifications developed by the Working Group.

ISO/IEC JTC 1/SC 17/WG 10
Ensure that the mobile driving licenses being modeled and expressed by the ISO SC17 WG10 community are compatible with the work of the Verifiable Credentials WG.

ISO/IEC JTC 1/SC 17/WG 4
Ensure that the 23220-2 data model expressed by the ISO SC17 WG4 community is compatible with the work of the Verifiable Credentials WG.



Other W3C Notables:
 - [Jan 2025 - W3C Verifiable Credentials for Education Task Force](https://w3c-ccg.github.io/vc-ed/charter/) begins work on chartering


 - W3C
   - VC 2.0
 - ISO
   - mDL (ISO/IEC 18013-5:2021)
    - To achieve
this, the mDL contains age attestation identifiers. An age attestation identifier has the format age_over_
NN where NN is a value from 00 to 99. The value of an age attestation identifier can be TRUE or FALSE.
   - MDL *does specify some transmission mechanisms, e.g., via NFC, BLE/GATT, WIFI Aware and QR code*
   - ISO/IEC touches upon *many* layers of the networking stack; e.g. touching upon discussion of which TLS method required.
   - ISO/IEC DTS 23220-4:
     - Defines largely domain specific attributes
     - Also has the ability to include biometric information
     - Also *repeats* information from the mDL specification; e.g., for age attestation

 - IETF
   - https://www.ietf.org/archive/id/draft-ietf-oauth-sd-jwt-vc-03.html
  - OpenID
    - OIDC4VP
    - OIDC4VCI
    - 

OpenID4VCI:
 - https://openid.net/specs/openid-4-verifiable-credential-issuance-1_0.html
 - 


SIOPv2:
 - https://openid.net/specs/openid-connect-self-issued-v2-1_0.html



In fact, multiple alternatives exist for credential data formats (e.g. ISO mDL and W3C), protocols (e.g. OpenID for Verifiable Credentials, DIDComm and ISO mDL), wallets, and verifiable data registries.


https://www.ietf.org/archive/id/draft-ietf-oauth-sd-jwt-vc-03.html

... and then there is OpenID4VP (https://openid.net/specs/openid-4-verifiable-credential-issuance-1_0.html) which supports all(?) of them
https://openid.net/specs/openid4vc-high-assurance-interoperability-profile-sd-jwt-vc-1_0-00.html

https://openid.net/wg/digital-credentials-protocols/charter/

### The (big) missing piece

Websites for instance need HTML to tell you how a Website is displayed - but also need HTTP(S) to tell your browser *where* that website document is, and how to get it.

### A push for alignment

The [Open Wallet Foundation](https://openwallet.foundation), hosted by the [Linux Foundation](https://www.linuxfoundation.org) has a mission to facilitate global interoperability of verifiable credentials.

![](../static/openwallet.png)

## Regulation Driving Data Wallets

### eIDAS

Inlude discussion of eIDAS popularit

Qualified Electronic Attestation of Attributes (QEAA)

(Q)EAA schema providers publish schemas and vocabularies describing (Q)EAA structure and semantics

PID = Personal Identification Data | A set of data enabling the identity of a natural person to be established.

[Architecture and Reference Framework](https://digital-strategy.ec.europa.eu/en/library/european-digital-identity-wallet-architecture-and-reference-framework)

"Note that Flows 3 and 4 from section 6.4 mandarte the ability to transfer credentials over the internet"

6.5.1

**Ideally this means a very small number of technical solutions to limit complexity**

Last page points to main relevant specs

[GitHub of Reference Framework](https://eu-digital-identity-wallet.github.io/eudi-doc-architecture-and-reference-framework/1.1.0/arf/#4114-qualified-and-non-qualified-electronic-attestation-of-attributes-schema-providers)

Note that 

![](../static/eidas.png)

https://www.criipto.com/blog/verifiable-credentials-vs-iso-18013-5#:~:text=The%20Verifiable%20Credential%20Data%20Model,%2C%20financial%20transactions%2C%20and%20more.
"""
The upcoming European Digital Identity (EUDI) wallet will support use cases across sectors like education, social security, financial transactions, and more. The wallet will leverage the VC Data Model, and its Architecture and Reference Framework explicitly mentions the W3C and ISO standards as part of its vision for a unified digital identity ecosystem.
"""

### Data (Use and Access) Bill

The [Data Use and Access Bill](https://bills.parliament.uk/bills/3825/) is proposed legislation currently at committee stage in the House of Commons. One mandate of the bill is to create a Digital Verification Services Trust Framework - driven by the Secretary of State maintaining a register of *service providers* accredited to provide some "digital verification services" in the UK. 

The [Digital Identity and Attributes Framework (DIATF)](https://www.gov.uk/government/publications/uk-digital-identity-and-attributes-trust-framework-04)

![](../static/daub.jpg)

Source: https://enablingdigitalidentity.blog.gov.uk/2024/10/28/what-the-data-bill-means-for-digital-identity/

### UK Digital Driver's License

![](../static/govuk.png)

At the time 

### Whatever is happening in Australia

![](../static/auswallet.jpg)

 - https://www.qld.gov.au/transport/projects/digital-licence/about


## Options for holders

## Why Solid as a Holder Service should be taken seriously

![](../static/solid.svg)

### What is Solid

[Solid](https://solidproject.org) is a standard for data storage on the Web - primarily created to allow *individuals* to store their personal data *separately* from websites. This enables re-use of data across platforms, and better control over consent management. Solid is now becoming an official W3C Standard under the [Linked Web Storage Working Group](https://www.w3.org/groups/wg/lws/).

Solid has three key features: [Solid-OIDC](https://solidproject.org/TR/oidc) enabling Single Sign On similar to the way we "Sign in with Google", a [standard HTTP interface](https://solidproject.org/TR/protocol#storage-resource) for applications to read and write data to a Personal Online Datastore (Pod), and [access controls](https://solidproject.org/TR/protocol#auxiliary-resources-web-access-control) so users can manage *who* can read and write data to their Pod.

### The Disclaimer

Now let me be upfront about the bias here. I work with Solid - *a lot*. 

I [lead work](https://theodi.org/profile/jesse-wright/) on Solid at the [Open Data Institute](https://theodi.org) which [stewards](https://theodi.org/news-and-events/news/odi-and-solid-come-together-to-give-individuals-greater-control-over-personal-data/) all opensource work on the Solid Project, am a [Doctoral Student](https://www.cs.ox.ac.uk/people/jesse.wright/) in the [Ethical Web and Data Architectures (EWADA)](https://ewada.ox.ac.uk) Group at the [University of Oxford](https://www.ox.ac.uk), independently contribute to [opensource projects](https://github.com/jeswr) for Solid technologies, and formerly worked as an Enterprise Software Engineer at [Inrupt](https://www.inrupt.com) - a commercial implementor of Solid.

### Solid as a Credential Holder

I am of the view that the Solid Pods are ideal for use as *holder services* in the verifiable credential ecosystem, it is certainly *possible* as a [Solid Wallet](https://github.com/openwallet-foundation-labs/solid-data-wallet) has already been donated to the [Open Wallet Foundation](https://openwallet.foundation) demonstrating how this can be implemented.


The advantages of using Solid as a Holder service are as follows:

<!-- Solid specification is ideally placed to act as a *holder

In direct relation to Solid/LWS, we recommended that it should be possible for holder storages and holder applications to be distinct services, this would allow implementations of the Solid/LWS specification to be certified against the framework without necessarily needing to be the implementor of the user-facing application for managing consent of the credentials. -->

#### Portability of credentials

![](../static/simondseconoart-small.png)

[Socially Aware Cloud Storage, Design Issues, Tim Berners-Lee](https://www.w3.org/DesignIssues/CloudStorage.html)

We've become accustomed to living in a world of [data silo's](https://www.w3.org/DesignIssues/CloudStorage.html) - so much so that we barely notice it anymore. On most websites we find ourselves entering and re-entering the same basic mobile, email and date-of-birth to every website that we visit; and we find ourselves reconstructing the same set of contacts across Instagram, Facebook, Twitter, LinkedIn, Whatsapp, the list goes on ...

Solid was created to solve this problem, providing a standard way of reading and writing data to personal cloud storage. The way it works is simple: when you log in to a Solid-compatible website with Single Sign On - all the personal data that you create gets saved to the store - and are made accessible to any other Solid-compatible applications that you use the second you hit "consent for data usage." Much easier!

The existing Apple Wallet gives us a pretty good sense of the current trajectory for digital wallets and credentials, which is:
 - I buy a GWR train ticket on my [GWR App](https://www.gwr.com/your-tickets/smart-tickets/mobile-app),
 - I click *add to my Apple Wallet*

Easy! But what if I:
 - Bought the ticket with a PC, and saved it to Google Wallet instead? or,
 - Your phone dies, and you want to access the ticket from a friends phone?

Then life is going to be a lot more difficult, because companies such as Apple want to keep these tickets closed within their ecosystem - just as they don't want your contacts or photo's to leave their ecosystem.

![](../static/apple-wallet.png)

The good news :tada: is that the Solid specification can be used here too - so we have a chance to intervene before this even becomes a problem.

#### Standard Web interface for transferring credentials

There are a *lot* of ways that credentials can be transferred. 

#### Standard Web interface for requesting access to credentials

Important Questions to answer:
 - Why don't we just use DCQL to fetch the credentials "Digital Credentials Query Language (DCQL) as an alternative, simpler mechanism to request specific credentials, alongside the existing Presentation Exchange format."
 - 

## Queryability of Verifiable Credentials

![](../static/sparql.webp)

Let me again present my bias' upfront. The last 5 years of my work and research have revolved around [Semantic Web Technologies](https://en.wikipedia.org/wiki/Semantic_Web) - and my current research is on the very topic of [Queryable Credentials](https://github.com/jeswr/queryable-credentials), and I recently [gave a talk on this topic at FOSDEM](https://fosdem.org/2025/schedule/event/fosdem-2025-5970-are-current-standards-enough-towards-verifiable-credentials-with-expressive-zero-knowledge-query/) (video below).

So when I heard that there was a [Digital Credentials Query Language (DCQL)](https://openid.net/specs/openid-4-verifiable-presentations-1_0.html#name-digital-credentials-query-l) as part of the [OID4VP](https://openid.net/sg/openid4vc/) specification I was thrilled - but sadly that was short-lived. This is because the expressivity of DQCL is largely restricted to filtering operations to determine:
 - Which Verifiable Credentials to include as part of a [Verifiable Presentation](https://www.w3.org/TR/vc-data-model-2.0/#presentations)
 - Which subset of attributes to from those Credentials to include in the Verifiable Presentation

Ok, but surely there must be a little more capability to the current specifications than this - after all, it is promised that you can prove your age without revealing your date of birth when using digital drivers licenses - so there must be some way of querying for age ...

... right?

**Wrong**. Taking a deeper look at the [ISO Mobile driving license (mDL)](https://www.iso.org/standard/69084.html) reveals that the **issuer** (e.g. the DVLA) has to *explicitly sign statements* about your age; so my digital drivers license might look something like this:

```json
{
  ...
  age: "00-00-2000",
  is_over_18: true,
  is_over_21: true,
  is_over_65: false,
  ...
}
```

This means that:
 - I have to tell the issuer (DVLA) that I want to prove I'm over 18 - when this isn't something they need to know.
 - I am *reliant* on the *issuer* (DVLA) to issue these statements - so if my driving authority doesn't want to issue `is_over_21` statements; I may be forced to reveal my age. Whilst this is less problematic - and less likely - in the case of age; it is an issue when trying to any *non-standard* derivation. For example, proving non-caucasian ethnicity, without revealaing the minority population that you belong to.
 - I cannot tell the verifier (e.g. my future employer at the tomato farm) about information that can be derived from multiple credentials. Want to prove to a car hire agency that you can drive in the UK without giving them details from your license, visa and passport; then you're out of luck! 

This is a far cry from the kind of derivations that can be performed using the [semantic reasoning and query engines](https://rubenverborgh.github.io/Semantic-Web-Reasoning/). The good news is that it is technically feasible for the *holder* (you) to do these kinds of derivations and then hand them to the *verifier* - that's what the [below talk](https://video.fosdem.org/2025/aw1126/fosdem-2025-5970-are-current-standards-enough-towards-verifiable-credentials-with-expressive-zero-knowledge-query.mp4) is about. The bigger challenge is now to get the technology production ready and standardised.

<video controls>
  <source src="https://video.fosdem.org/2025/aw1126/fosdem-2025-5970-are-current-standards-enough-towards-verifiable-credentials-with-expressive-zero-knowledge-query.mp4" type="video/mp4">
</video>

## Further Reading

In producing this article I came across a number of useful materials, here is my top selection for further reading:
 - [Auth0's take on Verifable Credentials](https://auth0.com/blog/our-take-on-verifiable-credentials/)
 - [Verifiable Credentials and ISO/IEC 18013-5 Based Credentials](https://collateral-library-production.s3.amazonaws.com/uploads/asset_file/attachment/36416/CS676613_-_Digital_Credentials_promotion_campaign-White_Paper_R3.pdf)
 - [Verifiable Credential Formats in the EUDI Wallet: W3C VC DM and ISO 18013-5 mDL/mDoc](https://www.linkedin.com/pulse/verifiable-credential-formats-eudi-wallet-w3c-vc-dm-iso-18013-5-kbcmf/)

[^1]: Trust me - Software Engineers will think about becoming a farmer at least once a day.
[^2]: ^^ Yes, really.
