---
title: "Raw (structured) data now: It's time to build the Human Knowledge Graph"
date: 2024-04-25
permalink: /2024/04/25/raw-data-now/
---

Sir Tim Berners-Lee's invention of the Web was a dramatic milestone in the information age, making vast amounts of human knowledge accessible to everyone. However, we have now reached a point where such availability is ironically creating inaccessibility, with humans and machines alike overwhelmed by false and duplicate information.

In his seminal 2001 article "The Semantic Web", Berners-Lee claimed that "Properly designed, the Semantic Web can assist the evolution of human knowledge as a whole". While this vision has been proven true in limited contexts, from powering [Google's Knowledge Panel](https://www.google.com/search?channel=fs&client=ubuntu-sn&q=sir+tim-berners+lee) (example shown below) to enabling biomedical discoveries, the full potential of the Semantic Web for capturing and organizing human knowledge remains largely unrealized.

![](/tim-pane.png)

Knowledge representation is a decades-old area of research, originally developed with symbolic reasoning in mind. However, [as I've previously discussed](/2024/04/18/better-ai), knowledge graphs are now playing a crucial role in system 1 reasoning systems, in particular being used to ground LLM queries using Retrieval Augmented Generation (RAG).

This only works if we have knowledge graphs in the first place. Enterprises have been throwing resources at building out structured databases from which they can generate knowledge graphs for decades. However, in some parts of academia, we are not doing this job so well. It's time to follow the lead of biomedical domains and start modeling our research and results so that humans and machines can better understand what knowledge we, as humanity, have discovered.

We now have a greater impetus and better means than ever before to create a comprehensive Human Knowledge Graph using Semantic Web technologies. The key is to describe and publish concepts in as granular a manner as possible. 

One promising domain to start with is mathematics, where every theorem, proof, and axiom can be represented as its own entity, with rich semantic links capturing the relationships between them. Efforts to formalize 21st century mathematics provide a foundation to build upon.

Beyond mathematics, we can extend this approach to other fields like physics, chemistry, and computer science. For example, a knowledge graph could precisely define different graph neural network architectures, link them to the mathematical foundations that characterize their expressivity, and connect them to experimental results on standard datasets. This provides a unified view of both the theoretical and empirical landscape.

Building such a knowledge graph of human knowledge is valuable for multiple reasons:

1. It enables AI systems to learn from a clean, structured representation of knowledge, improving their accuracy and grounding their outputs in precise concepts rather than just statistical patterns in raw text.

2. It facilitates research, especially interdisciplinary work, by allowing scientists to search and integrate knowledge at the concept level, across different languages and terminologies.  

3. It avoids information duplication and establishes clear provenance and authorship of ideas.

To realize this vision, we can leverage technologies like Solid, which provides a decentralized protocol for access-controlled linked data. This allows the public knowledge graph to be extended with private layers, enabling use cases like pre-publication research and internal industrial R&D.

So now is the time to revisit the call for ["Raw Data Now"](https://www.wired.com/story/raw-data/) and put resources into generating structured data for each of our domains.

In conclusion, the Semantic Web has immense untapped potential to revolutionize how we represent, integrate, and leverage human knowledge. By undertaking ambitious collaborative projects to build granular, multi-disciplinary knowledge graphs, we can take a major leap towards realizing this vision and transforming fields from AI to scientific research. The journey will be long, but the benefits are immense.

<!-- Knowledge representation is a decades-old area of research, originally developed with symbolic reasoning in mind. However, [as I've previously discussed](/2024/04/18/better-ai), knowledge graphs are playing a cruicual role in [system 1 reasoning systems](), in particular being used to ground LLM queries using Retrieval Augmented Generation (RAG).

This only works if we have knowledge graphs in the first place. Enterprises have been throwing resources at building out structued databases from which they can generate knowledge graphs for decades.

However, in some parts academia we are not doing this job so well. It's time to to follow the lead of biomedical domains and start modelling our research and results so that humans and machines can better _understand_ what knowledge, we as humanity, have discovered.

So now is the time to revisit the call for ["Raw Data Now"]() and put resources into generating structured data for each of our domains. -->
