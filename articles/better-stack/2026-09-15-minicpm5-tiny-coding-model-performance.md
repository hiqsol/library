---
title: This Tiny Coding Model Shouldn’t Be This Good (MiniCPM5)
author: Better Stack
channel: Better Stack
url: https://youtu.be/Wik_JQ-enUA?is=OP0xxddCC80JHitq
date: 2026-09-15 13:30
tags: ai, development
---

# This Tiny Coding Model Shouldn’t Be This Good (MiniCPM5)

[summary](../../summary/better-stack/2026-09-15-minicpm5-tiny-coding-model-performance.md)

MiniCPM5-2B is a small, local model aimed at a job where small models often fail:
acting as a coding agent that can follow tool schemas, make calls, and produce useful patches.
Josh from Better Stack argues that its strongest results are genuinely unusual for its size,
but also shows why the benchmark story and the default runtime settings need scrutiny.

## Why its agent results stand out

The presenter describes the usual small-model failure modes: a model may chat well, then
hallucinate a tool schema, forget it, or loop once tools enter the workflow. SWE-bench
Verified is especially demanding because models must resolve real GitHub issues with real
patches.

In the vendor figures shown, Qwen3.5-2B scores 5 and Gemma 4 E2B scores 2 on SWE-bench
Verified. MiniCPM5-2B is listed at 46. It also exceeds the score of Qwen3.5-4B, a model
roughly twice its size. The presenter treats that as evidence that focused agent training can
matter more than parameter count on selected workloads.

OpenBMB attributes the result to a conventional architecture, long context, and specialized
training. The model is described as plain Llama rather than an exotic design, with about
128,000 tokens of native context. Its training used 500,000 agent trajectories during
supervised fine-tuning, followed by reinforcement learning. Sixteen separate RL expert
models were then merged into one.

The release is Apache 2.0 and uses open datasets. The video concerns the text-only MiniCPM5
model, not another model in the broader MiniCPM family.

## A conventional model that runs in familiar tools

The video later describes the branded 2B model more precisely as a dense 2.5-billion-
parameter model with 42 layers and grouped-query attention. Its model class is
`LlamaForCausalLM`. That choice is important because MiniCPM4 used custom sparse attention
and multi-token prediction, which required special support in each runtime.

MiniCPM5 drops those custom components. The presenter's practical rule is that a runtime
that can load Llama has a good chance of loading MiniCPM5. He names MLX, llama.cpp, and
WebLLM, and calls compatibility one of the model's strongest features.

On a Mac, he installs MLX-LM with pip inside a virtual environment and pulls the weights with
the first prompt. The demonstrated quantized model is a 1.3 GB file. Its output includes a
thinking block, a final answer, and a tokens-per-second counter; it can also run as an
interactive chat.

Older MLX-LM releases are a trap: according to the presenter, they ignore this model's
end-of-sequence list, so generation may not stop. A current runtime is therefore part of the
setup, not merely a convenience.

For tool use, he starts llama.cpp in another terminal, points an OpenAI client at it, and
provides a simple weather tool. MiniCPM5 emits a structured function call, llama.cpp parses
it, and the client receives a proper `tool_calls` array. This is the video's direct practical
test of the agent behavior highlighted by the benchmarks.

## The benchmark table cuts both ways

Against Qwen3.5-4B, the vendor table gives MiniCPM5 a 69-to-56 lead on LiveCodeBench and a
46-to-34 lead on SWE-bench Verified. Those numbers support the claim that a 2B-class model
can replace a 4B model for some coding and agent tasks.

Other results reverse the conclusion. On SWE-bench Pro, MiniCPM5 scores 14 versus 28. On
Terminal-Bench, it scores about 8.5 versus about 26, roughly one third as much. The presenter
also says Qwen3.5-4B wins on MMLU-Pro, GPQA Diamond, and LongBench v2, while even
Qwen3.5-2B beats MiniCPM5 on plain instruction following.

His conclusion is narrow: the label “4B class” has merit for code, tool calls, math, and
parts of agent work, but not across the board. The benchmark results are vendor-run, and the
comparison table includes only Qwen and Gemma. It omits Llama, Phi, SmolLM3, and even a
MiniCPM4 row that would show generation-to-generation progress. The presenter says a GitHub
request for evaluation scripts had received no response.

## Quantization can make it look broken

The sharpest warning comes from a GitHub tracker test of HumanEval+ against GGUF files. With
the documented settings, Q8 scored about 43 and 55% of generations ran away into
repetition. Q4_K_M scored about 6, with 92% of generations running away.

Setting the repeat penalty to 1.15 changed the result dramatically: Q8 rose from about 43 to
92, while Q4 rose from 6 to 71. The presenter also reports that OpenBMB later explained on
Hugging Face that llama.cpp's default `min_p` value of 0.05 was the underlying problem and
should be set to 0. That guidance was not in the documentation when the tests were run.

For a model this small, sampling is effectively part of the model's usable behavior. A bad
default can turn a capable release into a looping one, so quantization results are not
meaningful without recording the sampler and stop-token handling.

## Remaining usability limits

The presenter says the model was not yet in the Ollama library, requiring a custom model
file, and had no LM Studio page, requiring the GGUF to be added manually. Thinking is on by
default, so every answer reasons before responding. The chat template has an
`enable_thinking` switch, but the official documentation provides a sampling profile only
for thinking mode. The video says no one had yet measured performance with thinking off.

The release supports English and Chinese. At the time cited, the 2B model had more than
100,000 downloads and the 1B model had 600,000, suggesting substantial use despite limited
public discussion.

## Practical verdict

For experimentation or a lightweight local coding agent, including on a MacBook Air, the
presenter would use the MLX 4-bit build or the Q8 GGUF. He would set `min_p` to 0 and use the
repeat penalty recommended for the task. He considers the model strong for its size but
would still choose Qwen3.5-4B for a large task.

The video's larger point is not that MiniCPM5 always beats a model twice its size. It is that
small local models are approaching the boundary of useful agent work, while operating close
enough to that boundary that one runtime default can determine whether they look excellent
or unusable.

*Source note: This account reflects the presenter's demonstrations, reported vendor tables,
and cited community tests; it does not independently verify them. The source transcript was
automatically captioned, so names and technical terms may contain transcription errors.*
