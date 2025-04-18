---
title: "Data Governance in Data Wallets"
date: 2025-03-14
permalink: /2025/02/14/wallet-governance/
status: Draft
---

![](/cookie.webp)

We are about to create another cookie problem :cookie: - with Digital Credentials in Data Wallets.

My previous article on [Data Wallets](/2025/02/14/data-wallets/) discussed what Verifiable Credentials were - and where they fit into regulatory frameworks such as eIDAS in Europe and the proposed Digital Verification Scheme (DVS) in the UK. 

Such credentials can contain sensitive personal information, that often requires the *verifier* to establish a legal basis upon which they can process the data - such as user consent. Within the [W3C Verifiable Credentials Specification](https://www.w3.org/TR/vc-data-model-2.0/) this is recognized, and a [`termsOfUse`](https://www.w3.org/TR/vc-data-model-2.0/#terms-of-use) entry is supported to support in precisely describing the *permissions* (e.g. Service Personalization) for which data may be used, what usage of data within the credential is *prohibited* (e.g. Marketing) and any *obligations* that must be met when using the data (e.g. report any 3rd parties this data is shared with). The formal language often used to describe these *permissions*, *prohibitions* and *obligations* is known as the [Open Digital Rights Language (ODRL)](https://www.w3.org/TR/odrl-model/#rule).

However, without the legal infrastructure to recognize the inclusion of this [`termsOfUse`](https://www.w3.org/TR/vc-data-model-2.0/#terms-of-use) entry as a valid way of *creating* a legal basis for data processing - such as being a valid way of proving consent; this entry is relegated to merely being a descriptor of the basis' for processing that have already been established. How are these bases' established? Likely, the mechanism that we know and love - a pop-up consent box, every time you use the credential<sup id="fnref1"><a href="#fn1">1</a></sup>!

As I discussed in [my previous article](https://blog.jeswr.org/2025/02/14/data-wallets#datauseandaccessbill) the [Digital Verification Scheme](https://www.gov.uk/guidance/digital-identity) is proposed within the UK's [Data (use and access) Bill](https://bills.parliament.uk/bills/3825/). The DVS provides a mechanism for the Secretary of State to create a list of certified service providers to provide services related to credential issuance, management and verification.

The [Digital Identity and Attributes Framework (DIATF)](https://www.gov.uk/government/collections/uk-digital-identity-and-attributes-trust-framework) is a framework that explicitly describes the different types of service providers that can be implemented under the DVS - including technical roles and responsibilities.

If we are specifically talking about the [Digital Identity and Attributes Framework (DIATF)](https://www.gov.uk/government/collections/uk-digital-identity-and-attributes-trust-framework) in the UK, it could take the form of terms of use term within [Verifiable Credentials](https://www.w3.org/TR/vc-data-model-2.0/#terms-of-use). Specifically in the context of DIATF what regulators could do is state that when a Verifiable Credential is sent from a Holder:
1. The Holder is legally obliged to use pre-defined user preferences or ask directly from the user, the privacy terms they wish to apply to the data. These would likely be described as a set of permissions, obligations, and prohibitions within an [ODRL Rule](https://www.w3.org/TR/odrl-model/#rule)
2. The service receiving the data is legally obliged to adhere to the stated privacy preferences.

In most cases - the rules would largely enumerate the [DPV Purposes](https://w3c.github.io/dpv/2.0/dpv/) for which the user consents their data to be used.

<div class="footnotes">
  <hr/>
  <ol>
    <li id="fn1">This is a little exaggerated since data processing for <a href="https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/lawful-basis/legitimate-interests/what-is-the-legitimate-interests-basis/">legitimate interests</a> does not require such a flow. <a href="#fnref1">↩</a></li>
  </ol>
</div>
