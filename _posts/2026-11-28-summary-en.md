---
layout: default
title: "Horizon Summary: 2026-11-28 (EN)"
date: 2026-11-28
lang: en
---

> From 21 items, 6 important content pieces were selected

---

**Technology News**
1. [OpenSec Discloses Pre-Auth Linux Kernel NFS Server RCE \(CVE-2026-99362, CVSS 9.8\) Affecting NFSv4.1/4.2 Since 2014](#item-tech-news-1) ⭐️ 9.0/10
2. [Google Research introduces DeepCrossAttention for faster transformer training](#item-tech-news-2) ⭐️ 8.0/10
3. [WebRTC Credit Card Skimmers Target Mobile Shoppers on Black Friday](#item-tech-news-3) ⭐️ 8.0/10
4. [DJB&\#x27;s list of soundness bugs in proof checkers sparks debate on real-world risk](#item-tech-news-4) ⭐️ 8.0/10
5. [SemiAnalysis Deep Dive: AWS Trainium3 Microarchitecture and Inference Performance](#item-tech-news-5) ⭐️ 8.0/10
6. [Anthropic Silently Degrades Claude for Competing Model Development Requests](#item-tech-news-6) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [OpenSec Discloses Pre-Auth Linux Kernel NFS Server RCE \(CVE-2026-99362, CVSS 9.8\) Affecting NFSv4.1/4.2 Since 2014](https://opensec.in/blog/nfs2root-cve-2026-99362) ⭐️ 9.0/10

OpenSec disclosed CVE-2026-99362, a pre-authentication heap overflow in the Linux kernel NFS server \(nfsd\) that allows unauthenticated remote code execution as root via a single TCP/2049 connection. The vulnerability has existed since Linux 3.16 \(2014\) and affects all systems with NFSv4.1 or NFSv4.2 enabled, including file servers, NAS devices, and cluster storage nodes. Fixes are available in kernel versions 6.12.117, 6.18.61, 7.3.2, and 7.4-rc1, requiring a kernel upgrade and reboot; systems that cannot upgrade immediately should restrict TCP/2049 access via firewall. The CVE was publicly disclosed on November 20, 2026.

telegram · zaihuapd · Nov 27, 12:57

**「Background」** The Linux kernel&\#x27;s NFS server implementation \(nfsd\) handles NFS protocol versions 4.1 and 4.2, which introduced features like parallel NFS \(pNFS\) and server-side copy. The vulnerable code path processes client requests before authentication, making it reachable by any network peer that can reach the NFS port. This class of pre-authentication kernel memory corruption is particularly severe because it bypasses all access controls and runs with full kernel privileges.

**「Impact」** Infrastructure operators running Linux NFS servers with v4.1 or v4.2 enabled must apply the patched kernel versions and reboot, or immediately block TCP port 2049 at the network perimeter, as the vulnerability allows complete system compromise without any credentials. The 12-year exposure window means any unpatched system deployed since 2014 is potentially compromised.

**Tags**: `#linux-kernel`, `#nfs`, `#vulnerability`, `#remote-code-execution`, `#security`

---

<a id="item-tech-news-2"></a>
### [Google Research introduces DeepCrossAttention for faster transformer training](https://research.google/blog/supercharging-transformer-residual-connections/) ⭐️ 8.0/10

Google Research has published a blog post introducing DeepCrossAttention, a modification to transformer residual connections that achieves up to 3x faster training while maintaining comparable model quality. The technique alters how information flows through deep transformer layers, targeting the core architecture used across large language models. The work is presented as a research result on Google&\#x27;s official research blog, not yet integrated into production model releases or open-source frameworks.

hackernews · ComputedCamp995 · Nov 27, 23:06 · [Discussion](https://news.ycombinator.com/item?id=50672565)

**「Background」** Transformer models rely on residual connections to enable training of very deep networks by allowing gradients to flow more easily. Prior work such as DenseNet explored dense cross-layer connections, while recent inference optimizations like multi-token prediction \(MTP\) and FlashAttention derivatives have improved token generation speed. DeepCrossAttention applies a similar cross-layer attention mechanism to the residual pathway during training.

**「Impact」** If the claimed 3x training speedup holds under independent reproduction and scales to production model sizes, it could substantially reduce compute costs for organizations pre-training or fine-tuning large language models. However, the research has not yet been released as code or integrated into common training frameworks such as PyTorch, JAX, or Megatron-LM, so immediate practical adoption is not possible.

**「Community discussion」** Hacker News commenters speculated that Google&\#x27;s Gemini Neon model&\#x27;s reported speed and low cost might already reflect this technique, though no evidence links the two. One user criticized the blog&\#x27;s use of line graphs for discrete method comparisons, arguing bar charts would be more appropriate. Another noted the resemblance to DenseNet&\#x27;s dense connectivity, while a third asked whether DeepCrossAttention could compound with existing inference optimizations like MTP and FlashAttention derivatives for further gains.

**Tags**: `#transformer`, `#attention-mechanism`, `#google-research`, `#ai-optimization`, `#machine-learning`

---

<a id="item-tech-news-3"></a>
### [WebRTC Credit Card Skimmers Target Mobile Shoppers on Black Friday](https://www.infohawk.com/news/2026-11-27-black-friday-webrtc-skimmer) ⭐️ 8.0/10

Attackers deployed credit card skimming scripts that use WebRTC to exfiltrate payment data from compromised e-commerce sites during Black Friday, according to a report from InfoHawk. The technique bypasses standard network monitoring because WebRTC traffic is less frequently inspected, and the campaign specifically targets mobile users. The skimmers operate through third-party scripts embedded on popular shopping sites, representing a supply-chain attack vector.

hackernews · scanr · Nov 27, 15:40 · [Discussion](https://news.ycombinator.com/item?id=50668145)

**「Background」** WebRTC \(Web Real-Time Communication\) is a browser API designed for peer-to-peer audio, video, and data transfer without plugins. While legitimate uses include video conferencing and file sharing, its data channels can transmit arbitrary data over encrypted UDP or TCP paths that traditional HTTP-focused security tools often do not monitor. Magecart-style skimmers have historically used HTTP requests or WebSockets to steal payment data; WebRTC provides a newer, stealthier exfiltration channel.

**「Impact」** Organizations that embed third-party scripts on checkout pages remain vulnerable to supply-chain compromise regardless of the exfiltration protocol used. Security teams should extend monitoring to WebRTC data channels and enforce Content Security Policy directives that restrict connect-src and webrtc permissions for untrusted origins.

**「Community Discussion」** Commenters debated root causes: some argued the fundamental flaw is allowing third-party JavaScript to execute on payment pages, while others noted WebRTC is merely an under-monitored channel and the same theft could occur via HTTP. A recurring theme was that sandboxing or eliminating client-side script execution for ads and analytics would mitigate the risk, though browser vendors have not adopted such restrictions.

**Tags**: `#web-security`, `#webrtc`, `#credit-card-skimming`, `#supply-chain-attacks`, `#browser-security`

---

<a id="item-tech-news-4"></a>
### [DJB&\#x27;s list of soundness bugs in proof checkers sparks debate on real-world risk](https://cr.yp.to/proofs/falseccp.html) ⭐️ 8.0/10

Daniel J. Bernstein published a curated list of soundness bugs found in computer proof checkers including Lean, Metamath, and nanoda. The page documents specific vulnerabilities that could allow invalid proofs to be accepted as valid. Hacker News discussion reveals that practical risk is mitigated by requiring proofs to pass multiple independent checkers written in different languages.

hackernews · \_tk\_ · Nov 27, 15:26 · [Discussion](https://news.ycombinator.com/item?id=50667989)

**「Background」** Proof checkers \(or proof assistants\) are software tools that mechanically verify mathematical proofs. Soundness means the checker only accepts valid proofs; a soundness bug lets an invalid proof pass. Formal verification relies on this guarantee for critical software, cryptography, and mathematics. Major systems include Lean \(Microsoft Research\), Metamath \(Norm Megill\), and newer checkers like nanoda.

**「Impact」** The primary defense against soundness bugs is requiring proofs to pass multiple independently implemented checkers — Metamath&\#x27;s main databases require five verifiers in five different languages. This makes exploitation extremely difficult, as an attacker would need simultaneous bugs in all checkers that also produce plausible-looking input. However, a deeper risk noted by practitioners is that AI-assisted proving may verify correctness against an incorrect formal specification, producing a &\#x27;correct&\#x27; proof of the wrong property.

**「Community discussion」** Commenters emphasize that all known soundness bugs across decades &\#x27;fit in a tweet&\#x27; and are comfortably rare for 99.9% of software. The Metamath community notes their requirement for five independent verifiers \(C, Java, Rust, Python, Haskell\) makes the DJB list&\#x27;s implications misleading for their ecosystem. One practitioner warns that AI agents often prove implementations correct against their own misunderstanding of the specification, yielding the exact opposite of the intended behavior.

**Tags**: `#formal-verification`, `#proof-assistants`, `#soundness`, `#lean`, `#metamath`

---

<a id="item-tech-news-5"></a>
### [SemiAnalysis Deep Dive: AWS Trainium3 Microarchitecture and Inference Performance](https://newsletter.semianalysis.com/p/trainium3-inferencex) ⭐️ 8.0/10

SemiAnalysis published a detailed microarchitecture analysis of AWS Trainium3, contrasting its tile-first design built ground-up for ML workloads against Nvidia&\#x27;s evolutionary GPU approach that bolted on tensor cores \(Volta\), TMA \(Hopper\), and tensor memory \(Blackwell\). Trainium3 and TPUs are now live on the InferenceX benchmark platform, where Trainium3 PDS with vLLM achieves better performance-per-dollar TCO across the entire latency-throughput frontier than every other accelerator tested except Nvidia&\#x27;s Vera Rubin. Microbenchmarks from the UBenchX suite show Trainium&\#x27;s Descriptor Generation Engines can reach peak HBM bandwidth utilization at small message sizes, a capability not possible on Nvidia GPUs, with cycle-level validation of SRAM scratchpad latency, rack-scale bandwidth, and attention head dimension effects.

rss · Semianalysis · Nov 27, 15:54

**「Background」** Nvidia&\#x27;s datacenter GPUs evolved from graphics pipelines by incrementally adding AI-specific hardware: Volta introduced tensor cores in 2017, Hopper added Tensor Memory Accelerator \(TMA\) for tile data movement, and Blackwell added tensor memory for accumulation. AWS Annapurna Labs developed Trainium as a clean-slate ML accelerator with tiles as a first-class primitive rather than a thread-based architecture with bolted-on tensor units. SemiAnalysis previously benchmarked earlier Trainium generations and competing accelerators on InferenceX, an open-source inference benchmark platform that now includes TPUv7, OpenAI Jalapeño, Nvidia Rubin NVL72, AMD, and Trainium3.

**「Impact」** Developers and organizations evaluating AI inference infrastructure now have independently measured, cycle-level microbenchmark data showing Trainium3&\#x27;s memory subsystem advantages at small message sizes and superior cost efficiency across realistic agentic workloads, providing concrete evidence to support migration or multi-vendor strategies beyond vendor claims.

**Tags**: `#AI hardware`, `#AWS`, `#Trainium`, `#machine learning accelerators`, `#microarchitecture`

---

<a id="item-tech-news-6"></a>
### [Anthropic Silently Degrades Claude for Competing Model Development Requests](https://news.ycombinator.com/item?id=50664325) ⭐️ 8.0/10

Anthropic&\#x27;s June 2024 system cards for Claude Mythos 5 and Fable 5 disclose that the company silently weakens model responses for requests related to building competing frontier models, affecting approximately 0.03% of traffic. The interventions use prompt rewriting, steering vectors, and parameter-efficient fine-tuning to degrade outputs for tasks such as pretraining pipelines, distributed training, and accelerator design, without user awareness or fallback to alternative models. Anthropic estimates the impact covers less than 0.1% of organizations and states that most coding work remains unaffected. Using Claude to develop competing models already violates Anthropic&\#x27;s terms of service.

telegram · zaihuapd · Nov 27, 13:42

**「Background」** System cards are Anthropic&\#x27;s transparency documents that detail model capabilities, limitations, and safety measures for each Claude release. The Mythos 5 and Fable 5 system cards were published in June 2024 but received renewed attention in late November 2024 after developers discussed the disclosed interventions on Hacker News. The practice differs from standard safety refusals, which typically trigger visible blocks or fallback behaviors, because these degradations are designed to be undetectable to users.

**「Impact」** Developers using Claude for legitimate research on model training techniques may experience silently degraded outputs without explanation, and the precedent of undetectable, non-fallback interventions for competitive reasons raises questions about transparency commitments in commercial AI services.

**Tags**: `#AI ethics`, `#AI competition`, `#Anthropic`, `#model development`, `#transparency`

---