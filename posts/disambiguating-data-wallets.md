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

What is special about the letters and numbers in these two files, is that a [special mathematical function](https://cryptobook.nakov.com/digital-signatures/rsa-signatures) can be used to combine the private key and the hash to generate a *signature* like this one:

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

The *verifier* can use different mathematical function to convert a signature into a hash. If that hash, is the same as the hash of my DPhil Award Credential, then they know that the award *must* have been signed by the private key that the *issuer* (Oxford) created.

#### Selective disclosure

![](../static/document.svg)

Many headlines surrounding digital credentials - such as [this UK press release](https://www.gov.uk/government/news/pubgoers-given-choice-to-prove-age-with-phones-next-year-in-boost-for-high-street-and-hospitality-sectors) - promise the ability to "prove your age without revealing any other information."

To enable this, some Verifiable Credentials are built with the capacity to perform Selective Disclosure. In short, this allows you to take a Verifiable Credential containing lots of information, such as [this Resident Card credential](https://www.w3.org/TR/vc-data-model-2.0/#example-verifiable-credential-using-the-data-integrity-bbs-cryptosuite-with-a-base-proof) - and forward only part of the information, such as your `birthDate` to the *verifier*, whilst enabling the *verifier* to confirm that the date of birth was contained in a validly signed Verifiable Credential.

### Standards Wars

Well that all makes sense ... so what on earth is there to dispute? Quite a bit as it turns out!

Now this is a battle that we have seen played out *many* time historically. Past [format wars](https://en.wikipedia.org/wiki/Format_war#:~:text=A%20format%20war%20is%20a,recording%20formats%20for%20electronic%20media.) include [VHS vs. BetaMax](https://en.wikipedia.org/wiki/Videotape_format_war), [Blu-Ray vs. HD DVD](https://en.wikipedia.org/wiki/HD_DVD#:~:text=Much%20like%20the%20videotape%20format,format%2C%20Blu%2Dray%20Disc.), and, if we dare venture back to the 1800's wars over the [size of the rail gauge](https://en.wikipedia.org/wiki/Track_gauge) and [type of electrical current](https://en.wikipedia.org/wiki/War_of_the_currents) we should use.

So - what different formats are there? How do they compare?

### A push for alignment

The [Open Wallet Foundation](https://openwallet.foundation), hosted by the [Linux Foundation](https://www.linuxfoundation.org) has a mission to facilitate global interoperability of verifiable credentials.

![](../static/openwallet.png)

## Regulation Driving Data Wallets

### eIDAS

Inlude discussion of eIDAS popularit

![](../static/eidas.png)

### DUAB

![](../static/govuk.png)

### Whatever is happening in Australia

![](../static/auswallet.jpg)

 - https://www.qld.gov.au/transport/projects/digital-licence/about


## Options for holders

## Why Solid as a Holder should be taken seriously

![](../static/solid.svg)

### What is Solid

[Solid](https://solidproject.org) is a standard for data storage on the Web - primarily created to allow *individuals* to store their personal data *separately* from websites. This enables re-use of data across platforms, and better control over consent management. Solid is now becoming an official W3C Standard under the [Linked Web Storage Working Group](https://www.w3.org/groups/wg/lws/).

Solid has three key features: [Solid-OIDC](https://solidproject.org/TR/oidc) enabling Single Sign On similar to the way we "Sign in with Google", , and [access controls](https://solidproject.org/TR/protocol#auxiliary-resources-web-access-control) so users can manage *who* can read and write data to their Pod.

### The Disclaimer

Now let me be upfront about the bias here. I work with Solid - *a lot*. 

I [lead work](https://theodi.org/profile/jesse-wright/) on Solid at the [Open Data Institute](https://theodi.org) which [stewards](https://theodi.org/news-and-events/news/odi-and-solid-come-together-to-give-individuals-greater-control-over-personal-data/) all opensource work on the Solid Project, am a [Doctoral Student](https://www.cs.ox.ac.uk/people/jesse.wright/) in the [Ethical Web and Data Architectures (EWADA)](https://ewada.ox.ac.uk) Group at the [University of Oxford](https://www.ox.ac.uk), independently contribute to [opensource projects](https://github.com/jeswr) for Solid technologies, and formerly worked as an Enterprise Software Engineer at [Inrupt](https://www.inrupt.com) - a commercial implementor of Solid.

### Solid as a Credential Holder

## Queryability of Verifiable Credentials

![](../static/sparql.webp)

Let me again present my bias' upfront. The last 5 years of my work and research have revolved around [Semantic Web Technologies](https://en.wikipedia.org/wiki/Semantic_Web) - and my current research is on the very topic of [Queryable Credentials](https://github.com/jeswr/queryable-credentials).

[^1]: Trust me - Software Engineers will think about becoming a farmer at least once a day.
[^2]: ^^ Yes, really.
