---
title: This Tiny Coding Model Shouldn’t Be This Good (MiniCPM5)
author: Better Stack
channel: Better Stack
url: https://youtu.be/Wik_JQ-enUA?is=OP0xxddCC80JHitq
date: 2026-09-15 13:30
tags: ai, development
---

# This Tiny Coding Model Shouldn’t Be This Good (MiniCPM5)
## Core claim

- Better Stack's Josh tests whether MiniCPM5-2B can work as a local coding agent.
- He says small models often chat well but hallucinate tool schemas, forget them, or loop.
- Vendor SWE-bench Verified scores shown are 5 for Qwen3.5-2B and 2 for Gemma 4 E2B.
- MiniCPM5 scores 46, above those models and Qwen3.5-4B's reported 34.

## Model and training

- OpenBMB's text-only model is branded 2B and described as a dense 2.5B-parameter model.
- It has 42 layers, grouped-query attention, and a plain `LlamaForCausalLM` architecture.
- Native context is about 128,000 tokens; the license is Apache 2.0 with open datasets.
- Training used 500,000 agent trajectories, supervised fine-tuning, and RL.
- Sixteen separate RL expert models were merged into the final model.
- Unlike MiniCPM4, it drops custom sparse attention and multi-token prediction.
- The standard design improves support in MLX, llama.cpp, and WebLLM.

## Demonstrations

- On a Mac, Josh installs MLX-LM with pip in a virtual environment.
- The quantized file is 1.3 GB and returns a thinking block, answer, and speed counter.
- Older MLX-LM versions ignore its end-of-sequence list and may never stop generating.
- Interactive chat works, and llama.cpp serves the model to an OpenAI client.
- Given a weather tool, it emits a structured call and a proper `tool_calls` array.

## Benchmark balance

- Against Qwen3.5-4B, MiniCPM5 leads LiveCodeBench 69-56 and SWE-bench Verified 46-34.
- It loses SWE-bench Pro 14-28 and Terminal-Bench about 8.5-26.
- Qwen also wins MMLU-Pro, GPQA Diamond, LongBench v2, and instruction following.
- Josh accepts “4B class” for some code, tool, math, and agent work, not overall ability.
- All shown benchmarks are vendor-run; the table compares only Qwen and Gemma.
- It omits Llama, Phi, SmolLM3, and MiniCPM4; requested evaluation scripts were unavailable.

## Quantization warning and verdict

- A GitHub HumanEval+ test gave Q8 about 43, with 55% of generations repeating endlessly.
- Q4_K_M scored about 6, with 92% running away into repetition.
- A 1.15 repeat penalty raised Q8 to 92 and Q4 to 71.
- OpenBMB later said llama.cpp's default `min_p` 0.05 should be 0.
- Josh recommends MLX 4-bit or Q8 GGUF, `min_p` 0, and the task's repeat penalty.
- Thinking defaults on; no non-thinking profile or reported measurement was available.
- Ollama needed a custom model file, while LM Studio required manual GGUF import.
- English and Chinese are supported; cited downloads exceed 100,000 for 2B and 600,000 for 1B.
- He would experiment locally, even on a MacBook Air, but use Qwen3.5-4B for large tasks.
*Source caveat: These are presenter, vendor, and cited community claims, not independent checks.*
*The source uses automatic captions, which may misrender model names or technical terms.*
