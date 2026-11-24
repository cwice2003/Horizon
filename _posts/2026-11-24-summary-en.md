---
layout: default
title: "Horizon Summary: 2026-11-24 (EN)"
date: 2026-11-24
lang: en
---

> From 26 items, 4 important content pieces were selected

---

**Technology News**
1. [Ladybird browser engine reaches alpha with strong real-world compatibility](#item-tech-news-1) ⭐️ 9.0/10

**Technology Blog**
1. [vLLM Day-0 Support for ERNIE 5.5 Flash Preview via Plugin](#item-tech-blog-1) ⭐️ 8.0/10

**Financial News**
1. [New York Fed President Signals Gradual Rate Hikes Ahead](#item-finance-news-1) ⭐️ 8.0/10
2. [Nvidia Reinstates Huang as CEO, Sparking Relief Rally After 9% S&amp;P 500 Correction](#item-finance-news-2) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Ladybird browser engine reaches alpha with strong real-world compatibility](https://ladybird.org/posts/alpha/) ⭐️ 9.0/10

The Ladybird browser project released its first alpha version on November 23, 2026, making the independent browser engine available for download on macOS and Linux without requiring compilation. Ladybird is built from scratch — not a fork of Chromium, WebKit, or Gecko — and implements its own HTML parsing, CSS engine, layout, JavaScript, and WebAssembly, while using external libraries including HarfBuzz for text shaping, Skia for 2D graphics, ffmpeg for video, and SQLite. The alpha uses a multi-process architecture with per-tab isolation. In October 2026, the project gained 75,650 new passes on the web-platform-tests suite \(reaching 2,184,722 subtests passed\), surpassing Safari&\#x27;s 2,172,990 and approaching Firefox&\#x27;s 2,189,315. The project attributes much of this rapid progress to AI coding agents \(Claude Code and Codex\) filling in missing functionality. The alpha release notes warn that some websites will not work and crashes may occur; service worker support is incomplete \(Datasette Lite fails with &quot;navigator.serviceWorker.startMessages&quot; undefined\).

hackernews · janvdberg · Nov 23, 16:13 · [Discussion](https://news.ycombinator.com/item?id=50614249)

**「Background」** Ladybird originated from the SerenityOS project, a hobbyist operating system written from scratch. In February 2026, the project announced it had ported 25,000 lines of its LibJS JavaScript engine from C++ to Rust in two weeks using AI coding agents. The October 2026 development surge included moving style and layout to a separate thread, landing a new JavaScript JIT, and replacing the Cranelift WebAssembly engine with new code achieving a 7x speedup on the JetStream 3 WASM benchmark. The alpha release marks the first time users can install pre-built binaries rather than compiling from source.

**「Impact」** Developers and early adopters can now test a genuinely independent browser engine that renders complex real-world applications — including WebAssembly-based tools like ffmpeg.wasm and Pyodide — with compatibility approaching Firefox on web-platform-tests. The alpha&\#x27;s multi-process architecture provides site isolation comparable to Chrome. However, the incomplete service worker implementation and acknowledged instability mean it is not yet suitable as a daily driver for general users. Security researchers are explicitly invited to test the browser, with crash reporting built in.

**「Community discussion」** Early testers report strong real-world compatibility: one user confirmed every site tested rendered correctly \(with only minor jerky scrolling\), while another found NoVNC \(web-based remote desktop\) snappier than in Firefox. A commenter noted that adopting production-grade libraries like SQLite and Skia accelerated progress but reduced the &quot;hacker spirit&quot; of the original SerenityOS approach. Others raised questions about fingerprinting resistance and security precautions for alpha usage.

**Tags**: `#browser-engine`, `#ladybird`, `#web-standards`, `#open-source`, `#software-engineering`

---

## Technology Blog

<a id="item-tech-blog-1"></a>
### [vLLM Day-0 Support for ERNIE 5.5 Flash Preview via Plugin](https://vllm.ai/blog/2026-11-24-ernie-5-5-flash-preview) ⭐️ 8.0/10

rss · vLLM Blog · Nov 24, 00:00

**「Background」** The Baidu ERNIE team and vLLM community collaborated to deliver day-0 inference support for ERNIE 5.5 Flash Preview, a 280B-parameter sparse MoE model with 14B activated parameters per token and 1M-token context, without requiring a vLLM fork or custom Docker image.

**「Solution」** Support arrives through the standalone vLLM-ERNIE plugin, which registers the model architecture via vLLM&\#x27;s general\_plugins entrypoint and loads only when ERNIE configs are detected. The teams co-designed a full-stack acceleration pipeline: dedicated fused kernels for VHA cross-head mixing \(1.56–1.73×\), Multi-Router Latent MoE routing \(3.54–6.10×\), MultiMax output head \(4.33–6.53×\), and gated attention \(1.55–1.75×\) eliminate intermediate tensor round-trips while preserving bitwise numerics; FlashIndexer adds a lightweight dynamic head router with threshold pre-filtering that cuts sparse indexing cost by 40% at 1M context; FP4 quantization-aware training aligns training-time fake quantization with inference MXFP4 \(W4A8\) numerics for routed experts, with FP8 elsewhere and FP8 KV cache; and a multi-stage DSpark speculative decoding pipeline—trained via mid-training, post-training, and on-policy distillation—achieves &gt;4.0 mean acceptance length on coding and agent workloads with up to 7 draft tokens per step.

**「Takeaway」** The plugin model demonstrates how new model architectures can integrate with vLLM on release day while immediately inheriting upstream features like prefix caching, PD disaggregation, and CUDA graphs, establishing a reusable pattern for vendor-community co-development that avoids forks and nightly dependencies.

**Tags**: `#vLLM`, `#Mixture-of-Experts`, `#Kernel Fusion`, `#Speculative Decoding`, `#Model Deployment`

---

## Financial News

<a id="item-finance-news-1"></a>
### [New York Fed President Signals Gradual Rate Hikes Ahead](https://www.cnbc.com/2026/11/23/john-williams-fed-inflation-rate-hikes.html) ⭐️ 8.0/10

New York Fed President John Williams said policymakers still have work to do to bring inflation to the 2% target, indicating further rate increases will unfold over time as the economy grows. He projected inflation nearing 2% in 2027 and reaching it in 2028, with markets fully pricing a 25-basis-point hike at the December 8-9 FOMC meeting from the current 3.75%-4% range.

rss · CNBC Finance · Nov 23, 21:02

**「Background」** Williams, a permanent FOMC voter, delivered the last major Fed communication before the December policy meeting, attributing current price pressures to the Iran conflict, AI-related demand, and tariffs whose effects he said have largely faded.

**Tags**: `#Federal Reserve`, `#monetary policy`, `#inflation`, `#interest rates`, `#John Williams`

---

<a id="item-finance-news-2"></a>
### [Nvidia Reinstates Huang as CEO, Sparking Relief Rally After 9% S&amp;P 500 Correction](https://www.cnbc.com/2026/11/23/nvidia-jensen-huang-ceo-market-rally.html) ⭐️ 8.0/10

Nvidia reinstated Jensen Huang as CEO on Monday, sparking a relief rally after the S&amp;P 500 tumbled more than 9% into correction territory following his Nov. 12 departure announcement.

rss · CNBC Finance · Nov 23, 18:00

**「Background」** The sell-off began before Huang&\#x27;s exit, driven by concerns over financing the AI buildout, data-center approvals after Democratic midterm wins, and fears that hyperscaler capital spending may have peaked.

**「Impact」** Strategists warn the rally may fade because the &quot;picks and shovels&quot; AI trade remains dependent on the pace of capital expenditure and faces congressional scrutiny, leaving the durable bottom uncertain.

**Tags**: `#Nvidia`, `#Jensen Huang`, `#AI trade`, `#market correction`, `#CEO change`, `#market sentiment`

---