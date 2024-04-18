---
title: "The Old and the New - Using Semantic Web Technologies to Build Better AI"
date: 2024-04-18
permalink: /2024/04/18/better-ai/
---

<!-- **Introduction** -->

## Introduction

As artificial intelligence (AI) continues to advance at a breakneck pace, particularly with the rise of large language models (LLMs), it is imperative to ensure that these systems are truthful, trustworthy, accountable, and robust. Without such properties, current LLM-style AI systems will struggle to move beyond their roles as [sophisticated search engines](https://www.forbes.com/sites/rashishrivastava/2024/04/11/inside-the-buzzy-ai-startup-coming-for-googles-lunch/) and [writing assistants](/2024/04/18/better-ai/), hindering their ability to autonomously perform tasks such as acting as [web services or agents](https://link.springer.com/journal/10458).

Enter the Semantic Web, a long-standing vision of a machine-readable web that enables agents to understand and interact with data in a meaningful way ([Berners-Lee et al., 2001](https://www.scientificamerican.com/article/the-semantic-web/)). To learn about the original architectural vision of the Semantic Web, see [this design issue](https://www.w3.org/DesignIssues/Semantic.html). In this blog post, we'll explore how Semantic Web technologies can be leveraged to build better AI systems that are more reliable, accountable, and aligned with human values.


<!--    The Semantic Web provides a framework for representing data in a structured and interoperable format, allowing AI systems to reason over and draw insights from this information ([Feigenbaum et al., 2007](https://www.science.org/doi/10.1126/science.1200831)). In this blog post, we'll explore how Semantic Web technologies can be leveraged to build better AI systems that are more reliable, accountable, and aligned with human values. -->

<!-- As artificial intelligence (AI) continues to advance at a rapid pace, particularly with the rise of large language models (LLMs), it's essential to ensure that these systems are truthful, trustworthy, accountable, and robust. Without such properties, current LLM-style AI systems will struggle to move beyond their role as glorified Search Engines and Essay Writers [] and autonomously perform tasks such as acting as a Web Service or Agent []. -->

<!-- Enter the Semantic Web, a long-standing vision of a machine-readable web that enables AI agents to understand and interact with data in a meaningful way [1]. In this blog post, we'll explore how Semantic Web technologies can be leveraged to build better AI systems.
Enter the Semantic Web, a long-standing vision of a machine-readable web that enables AI agents to understand and interact with data in a meaningful way ([Berners-Lee et al., 2001](https://www.scientificamerican.com/article/the-semantic-web/)). The Semantic Web provides a framework for representing data in a structured and interoperable format, allowing AI systems to reason over and draw insights from this information ([Feigenbaum et al., 2007](https://www.science.org/doi/10.1126/science.1200831)). In this blog post, we'll explore how Semantic Web technologies can be leveraged to build better AI systems that are more reliable, accountable, and aligned with human values.

As artificial intelligence (AI) continues to advance at a rapid pace, particularly with the rise of large language models (LLMs), it's essential to ensure that these systems are truthful, trustworthy, accountable, and robust. Without such properties, current LLM-style AI systems will struggle to move beyond their role as glorified Search Engines and Essay Writers [] and autonomously perform tasks such as acting as a Web Service or Agent [].

Enter the Semantic Web, a long-standing vision of a machine-readable web that enables AI agents to understand and interact with data in a meaningful way [1]. In this blog post, we'll explore how Semantic Web technologies can be leveraged to build better AI systems. -->

## Grounding LLMs with Knowledge Graphs

One of the key challenges with LLMs is ensuring the quality and truthfulness of their responses. By grounding LLMs with high-quality data represented in a knowledge graph (KG), we can significantly improve the accuracy and reliability of their outputs. Knowledge graphs, a core component of the Semantic Web, provide a structured and interconnected representation of data, allowing LLMs to reason over and draw insights from this information. Industry is rapidly adopting this approach, with companies like [Ontotext](https://www.ontotext.com/knowledgehub/fundamentals/what-is-graph-rag/) and [Neo4J](https://www.youtube.com/watch?v=ftlZ0oeXYRE) offering out-of-the-box solutions for performing Retrieval Augmented Generation (RAG) with Knowledge Graphs. The interest in grounding LLMs using information from Knowledge Graphs extends beyond companies run by Semantic Web enthusiasts. [Andrew Ng](https://twitter.com/AndrewYNg/status/1767941813820862655), a prominent figure in the AI community, has co-developed a course on RAG with Knowledge Graphs. Furthermore, during [Langchain's Memory Hackathon](https://medium.com/enterprise-rag/knowledge-graphs-memory-semantic-structure-in-rag-takeaways-from-langchains-memory-hackathon-6630f8bb98c0), 30% of the participating teams sought to implement knowledge graphs in their architectures, highlighting the growing recognition of their potential in enhancing LLM performance.

## Protecting User Privacy and Ensuring Ethical Data Usage

<!-- Coming soon ... -->
As AI systems increasingly rely on user and enterprise data to function, it's crucial to ensure that this data is used ethically and in compliance with legal governance frameworks. Semantic Web, and satellite technologies such as [Solid](/2024/02/06/role-of-solid) offer strategies [for attaching access controls, and usage agreements](https://ruben.verborgh.org/blog/2023/11/10/no-more-raw-data/) to data in order to [support responsible data usage](https://www.inrupt.com/blog/safe-ai-101).

<!-- https://www.inrupt.com/blog/safe-ai-101 -->

 <!-- - https://ruben.verborgh.org/blog/2023/11/10/no-more-raw-data/ -->

## Towards Trustworthy and Accountable Personal AI Agents

The Semantic Web has long envisioned a future where autonomous AI agents work on behalf of users, assisting them with various tasks and decision-making processes. By leveraging Semantic Web technologies, we can build the groundwork protocols that enable conversational agents to negotiate and transact over the web which contain features such as:
1. Mechanism for describing the origin and provenance of exchanged data
2. Mechanisms to determine the "trustworthiness" of data by modelling which sources / individuals / organisations are reliable, and which are not.
3. Unambiguous description of usage restrictions on exchanged data to protect privacy allowing conversational LLM-agents can become more trustworthy, accountable, and compliant with data protection regulations such as GDPR.
4. Clear definition of dialogue outcomes that require agreement or transaction
5. The ability to discover AI representitives of individuals & organisations using [Web Identities](https://en.wikipedia.org/wiki/WebID).

More on this topic soon ...

<!-- The protocol also incorporates the concept of WebID, allowing real-world entities (humans, organizations, or devices) to be represented on the web and authorize conversational agents to act on their behalf.

When an LLM-agent is tasked with performing an action, it follows a series of steps:

1. Establish which external entities it needs to converse with and what information needs to be disclosed
2. Discover the external conversational LLM-agents using WebID-Profiles
3. Negotiate terms of use for shared data using structured data formats (e.g., RDF, ODRL)
4. Exchange "packaged data" and conclude the dialogue with an agreed-upon structured result

The proposed protocol offers several key features, including well-defined discovery of conversation agents via WebIDs, declaration of usage and sharing requirements, proof and provenance for establishing data trustworthiness, and the use of RDF to ensure unambiguous outcomes.

The novelty of this approach lies in its ability to express trust between agents, provide a provenance track for trust expressions, package data with provenance and data terms of use expressions, and use RDF to verify outcomes. By implementing this protocol, conversational LLM-agents can become more trustworthy, accountable, and compliant with data protection regulations such as GDPR. -->


## Conclusion

The Semantic Web, with its rich history and powerful technologies, holds the key to building better AI systems in the age of LLMs. By grounding LLMs with knowledge graphs, ensuring ethical data usage through explicit policies, and laying the foundation for trustworthy personal AI agents, the Semantic Web complements and enhances the capabilities of modern AI. As we continue to push the boundaries of what's possible with AI, it's essential to look to the past and leverage the insights and technologies developed by the Semantic Web community. By combining the old and the new, we can create AI systems that are not only powerful but also accountable, transparent, and aligned with human values.

<!-- These agents can communicate with each other using standardized protocols, exchange data securely, and make decisions based on user preferences and policies. The use of WebIDs, which are HTTP URIs that denote an agent and resolve to a profile document describing the agent's capabilities and authorization to act on behalf of an entity, facilitates the discovery and identity management of AI agents [11]. -->


<!-- Coming soon ... -->

<!-- This approach, known as Retrieval Augmented Generation (RAG), has proven effective in enhancing the performance of conversational AI systems [2]. Recent studies have shown that 30% of teams participating in a memory hackathon were explicitly looking to implement knowledge graphs into their architecture, with teams using knowledge graphs performing well in the judging process [3]. Furthermore, the synergy between RAG and knowledge graphs has been explored in various contexts, such as using GraphDBs' natural language interface to interact with content [4] and leveraging Cypher search in LangChain [5].

Protecting User Privacy and Ensuring Ethical Data Usage:
As AI systems increasingly rely on user data to function, it's crucial to ensure that this data is used ethically and in compliance with legal governance frameworks. The Semantic Web provides a mechanism for explicitly annotating data with privacy and usage policies, enabling LLMs to understand and adhere to these restrictions [6]. By representing policies using Semantic Web technologies, such as the Web Ontology Language (OWL) and the Resource Description Framework (RDF), AI agents can reason over these policies and ensure that data is used only in ways that users have consented to, promoting trust and accountability [7]. This is particularly relevant in the context of personal data stored in Solid Pods, where access control policies and data terms of use can be automatically generated based on the data and integrated into the standard authorization flow [8].


Towards Trustworthy and Accountable Personal AI Agents:
The Semantic Web has long envisioned a future where autonomous AI agents work on behalf of users, assisting them with various tasks and decision-making processes. This notion aligns closely with the concept of Vendor Relationship Management (VRM) [9], which seeks to empower individuals to manage their relationships with vendors and service providers. By leveraging Semantic Web technologies, we can build the groundwork for trustworthy and accountable personal AI agents and services at a web scale [10]. These agents can communicate with each other using standardized protocols, exchange data securely, and make decisions based on user preferences and policies. The use of WebIDs, which are HTTP URIs that denote an agent and resolve to a profile document describing the agent's capabilities and authorization to act on behalf of an entity, facilitates the discovery and identity management of AI agents [11].

Conclusion:
The Semantic Web, with its rich history and powerful technologies, holds the key to building better AI systems in the age of LLMs. By grounding LLMs with knowledge graphs, ensuring ethical data usage through explicit policies, and laying the foundation for trustworthy personal AI agents, the Semantic Web complements and enhances the capabilities of modern AI. As we continue to push the boundaries of what's possible with AI, it's essential to look to the past and leverage the insights and technologies developed by the Semantic Web community. By combining the old and the new, we can create AI systems that are not only powerful but also accountable, transparent, and aligned with human values. -->

<!-- [^1] I even used one to assist in writing this article! -->

<!-- References:
[1] Berners-Lee, T., Hendler, J., & Lassila, O. (2001). The Semantic Web. Scientific American, 284(5), 34-43. https://www.scientificamerican.com/article/the-semantic-web/

[2] Lewis, P., Perez, E., Piktus, A., Petroni, F., Karpukhin, V., Goyal, N., ... & Kiela, D. (2020). Retrieval-augmented generation for knowledge-intensive NLP tasks. arXiv preprint arXiv:2005.11401. https://arxiv.org/pdf/2005.11401.pdf

[3] Langchain Memory Hackathon: Takeaways and Insights. (2023). Medium. https://medium.com/enterprise-rag/knowledge-graphs-memory-semantic-structure-in-rag-takeaways-from-langchains-memory-hackathon-6630f8bb98c0

[4] Using GraphDB's Natural Language Interface to Talk with Your Content. (2021). Ontotext. https://www.ontotext.com/blog/using-graphdbs-natural-language-interface-to-talk-with-your-content/

[5] LangChain Has Added Cypher Search. (2023). Towards Data Science. https://towardsdatascience.com/langchain-has-added-cypher-search-cb9d821120d5

[6] Kirrane, S., Fernández, J. D., Dullaert, W., Milosevic, U., Polleres, A., Bonatti, P. A., ... & Wenning, R. (2018). A scalable consent, transparency and compliance architecture. In European Semantic Web Conference (pp. 131-136). Springer, Cham. https://link.springer.com/chapter/10.1007/978-3-319-98192-5_25

[7] Bonatti, P. A., Kirrane, S., Petrova, I. M., Sauro, L., & Schlehahn, E. (2020). The SPECIAL usage policy language, version 1.0. SPECIAL Project Deliverable D2.8. https://www.specialprivacy.eu/images/documents/SPECIAL_D28_M30_V10.pdf

[8] Data Terms of Use Negotiation. (2023). Solid Project. https://docs.google.com/document/d/1icPtGL1fnsQImWyK1tbrwKsKBpKv7s3C0oFwr6J-I-w/edit

[9] Project VRM. (2023). Project VRM. https://cyber.harvard.edu/projectvrm/Main_Page

[10] Solid: Your data, your choice. (2023). Solid Project. https://solidproject.org/

[11] WebID Profile. (2023). Solid Project. https://solidproject.org/TR/webid-profile -->
