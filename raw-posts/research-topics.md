---
title: "Research topics ..."
date: 2025-03-17
permalink: /2025/02/17/research-topics/
---
... that I'm interested in but don't have time to work on at the moment.

If you're looking for topics specifically related to Solid and data sovereignty look [here](https://github.com/solid/research-topics).

If you're looking for some more topics related to semi-autonomous Web Agents look [here](https://jeswr.solidcommunity.net/public/iswc_doctoral_consortium.pdf) and for early work on the topic see [here](https://arxiv.org/html/2409.04465v1).

## Suitable Representations

```mermaid
flowchart LR
    %% Expressivity is represented as columns:
    %% Left column: Low Expressivity (High Precision)
    subgraph "Low Expressivity"
        FS["Formal Semantic Languages<br>(High Precision, Low Expressivity)"]
    end

    %% Middle column: Medium Expressivity (Target and Bridging region)
    subgraph "Medium Expressivity"
        ULF["Unified Lingua Franca<br>(Integration Target: High Precision & Broad Expressivity)"]
        IT["Intermediate Token Representations<br>(Moderate/Low Precision, Medium Expressivity)"]
    end

    %% Right column: High Expressivity (Low Precision)
    subgraph "High Expressivity"
        NL["Natural Languages<br>(Low Precision, High Expressivity)"]
    end

    %% Arrows indicate the convergence (conceptual alignment) toward the unified lingua franca:
    FS --- ULF
    IT --- ULF
    NL --- ULF
```

*Kind-of-ok LLM generated mermaid diagram*

Formal semantic languages such as RDF encoded description logics (which in most profiles has a sub first-order expressivity), are a good means of precisely describing information – supporting interpretability and interoperability of data between systems. For much data with clear-cut attributes like the address, DOB, and website of a user – these languages can capture full information.

However, the fact that these languages are constrained to a particular logical profile, (e.g. First Order Logic) means that there – by definition - is a limitation to what they can express. In contrast, natural languages such as English are highly expressive – and have no formal ruleset to describe how the language should be interpreted and executed. Instead, the only systems to date that can operate upon the full spectrum of natural language (including the human brain, LLMs and other machine learning systems) are those which have learned by example; and thus, will have contextually dependent interpretations and reactions to the language. Moreover, multilingual speakers often attest to the idea that there are gaps in the expressible concepts between different languages – thus indicating that contemporary natural language does not effectively capture of all concepts relevant to daily life – let alone all concepts that could be communicated by a human or machine.
In the context of communication between LLMs, there is an emergent discussion of whether it would be appropriate to communicate using intermediate token representations rather than natural language. In theory this may improve expressivity but will nevertheless remain restricted to the conceptual model that lives within LLMs.

