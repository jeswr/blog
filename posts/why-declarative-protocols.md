---
title: "Dynamic and declarative protocols for decentralised AI"
date: 2025-03-23
permalink: /2025/03/23/dynamic-declarative-protocols/
---

**ARTICLE IN DRAFT**

![](/dynamic-protocol.png)

*Placeholder image [produced by ChatGPT 4.5](https://chatgpt.com/share/67dffbd1-bfa0-800c-8a7c-c48c0737716e)*

This post discusses why we need to create infrastructure that supports a network of systems to:
 1. Declaratively describe what features they need a protocol[^1] to achieve for them such as:
    - proving that the user of a particular device in the network is a particular entity,
    - calculating an aggregate result from data living on multiple devices in the network (think Multi Party Computation, Federated Learning etc.),
    - proving that a payment has been made, and
    - coordinating to ensure that a payment is made once an action has been performed (think smart contract)
2. Declaratively describe their acceptable security requirements, including:
    - what operations other systems in the network can be trusted to perform, 
    - what information can be trusted to come from other systems in the network,
    - who in the network do they permit to view particular pieces of information, and
    - other requirements that may be identified in a [W3C Security Review](https://www.w3.org/mission/security/#ping)
3. Have a means to create or discover and agree to use a protocol on-the-fly that satisfies these set of requirements.
4. Whilst still allowing for long term planning
   - For instance, a desirable feature of the ongoing use of HTTP(s) is the ability to use documents cached in DNSs.

We observe that:
 - this proposal largely reflects my view that we should - for the most part - not need to use Generative AI at the layer of deciding how to transfer data, but instead to declaratively state what data is needed,
 - this proposal assumes that we are going to have some level of data and compute sovereignty - whilst also moving us towards that world, and
 - the capability to generate a *proof* that the proposed protocol has a particular set of security properties is critical
 to enabling all parties to 'buy in' to use the protocol

The kinds of use-cases which this unlocks include:
 - 
 - Dynamic Authentication Flows: Currently, the flows for, e.g., authentication are often quite fixed; and require heavy changes to specification documents + flows to evolve. In this use-case we show that the OIDC flow can “emerge” simply by having 2 agents negotiate for data they need to identify one another. A specific example is this [e-reader access use-case](https://github.com/jeswr/queryable-credentials/blob/main/use-cases/e-reader-access.md).
 - Agents performing scheduling: As described in [this paper](https://arxiv.org/abs/2409.04465).
 - Features people care about in the blockchain world: For example, could show how a DAOs could form.
 

[^1]: Note that here we are using the term protocol to refer to the sequence of steps that a set of systems should take in order to achieve a joint goal. This includes how to collaboratively transport information (networking protocols), secure data in transport (encryption protocols) and proving the identity of an end user on one system to another system (authentication).
