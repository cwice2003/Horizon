---
layout: default
title: "Horizon Summary: 2026-11-16 (ZH)"
date: 2026-11-16
lang: zh
---

> 从 23 条内容中筛选出 3 条重要资讯。

---

**科技新闻**
1. [MacBook Pro 串联 OLED 屏幕存在 PWM 频闪问题](#item-tech-news-1) ⭐️ 8.0/10
2. [美团开源 LongCat-2.5 称仅用华为升腾芯片训练](#item-tech-news-2) ⭐️ 8.0/10

**财经新闻**
1. [美国商务部长卢特尼克面临利益冲突质疑，其子公司大幅减持英伟达股份](#item-finance-news-1) ⭐️ 8.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [MacBook Pro 串联 OLED 屏幕存在 PWM 频闪问题](https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/) ⭐️ 8.0/10

MacAnorak 报道称，新款 MacBook Pro 采用的串联 OLED 屏幕在可用亮度范围内表现为 480-960Hz 的 PWM 调光，而非预期的直流调光，导致对频闪敏感的用户出现眼疲劳、头痛等健康问题。文章通过示波器实测发现，双层 OLED 面板各以 480Hz、相位相差 180 度工作，叠加后在大部分亮度下呈现 960Hz 等效频闪。该问题影响广泛使用该设备的专业用户群体。

hackernews · MacAnorak · 11月15日 13:15 · [社区讨论](https://news.ycombinator.com/item?id=50506719)

**「背景」** 串联 OLED 技术通过堆叠两层发光层提升亮度与寿命，本应支持直流调光以消除频闪。此前业界普遍预期苹果在高端机型上采用无频闪调光方案，但实测显示新机型在典型亮度下仍依赖高频 PWM。

**「影响」** 对频闪敏感的用户（包括脑震荡恢复期人群）在使用新款 MacBook Pro 时可能加重症状，需通过降低亮度至极低水平或使用外接显示器规避，无法通过软件更新彻底解决。

**「社区讨论」** Hacker News 讨论中，用户 legitronics 指出实测频率可能为 960Hz 而非文中所述 240Hz，认为双层面板相位差导致等效频率翻倍；achr2 引用 Nature 论文指出人类可感知显示器刷新率两倍以上的频闪，质疑苹果发布低频 PWM 屏幕的决策。

**标签**: `#display-technology`, `#pwm`, `#macbook-pro`, `#oled`, `#accessibility`

---

<a id="item-tech-news-2"></a>
### [美团开源 LongCat-2.5 称仅用华为升腾芯片训练](https://the-decoder.com/meituan-releases-a-1-6-trillion-parameter-agent-model-that-never-touched-an-nvidia-gpu/) ⭐️ 8.0/10

美团旗下 LongCat 团队开源了 LongCat-2.5，这是一个拥有 1.6 万亿总参数、每 token 激活约 480 亿参数的多模态编程智能体模型。官方声称训练全程仅使用华为升腾加速卡，未使用任何英伟达 GPU。模型支持文本、图像和视频输入，权重采用 MIT 许可证发布，允许商用。在 Terminal Bench v2.1 基准测试中得分 88.4，接近 Claude Opus 5 的 89.1。

telegram · zaihuapd · 11月15日 11:08

**「背景」** LongCat-2.5 是 LongCat 模型正式发布一周后公开的权重版本，专为能自主完成冗长、多步骤编程任务的智能体设计。该发布延续了中国科技公司在大模型训练上探索国产芯片替代方向的趋势。

**「影响」** 开发者和组织获得了一个可商用的高性能编程智能体模型，其声称的纯国产芯片训练路径为寻求减少对英伟达硬件依赖的 AI 基础设施提供了一个可参考的替代选择。

**标签**: `#large-language-models`, `#ai-hardware`, `#open-source-ai`, `#coding-agents`, `#china-tech`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [美国商务部长卢特尼克面临利益冲突质疑，其子公司大幅减持英伟达股份](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 8.0/10

CNBC 报道显示，美国商务部长霍华德·卢特尼克在白宫和情报机构施压要求打击涉嫌向中国走私英伟达芯片的新加坡公司 Megaspeed 时多次抵制，而其儿子布兰登和凯尔领导的 Cantor Fitzgerald 公司在 2025 年 9 月至 2026 年 3 月间将持有的英伟达股份减少近 50%（从 350 万股降至 178 万股），市值从 6.52 亿美元跌至 3.1 亿美元。同期卢特尼克收到关于英伟达 CEO 黄仁勋涉嫌与中国间谍有关联的机密情报警告，黄仁勋随后于 2026 年 11 月辞职。

rss · CNBC Finance · 11月15日 19:58

**「背景脉络」** 卢特尼克于 2025 年 2 月出任商务部长前长期掌管 Cantor Fitzgerald，该公司曾是英伟达第二大持仓股票；2025 年夏季特朗普政府放宽对英伟达 H20 芯片对华销售限制后，Cantor 持仓市值一度上涨 36%。参议员班克斯和沃伦曾在 2026 年 3 月敦促卢特尼克重新审查英伟达出口许可。财长贝森特近日表示财政、国防、国务院和贸易代表办公室均支持将 Megaspeed 列入实体清单，但商务部负责执行。

**「潜在影响」** 伦理专家指出卢特尼克与家族公司持仓变动的时间重合引发利益输送嫌疑，虽无直接证据证明其共享机密信息，但可能削弱公众对芯片出口管制政策公正性的信任，并加剧国会对商务部执法独立性的监督压力。

**标签**: `#semiconductors`, `#export-controls`, `#ethics`, `#Nvidia`, `#China-trade`

---