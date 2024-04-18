---
title: "Reclaiming data autonomy: The role of Solid in a safer Web"
date: 2024-02-06
permalink: /blog/2024/02/06/role-of-solid/
---

**This article was originally for the Oxford University department of Computer Science as part of the [DPhil the future](https://www.cs.ox.ac.uk/news/2287-full.html) series.**
ic online world.**  

The modern Web has seen a significant erosion of data privacy and control. User-generated data, stored in [centralised data silos](https://www.w3.org/DesignIssues/CloudStorage.html), is often used without the knowledge or control of the individuals it belongs to.

> In the age of AI and Big Data, this lack of data autonomy becomes increasingly detrimental to both individuals and society.  DPhil student Jesse Wright

A striking example is a recent [lawsuit](https://www.nytimes.com/2023/10/24/technology/states-lawsuit-children-instagram-facebook.html) against Meta by U.S. states, alleging the unlawful collection of minors' personal data without parental consent and exposing them to harmful content. This is but a glimpse into the dangers posed by emerging technologies such as [personal AI agents](https://ruben.verborgh.org/blog/2013/01/31/what-web-agents-want/) if they are not designed to “legally, ethically and algorithmically” work for you and with data you control ([Charlie works for Bob](https://www.w3.org/DesignIssues/Charlie.html), Berners-Lee 2023).

**Celebrating Safer Internet Day**  

Today, we celebrate the 20th anniversary of [Safer Internet Day](https://www.saferinternetday.org/about), with a theme that resonates deeply with our current digital challenges: “_Inspiring change? Making a difference, managing influence and navigating change online._” This aligns with the mission of the [The Ethical Web and Data Architectures](https://ewada.ox.ac.uk/) (EWADA) programme funded by the [Oxford Martin School](https://www.oxfordmartin.ox.ac.uk/). EWADA aims to address the concentration of power on the World Wide Web by developing new technical and legal infrastructures. 

**Solid Project - A Beacon of Hope** 

In the context of data autonomy, EWADA is putting a spotlight on Sir Tim Berners-Lee’s [_Solid_ project](http://emansour.com/research/lusail/solid_protocols.pdf) which was created with the aim of revitalising the Web. Where the current system of centralised data silos creates an ecosystem of limited integration, availability and innovation, Solid brings a course correction for the Web. Based on the [_separation of data and applications_](https://solidlabresearch.github.io/WhatsInAPod/), the vision defines an ecosystem that facilitates the integration of data in different applications, while keeping people in direct control of their data. 

**Understanding Solid Pods** 

At Solid's core is the ‘pod’ - a personal online data store. Utilising the [Linked Data Platform (LDP)](https://www.w3.org/TR/ldp/), pods offer an HTTP interface for access-controlled storage of documents to a [personal server](https://communitysolidserver.github.io/CommunitySolidServer/latest/usage/starting-server/) or [trusted cloud storage](https://www.inrupt.com/blog/data-decoupling-and-cloud-services-a-new-way-to-ensure-data-privacy). Coupled with [OAuth](https://auth0.com/intro-to-iam/what-is-oauth-2) - the same protocol we use every day for [SSO login](https://www.ox.ac.uk/students/selfservice) - this system facilitates a global single sign-on across all Solid-compliant web applications.

Together, these pods form a decentralised Solid ecosystem, from which applications can directly integrate data from people’s Solid pods, after receiving their permission. Solid applications are encouraged to store data using the [RDF](https://www.w3.org/RDF/) data model of the [Semantic Web](https://www.w3.org/DesignIssues/Semantic.html) (I strongly recommend reading the [design issue](https://www.w3.org/DesignIssues/Semantic.html) if you’ve not heard of it before) - and serialised in a syntax such as JSON-LD or [Turtle](https://www.inrupt.com/videos/readable-turtle). By having applications read/write data with explicit [semantics](https://en.wikipedia.org/wiki/Semantic_Web) rather than using the typical smorgasbord of JSON, GraphQL and other platform-specific API’s [that modern Web developers are accustomed to](https://www.datasciencecentral.com/why-json-users-should-learn-turtle/) it becomes possible for applications to re-use one another's data. 

Such applications include [BBC Together](https://www.bbc.co.uk/together), [itsme](https://www.itsme-id.com/), [Umai](https://umai.noeldemartin.com/), [Solid Focus](https://noeldemartin.github.io/solid-focus/), [KNoodle](https://github.com/KNowledgeOnWebScale/knoodle) and [SolidFlix,](https://github.com/OxfordHCC/solid-media/) which was developed here at Oxford. 

To learn more about the anatomy of a _pod_ - see [What is a Solid Pod](https://www.inrupt.com/videos/what-is-a-solid-pod)? 

**Benefits and Future of Solid Architecture** 

In 2009, Berners-Lee [enumerated a number of benefits to this architecture which remain relevant to this day](https://www.w3.org/DesignIssues/CloudStorage.html) (these come from his [design issues;](https://www.w3.org/DesignIssues/) if you’ve never come across these it’s definitely worth a read): 

1.  Users control data access, including the ability to revoke an applications’ access to your data at any point in time. 
2.  It allows the data from various applications to be cross-linked, at great derived extra value. For instance, if I relocate, there's no need to separately inform my bank, insurance agency, and driving authority. By simply updating my address in my personal data pod, any authorised organisation can access the new information instantly. 
3.  It allows innovation in the market for applications, because the bar for launching an app is far lower, as the app can run in the open data cloud. 
4.  The persistence of applications and data may be very different. In some cases, a well-established application which people have grown very familiar with may be used to make an online discussion which is ephemeral, in another case an application may be developed to solve a short-term problem in an enterprise where the life of the data exceeds that of any of the applications the enterprise uses. By decoupling the application and data, these persistences can be managed independently. 

**Concluding** 

By reimagining the web as a place where users have sovereignty over their data, initiatives such as Solid pave the way for a more ethical, transparent, and user-centric online world. Realising this ambitious vision demands a collaborative approach that spans various sectors and roles. Whether you're keen on [exploring personal pods](https://solidproject.org/users/get-a-pod), disseminating your research through a Pod, engaging in [privacy-focused computation with Solid](https://arxiv.org/abs/2309.16365), [developing innovative applications](https://solidproject.org/users/get-a-pod), or shaping relevant policies, your contribution is vital. Let's join forces and work together to make this vision a reality!