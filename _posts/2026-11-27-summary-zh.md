---
layout: default
title: "Horizon Summary: 2026-11-27 (ZH)"
date: 2026-11-27
lang: zh
---

> 从 29 条内容中筛选出 3 条重要资讯。

---

**科技新闻**
1. [sqlite3\_rsync：SQLite 数据库远程增量复制工具](#item-tech-news-1) ⭐️ 8.0/10
2. [荷兰拒接受美国 MATCH 法案对 ASML 对华销售的域外限制](#item-tech-news-2) ⭐️ 8.0/10

**财经新闻**
1. [半导体出口首超石油天然成全球第一大出口商品](#item-finance-news-1) ⭐️ 9.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [sqlite3\_rsync：SQLite 数据库远程增量复制工具](https://simonwillison.net/2026/Nov/26/sqlite3-rsync/) ⭐️ 8.0/10

SQLite 官方工具 sqlite3\_rsync 允许通过 SSH 将数据库快照增量复制到远程机器，无需在本地创建完整副本。该工具在 SQLite 3.47.0（2024 年 10 月）作为实验性功能引入，并在 3.50.0（2025 年 5 月）得到增强。它采用类似 rsync 的协议：副本端发送页面哈希，源端仅返回差异页面内容，网络开销仅比数据库大小多出几个百分点。这解决了备份 API 和 VACUUM INTO 都需要双倍磁盘空间的限制。

rss · Simon Willison · 11月26日 06:08

**「背景」** SQLite 传统备份方式（backup API 和 VACUUM INTO）都要求在本地生成完整数据库副本，导致磁盘占用超过 50% 时无法备份。sqlite3\_rsync 利用 SQLite 的页面级哈希比对，实现跨机器增量同步，适合资源受限环境下的数据库快照与灾备。

**「影响」** 运维人员可在磁盘空间不足的小型实例上直接通过 SSH 将 SQLite 数据库增量同步到远程存储，避免因空间不足导致备份失败；同时减少全量传输带宽占用，适合定期同步大型数据库场景。

**标签**: `#sqlite`, `#database`, `#backup`, `#rsync`, `#tools`

---

<a id="item-tech-news-2"></a>
### [荷兰拒接受美国 MATCH 法案对 ASML 对华销售的域外限制](https://www.bloomberg.com/news/articles/2026-11-26/netherlands-plans-to-fight-rollout-of-proposed-us-curbs-on-asml) ⭐️ 8.0/10

荷兰外贸与发展合作大臣 Sjoerd Sjoerdsma 11 月 26 日在议会表示，荷兰不会接受美国通过 MATCH Act 对 ASML 对华销售实施域外管辖，称荷兰“不会任人摆布”。MATCH Act 由美国两党共同提出，要求荷兰、日本等盟友对华实施更严格出口管制，否则美方将单方面限制其半导体设备出口。中国约占 ASML 今年销售额的 20%。荷兰正与欧盟委员会协调，并联合德国、法国游说，争取将该法案从美国年度国防政策法案中剔除；美国国会预计 12 月中旬表决，通过可能性很大。

telegram · zaihuapd · 11月26日 14:56

**「背景」** ASML 是全球唯一极紫外光刻机（EUV）供应商，其设备对先进芯片制造至关重要。美国此前已通过双边协议施压荷兰限制 ASML 对华出口浸没式深紫外光刻机（DUV），MATCH Act 则试图以美国国内法形式强制盟友配合更广泛的对华半导体出口管制，并赋予美国单方面制裁不配合盟友的权力。

**「影响」** 若 MATCH Act 随国防法案通过，ASML 面临在遵守美国域外法规与荷兰/欧盟主权法律之间的合规冲突，可能被迫进一步削减对华出口，影响其约 20% 的营收来源，同时加剧全球半导体供应链的地缘政治碎片化。

**标签**: `#semiconductor`, `#export-controls`, `#ASML`, `#geopolitics`, `#supply-chain`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [半导体出口首超石油天然成全球第一大出口商品](https://www.cnbc.com/2026/11/26/semiconductor-chips-are-the-new-oil-heres-why.html) ⭐️ 9.0/10

德意志银行分析国际贸易中心数据显示，2026 年第一季度全球半导体出口额达 1.61 万亿美元，首次超过同期石油天然气出口的 1.53 万亿美元；第二季度差距扩大至 1.60 万亿对 1.47 万亿，伊朗战争导致霍尔木兹海峡石油日流量暴跌 77%加剧了这一趋势。

rss · CNBC Finance · 11月26日 17:52

**「背景脉络」** AI 热潮推动数据中心建设激增，GPU 等算力芯片需求旺盛；德银指出这类似 1970 年代石油贸易爆发形成的“石油美元”循环，亚洲芯片顺差国可能将收益回流投资美股科技股、初创企业和数据中心，进一步为 AI 投资周期提供融资。

**「潜在影响」** 全球贸易结构性转移可能重塑跨境资金流向：半导体顺差回流美股科技资产或推高企业和政府债券收益率，同时芯片股极端波动（SOX 指数周跌 17%、英伟达七周跌 46%）凸显新周期的高波动特征。

**标签**: `#semiconductors`, `#global trade`, `#macroeconomics`, `#AI`, `#financial markets`

---