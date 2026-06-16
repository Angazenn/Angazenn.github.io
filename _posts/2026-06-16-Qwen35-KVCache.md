---
layout: post
title: "vLLM-Ascend中Qwen3.5 KV Cache管理实现"
date: 2026-06-16 09:00:00 +0700
categories: general
description: "介绍vLLM/vLLM-Ascend中当前Qwen3.5 GDN + Full Attention的KV Cache实现."
---

Qwen3.5代表了Qwen系列模型的最新一代架构，其创新的使用了GDN、Full Attention交替的Attention架构。本文将介绍vLLM、vLLM-Ascend中对Qwen3.5的混合KV Cache方案设计，并记录在实际部署过程中所遇到的一系列问题。

## Qwen3.5（GDN）简介

## Hybrid KV Cache

### vLLM

vLLM当前采用HMA的方式来实现Hybrid KV Cache管理，其核心是同一块KV Cache tensor（本文称其为一块shared_by tensor）可以由不同attention group（可以在不同层）共享。这里可以参考Mengqing佬的讲解 [vLLM 中的几种 KVCache 分组机制](https://mengqingcao.github.io/posts/vllm-kvcache-grouping/)。

对于Qwen3.5而言，尽管其有不同参数量的模型，但基本遵循了3层Linear Attention + 1层Full Attention交替构成的架构。因此在vLLM中，Qwen3.5的KV Cache被自然地分成了4组，每一块shared_by由4组中各出一层（实际上也就是连续的4层）来共享。在每一块shared_by中，full attention block会被强制要求增大block_size，从而让其page_size与GDN block对齐

### vLLM-Ascend

vLLM-Ascend当前基本复用了vLLM对Qwen3.5的Hybrid KV Cache设计，但仍然有一点关键差异：vLLM-Ascend当前使用的Attention算子必须要求k cache tensor与v cache tensor各自为连续tensor，而vLLM GPU Attention后端（例如flash infer）支持kv cache按非连续方式存储。考虑仅有Full Attention的情况，两边的差异为：

*vLLM-Ascend*

|       | block 0 | block 1 | block 2 | ... |
|-------|-----|-------|-------|-------|
| K Cache Tensor  |   k |   k |   k | ... |
| V Cache Tensor  |   v|   v |   v | ... |

*vLLM*

|       | block 0 | block 1 | block 2 | ... |
|-------|-----|-------|-------|-------|
| KV Cache Tensor  |   k,v |   k,v |   k,v | ... |

换而言之，

## Prefix-Cache

### Align Mode

### 叠加MTP

### Marconi-Style Admission
