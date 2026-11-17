---
layout: default
title: "Horizon Summary: 2026-11-17 (ZH)"
date: 2026-11-17
lang: zh
---

> 从 28 条内容中筛选出 6 条重要资讯。

---

**科技新闻**
1. [vLLM v0.34.0 发布：默认启用可扩展 KV 缓存，移除 Model Runner V1，新增 10 个模型支持](#item-tech-news-1) ⭐️ 8.0/10
2. [卡内基梅隆大学推出 CS Learn 免费公开计算机科学课程](#item-tech-news-2) ⭐️ 8.0/10
3. [Jiff 1.0 发布：Rust 新日期时间库](#item-tech-news-3) ⭐️ 8.0/10
4. [Optimizely 供应链攻击导致 Zoom、GitLab 等大型网站分发恶意软件](#item-tech-news-4) ⭐️ 8.0/10

**财经新闻**
1. [英伟达 CEO 辞职与民主党控制国会重塑 AI 交易格局](#item-finance-news-1) ⭐️ 8.0/10
2. [美国商务部长卢特尼克因英伟达芯片走私调查面临利益冲突质疑](#item-finance-news-2) ⭐️ 8.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [vLLM v0.34.0 发布：默认启用可扩展 KV 缓存，移除 Model Runner V1，新增 10 个模型支持](https://github.com/vllm-project/vllm/releases/tag/v0.34.0) ⭐️ 8.0/10

vLLM v0.34.0 于 2026 年 11 月 16 日发布，包含 1,061 个提交和 412 位贡献者。此版本默认启用可扩展 KV 缓存，根据预热后的实际空闲显存调整缓存大小，使大多数模型获得更大缓存和更高吞吐（如 MiniMax-M3 在 H200 上从 433k 提升至 672k tokens）。Model Runner V1 被完全移除，V2 成为唯一 GPU 运行器。在 Blackwell 和 MI355X 上实现显著加速：Step5 NVFP4 MoE 解码最高提升 1.95 倍，GLM-5.3-Flash 吞吐提升 1.6 倍，长提示 TTFT 提升 1.24–1.40 倍。新增 10 个模型支持，包括 Mistral Large 4、MiniMax-M3.1-Flash、Nemotron-3.5-Transcribe 等。重大破坏性变更：默认 block-size 从 16 改为 64，移除 ROCm 7.2 制品，要求 huggingface\_hub &gt;= 2.0.0，移除 QuTLASS/fp\_quant 和 Marlin W4A8 量化。新增检查点/恢复（CRIU）、容错 DP+EP 缩容、NUMA 绑定、Rust 前端 Responses API 及 n&gt;1 支持。

github · khluu · 11月16日 23:22

**「背景」** vLLM 是广泛采用的开源大语言模型推理引擎，支持 PagedAttention、张量并行、流水线并行等技术。此前版本通过 Model Runner V1/V2 双运行器过渡，V2 引入了更灵活的调度和推测解码支持。可扩展 KV 缓存此前作为实验性功能存在，通过在 CUDA 图捕获和预热后测量实际可用显存来确定缓存大小，而非依赖静态估算。ROCm 10.0 是 AMD GPU 的当前主流栈，vLLM 已逐步淘汰旧版 ROCm 支持。

**「影响」** 现有部署必须迁移：移除 VLLM\_USE\_V2\_MODEL\_RUNNER=0 环境变量（否则启动失败），将 V1 logits processor 迁移至 vllm.v1.worker.gpu.sample.logits\_processor；如需保持旧行为需显式传入 --block-size 16 和 --gpu-memory-utilization 0.9 或 --no-enable-extensible-kv-cache；ROCm 用户必须升级至 10.0 镜像和轮子；依赖 fp\_quant 或 Marlin W4A8 量化的检查点需转换为 Humming 格式。可扩展 KV 缓存默认开启可能在高并发下增加单 token 解码延迟（TPOT +6–18%），需根据负载评估是否关闭。

**标签**: `#vLLM`, `#LLM inference`, `#open source`, `#GPU acceleration`, `#performance optimization`

---

<a id="item-tech-news-2"></a>
### [卡内基梅隆大学推出 CS Learn 免费公开计算机科学课程](https://www.cs.cmu.edu/learn/) ⭐️ 8.0/10

卡内基梅隆大学（CMU）计算机科学学院于 2026 年 11 月 16 日正式推出 CS Learn 平台，将当前学期的完整计算机科学课程免费发布到 YouTube。首批课程包括《概率与计算》（15-259）、Tianqi Chen 的《机器学习系统》、Dave Andersen 的《分布式系统》以及《操作系统》等，采用每天首播一门课程的节奏，更多课程将于 2027 年 1 月陆续上线。该项目由学生开发的自动化制作工具支撑，使小团队能高效完成课程视频的录制、剪辑与发布。

hackernews · pcompeau · 11月16日 20:43 · [社区讨论](https://news.ycombinator.com/item?id=50522980)

**「背景」** MIT 于 2001 年启动 OpenCourseWare 开创了高校公开课程先河，CMU 此次推出的 CS Learn 延续了这一开放教育传统，但通过学生自建的自动化工具链大幅降低了课程视频化的制作成本。Phillip Compeau 教授在 Hacker News 确认，后续还将发布配套的课件、项目作业等完整教学资料。

**「影响」** 开发者与自学者可直接获取 CMU 顶尖 CS 课程的完整讲座视频，尤其在机器学习系统、分布式系统、操作系统等核心系统方向，配合即将发布的项目作业可构建接近正规教学的学习路径，降低了获取一流计算机教育的门槛。

**「社区讨论」** 社区普遍欢迎此举，校友特别期待《概率与计算》与《机器学习系统》的上线，并建议补充 Larry Wasserman 的《中级统计学》等研究生级课程；也有用户指出仅有讲座视频不足，配套项目与反馈机制对学习效果至关重要。

**标签**: `#education`, `#computer-science`, `#open-courseware`, `#machine-learning`, `#systems`

---

<a id="item-tech-news-3"></a>
### [Jiff 1.0 发布：Rust 新日期时间库](https://burntsushi.net/jiff/) ⭐️ 8.0/10

Rust 生态核心贡献者 Andrew Gallant \(burntsushi\) 发布 Jiff 1.0，这是一个全新的日期时间库，旨在解决现有 chrono 库长期存在的 API 设计问题。前 chrono 维护者明确背书该库，认为其解决了因稳定性约束而无法修复的根本缺陷。Jiff 1.0 已作为正式版本发布，并明确文档化了不适用场景，体现专业工程实践。

hackernews · burntsushi · 11月16日 16:53 · [社区讨论](https://news.ycombinator.com/item?id=50519744)

**「背景」** chrono 曾是 Rust 标准的日期时间库，但其 API 设计存在长期被诟病的问题，前维护者因稳定性承诺阻碍改进而最终放弃维护。Jiff 由以 ripgrep、regex 等知名库著称的 burntsushi 开发，专门针对时标处理（TAI、UT1 等）提供更严谨的抽象。

**「影响」** Rust 开发者获得一个可替代 chrono 的现代选择，尤其在科学计算、天文模拟等需要高精度时标转换的场景中，Jiff 的显式时标支持可减少手动实现的负担。生态迁移将取决于第三方 crate 的适配进度。

**「社区讨论」** 前 chrono 维护者 quodlibetor 证实 API 改进受阻于稳定性承诺，导致维护倦怠；用户 ddahlen 关注 Jiff 在百万年尺度与微秒精度混合场景下的时标（TAI/UT1）支持细节；社区普遍肯定 burntsushi 库的工程质量，并期待其逐步替代 chrono。

**标签**: `#rust`, `#datetime`, `#library-release`, `#systems-programming`, `#open-source`

---

<a id="item-tech-news-4"></a>
### [Optimizely 供应链攻击导致 Zoom、GitLab 等大型网站分发恶意软件](https://blog.report-uri.com/worlds-largest-brands-infected-with-malware-via-optimizely/) ⭐️ 8.0/10

Optimizely 的实验平台被攻破，攻击者向其 CDN 注入恶意 JavaScript，导致 Zoom、GitLab、CNN、BBC 等知名网站向访问者分发恶意代码。报告指出 Optimizely 自身站点（www.optimizely.com 和 login.optimizely.com）同样受影响，且这并非 CDN 缓存投毒，而是平台直接分发了被篡改的代码片段。目前尚不清楚攻击者如何获得跨客户项目的写入权限。

hackernews · kristjansson · 11月16日 23:00 · [社区讨论](https://news.ycombinator.com/item?id=50524767)

**「背景」** Optimizely 是广泛使用的第三方 A/B 测试与实验平台，通过 JavaScript 片段嵌入客户网站。此类营销/实验标签常由非工程团队通过标签管理器（如 Google Tag Manager）直接部署，绕过代码审查与发布流程，形成供应链攻击面。

**「影响」** 受影响网站的访问者可能在不知情下执行恶意脚本，面临凭证窃取、会话劫持或进一步恶意软件下载风险。事件凸显大型站点若不自行托管并审核第三方脚本、或缺乏分阶段发布与完整性校验机制，将难以阻断此类供应链攻击。

**「社区讨论」** 评论者指出营销团队通过标签管理器直接注入脚本、缺乏工程审查是根源；有人主张大型站点应自行托管供应商代码并实施分阶段发布、自动安全检查等内部管控；也有讨论质疑为何 CNN、BBC 等内容站点会在同一域名下处理加密货币或信用卡业务，增加攻击价值。

**标签**: `#security`, `#supply-chain-attack`, `#web-security`, `#third-party-scripts`, `#malware`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [英伟达 CEO 辞职与民主党控制国会重塑 AI 交易格局](https://www.cnbc.com/2026/11/14/nvidia-ai-trade-data-centers-congress.html) ⭐️ 8.0/10

英伟达创始人兼 CEO 黄仁勋辞职，临时 CEO 由 CFO 库莱特·克雷斯担任；Yorkville Ives 将英伟达目标价从 300 美元下调至 225 美元，维持买入评级，股价周收报 162.85 美元。专家预计民主党控制国会可能导致 10%-20%规划数据中心搁置，但算力需求仍超供给 4 倍，利好大型科技股及 AMD、博通等替代芯片厂商。

rss · CNBC Finance · 11月16日 12:13

**「背景」** 英伟达经历自 2012 年以来最长连跌周期，Roundhill 旗下“七巨头 ETF”（MAGS）周涨不足 1%，Neocloud ETF（NCLD）周涨超 1%但自 2026 年 8 月发行以来累跌 39%。

**「影响」** 数据中心建设放缓将使现有算力更稀缺，纳斯达克指数录得 8 月以来最佳周表现，AMD 与博通股价周涨近 13%，市场资金在短期动荡中向大型云厂商及替代芯片供应商转移。

**标签**: `#Nvidia`, `#AI chips`, `#ETFs`, `#data centers`, `#Congress policy`

---

<a id="item-finance-news-2"></a>
### [美国商务部长卢特尼克因英伟达芯片走私调查面临利益冲突质疑](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 8.0/10

据 CNBC 报道，美国商务部长霍华德·卢特尼克因其儿子管理的投行 Cantor Fitzgerald 持有大量英伟达股份并与英伟达保持紧密业务往来，而在白宫和情报机构施压要求打击涉嫌向中国走私英伟达 AI 芯片的新加坡公司 Megaspeed 时表现出抵制，引发利益冲突质疑。Cantor 在 2025 年 9 月至 2026 年 3 月期间将披露的英伟达持股减少约 49%（从 350 万股降至 178 万股），同期卢特尼克收到关于英伟达 CEO 黄仁勋涉嫌与中国间谍有关联的机密情报警告。

rss · CNBC Finance · 11月16日 12:14

**「背景脉络」** 卢特尼克于 2025 年 2 月出任商务部长前长期掌管 Cantor Fitzgerald，现由其两子布兰登和凯尔领导。特朗普政府曾于 2025 年夏季放宽英伟达 H20 芯片对华销售限制，后于 2025 年 11 月 5 日第三次授权对涉嫌走私公司实施出口管制。财长贝森特透露财政、国防、国务及贸易代表办公室均支持将 Megaspeed 列入实体清单，但商务部负责执行。

**「潜在影响」** 伦理专家指出卢特尼克与其家族企业投资的关联可能损害公众对政府决策公正性的信任，参议员已敦促重新审查英伟达出口许可；若调查证实存在利用非公开情报指导私人投资或政策阻挠，将冲击美中科技竞争政策的可信度及半导体出口管制执行。

**标签**: `#Nvidia`, `#Howard Lutnick`, `#export controls`, `#China`, `#conflict of interest`

---