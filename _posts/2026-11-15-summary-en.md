---
layout: default
title: "Horizon Summary: 2026-11-15 (EN)"
date: 2026-11-15
lang: en
---

> From 23 items, 4 important content pieces were selected

---

**Technology News**
1. [SpaceX catches Starship upper stage on Flight 15; Super Heavy booster splashes down](#item-tech-news-1) ⭐️ 8.0/10
2. [Lovable AI Apps Leak Passport Data and 200K+ Messages via Supabase RLS Misconfiguration](#item-tech-news-2) ⭐️ 8.0/10
3. [DeepSeek V3 Implemented in ~200 Lines of Pure JAX](#item-tech-news-3) ⭐️ 8.0/10
4. [Cloudflare Open-Sources Kitesurf AI Agent Browser](#item-tech-news-4) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [SpaceX catches Starship upper stage on Flight 15; Super Heavy booster splashes down](https://www.spacex.com/launches/starship-flight-15) ⭐️ 8.0/10

SpaceX completed Starship Flight 15 on November 14, 2026, achieving the first successful tower catch of the Starship upper stage \(Ship\) after a roughly 22.5-hour, 14-orbit mission. The Ship returned to the Texas launch site and was captured by the launch tower&\#x27;s mechanical arms. The Super Heavy booster, however, did not return to the tower as planned and instead splashed down in the Gulf of Mexico. The flight also deployed 26 next-generation Starlink V3 satellites.

hackernews · ls612 · Nov 14, 21:22 · [Discussion](https://news.ycombinator.com/item?id=50500963)

**「Background」** Starship is SpaceX&\#x27;s fully reusable two-stage launch system designed for both stages to return to the launch tower for catch by &quot;chopstick&quot; arms. Previous test flights had demonstrated various phases of ascent, reentry, and splashdown, but Flight 15 marks the first time the upper stage was caught by the tower. The Super Heavy booster catch remains to be demonstrated in a future flight.

**「Impact」** The successful Ship catch validates the tower-capture recovery method for the upper stage, a key step toward full reusability. However, the booster splashdown means the system has not yet demonstrated simultaneous recovery of both stages. The Starlink V3 deployment shows Starship can carry operational payloads while testing recovery.

**「Community Discussion」** Commenters compared Starship to the Space Shuttle, noting Starship avoids the Shuttle&\#x27;s side-mounted orbiter and solid boosters that contributed to the Challenger and Columbia disasters. Others debated the final mass fraction to orbit and the significance of Merlin engines lost in previous ocean splashdowns. One user estimated Falcon 9 achieves roughly 60% reusability by cost \(booster plus fairings\).

**Tags**: `#spacex`, `#starship`, `#reusable-rockets`, `#spaceflight`, `#aerospace-engineering`

---

<a id="item-tech-news-2"></a>
### [Lovable AI Apps Leak Passport Data and 200K+ Messages via Supabase RLS Misconfiguration](https://www.crissyfield.de/research/lovable-en/) ⭐️ 8.0/10

Security research by Crissy Field revealed that applications built with the Lovable AI app-building platform exposed passport details and over 200,000 private messages due to insufficient Row-Level Security \(RLS\) in the underlying Supabase database. The vulnerability affected multiple Lovable-generated apps that were published without proper access controls on sensitive data tables. Lovable&\#x27;s Head of Security acknowledged the root cause and stated the platform scans every app before publish and offers free SAST scanning with auto-fix capabilities. The researcher noted the issue is fairly self-explanatory and stems from misconfigured database permissions.

hackernews · armcat · Nov 14, 17:43 · [Discussion](https://news.ycombinator.com/item?id=50499017)

**「Background」** Lovable is an AI-powered platform that generates full-stack applications using Supabase as a backend-as-a-service. Supabase uses PostgreSQL with Row-Level Security policies to control data access, but historically defaulted to permissive settings to reduce onboarding friction, a design choice discussed in Supabase&\#x27;s GitHub discussions. AI-generated code platforms like Lovable automate app creation and deployment, which can amplify configuration mistakes across many applications if secure defaults are not enforced.

**「Impact」** Users of affected Lovable-generated apps had their passport information and private messages exposed to anyone who could inspect network traffic, requiring no sophisticated attack. Developers using AI app builders must verify that database-level security policies are correctly applied before publishing, as automated scanning may not catch all misconfigurations in generated code.

**「Community Discussion」** Commenters debated responsibility: some argued Supabase bears culpability for permissive historical defaults that prioritized ease of onboarding, while others emphasized that platforms like Lovable must enforce deny-by-default databases and automated auth tests to make insecure deployments difficult. Lovable&\#x27;s Head of Security participated directly, describing the platform&\#x27;s pre-publish scanning and auto-fix features as mitigations.

**Tags**: `#security`, `#ai-generated-code`, `#vulnerability-disclosure`, `#supabase`, `#data-breach`

---

<a id="item-tech-news-3"></a>
### [DeepSeek V3 Implemented in ~200 Lines of Pure JAX](https://github.com/Vaibhaav-Tiwari/deepseek-v3-jax) ⭐️ 8.0/10

A developer published a concise, educational implementation of DeepSeek V3 in approximately 200 lines of pure JAX that runs on AMD ROCm hardware. The GitHub repository serves as a learning resource for understanding LLM transformer architecture from first principles. Community members confirmed it runs end-to-end on consumer AMD GPUs like the RX 7600 XT with minimal configuration.

hackernews · VaibhaavTiwari · Nov 14, 15:04 · [Discussion](https://news.ycombinator.com/item?id=50497589)

**「Background」** DeepSeek V3 is a large language model from DeepSeek AI that uses a mixture-of-experts architecture. JAX is a high-performance numerical computing library from Google that supports automatic differentiation and hardware acceleration across CPUs, GPUs, and TPUs. Minimal reference implementations of major LLM architectures have become popular educational tools for engineers learning model internals.

**「Impact」** Engineers with AMD GPUs now have a working, readable reference for running and studying a modern MoE model locally without CUDA dependencies. One user reported successful execution on an RX 7600 XT 16GB after setting HSA\_OVERRIDE\_GFX\_VERSION=11.0.0 to work around JAX&\#x27;s gfx1102 rejection.

**「Community Discussion」** Commenters praised the implementation&\#x27;s educational value and motivational effect for learning LLM internals. A user requested a roadmap for building intuition around such implementations, while another confirmed the code ran immediately on their Fedora ROCm setup, calling it the first project to work end-to-end on their hardware.

**Tags**: `#jax`, `#deepseek`, `#llm-implementation`, `#open-source`, `#education`

---

<a id="item-tech-news-4"></a>
### [Cloudflare Open-Sources Kitesurf AI Agent Browser](https://www.phoronix.com/news/Cloudflare-Kitesurf-Open-Source) ⭐️ 8.0/10

Cloudflare has released Kitesurf, an open-source stateless browser designed for AI agents, under the Apache 2.0 license with code available on GitHub. Built on Cloudflare Workers, Kitesurf parses HTML, processes CSS, and executes JavaScript without requiring browser containers. Cloudflare states it consumes less CPU and memory than Chromium and can scale on-demand across its global Workers network.

telegram · zaihuapd · Nov 14, 09:33

**「Background」** Traditional browser automation for AI agents typically relies on headless Chromium instances running in containers, which incur significant resource overhead. Cloudflare Workers provides a serverless execution environment that runs code at the edge; Kitesurf leverages this platform to eliminate container management and reduce resource consumption for AI-driven web interactions.

**「Impact」** Developers can now deploy AI agent browser tasks directly on Cloudflare Workers without provisioning or managing browser containers, benefiting from lower resource usage and automatic global scaling. The Apache 2.0 license permits immediate adoption and modification for production or research use.

**Tags**: `#AI agents`, `#browser automation`, `#Cloudflare Workers`, `#open source`, `#serverless`

---