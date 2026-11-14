---
layout: default
title: "Horizon Summary: 2026-11-14 (ZH)"
date: 2026-11-14
lang: zh
---

> 从 20 条内容中筛选出 3 条重要资讯。

---

**科技新闻**
1. [Orcas Island 全频段航空无线电实时流式传输上线](#item-tech-news-1) ⭐️ 8.0/10
2. [DeepSeek 开放全家桶 API 并开源本地部署聊天 Demo](#item-tech-news-2) ⭐️ 8.0/10

**财经新闻**
1. [英伟达黄仁勋辞职引发间谍指控 美中芯片战升级风险加剧](#item-finance-news-1) ⭐️ 9.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Orcas Island 全频段航空无线电实时流式传输上线](https://orcasairband.com/) ⭐️ 8.0/10

Orcas Island 的开发者 mmaunder 部署了一个实时流式传输系统，使用 Ettus B210 SDR 和双 RTX 4090 GPU，通过 CUDA 实现的多相位信道化器，同时捕获并解调整个 118-137 MHz 航空频段。该系统在 2026 年 11 月 13 日维多利亚/温哥华因通信故障实施地面停飞时提供了即时监听价值。

hackernews · mmaunder · 11月13日 22:04 · [社区讨论](https://news.ycombinator.com/item?id=50490593)

**「背景」** 传统 SDR 接收机通常一次只能监听单一频率或窄带宽。该项目采用 GPU 加速的多相位信道化技术，将整个航空频段并行分解为多个窄带信道并同时解调，再丢弃无传输数据以节省带宽。作者在 Hacker News 发布时同步提供了地面停飞期间的原始通话记录。

**「影响」** 该系统为飞行员、管制员和爱好者提供了免费、全频段的实时监听入口，尤其在通信故障等异常情况下可作为辅助态势感知工具。开源实现也为 GPU 加速宽带 SDR 信号处理提供了可参考的工程范例。

**「社区讨论」** 评论者 plipt 指出传输音频仍有约 50% 难以辨认，质疑是否仍为模拟调制以兼容互操作性；molsongolden 确认在发布时刻已捕获到 Encore 3325 航班与管制员关于温哥华地面停飞的对话；ltrg 将其与基于 KiwiSDR 的船舶 DSC 解码项目作比较，认为多接收机时延可用于暗舰定位。

**标签**: `#SDR`, `#GPU-computing`, `#aviation`, `#signal-processing`, `#open-source`

---

<a id="item-tech-news-2"></a>
### [DeepSeek 开放全家桶 API 并开源本地部署聊天 Demo](https://mp.weixin.qq.com/s/78KBHc4-4N5b2vfL9SkutQ) ⭐️ 8.0/10

DeepSeek 正式开放全家桶应用 API，开发者在现有 API 中启用对应参数即可获得深度思考搜索、文件输入、链接阅读、语音对话等能力，服务端自动完成工具调用与上下文拼接。V4.1-Flash 模型已在三个接口中支持；Search、Fetch、OCR、ASR、TTS 亦可单独调用。官方同步开源 deepseek-ai/chat-demo 前端项目，支持导入历史对话，可在本地部署体验类网页端功能，演示地址为 https://deepseek-ai.github.io/chat-demo/。

telegram · zaihuapd · 11月13日 14:27

**「背景」** 此前 DeepSeek 已提供基础大模型 API 服务，此次更新将搜索、文件解析、链接抓取、语音识别与合成等工具能力集成到统一接口中，降低了构建 RAG 与多模态应用的工程门槛。开源聊天 Demo 则让开发者能快速验证 API 集成效果，并支持私有化部署。

**「影响」** 开发者无需自行编排工具调用链路，即可在单次 API 请求中完成联网检索、文档解析、语音交互等复杂任务，显著缩短多模态应用的开发周期；开源 Demo 亦为二次开发与私有化部署提供了现成的前端基座。

**标签**: `#DeepSeek`, `#API`, `#LLM`, `#developer-tools`, `#open-source`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [英伟达黄仁勋辞职引发间谍指控 美中芯片战升级风险加剧](https://www.cnbc.com/2026/11/13/jensen-huang-nvidia-us-china-relations.html) ⭐️ 9.0/10

英伟达 CEO 黄仁勋因与涉嫌中国间谍的婚外情辞职，并同意在 11 月 26 日感恩节前向国会作证；众议院外委会主席马斯特暗示可能举行更多公开听证会。分析人士预测，此事将破坏黄仁勋作为反对对华芯片出口管制最大企业游说者的可信度，国会可能在年内收紧 MATCH 法案和关联企业规则等限制，中国或以切断稀土供应报复。

rss · CNBC Finance · 11月13日 02:56

**「背景脉络」** 美国 2022 年起限制英伟达向中国出口先进芯片，特朗普政府 2025 年放宽部分禁令；黄仁勋曾于 9 月陪同特朗普和习近平在华盛顿宴会同桌，两国领导人将于 11 月 18-19 日在深圳 APEC 峰会再次会晤。11 月 3 日美国中期选举民主党大胜后，媒体曝光黄仁勋涉间谍指控，中国外交部称指控为「无端抹黑」。

**「潜在影响」** 分析师警告美中科技「脱钩」可能重启：美国或加速出口管制立法，中国将加大芯片自主研发并可能限制稀土等关键材料出口，导致全球半导体供应链不确定性显著上升。

**标签**: `#U.S.-China relations`, `#semiconductors`, `#export controls`, `#Nvidia`, `#geopolitics`

---