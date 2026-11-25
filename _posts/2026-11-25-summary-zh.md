---
layout: default
title: "Horizon Summary: 2026-11-25 (ZH)"
date: 2026-11-25
lang: zh
---

> 从 20 条内容中筛选出 3 条重要资讯。

---

**科技新闻**
1. [Check Point 安全管理服务器遭 V8 PRNG 弱点攻击伪造管理员会话](#item-tech-news-1) ⭐️ 8.0/10
2. [PrismML 发布 Ternary Bonsai 2.5 27B 三元量化模型](#item-tech-news-2) ⭐️ 8.0/10
3. [VMware vCenter 曝 9.8 分认证绕过漏洞，Broadcom 发布 23 个补丁](#item-tech-news-3) ⭐️ 8.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Check Point 安全管理服务器遭 V8 PRNG 弱点攻击伪造管理员会话](https://www.greynoise.io/blog/check-point-security-management-servers-intrusion-campaign) ⭐️ 8.0/10

GreyNoise 报告发现针对 Check Point 安全管理服务器的活跃入侵活动，攻击者利用 Node.js V8 引擎 Math.random\(\) 的伪随机数生成器（PRNG）状态恢复弱点，通过向 HFS 登录端点 loginSrp1 发送多次 POST 请求收集会话 cookie 中的 sid 值，重构 PRNG 内部状态并恢复会话 cookie 签名密钥，从而伪造签名的管理员会话 cookie 实现未授权访问。该攻击已在多个 Check Point 客户环境中被观测到，初始入侵向量疑似为 CVE-2026-16232。

hackernews · louiereederson · 11月24日 16:32 · [社区讨论](https://news.ycombinator.com/item?id=50630594)

**「背景」** Node.js V8 引擎的 Math.random\(\) 使用非加密安全的伪随机数生成器（XorShift128+ 算法），其输出在观测足够数量后可推导内部状态，进而预测后续值。Check Point 安全管理服务器的 HFS 组件使用该函数生成会话标识符 sid 并对 cookie 进行签名，若攻击者能收集足够多的登录响应，即可恢复签名密钥并伪造任意用户（包括管理员）的有效会话。CVE-2026-16232 疑似为攻击者获取初始访问权限的漏洞，但具体细节尚未在公开报告中披露。

**「影响」** 运行暴露在互联网上的 Check Point 安全管理服务器的组织面临管理员账户被接管的直接风险，攻击者可完全控制安全策略配置、日志审计及下游网关。受影响组织应立即检查管理服务器是否对公网开放，轮换所有会话密钥，并应用厂商发布的缓解补丁或配置指南。

**「社区讨论」** 社区成员 miohtama 和 PyWoody 确认了攻击技术细节：攻击者通过连续登录收集 Math.random\(\) 输出重构 V8 PRNG 状态。用户 omh 质疑初始访问向量，指出 CVE-2026-16232 可能要求管理服务器直接暴露在公网。用户 20after4 提出 Math.random\(\) 本身应修复而非依赖应用层正确使用，但这属于长期语言层面的争议，不构成当前缓解措施。

**标签**: `#security`, `#vulnerability`, `#intrusion`, `#check-point`, `#prng`

---

<a id="item-tech-news-2"></a>
### [PrismML 发布 Ternary Bonsai 2.5 27B 三元量化模型](https://prismml.com/news/bonsai-2-5-27b) ⭐️ 8.0/10

PrismML 发布了 Ternary Bonsai 2.5 27B，这是一个 2-bit 三元量化的 270 亿参数模型，在消费级 Mac 硬件（如 Mac Mini M5 Pro）上可达到 22+ tokens/秒的推理速度，支持 128k 上下文长度。根据社区实测，该模型在 SWE-bench Verified 基准上得分接近 Opus 4.6（2026 年 2 月发布），并在自建长程任务基准中将完成时间缩短 29%。该模型以 GGUF 格式发布，适合本地智能体编码工作流。

hackernews · b0m · 11月24日 20:08 · [社区讨论](https://news.ycombinator.com/item?id=50633922)

**「背景」** 三元量化将权重压缩至约 2-bit，极大降低显存占用，使大参数模型能在消费级设备运行。Bonsai 系列此前已有 2.0 版本，2.5 版本在保持量化优势的同时提升了编码基准表现。

**「影响」** 开发者可在 24GB 内存的 Mac Mini 上本地运行具备前沿编码能力的 27B 模型，无需云端 API，支持 128k 上下文的智能体编码任务，显著降低本地 LLM 推理的硬件门槛。

**「社区讨论」** 社区讨论集中在基准分数的可信度：有用户实测确认 22-25 tok/s 速度和 128k 上下文可用性，但也有人质疑 SWE-bench Verified 是否具备代表性，并呼吁与同量级量化模型（如 Qwen 3.8B Q1/Q2）直接对比。

**标签**: `#LLM quantization`, `#local inference`, `#coding benchmarks`, `#ternary quantization`, `#agentic coding`

---

<a id="item-tech-news-3"></a>
### [VMware vCenter 曝 9.8 分认证绕过漏洞，Broadcom 发布 23 个补丁](https://thehackernews.com/2026/11/vmware-vcenter-hit-by-another-critical.html) ⭐️ 8.0/10

Broadcom 已为 VMware vCenter 发布补丁，修复 23 个漏洞，其中最严重的是 vCenter 目录服务（vmdir）的认证绕过漏洞 CVE-2026-123903，CVSS 评分 9.8。攻击者只需能访问 vCenter 即可绕过认证直接进入系统，该漏洞近期已被作为零日漏洞利用。管理员应立即应用补丁。

telegram · zaihuapd · 11月24日 14:50

**「背景」** vCenter 是 VMware 的集中管理平台，vmdir 是其目录服务组件，负责身份认证和授权。此次漏洞允许未认证攻击者完全绕过 vmdir 的鉴权机制。

**「影响」** 使用 vCenter 的企业必须尽快部署补丁，因为漏洞已被在野利用，延迟修补将导致整个虚拟化基础设施面临完全接管风险。

**标签**: `#security`, `#vulnerability`, `#vmware`, `#vcenter`, `#authentication-bypass`

---