## TOS Overview

This report defines our research project, designed to progress the development of Semi-autonomous agents at Web scale. We are considering neurosymbolic systems which 


Through our work, we are working towards a near-term future in which legal entities, such as individuals and organisations can entrust semi-autonomous AI-driven agents to carry out online interactions on their behalf. Our research concerns the development of semi-autonomous Web agents, which consult users if and only if the system does not have sufficient context or confidence to proceed working autonomously. This creates a user-agent dialogue that allows the user to teach the agent about the information sources they trust, their data-sharing preferences, and their decision-making preferences. Ultimately, this enables the user to maximise control over their data and decisions while retaining the convenience of using agents, including those driven by LLMs.
In view of developing near-term solutions, the research seeks to answer the overarching question: “How do we build a trustworthy and reliable network of semi-autonomous agents which represent individuals and organisations on the Web?”. After identifying key requirements, the paper presents a demo for a sample use case of a generic personal assistant. This is implemented using (Notation3) rules to enforce safety guarantees around belief, data sharing and data usage and LLMs to allow natural language interaction with users and serendipitous dialogues between software agents.

## TOS Methodologies

### Methodologies
In this section we summarise the methodologies that we shall be applying to answer a range of questions throughout our thesis.

Random quotes:
Clive Humby, a business intelligence technology pioneer in the UK, and founder of the Tesco
(national, household-name, UK supermarket chain) Clubcard loyalty scheme, famously spoke of data as the
‘New Oil’, and noted in the same presentation that, “without context a fact is just that: A fact. It is not an
insight” [96.]

In a 2021 paper, IBM® conceived of “data objects”. These were defined as: “the information or data
owned within the scope of ownership” [1o2.] This introduced concepts of ownership of data, of their
stewardship and custodianship, but also of a bounding of ownership, a domain or scope.

### Ontology Design
Modelling Identity and Identity flows
Model, for instance, all of the concepts from OpenID and demonstrate how you can develop OpenID equivalent flows by having systems declaratively write their security assumptions – rather than hard coding the flows. The goal is to make it easy to support a range of identity and authentication flows (including with SSI, OpenID, Passkey etc. infrastructure), and to declaratively model e.g. concepts from the DIATF.

https://www.w3.org/2019/wot/security#APIKeySecurityScheme
Need to dig back out a systematic review of identity like the following to get that working
https://ieeexplore.ieee.org/document/9842532

### User Interaction Design

### Speculative Design

### Complexity Analysis of Selective Disclosure Query

## User studies with Legal Scholars for ODRL Generation work

Topics to cover:

Jun:
 - User studies, set of scenarios to legal experts - please tell me what legal structures are necessary. Then do a follow up study to say "Hi I designed this, what do you think".
- Individuals vs. organisatons, (commercial | non-commercial) organisations w. (commercial | non-commercial) organisation,
- More rigorous is x2 criticalness
- Within the 6 then say half of them is life critical and half is not
- Another way is to look into the literature to see what has been discussed and what has not

<!-- TODO: Move this to research topics of interest to me -->
## Understanding the future that people want
What if we dropped all assumptions, we have about what technology has to look like, and instead start to think about what we want technology to look like. Visionaries such as [] are always leading the charge to build the future that they envision, the future that they want. But what does everyone else want? Do they even know?
In this set of research, inspired by David Hyland-Wood, we shall 

Study design:
-	First ask a broad set of questions about what people want the future of technology to look like, no prompting around data centralisation around the user, disruption of monopolistic power, or otherwise swaying the response in that manner
-	Then start to unpack what is possible / provide more inspiration

## Research Questions
In working towards the development of Semi-autonomous agents operational at Web scale, this thesis plans to answer the following research questions.
-	DPhil wiki on Atlassian https://jeswr.atlassian.net/wiki/spaces/DC/

## Research Topic 1d: Provable provenance trails with RDF / SPARQL 1.2
Reference to ZK snarks in real-world use-cases:
-	https://eprint.iacr.org/2025/404
-	

Proposed research plan with this one:
 - https://claude.ai/chat/68bc9724-3e1e-417d-aa08-4c94a92d37d7


## Trust

