---
title: "Paper Summary: COT Prompting Elicits Reasoning in Large Language Models"
format: html
date: 2024-08-12
tags: [paper, LLM, reasoning]
---


Paper - https://arxiv.org/abs/2201.11903 

> We explore how generating a chain of thought -- a series of intermediate reasoning steps -- significantly improves the ability of large language models to perform complex reasoning. In particular, we show how such reasoning abilities emerge naturally in sufficiently large language models via a simple method called chain of thought prompting, where a few chain of thought demonstrations are provided as exemplars in prompting. Experiments on three large language models show that chain of thought prompting improves performance on a range of arithmetic, commonsense, and symbolic reasoning tasks. The empirical gains can be striking. For instance, prompting a 540B-parameter language model with just eight chain of thought exemplars achieves state of the art accuracy on the GSM8K benchmark of math word problems, surpassing even finetuned GPT-3 with a verifier.

In other words, when we use fewshot prompting, if we provide the sample answers in the chain of thought format instead of just providing the answer, LLMs are able to perform complex reasoning. 

Let us see a few examples of Q & A, where the answers follow the chain-of-thought pattern. 

#### Examples
Q: Roger has 5 tennis balls. He buys 2 more cans of tennis balls. Each can has 3 tennis balls. How many tennis balls does he have now?

A: Roger started with 5 balls. 2 cans of 3 tennis balls each is 6 tennis balls. 5 + 6 = 11. The answer is 11.

---

Q: The fox walked from the city into the forest, what was it looking for? Answer Choices: (a) pretty flowers (b) hen house (c) natural habitat (d) storybook

A: The answer must be something in the forest. Of the above choices, only natural habitat is in the forest. So the answer is (b)

#### Results
What are main take-aways?

1. Chain-of-thought prompting does not positively impact performance for small models, and only yields performance gains when used with models of  100B parameters.
2. Chain-of-thought prompting has larger performance gains for more-complicated problems. 
3. Chain-of-thought prompting via GPT-3 175B and PaLM 540B compares favorably to prior state of the art, which typically finetunes a task-specific model on a labeled training dataset.