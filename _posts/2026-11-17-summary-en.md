---
layout: default
title: "Horizon Summary: 2026-11-17 (EN)"
date: 2026-11-17
lang: en
---

> From 28 items, 6 important content pieces were selected

---

**Technology News**
1. [vLLM v0.34.0: Extensible KV Cache Default, Model Runner V2 Only, 10 New Models](#item-tech-news-1) ⭐️ 8.0/10
2. [Carnegie Mellon launches free CS courses on YouTube with student-built automation](#item-tech-news-2) ⭐️ 8.0/10
3. [Jiff 1.0: New Rust datetime library from burntsushi](#item-tech-news-3) ⭐️ 8.0/10
4. [Optimizely Supply-Chain Attack Injects Malware on Major Sites](#item-tech-news-4) ⭐️ 8.0/10

**Financial News**
1. [Nvidia CEO Resignation and Democratic Congress Reshape AI Trade Outlook](#item-finance-news-1) ⭐️ 8.0/10
2. [Commerce Secretary Lutnick Scrutinized Over Nvidia Ties Amid Chip Smuggling Probe](#item-finance-news-2) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [vLLM v0.34.0: Extensible KV Cache Default, Model Runner V2 Only, 10 New Models](https://github.com/vllm-project/vllm/releases/tag/v0.34.0) ⭐️ 8.0/10

vLLM v0.34.0 releases with 1,061 commits from 412 contributors, enabling extensible KV cache by default to size cache from actual free memory after warmup, removing legacy Model Runner V1 so V2 is now the only GPU execution path, and adding 10 new models including Mistral Large 4, MiniMax-M3.1-Flash, and Nemotron-3.5-Transcribe. The release delivers up to 1.95× decode throughput on GB200 \(Step5 NVFP4 MoE\), 1.6× output throughput on GLM-5.3-Flash via DeepGEMM FP8 MegaMoE, and 1.24–1.40× faster long-prompt TTFT on GLM-5.3. Breaking changes include default block size changing from 16 to 64, ROCm 7.2 artifacts dropped in favor of ROCm 10.0, and a new requirement for huggingface\_hub &gt;= 2.0.0.

github · khluu · Nov 16, 23:22

**「Background」** vLLM is an open-source LLM inference engine widely used for high-throughput serving of large language models on GPUs. The extensible KV cache feature, previously opt-in, dynamically calculates available GPU memory after CUDA graph capture and warmup rather than relying on static estimates, allowing larger cache allocations. Model Runner V2 has been in development as a unified execution engine replacing the original V1 architecture, supporting features like dual-batch overlap, speculative decoding, and disaggregated prefill/decode. This release marks the completion of that migration.

**「Impact」** Operators upgrading to v0.34.0 must remove any VLLM\_USE\_V2\_MODEL\_RUNNER=0 environment variable \(startup will now fail\), adjust --block-size to 16 if the previous default is needed \(ROCm paged attention remains at 16\), and either accept the new extensible KV cache default \(gpu\_memory\_utilization=1.0\) or opt out with --gpu-memory-utilization 0.9 or --no-enable-extensible-kv-cache. ROCm users must migrate to ROCm 10.0 wheels and images. The new default block size of 64 may increase memory fragmentation for some workloads; the release notes note per-token decode latency can rise 6–18% on some H200 models at concurrency 128 with extensible KV cache enabled.

**Tags**: `#vLLM`, `#LLM inference`, `#open source`, `#GPU acceleration`, `#performance optimization`

---

<a id="item-tech-news-2"></a>
### [Carnegie Mellon launches free CS courses on YouTube with student-built automation](https://www.cs.cmu.edu/learn/) ⭐️ 8.0/10

Carnegie Mellon University&\#x27;s Griffin School of Computer Science launched CS Learn, releasing full-semester lectures from current computer science courses for free on YouTube. The initial rollout includes one course premiering daily this week, with additional courses arriving in January, covering topics such as probability and computing \(15-259\), ML systems, distributed systems, and operating systems. A small team of students built automation tooling that handles much of the video production workload, enabling the release pipeline.

hackernews · pcompeau · Nov 16, 20:43 · [Discussion](https://news.ycombinator.com/item?id=50522980)

**「Background」** MIT pioneered open courseware 25 years ago, but CMU&\#x27;s approach distinguishes itself by using student-developed automation to reduce production overhead for current, in-session courses rather than archived material. The program is led by Phillip Compeau, a teaching faculty member who runs CS Learn.

**「Impact」** Developers and students gain direct, no-cost access to lectures from active CMU courses — including Tianqi Chen&\#x27;s ML Systems course that complements the MLC AI book on modern GPU programming — though projects, assignments, and feedback mechanisms are not yet included and are slated for future release.

**「Community discussion」** Commenters welcomed specific course inclusions such as 15-259 Probability and Computing and requested additions like Larry Wasserman&\#x27;s Intermediate Statistics, Dave Andersen&\#x27;s Distributed Systems, and Dave Eckhardt&\#x27;s Operating Systems; one alumnus noted that without projects and feedback loops, lecture videos alone can fall flat, and another observed that introductory courses often get published while advanced graduate courses \(e.g., compilers\) do not.

**Tags**: `#education`, `#computer-science`, `#open-courseware`, `#machine-learning`, `#systems`

---

<a id="item-tech-news-3"></a>
### [Jiff 1.0: New Rust datetime library from burntsushi](https://burntsushi.net/jiff/) ⭐️ 8.0/10

Andrew Gallant \(burntsushi\) has released Jiff 1.0, a new datetime library for Rust designed to address long-standing API limitations in the existing chrono crate. The former chrono maintainer explicitly endorsed Jiff as a solution to fundamental problems that could not be fixed in chrono due to stability constraints. Jiff distinguishes itself by clearly documenting when not to use it, reflecting a professional engineering approach. The library is now available for adoption in the Rust ecosystem.

hackernews · burntsushi · Nov 16, 16:53 · [Discussion](https://news.ycombinator.com/item?id=50519744)

**「Background」** Chrono has been the de facto standard datetime library for Rust for years, but its API design accumulated limitations that could not be changed without breaking stability guarantees. The former chrono maintainer \(quodlibetor\) noted that attempts to improve the API were met with resistance from users who valued stability over API improvements, leading to maintainer burnout. Jiff represents a fresh start from a highly respected Rust ecosystem contributor known for libraries like ripgrep and regex.

**「Impact」** Rust developers now have a credible alternative to chrono for datetime handling, with explicit guidance on when Jiff is and is not appropriate. Early community feedback suggests hope for wider ecosystem adoption over time, though migration from the entrenched chrono crate will be gradual. The library&\#x27;s attention to time scales like TAI and UT1 also makes it relevant for scientific computing use cases requiring high-precision time handling.

**「Community discussion」** The former chrono maintainer confirmed that API stability constraints prevented fixing chrono&\#x27;s fundamental design problems, validating Jiff&\#x27;s approach as a necessary fresh start. A scientific computing user inquired about support for additional time scales like UT1 beyond the mentioned TAI handling, indicating interest from domains requiring microsecond precision at giga-year scales. Multiple commenters praised the project&\#x27;s honest documentation about when not to use Jiff as a sign of professional engineering.

**Tags**: `#rust`, `#datetime`, `#library-release`, `#systems-programming`, `#open-source`

---

<a id="item-tech-news-4"></a>
### [Optimizely Supply-Chain Attack Injects Malware on Major Sites](https://blog.report-uri.com/worlds-largest-brands-infected-with-malware-via-optimizely/) ⭐️ 8.0/10

Optimizely&\#x27;s experimentation platform was compromised and served malicious JavaScript to high-profile websites including Zoom, GitLab, CNN, and BBC. The attack originated from Optimizely&\#x27;s own CDN, which delivered injected code to customer projects across multiple unrelated accounts. Optimizely&\#x27;s own domains \(www.optimizely.com and login.optimizely.com\) were also affected. The exact mechanism of how attackers gained write access to so many customer projects remains unexplained by Optimizely.

hackernews · kristjansson · Nov 16, 23:00 · [Discussion](https://news.ycombinator.com/item?id=50524767)

**「Background」** Optimizely provides A/B testing and experimentation tooling that marketing teams embed via third-party JavaScript snippets, often managed through tag managers like Google Tag Manager. This supply-chain model allows non-engineering staff to deploy code changes without code reviews or staged rollouts, creating a broad attack surface when the vendor&\#x27;s build or delivery pipeline is compromised.

**「Impact」** Organizations using Optimizely or similar third-party experimentation scripts should audit their Content Security Policies, implement Subresource Integrity where possible, and evaluate vendor hygiene practices such as phased rollouts and automated security checks before deploying vendor-served JavaScript to production.

**「Community Discussion」** Commenters argue the incident exposes systemic accountability gaps: marketing-tag workflows bypass engineering controls, and high-traffic sites like CNN and BBC have no excuse for not self-hosting or vendoring critical dependencies. Others note the root cause of cross-customer write access remains unknown, and some suggest browser extensions like NoScript as a user-level mitigation.

**Tags**: `#security`, `#supply-chain-attack`, `#web-security`, `#third-party-scripts`, `#malware`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Nvidia CEO Resignation and Democratic Congress Reshape AI Trade Outlook](https://www.cnbc.com/2026/11/14/nvidia-ai-trade-data-centers-congress.html) ⭐️ 8.0/10

Nvidia founder and CEO Jensen Huang resigned after a tumultuous week, while a Democratic-controlled Congress following the Nov. 3 elections may slow data-center buildout by an estimated 10-20%, according to ETF experts on CNBC&\#x27;s &quot;ETF Edge.&quot; Despite Nvidia&\#x27;s stock falling to $162.85 \(Yorkville Ives cut its price target to $225 from $300\), analysts see Big Tech and alternative chip makers like AMD \(up ~13%\) and Broadcom as beneficiaries, with the Nasdaq posting its best week since August.

rss · CNBC Finance · Nov 16, 12:13

**「Background」** Nvidia has dominated AI GPU chips with a 2-3 year lead over competitors, but Huang&\#x27;s departure creates uncertainty; simultaneously, Democratic congressional gains could restrict data-center expansion, making existing compute capacity more valuable.

**「Impact」** Investors in AI-focused ETFs saw mixed results: the Roundhill Magnificent Seven ETF \(MAGS\) gained under 1% for the week, while the Neocloud ETF \(NCLD\) rose over 1% but remains down 39% since its August 2026 launch amid balance-sheet concerns.

**Tags**: `#Nvidia`, `#AI chips`, `#ETFs`, `#data centers`, `#Congress policy`

---

<a id="item-finance-news-2"></a>
### [Commerce Secretary Lutnick Scrutinized Over Nvidia Ties Amid Chip Smuggling Probe](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 8.0/10

Commerce Secretary Howard Lutnick is under scrutiny for repeatedly resisting White House and intelligence pressure to crack down on a Singapore firm suspected of smuggling Nvidia AI chips to China, while his sons&\#x27; firm Cantor Fitzgerald held a large Nvidia stake and hosted CEO Jensen Huang weeks before Huang&\#x27;s resignation. Cantor&\#x27;s reported Nvidia holdings fell nearly 50% from September 2025 to March 2026, coinciding with classified warnings about Huang&\#x27;s ties to a suspected Chinese spy and the Trump administration&\#x27;s third authorization of export restrictions on Nov. 5.

rss · CNBC Finance · Nov 16, 12:14

**「Background」** Lutnick left Cantor Fitzgerald to become Commerce Secretary in February 2025; his sons Brandon and Kyle now lead the firm. Nvidia dominates the AI chip market and its advanced chips are subject to U.S. export controls aimed at limiting China&\#x27;s military AI capabilities. The entity list, managed by the Commerce Department, restricts business with designated foreign entities.

**「Impact」** Treasury Secretary Scott Bessent publicly stated that the Treasury, Defense, State departments and the U.S. Trade Representative all favored placing the suspected smuggling firm on the entity list for months, highlighting a split in the administration&\#x27;s enforcement of semiconductor export controls. Ethics experts say the convergence of Lutnick&\#x27;s official actions, classified briefings, and his family firm&\#x27;s financial ties to Nvidia creates an appearance of conflict, though no evidence of illegal information sharing has emerged.

**Tags**: `#Nvidia`, `#Howard Lutnick`, `#export controls`, `#China`, `#conflict of interest`

---