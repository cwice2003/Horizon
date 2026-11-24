---
layout: default
title: "Horizon Summary: 2026-11-24 (ZH)"
date: 2026-11-24
lang: zh
---

> 从 26 条内容中筛选出 4 条重要资讯。

---

**科技新闻**
1. [Ladybird 浏览器引擎发布首个 Alpha 版本](#item-tech-news-1) ⭐️ 9.0/10

**科技博客**
1. [vLLM 插件实现 ERNIE 5.5 Flash 首日支持与全链路加速](#item-tech-blog-1) ⭐️ 8.0/10

**财经新闻**
1. [纽约联储主席威廉姆斯暗示将逐步加息以抑制通胀](#item-finance-news-1) ⭐️ 8.0/10
2. [英伟达黄仁勋回归 CEO 引发反弹，专家争论是否确立市场底部](#item-finance-news-2) ⭐️ 8.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Ladybird 浏览器引擎发布首个 Alpha 版本](https://ladybird.org/posts/alpha/) ⭐️ 9.0/10

Ladybird 浏览器项目于 2026 年 11 月 23 日发布首个 Alpha 版本，提供 macOS 和 Linux 的预编译安装包。这是一个从零编写、不基于 Chromium、WebKit 或 Gecko 的独立浏览器引擎，核心组件（HTML 解析、CSS、布局、JavaScript、WebAssembly）均为自主实现，仅使用 HarfBuzz、Skia、ffmpeg、SQLite 等少量外部库。Alpha 版已展示较强的真实网站兼容性，能运行基于 WebAssembly 的 ffmpeg 视频压缩工具、Pyodide Python REPL 等复杂应用，但 Service Worker 尚未完全实现（Datasette Lite 无法运行）。项目在 2026 年 10 月借助 AI 编码代理大幅提升 web-platform-tests 通过数，新增 75,650 个子测试通过，超越 Safari 接近 Firefox 水平。

hackernews · janvdberg · 11月23日 16:13 · [社区讨论](https://news.ycombinator.com/item?id=50614249)

**「背景」** Ladybird 起源于 SerenityOS 项目，此前仅能通过自行编译运行。2026 年 2 月项目宣布将部分 LibJS 引擎从 C++ 移植到 Rust，并大量采用 AI 编码工具（Claude Code、Codex）加速开发。10 月的贡献激增对应了样式/布局线程分离、新 JavaScript JIT、WebAssembly 引擎替换为 Cranelift 并实现 JetStream 3 基准 7 倍提升等重大改进。

**「影响」** 开发者和早期采用者可在不编译的情况下测试一个真正独立的浏览器引擎，验证其对现代 Web 标准（含 WebAssembly、多进程隔离）的支持程度。但 Alpha 版明确警告会崩溃且部分网站不工作，不建议作为日常主力浏览器；安全研究人员受邀参与测试并上报漏洞。

**「社区讨论」** 用户普遍对渲染兼容性表示惊讶：多位测试者称常用网站、Proxmox、NoVNC 等复杂应用均能正确运行，甚至 NoVNC 响应速度优于 Firefox；唯一共性抱怨是页面滚动略有卡顿。也有怀旧声音指出项目放弃自研库转用成熟组件虽提升质量但失去了早期黑客精神；另有用户期望未来加强指纹防护和权限粒度控制。

**标签**: `#browser-engine`, `#ladybird`, `#web-standards`, `#open-source`, `#software-engineering`

---

## 科技博客

<a id="item-tech-blog-1"></a>
### [vLLM 插件实现 ERNIE 5.5 Flash 首日支持与全链路加速](https://vllm.ai/blog/2026-11-24-ernie-5-5-flash-preview) ⭐️ 8.0/10

rss · vLLM Blog · 11月24日 00:00

**「背景」** 百度 ERNIE 团队与 vLLM 社区合作，在模型发布当天通过独立插件实现了 ERNIE 5.5 Flash Preview 的 vLLM 原生支持，避免了维护分支或等待夜 ly 构建的麻烦。

**「方案」** 该模型采用 280B 总参数、14B 激活参数的稀疏 MoE 架构，包含 37 层 HCA 和 6 层 MLA-DSA 注意力，支持 1M 上下文。团队针对 VHA 跨头混合、Multi-Router Latent MoE、MultiMax 输出头、门控注意力等新结构设计了专用融合内核，将权重预折叠并融合量化操作，单内核加速 1.55-6.53 倍；FlashIndexer 通过动态头路由和阈值预过滤在 1M 上下文实现 40%加速；FP4 量化感知训练消除训练推理数值差异；三阶段 DSpark 投机解码训练流水线使平均接受长度超 4.0。插件通过 vllm.general\_plugins 入口点自动注册，仅在加载 ERNIE 架构时导入代码，不影响其他模型。

**「启示」** 这种插件化部署模式结合全链路内核融合、稀疏索引加速和协同训练的投机解码，展示了如何在不分叉上游框架的前提下实现新架构的首日高性能推理支持。

**标签**: `#vLLM`, `#Mixture-of-Experts`, `#Kernel Fusion`, `#Speculative Decoding`, `#Model Deployment`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [纽约联储主席威廉姆斯暗示将逐步加息以抑制通胀](https://www.cnbc.com/2026/11/23/john-williams-fed-inflation-rate-hikes.html) ⭐️ 8.0/10

纽约联储主席威廉姆斯（John Williams）表示，为将通胀率恢复至 2%目标，美联储仍需「随时间推移」采取进一步加息行动；他预计通胀将在 2027 年接近 2%，2028 年达标，当前联邦基金利率目标区间为 3.75%-4%，市场完全定价 12 月 8-9 日议息会议加息 25 个基点。

rss · CNBC Finance · 11月23日 21:02

**「背景信息」** 威廉姆斯是联邦公开市场委员会（FOMC）永久票委，其讲话被视为 12 月议息会议前最后一位重要美联储官员的公开表态；此前 10 月会议声明称将视后续数据决定政策路径。

**「潜在影响」** 若如市场预期 12 月加息 25 个基点，借贷成本将进一步上升，可能加重房贷、车贷及企业融资负担，但威廉姆斯强调经济增长依然强劲、失业率边际下降，显示美联储试图在抑制通胀与避免硬着陆间寻求平衡。

**标签**: `#Federal Reserve`, `#monetary policy`, `#inflation`, `#interest rates`, `#John Williams`

---

<a id="item-finance-news-2"></a>
### [英伟达黄仁勋回归 CEO 引发反弹，专家争论是否确立市场底部](https://www.cnbc.com/2026/11/23/nvidia-jensen-huang-ceo-market-rally.html) ⭐️ 8.0/10

英伟达宣布黄仁勋重返 CEO 职位后，美股三大指数周一大幅反弹，此前标普 500 指数在黄仁勋 11 月 12 日离职消息公布后至周五累计下跌逾 9%进入回调区间。

rss · CNBC Finance · 11月23日 18:00

**「背景脉络」** 黄仁勋离职引发的抛售叠加了对 AI 资本开支见顶、中期选举后数据中心审批前景及监管担忧，导致市场恐慌性抛售波及除 AI 板块外的所有行业。

**「潜在影响」** 黄仁勋回归缓解了市场对英伟达治理的担忧，但“铲子卖家”类 AI 股票能否持续上涨仍取决于大型科技公司的资本开支节奏，多位策略师认为这可能只是超跌反弹而非趋势反转。

**标签**: `#Nvidia`, `#Jensen Huang`, `#AI trade`, `#market correction`, `#CEO change`, `#market sentiment`

---