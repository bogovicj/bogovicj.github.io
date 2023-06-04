---
layout: post
title:  InstructGPT
date:   2023-06-04 14:30:01 -0400
categories: ai machine-learning language-models gpt
---

Our journal club recently read the OpenAI paper ["Training language models to follow instructions with human
feedback"](https://arxiv.org/abs/2203.02155), describing InstructGPT. The goal of the work is to fine-tune a large language model
(GPT-3) to produce output that are more closely "aligned" to user intentions. They define

> models to be aligned if they are helpful, honest, and harmless.

where these "three H's" have their own somewhat vague, but reasonable definitions. The hope is that a model that is better
aligned will be less likely to produce "bad" outputs: express bias, encourage or fail to discourage harm, produce toxic outputs,
or fabricate information.

GPT-3 was fine-tuned using data collected from human labelers, and responses from the fine-tuned model were preferred by humans
to the baseline model. The behavior of the model certainly changed, often for the better, but arguably, sometimes also for the
worse. 

The fine-tuned model produces less toxic outputs when the prompt contains a request to avoid toxicity - that's good. If
no such request is present in the prompt though, there is no change in the prevalence of toxic outputs. However, if the prompt
requests a toxic output, the fine-tuned model is *more likely to produce toxic responses than the baseline*. That could be
concerning. On the one hand, if followed instructions. On the other hand, it's causing harm. There is a real difficulty in
trading off between these factors (see below), but it all depends on context.

An optimistic interpretation of the results is "fine-tuned models follow instructions better and are therefore more sensitive to
context." I don't see much of a reason to be that optimistic though. Can a language model produce outputs appropriate to that
context by providing instructions in the prompt? Does this count as the model "knowing" its context. Probably not.

While this work does appear to improve language models in important ways, there is much more work to do. In particular,
fine-tuned models are sometimes *more biased than the baseline language models.* 

> The [fine-tuned] model shows similar bias to GPT-3, but when instructed to act respectfully it exhibits lower entropy and thus higher bias.

Maybe this is another case of AI being a reflection of us as we are, not as we aspire to be.

### Data collection 

A critical and challenging part of the work has to do with the process of collecting data from human beings both for fine-tuning
and evaluating the results. One task for the human labelers was to rank the responses of different models to the same input
prompt. This is already tricky, since 

> our alignment criteria may come into conflict: for example, when a user requests a potentially harmful response

do we prefer a helpful or harmless answer? It sounds like the balance changes in different parts of the study:

> during training we prioritize helpfulness to the user...in our final evaluations we asked labelers prioritize truthfulness and harmlessness

Even more, the human labelers were (obviously) not in perfect agreement about what responses they preferred.

> labelers agree with each-other 72.6 ± 1.5% of the time

