---
layout: default
title: "Horizon Summary: 2026-11-18 (EN)"
date: 2026-11-18
lang: en
---

> From 31 items, 8 important content pieces were selected

---

**Technology News**
1. [Java4Shell: RCE in OpenJDK HotSpot via Base64 Processing](#item-tech-news-1) ⭐️ 9.0/10
2. [Quad9 withdraws from France over court-ordered DNS filtering](#item-tech-news-2) ⭐️ 8.0/10
3. [Microsoft Releases MAI Code 2 and Code 2 Flash in GitHub Copilot](#item-tech-news-3) ⭐️ 8.0/10
4. [Microsoft ONNX Runtime Repository Vanishes from GitHub](#item-tech-news-4) ⭐️ 8.0/10
5. [SolidJS 2.0 Released with Server RPC and Live Primitives](#item-tech-news-5) ⭐️ 8.0/10
6. [Nvidia halts Singapore sales disclosure amid $104B revenue routing probe](#item-tech-news-6) ⭐️ 8.0/10
7. [External sandboxes for coding agents: three implementations](#item-tech-news-7) ⭐️ 8.0/10
8. [Datasette Lite Runs Full Python App in Browser via Service Workers](#item-tech-news-8) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Java4Shell: RCE in OpenJDK HotSpot via Base64 Processing](https://calif.io/java4shell/) ⭐️ 9.0/10

Security researchers at Calif disclosed CVE-2024-21131, a critical remote code execution vulnerability in the OpenJDK HotSpot VM triggered when processing Base64-encoded data. The exploit demonstrates reliable heap grooming over real network conditions \(&quot;Remote Heap Feng Shui&quot;\) and affects all major JDK distributions using HotSpot, including OpenJDK builds, Oracle JDK, and GraalVM JDK. Azul Prime \(Zing\) and OpenJ9 are not affected due to different JIT implementations. Semgrep has published free detection scripts identifying five specific vulnerability conditions.

hackernews · werrett · Nov 17, 21:11 · [Discussion](https://news.ycombinator.com/item?id=50538240)

**「Background」** HotSpot is the default JVM for most Java distributions and uses just-in-time \(JIT\) compilation to generate optimized machine code stubs for common operations like Base64 decoding. The vulnerability resides in the AVX-512 implementation of Base64 decoding within HotSpot&\#x27;s C2 compiler, where a memory-safety flaw allows controlled heap corruption. Previous Java RCEs such as Log4Shell \(CVE-2021-44228\) exploited application-layer libraries, whereas Java4Shell targets the runtime&\#x27;s native code generation directly.

**「Impact」** Organizations running affected HotSpot-based JDKs on internet-exposed services processing untrusted Base64 input face immediate remote compromise risk. A practical mitigation is starting the JVM with \`-XX:UseAVX=2\` to disable the vulnerable AVX-512 code path, though this may reduce Base64 decoding performance. Semgrep&\#x27;s detection scripts enable automated scanning for the five prerequisite conditions: HotSpot VM, vulnerable JDK version, Base64 processing code paths, network exposure, and absence of the AVX workaround.

**「Community Discussion」** Commenters note the exploit&\#x27;s sensitivity to network round-trip time and jitter, with Calif demonstrating it over public internet links rather than only in lab conditions. An unconfirmed workaround circulating on social media suggests the \`-XX:UseAVX=2\` flag disables the vulnerable AVX-512 Base64 path. Semgrep&\#x27;s Ivan Evans emphasizes that only HotSpot-based VMs are affected, while OpenJ9, GCJ, and Azul Prime remain safe due to different JIT architectures.

**Tags**: `#security`, `#java`, `#rce`, `#openjdk`, `#vulnerability`

---

<a id="item-tech-news-2"></a>
### [Quad9 withdraws from France over court-ordered DNS filtering](https://blog.cloudflare.com/quad9-withdrawal-from-france/) ⭐️ 8.0/10

Quad9, a major recursive DNS resolver, has withdrawn its service from France following a court order requiring DNS-level copyright filtering. The decision marks the first known exit of a global DNS infrastructure provider from a democratic country over content-blocking mandates. Quad9&\#x27;s CTO confirmed at IETF 127 that the industry broadly opposes such filtering, with 100% support for Quad9&\#x27;s position among non-rightsholder participants.

hackernews · subset · Nov 17, 22:13 · [Discussion](https://news.ycombinator.com/item?id=50538994)

**「Background」** Recursive DNS resolvers like Quad9 translate domain names into IP addresses for end users. Courts in several European countries have increasingly ordered ISPs and infrastructure providers to block access to alleged pirate sites at the DNS level. Quad9 had previously challenged similar orders in Germany, but the French ruling appears to have made continued operation legally untenable for the non-profit resolver.

**「Impact」** French users lose access to Quad9&\#x27;s privacy-focused, security-filtering DNS service unless they manually configure alternative resolvers. The withdrawal sets a precedent that infrastructure providers may exit jurisdictions rather than implement content filtering, potentially fragmenting global DNS infrastructure and shifting blocking burdens to VPNs or encrypted DNS protocols.

**「Community discussion」** Quad9&\#x27;s CTO reported unanimous opposition to DNS filtering among IETF 127 attendees not employed by rightsholder groups, describing a &quot;general dread&quot; about the direction of DNS policy. Commenters criticized Cloudflare&\#x27;s blog post for not committing to similar withdrawal if its own appeal fails, and lamented the erosion of European internet freedoms since the 2000s.

**Tags**: `#DNS`, `#internet governance`, `#digital rights`, `#censorship`, `#infrastructure`

---

<a id="item-tech-news-3"></a>
### [Microsoft Releases MAI Code 2 and Code 2 Flash in GitHub Copilot](https://microsoft.ai/news/introducing-mai-code-2-and-mai-code-2-flash/) ⭐️ 8.0/10

Microsoft has released MAI Code 2 and MAI Code 2 Flash, two new code-focused language models now available in GitHub Copilot. The models are reported to match Claude Opus performance on real-world coding tasks including Python builds, test generation, and Azure Bicep deployments. GitHub Copilot offered MAI Code 2 at a 50% discount at launch. The release represents Microsoft&\#x27;s latest competitive move in AI-assisted coding.

hackernews · lemonish97 · Nov 17, 18:25 · [Discussion](https://news.ycombinator.com/item?id=50535885)

**「Background」** Microsoft has been developing its own foundation models alongside its partnership with OpenAI. The MAI \(Microsoft AI\) series follows earlier internal model efforts such as the Phi series of small language models. GitHub Copilot, which Microsoft acquired in 2018, has historically relied on OpenAI&\#x27;s Codex and GPT models; integrating first-party MAI models reduces dependency on external providers and allows Microsoft to control pricing and model behavior for coding workloads.

**「Impact」** Developers using GitHub Copilot can immediately switch to MAI Code 2 or Code 2 Flash for coding tasks at lower cost, with early users reporting parity with Claude Opus on Python, WSL/Ubuntu builds, test generation, and Azure Bicep deployments. Organizations evaluating Copilot subscriptions now have a cheaper, first-party model option that may reduce per-seat costs if the discount persists.

**「Community Discussion」** Hacker News commenters debate whether Microsoft&\#x27;s rapid catch-up to Claude Opus signals a sustainable competitive moat or merely a temporary lead; some speculate about possible distillation from GPT models given Microsoft&\#x27;s OpenAI access, while others note the Phi series&\#x27; earlier OpenAI-like behavior. Several users report canceling Copilot subscriptions due to credit limits and lack of customization, but say they may return to test the new models.

**Tags**: `#AI`, `#code-generation`, `#Microsoft`, `#GitHub-Copilot`, `#LLM`

---

<a id="item-tech-news-4"></a>
### [Microsoft ONNX Runtime Repository Vanishes from GitHub](https://github.com/microsoft/onnxruntime) ⭐️ 8.0/10

Microsoft&\#x27;s ONNX Runtime repository \(github.com/microsoft/onnxruntime\), a critical ML inference library with over 22,000 stars, disappeared from GitHub without prior notice on November 17, 2026. The removal broke CI pipelines for dependent projects, with users reporting evaluation failures in production workflows. No official explanation has been provided by Microsoft as of the time of reporting.

hackernews · nvader · Nov 17, 23:18 · [Discussion](https://news.ycombinator.com/item?id=50539610)

**「Background」** ONNX Runtime is Microsoft&\#x27;s open-source inference engine for Open Neural Network Exchange \(ONNX\) models, widely used in production ML pipelines for cross-platform model deployment. The repository served as the primary distribution point for source code, releases, and community contributions. Its sudden removal affects both direct users and downstream packages that depend on its availability for building and testing.

**「Impact」** Production CI/CD pipelines that clone or reference the upstream repository directly are failing, forcing teams to seek alternative sources such as Intel&\#x27;s fork \(github.com/intel/onnxruntime\), which includes OpenVINO-specific modifications. Organizations must now audit their build dependencies and decide whether to vendor the code, switch forks, or wait for official communication.

**「Community Discussion」** Commenters speculate on possible causes including a supply-chain compromise \(referencing a reported PyPI package compromise\), mandatory telemetry that exfiltrates application data without an opt-out, and potential backdoor vectors in model files discussed in recent security research. The Intel fork is currently the most prominent accessible alternative, though it carries vendor-specific modifications.

**Tags**: `#onnx`, `#machine-learning`, `#open-source`, `#security`, `#supply-chain`

---

<a id="item-tech-news-5"></a>
### [SolidJS 2.0 Released with Server RPC and Live Primitives](https://www.solidjs.com/blog/solid-2-0-the-long-hold/) ⭐️ 8.0/10

SolidJS 2.0 has been released, introducing server RPC, live and broadcast primitives, and agent-ready authoring features. The major version update targets developers building reactive user interfaces and emphasizes seamless server-client integration. The release is available now as a shipped capability, not an announced plan.

hackernews · pier25 · Nov 17, 18:56 · [Discussion](https://news.ycombinator.com/item?id=50536387)

**「Background」** SolidJS is a performant reactive UI framework known for fine-grained reactivity without a virtual DOM. Previous versions established its compiler-based approach and client-side rendering model. This 2.0 release extends the framework into server-side primitives and real-time capabilities.

**「Impact」** Developers gain a unified mental model for server-client communication through RPC and live/broadcast primitives, which community members describe as more natural than alternatives like Phoenix LiveView or htmx. The agent-ready authoring improvements also enhance debug diagnostics for human developers.

**「Community Discussion」** Commenters highlight the seamless server-client integration as a key advancement over Remix, LiveView, and htmx. One notes that the &\#x27;agent-ready&\#x27; features improve human developer experience through better diagnostics. Another expresses anticipation for Vue Vapor as a competitive performance alternative.

**Tags**: `#solidjs`, `#frontend-framework`, `#major-release`, `#server-rpc`, `#reactive-programming`

---

<a id="item-tech-news-6"></a>
### [Nvidia halts Singapore sales disclosure amid $104B revenue routing probe](https://www.ft.com/content/dbde7a30-548c-4f9d-a4be-7898a0c24dcf) ⭐️ 8.0/10

Nvidia booked $104 billion in revenue through its Singapore subsidiary in 2025 and stopped breaking out those sales in financial disclosures, according to a Financial Times report. The change comes as U.S. authorities investigate whether the Singapore entity, identified as Megaspeed, was involved in diverting Nvidia chips to China in violation of export controls. The $104 billion figure represents the external revenue of the Singapore subsidiary, which handles orders routed through Nvidia&\#x27;s network of OEMs, ODMs, and resellers rather than direct end-customer sales.

hackernews · louiereederson · Nov 17, 17:12 · [Discussion](https://news.ycombinator.com/item?id=50534631)

**「Background」** Nvidia sells its GPUs primarily through a global network of original equipment manufacturers, original design manufacturers, and resellers rather than directly to end users. Singapore has long served as a major logistics and invoicing hub for semiconductor shipments in the Asia-Pacific region. Since 2022, the U.S. has imposed escalating export controls on advanced AI chips to China, requiring licenses for the most powerful data-center GPUs. These restrictions have created incentives for third parties to obscure the final destination of controlled hardware.

**「Impact」** The loss of geographic revenue breakdowns reduces transparency for investors and regulators tracking compliance with export controls. Companies planning AI infrastructure must now factor in heightened scrutiny of supply-chain routing through Southeast Asia, which could delay deliveries or trigger additional due-diligence requirements for high-end GPU orders.

**「Community discussion」** Commenters debate whether the $104 billion figure signals actual sanctions evasion or merely reflects standard multinational accounting. One argument notes the sum is the Singapore subsidiary&\#x27;s external revenue — including legitimate orders routed through the entity — not proof of direct sales to China. Others question why physical chips would need to reach China when Chinese developers can access compute remotely, while a separate thread speculates the disclosure halt relates to an unrelated executive departure rather than the investigation.

**Tags**: `#Nvidia`, `#AI hardware`, `#export controls`, `#supply chain`, `#geopolitics`

---

<a id="item-tech-news-7"></a>
### [External sandboxes for coding agents: three implementations](https://simonwillison.net/2026/Nov/17/external-sandboxes-for-coding-agents/) ⭐️ 8.0/10

Simon Willison and Prime Radiant have introduced the external sandbox pattern for coding agents, where agent-executed code runs in a dedicated sandbox separate from the agent itself. They released three open-source sandbox server implementations: external-sandbox-v86 \(Node.js with v86 WebAssembly Alpine Linux\), external-sandbox-container \(Python with Apple Containers Alpine Linux\), and external-sandbox-quicksand \(Python with Microsoft Quicksand bundling QEMU and Alpine Linux\). Each provides a common localhost API compatible with Pi, Claude Code, and Codex, and includes an optional HTTP/HTTPS allow-list proxy with credential replacement to control outbound network access and inject secrets without exposing them to the agent.

rss · Simon Willison · Nov 17, 22:52

**「Background」** Coding agents that execute arbitrary code pose safety risks because prompt injection or model errors can trigger damaging actions on the host machine. Willison has previously explored sandboxing techniques to mitigate this, and the external sandbox pattern isolates the execution environment entirely from the agent process, allowing developers to experiment with local models more safely.

**「Impact」** Developers can now deploy coding agents with a choice of three sandbox backends — WebAssembly, Apple Containers, or Quicksand — while using a consistent API and centralized network policy enforcement. The allow-list proxy and credential replacement mechanism let operators restrict outbound connections and supply API keys without the agent ever seeing them, reducing the blast radius of prompt injection attacks.

**Tags**: `#AI safety`, `#coding agents`, `#sandboxing`, `#prompt injection`, `#AI research`

---

<a id="item-tech-news-8"></a>
### [Datasette Lite Runs Full Python App in Browser via Service Workers](https://simonwillison.net/2026/Nov/17/datasette-lite/) ⭐️ 8.0/10

Simon Willison released a complete rewrite of Datasette Lite that runs the full server-side Datasette Python application in the browser using Pyodide and service workers. The new version at lite.datasette.io supports loading arbitrary SQLite databases, JSON, CSV, and SQL files; selecting from over 100 SQLite versions; pinning specific Datasette releases or Git commits; and installing plugins from PyPI or wheel URLs. Unlike the 2022 prototype that used a web worker and innerHTML injection, the service worker architecture enables full JavaScript execution, making the browser version nearly indistinguishable from the server-side application.

rss · Simon Willison · Nov 17, 16:48

**「Background」** Datasette is a Python tool for exploring and publishing SQLite databases as interactive websites. The original Datasette Lite launched in May 2022 as an experimental port running in a Pyodide web worker, but its innerHTML-based rendering broke JavaScript-dependent features. Pyodide provides a WebAssembly build of CPython with scientific Python packages, enabling Python execution in browsers without a server.

**「Impact」** Developers can now share reproducible, version-pinned Datasette demos and bug reproductions via a single URL without deploying any server infrastructure, as demonstrated by Willison&\#x27;s use of Lite links to show a pagination bug and its fix across two alpha releases.

**「Community Discussion」** No community comments were available for this item.

**Tags**: `#WebAssembly`, `#Pyodide`, `#Datasette`, `#SQLite`, `#browser-based-applications`

---