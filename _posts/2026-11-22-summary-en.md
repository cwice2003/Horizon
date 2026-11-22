---
layout: default
title: "Horizon Summary: 2026-11-22 (EN)"
date: 2026-11-22
lang: en
---

> From 17 items, 4 important content pieces were selected

---

**Technology News**
1. [Lean formalizes Riemann Hypothesis proof with AI and multi-kernel verification](#item-tech-news-1) ⭐️ 8.0/10
2. [Graham Dumpleton Announces Muru: AI-Assisted Rust Server for ASGI/WSGI Python Apps](#item-tech-news-2) ⭐️ 8.0/10
3. [Zhejiang University Achieves First On-Chip QRAM Implementation](#item-tech-news-3) ⭐️ 8.0/10

**Technology Blog**
1. [To Code Well, Avoid Blunders](#item-tech-blog-1) ⭐️ 6.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Lean formalizes Riemann Hypothesis proof with AI and multi-kernel verification](https://leanprover-community.github.io/blog/posts/riemann-hypothesis/) ⭐️ 8.0/10

On November 20, 2026, Levent Alpöge published a Lean formalization of a proof of the Generalized Riemann Hypothesis totaling approximately 17 million lines of code. The Lean FRO and Mathlib Initiative jointly certified the statement and proof on November 21, confirming the proposition matches Mathlib&\#x27;s RiemannHypothesis, the codebase compiles without errors, and multiple independent kernel checkers — con-leche and con-ron — validated the proof. An LLM \(Claude\) was used to formalize a substantial portion of the required modern mathematics, with Alpöge directing the process.

hackernews · g-b-r · Nov 21, 14:36 · [Discussion](https://news.ycombinator.com/item?id=50589618)

**「Background」** The Riemann Hypothesis, concerning the zeros of the Riemann zeta function, is one of the most famous unsolved problems in mathematics. Lean is a proof assistant based on dependent type theory; Mathlib is its community-maintained mathematical library. Independent kernel checkers such as con-leche and con-ron are separate implementations of Lean&\#x27;s trusted kernel, written in different languages and with their own consistency proofs, providing cross-validation that reduces the risk of a single kernel bug invalidating a result.

**「Impact」** This work demonstrates that AI-assisted formalization can scale to encode vast swathes of modern mathematics and that multi-kernel verification provides a practical defense against kernel-level bugs. Developers of proof assistants and formal verification tools now have a concrete, large-scale case study showing how LLM-driven formalization combined with independent kernel checking can increase confidence in mechanically checked proofs.

**「Community discussion」** Commenters note that while multi-kernel verification makes a kernel bug extremely unlikely, a fake Collatz conjecture refutation previously passed one independent checker, so the checkers are not fully independent. Several emphasize that Alpöge&\#x27;s expertise in directing Claude was crucial — the result reflects a human–AI collaboration rather than autonomous AI proof discovery.

**Tags**: `#formal-verification`, `#lean-theorem-prover`, `#ai-assisted-proofs`, `#riemann-hypothesis`, `#proof-assistants`

---

<a id="item-tech-news-2"></a>
### [Graham Dumpleton Announces Muru: AI-Assisted Rust Server for ASGI/WSGI Python Apps](https://simonwillison.net/2026/Nov/21/muru/) ⭐️ 8.0/10

Graham Dumpleton, creator of the 20-year-old mod\_wsgi project, has announced Muru, a new AI-assisted Rust server designed to run both ASGI and WSGI Python applications in development and production. The project is being developed publicly with extensive technical documentation published across 18 blog posts from November 4–21, 2026, covering architecture, worker design, HTTPS in development, canary deployments, Kubernetes integration, scaling to zero, and an integrated debugging toolbar. The source code is available at github.com/muruhq/muru.

rss · Simon Willison · Nov 21, 23:56

**「Background」** Dumpleton created mod\_wsgi in 2006, which became a foundational component for deploying Python web applications under Apache. His new project applies two decades of production deployment experience and an AI-assisted development methodology he previously used for the wrapture project. Muru aims to address long-standing operational challenges such as zero-downtime releases, container-friendly resource usage, and unified ASGI/WSGI support without requiring a service mesh.

**「Impact」** Python teams evaluating production servers gain a new Rust-based option that promises unified ASGI/WSGI support, built-in canary deployments, and Kubernetes-native scaling — features that currently require assembling multiple tools. The detailed public design notes let operators assess architectural trade-offs before adoption, though the project has not yet announced a stable release or production readiness milestone.

**Tags**: `#python`, `#rust`, `#web-servers`, `#asgi`, `#wsgi`, `#ai-assisted-development`

---

<a id="item-tech-news-3"></a>
### [Zhejiang University Achieves First On-Chip QRAM Implementation](https://finance.sina.com.cn/stock/2026-11-21/doc-iniznhsk3530826.shtml) ⭐️ 8.0/10

Zhejiang University researchers have demonstrated the first experimental implementation of a quantum random-access memory \(QRAM\) on a real superconducting quantum processor, the Tianmu 2 chip. The 4-bit and 8-bit prototypes achieved 80.9% and 60.4% accuracy respectively, reduced circuit depth by over 30% compared to unoptimized approaches, and showed local noise resilience. The work is published in Nature Physics. The team plans to scale up QRAM in future research.

telegram · zaihuapd · Nov 21, 08:31

**「Background」** QRAM is a theoretical quantum memory model that allows superposition-based addressing of classical data, a key subroutine for many quantum algorithms. Prior to this experiment, QRAM had only been simulated or implemented in limited photonic systems, not on superconducting qubit hardware.

**「Impact」** The demonstrated fidelity and depth reduction provide a concrete benchmark for integrating QRAM into superconducting quantum algorithms, enabling researchers to evaluate memory-access overhead and error-correction requirements for practical deployments.

**Tags**: `#quantum computing`, `#QRAM`, `#superconducting qubits`, `#quantum memory`, `#Nature Physics`

---

## Technology Blog

<a id="item-tech-blog-1"></a>
### [To Code Well, Avoid Blunders](https://seangoedecke.com/to-code-well-avoid-blunders/) ⭐️ 6.0/10

rss · Sean Goedecke · Nov 22, 00:00

**「Background」** The author argues that durable code quality in large commercial codebases stems from avoiding catastrophic mistakes rather than pursuing clever abstractions, since a single blunder can irreversibly degrade an elegant system.

**「Solution」** The cardinal sins are inconsistency and unnecessary requirements: inconsistency breaks trust by forcing engineers to hunt for surprises, while unnecessary requirements persist because they&\#x27;re sticky and create combinatorial explosion when new features must interoperate with them. To avoid blunders, engineers should fit each task into the codebase as normally as possible and trim requirements to the smallest viable set, treating clever patterns or &quot;extra credit&quot; features as warning signs of distraction. The author notes current AI agents match humans on consistency but struggle to avoid unnecessary requirements.

**「Takeaway」** In large-team codebases, attention to detail and ruthless focus on consistency and minimal requirements matter more than cleverness for producing maintainable software.

**Tags**: `#software-engineering`, `#code-quality`, `#technical-debt`, `#large-codebases`, `#engineering-philosophy`

---