- https://www.turing.ac.uk/sites/default/files/2021-11/technical_briefing_a_conceptual_model_of_trust_and_trustworthiness.pdf


## Work Package 2: Semi-Automated Data Sharing & Data Sharing Agreements

Current Status: I think I am better positioned to push on this line of work with the use-cases that we have at the ODI. In particular, CDMC already has a series of catalogues defining the different data governance requirements for different datatypes in different jurisdictions which need to be accounted for.
We note that the Data (Use and Access) Bill is presently under debate in the House of Lords – amongst other matters, the bill amends Data Protection Regulation in the UK as originally defined in the UK Data Protection Act 2018, adds new provisions to facilitate the sharing of data for research purposes, and makes updates to requirements around Data Subject Access Requests (SAR).

Should this bill is passed prior to the commencement of this work package in February 2025, our work will make a timely contribution to the understanding of, and commentary around, this key piece of legislation.
Outputs to date:
-	Me want cookie paper; presenting the vision for semi-automated data governance
o	https://arxiv.org/abs/2408.09071, in retrospect – this was a good pedagogical exercise for myself, but not particularly impactful research. It pushes on many ideas that were already present in Oshani’s PhD research https://groups.csail.mit.edu/dig/2009/oshani-thesis/main.pdf
-	Purpose generation work (I *hope* this is done my the time I transfer – note this has similarities to the paper that Rui is currently working on):
o	https://github.com/jeswr/cookie-analysis
o	https://github.com/jeswr/cookie-purpose
Expected Outputs:
•	(Optional) Implementation of a prototype compliance-checking engine, with contributions from both teams, to automate the creation, negotiation and compliance-checking of machine-readable contracts. The prototype will be available open source under the MIT license.
•	(Optional) Series of papers in collaboration with legal experts, demonstrating the feasibility of semi-automated, legally binding data-sharing contracts in various jurisdictions. The papers will focus on:
o	Demonstrating such contracts’ legal enforceability under UK law.
o	Extending the approach to other jurisdictions and analyzing the differing requirements for compliance.
Further pointers:
-	https://hendersoni.substack.com/p/the-very-necessary-shift-from-consent
-	Projects like CDMC are already creating a set of assets for describing Cloud Controls within industry, which is beginning to include the development of registries which describe the https://edmcouncil.org/frameworks/cdmc/.

## Work Package 6 (Optional): KG’s in LLM Architectures
Formal semantic languages such as RDF encoded description logics (which in most profiles has a sub first-order expressivity), are a good means of precisely describing information – supporting interpretability and interoperability of data between systems. For much data with clear-cut attributes like the address, DOB, and website of a user – these languages can capture full information.

## Work Package 7.5 (Optional): Suitable representations for agentic alignment
A pressing challenge of LLM-based agentic research that of conceptual alignment. Fundamentally, this comes down to the question “If we have two agents talking to each other, how do we know they have an aligned understanding of the concepts they talk about.”
One approach is to have agents share a global “whiteboard” of precise definitions of the topics they use. In the Semantic Web context – the equivalent would be to jointly pick a certain vocabulary to use, which in theory would have a set of “globally understood” Semantics.
Another approach is to have agents
In the description logic world this would be more of a conflict resolution process – as opposed to a  

## Actions

Work Package 8 (Optional): Bodies to contact in relation to Solid
-	https://www.iso.org/committee/601355/x/catalogue/p/0/u/1/w/0/d/0
-	https://datatracker.ietf.org/doc/html/draft-ietf-gnap-core-protocol
State of the art multi-agent systems
-	https://agent-network-protocol.com
-	https://arxiv.org/abs/2410.11905

## How do we Trust?

One facet of trust is the process of establishing that the entity that you are communicating with, is who they claim they are. In the financial services, there is a billion-dollar market around this – Know Your Customer.
Within the UK’s Digital Identity and Attributes Framework (DIATF) [1], this also makes an appearance. There four confidence intervals are defined, with further evidence that the entity is who they claim to be at each stage.  
[1] https://www.gov.uk/government/publications/identity-proofing-and-verification-of-an-individual/how-to-prove-and-verify-someones-identity
[2] 
It’s all just data …

