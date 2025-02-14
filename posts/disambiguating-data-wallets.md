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

The common goal of data wallets is to allow you to prove that a . 

These are called digital credentials, examples include the [UK digital drivers license](https://www.gov.uk/government/news/digital-driving-licence-coming-this-year) :credit_card: and [Digital Student Certificates](https://athumi.be/en/blog/news/athumi-and-itsme-launch-groundbreaking-digital-student-certificate-first-implemented-by-dibbs-en-be).

### The tech

Now I said the tech wasn't that hard - to prove that let's take a look at what is going on under the hood of these credentials.

<!-- All data wallet standards have the same common goal.  -->

### Standards Bodies

Most of these technologies 

### A push for alignment

The [Open Wallet Foundation](https://openwallet.foundation), hosted by the [Linux Foundation](https://www.linuxfoundation.org) has a mission to facilitate global interoperability of verifiable credentials.

![](../static/openwallet.png)

## Regulation Driving Data Wallets

### eIDAS

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


