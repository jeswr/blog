---
title: "Proposal: A Conversational Interface for trusted data"
date: 2025-03-22
permalink: /2025/03/22/conversational-interface-trusted-data/
---

<!-- Recently meta announced their work on [Large Concept Models (LCMs)]() -->

In this post I set out the interface that I would like to have in order to get more value out of language models for tasks such as research that require high levels of information accuracy and provenance. These include:
 - Indicate the likelihood of correctness of statements in a response via color coding of the text. This color coding should be personalisable based on whether I:
   - confirm whether entities in a sentence are the ones I want to talk about
   - confirm that I trust information sources from which the answer was derived
   - confirm further background questions that the model has if I ask it to "improve its certainty"
 - Hyperlinking entities (things such as people, places, objects etc.) in a response, so I can confirm that this is the entity I care about. If I hover over the hyperlink I should be able to see extra information about the entity, such as a picture, full name and other key details and have the option to say "this is not what I'm after" or hit a green check mark in the top right corner to allow the interface to update its accuracy color-codings.

<!-- <iframe src="/ltcm" width="100%" height="500" frameborder="0"></iframe> -->

This example can be found [here](/ltcm).

This requires advancements beyond current [Large Language Model (LLM)](https://en.wikipedia.org/wiki/Large_language_model) and emergent [Large Concept Models (LCMs)](https://ai.meta.com/research/publications/large-concept-models-language-modeling-in-a-sentence-representation-space/) architectures. In particular, this would require models to:
 - Have in-built mechanisms for entity resolution
 - Have knowledge of the provenance trails of the information it has learned

I am interested in developing architectures that are in support of this vision.


