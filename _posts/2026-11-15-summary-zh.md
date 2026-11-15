---
layout: default
title: "Horizon Summary: 2026-11-15 (ZH)"
date: 2026-11-15
lang: zh
---

> 从 23 条内容中筛选出 4 条重要资讯。

---

**科技新闻**
1. [SpaceX 星舰飞船首次被机械臂捕获，助推器溅落](#item-tech-news-1) ⭐️ 8.0/10
2. [Lovable AI 应用因 Supabase RLS 配置错误泄露护照及 20 万消息](#item-tech-news-2) ⭐️ 8.0/10
3. [DeepSeek V3 纯 JAX 实现：约 200 行可在 AMD 硬件运行的教学代码](#item-tech-news-3) ⭐️ 8.0/10
4. [Cloudflare 开源 AI 代理无状态浏览器 Kitesurf](#item-tech-news-4) ⭐️ 8.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [SpaceX 星舰飞船首次被机械臂捕获，助推器溅落](https://www.spacex.com/launches/starship-flight-15) ⭐️ 8.0/10

SpaceX 在星舰第 15 次试飞中首次成功用发射塔机械臂捕获返回的星舰飞船（上级），飞船完成约 22.5 小时、绕地球 14 圈的轨道飞行后返回得克萨斯星港；超重型助推器未能按计划返回发射塔，最终在墨西哥湾溅落，两级同步回收尚未实现。本次任务还成功部署 26 颗新一代星链 V3 卫星。

hackernews · ls612 · 11月14日 21:22 · [社区讨论](https://news.ycombinator.com/item?id=50500963)

**「背景」** 星舰是 SpaceX 开发的完全可复用两级重型运载火箭，此前多次试飞均以飞船或助推器失意为告终；飞行 15 标志着上级首次实现机械臂捕获回收，验证了“筷子”捕获架构的可行性。

**「影响」** 这一突破为后续实现两级全流程复用、大幅降低发射成本奠定基础；但助推器回收失败表明仍需改进着陆燃料余量与制导系统。

**「社区讨论」** 社区讨论聚焦于与航天飞机的对比（GMoromisato 认为星舰避免了固体助推器与侧挂设计的风险）、热盾可靠性是下一关键（small\_model）、以及助推器质量分数与双级捕获的工程权衡（ChuckMcM）。

**标签**: `#spacex`, `#starship`, `#reusable-rockets`, `#spaceflight`, `#aerospace-engineering`

---

<a id="item-tech-news-2"></a>
### [Lovable AI 应用因 Supabase RLS 配置错误泄露护照及 20 万消息](https://www.crissyfield.de/research/lovable-en/) ⭐️ 8.0/10

安全研究团队 Crissy Field 发现，Lovable AI 生成的多个应用因 Supabase 行级安全（RLS）配置不当，导致护照详情和超过 20 万条私密消息泄露。研究者通过博客披露该漏洞，Lovable 安全负责人确认根因是 RLS 不足，并表示平台已提供自动扫描与自动修复功能。Supabase 历史默认设置因优先上手便利而牺牲安全性，也被指为此次事件的系统性因素。

hackernews · armcat · 11月14日 17:43 · [社区讨论](https://news.ycombinator.com/item?id=50499017)

**「背景」** Lovable 是一个 AI 应用构建平台，使用 Supabase 作为后端数据库。Supabase 早期默认的 RLS 策略为降低新用户门槛而放宽了安全限制，这一设计选择在现有项目中可能仍然生效。研究者的博客文章最早两周前提交至 Hacker News，近期重新提交后获得广泛关注。

**「影响」** 使用 Lovable 或类似 AI 代码生成平台的开发者应立即审查 RLS 策略，并启用自动化安全扫描。受影响应用的用户可能面临护照信息和私密通讯泄露风险，建议关注身份监控与隐私保护措施。

**「社区讨论」** 研究者 neathack 确认作者身份并表示情况不言自明。Lovable 安全负责人 igorandri 承认 RLS 问题，并强调平台提供的扫描与自动修复能力。评论者 SOLAR\_FIELDS 指出 Supabase 不安全默认设置的责任，liquid\_thyme 呼吁平台采用拒绝默认、最小权限等更安全的基础设施，Oras 则指出 AI 生成应用数量庞大且易成为攻击目标，普通用户难以评估风险。

**标签**: `#security`, `#ai-generated-code`, `#vulnerability-disclosure`, `#supabase`, `#data-breach`

---

<a id="item-tech-news-3"></a>
### [DeepSeek V3 纯 JAX 实现：约 200 行可在 AMD 硬件运行的教学代码](https://github.com/Vaibhaav-Tiwari/deepseek-v3-jax) ⭐️ 8.0/10

作者 VaibhaavTiwari 在 GitHub 开源了一个约 200 行的纯 JAX 实现 DeepSeek V3，代码可在 AMD ROCm 硬件（经测试在 RX 7600 XT 16GB 上运行）上端到端执行，旨在作为理解大语言模型架构的教学参考。该实现不依赖 PyTorch 或 TensorFlow，仅用 JAX 从头构建 Transformer 核心组件，展示了注意力机制、MoE 等关键结构。

hackernews · VaibhaavTiwari · 11月14日 15:04 · [社区讨论](https://news.ycombinator.com/item?id=50497589)

**「背景」** DeepSeek V3 是 DeepSeek 公司发布的大语言模型；JAX 是 Google 推出的高性能数值计算库，支持自动微分和硬件加速。大多数 LLM 参考实现基于 PyTorch 并依赖 CUDA，这份极简 JAX 代码填补了“可在 AMD 显卡上直接运行、且代码量极小便于逐行研读”的空白。

**「影响」** 想从第一性原理学习 LLM 内部结构的工程师现在拥有一个可在非 CUDA 硬件上直接跑通的最小代码库；社区反馈确认仅需设置 HSA\_OVERRIDE\_GFX\_VERSION=11.0.0 等环境变量即可在 ROCm 上运行，降低了 AMD 显卡用户实验模型架构的门槛。

**「社区讨论」** 多位评论者确认在 RX 7600 XT 上通过设置环境变量成功运行，并表示该项目极大激发了他们重新学习 JAX 与从头复现模型架构的动力；有人询问系统性学习路线图，显示出对“从零理解推理过程”的强烈需求。

**标签**: `#jax`, `#deepseek`, `#llm-implementation`, `#open-source`, `#education`

---

<a id="item-tech-news-4"></a>
### [Cloudflare 开源 AI 代理无状态浏览器 Kitesurf](https://www.phoronix.com/news/Cloudflare-Kitesurf-Open-Source) ⭐️ 8.0/10

Cloudflare 以 Apache 2.0 许可证开源了 Kitesurf，这是一个面向 AI 代理的无状态浏览器，基于 Cloudflare Workers 构建，无需浏览器容器即可解析 HTML、处理 CSS 并执行 JavaScript。该项目旨在为 AI 代理提供轻量、高效的浏览环境，相比 Chromium 占用更少 CPU 和内存，并能在全球 Workers 网络上按需扩展。代码已发布在 GitHub，可供开发者立即采用和进一步开发。

telegram · zaihuapd · 11月14日 09:33

**「背景」** Cloudflare Workers 是 Cloudflare 的无服务器执行平台，允许在边缘网络上运行 JavaScript/Wasm 代码。Kitesurf 利用这一架构实现了无容器的浏览器自动化，区别于传统基于 Chromium 或无头浏览器的方案。此前，AI 代理进行网页交互通常需要部署完整的浏览器实例，资源开销大且扩展复杂。

**「影响」** 开发者可直接在 Cloudflare Workers 上部署 AI 代理的网页交互任务，无需管理浏览器基础设施，降低运维成本并提高弹性扩展能力。Apache 2.0 许可证允许商业使用和二次开发，有望推动无服务器浏览器自动化的标准化。

**标签**: `#AI agents`, `#browser automation`, `#Cloudflare Workers`, `#open source`, `#serverless`

---