If we are to work towards a Web of Agents that accurately and effectively [negotiate, communicate and cooperate](https://www.cs.ox.ac.uk/people/michael.wooldridge/pubs/imas/IMAS2e.html) with maximal versatility, efficiency and unambiguity (where versatility and efficiency are defined as per Section 3 of [this paper](https://arxiv.org/pdf/2410.11905)) then we must work towards the design of a lingua franca for inter-system communication that encapsulates all of these different language modalities.

Moreover, we observe that the process of describing a concept in a higher-order modality, may be seen as conceptual alignment to allow that concept to be operationalised across systems in a lower-order modality. We already see this today in the way that RDF taxonomies are created – the Data Privacy Vocabulary for instance creates a taxonomy of terms defining a range of purposes for which data may be used.  However, the definition of the purpose is still described using the natural language rdfs:description.

This means that whilst, for instance, an ODRL policy can be formalised using a first-order-logic calculus description with the ODRL data model and DPV terms; the implementation of a policy engine operationalising that description will still require a human (or LLM) to interpret the natural language and codify the actions the system should take when, for instance, one is permitted to use data for dpv:Marketing which is defined in natural language as “Purposes associated with conducting marketing in relation to organisation or products or services e.g. promoting, selling, and distributing”.
There is also a question of what, if anything, sits between formal-logic and natural language. [We are not the first to pose such a question](https://chatgpt.com/share/67abac98-8de0-800c-9114-2e72ac12164f).

I’m sure there is some interesting Thery of Mind type stuff to investigate in here if one was to start properly digging – but I am going to withhold from that until I decide if I am going to do research in this direction.
Guidance note I don’t think it is going to be possible to invent much of this in a top-down manner. Would start first in a use-case driven manner.

Possible intermediary points include:

- Normalised natural language (e.g. application of strict grammar rules and/or reduction to a concise and precise language.)
- Building hybrid KG / VDB architectures and understanding the internal representation + mapping between the two views may go a long way in assisting with the creation of this intermediate representation.

## Web-aware agents
In [this paper](https://openaccess.city.ac.uk/id/eprint/34788/) we present a vision of how we can evolve from the current paradigm of Computer Using Agents (CUAs) towards Personal AI Agents reminiscent of the 2001 Semantic Web Vision Paper.
In [the same paper](https://openaccess.city.ac.uk/id/eprint/34788/), we posit that a migration towards a Web of self-describing agents will only be possible should we make operator style agents Web-aware.
What this enables is for Web Agents to more feasibly learn what the “action space” of a particular website is, and more efficiently affect operations.

## Bootstrapping Web Agents

In [this paper](https://openaccess.city.ac.uk/id/eprint/34788/) we present a vision of how we can evolve from the current paradigm of Computer Using Agents (CUAs) towards Personal AI Agents reminiscent of the 2001 Semantic Web Vision Paper.

In [the same paper paper](https://openaccess.city.ac.uk/id/eprint/34788/), we posit that a migration towards a Web of self-describing agents will only be possible should we first bootstrap a critical mass of such agents from existing Web Services. This is particularly important when interacting with legacy services that may not have any active maintainers.
The core research questions here are:
  1. How does one discover the action space of a Website
  2. How does one describe that action space of said Website, e.g., with Semantic Web Service Descriptions
In parallel, we create the opportunity to begin to develop more bespoke search engines / indexing engines for a Web of Agents. In the same way that schema.org enabled Google to effectively index information embedded in Websites - including movie schedules - and present aggregate information at the top of a search result, this work creates the possibility to create an index of what range of actions a particular platform supports. 

## Privacy Preserving Reasoning over Decentralised Ecosystems

See [here](https://jeswr.solidcommunity.net/public/DPhil_Proposal.pdf).

## “Belief” in semi-autonomous agents via personalised models of trust

## Extracting ontological models from LLMs

Ontological construction has traditionally been a time consuming, slow and expensive progress – requiring close collaboration between knowledge engineers and domain experts.

In this work package shall test the viability of using LLMs to do a first pass of ontology construction. However, the goal is to investigate whether this can be done using [mind mapping](https://www.anthropic.com/research/mapping-mind-language-model) techniques rather than prompt engineering.

## Hybrid KG & Vector Database architectures
The core idea here is to build a DB with both a VDB and a KG view. Bergi has already done some work on this topic [here](https://www.bergnet.org/2024/05/unified-landscape/) and [here](https://www.bergnet.org/2024/09/llm-kg-wombat/).


The VDB view enables 
The KB view presents data as a probabilistic KG.

Article on the Graph RAG side of things https://medium.com/towards-data-science/how-to-implement-graph-rag-using-knowledge-graphs-and-vector-databases-60bb69a22759

Deliverables:
-	A formal specification for calculating points in vector space of knowledge graph concepts
-	

## Probabilistic RDF 1.2

Following on from the above topic we need to define precise semantics for describing probabilities and performing inference with said probabilities in RDF/SPARQL 1.2. In particular, see Bergi's article on [tackling uncertainty](https://www.bergnet.org/2024/09/llm-kg-wombat/).

This may take the form of a prov-o(?) extension to enable the expression of concepts such as how sure a given entity is that a claim is true.

## Knowledge Graph Memory For LLM-Based Agents

There is emerging work, such as [this](https://arxiv.org/pdf/2309.11696) on LLM memory, which build memory such as SSD access directly into the LLM architecture - rather than needing to perform this via RAG into the LLM prompt.

The goal here is to build specialised architectures for access to graph-structured data.

## Open Research Dashboard

As a way towards having a fully online collaborative environment – encourage researchers to discuss ideas on a topic on a platform that uses Solid and [ActivityPub](https://en.wikipedia.org/wiki/ActivityPub), and have either humans or machines label the topics for each idea.

Then allow one to browse / view who is working on what, as well as their latest progress – e.g. on GH.
