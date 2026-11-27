---
layout: default
title: "Horizon Summary: 2026-11-27 (EN)"
date: 2026-11-27
lang: en
---

> From 29 items, 3 important content pieces were selected

---

**Technology News**
1. [sqlite3\_rsync Enables Space-Efficient Remote SQLite Copies](#item-tech-news-1) ⭐️ 8.0/10
2. [Dutch Minister Rejects US MATCH Act Curbs on ASML China Sales](#item-tech-news-2) ⭐️ 8.0/10

**Financial News**
1. [Semiconductor exports overtake oil and gas in global trade value for first time](#item-finance-news-1) ⭐️ 9.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [sqlite3\_rsync Enables Space-Efficient Remote SQLite Copies](https://simonwillison.net/2026/Nov/26/sqlite3-rsync/) ⭐️ 8.0/10

SQLite&\#x27;s sqlite3\_rsync tool, introduced experimentally in version 3.47.0 \(October 2024\) and enhanced in 3.50.0 \(May 2025\), allows copying a database snapshot to a remote machine over SSH without requiring enough local disk space for a full duplicate. Unlike the backup API or VACUUM INTO, which need double the database size on disk, sqlite3\_rsync uses an rsync-like protocol that exchanges cryptographic page hashes and transfers only differing pages. The tool can also incrementally synchronize an existing remote copy, with network overhead of only a few percent above the database size.

rss · Simon Willison · Nov 26, 06:08

**「Background」** Standard SQLite backup methods — the backup API and VACUUM INTO — create a complete local copy before any transfer, making them impractical on storage-constrained hosts where the database already occupies more than half the available space. sqlite3\_rsync was added to SQLite&\#x27;s source tree as an experimental utility to address this limitation by streaming changes directly to a remote replica.

**「Impact」** Developers and operators running SQLite on small instances \(e.g., edge devices, containers, or low-cost VMs\) can now take off-site backups or replicate databases without provisioning extra local storage, and can keep replicas current with minimal bandwidth using incremental syncs.

**Tags**: `#sqlite`, `#database`, `#backup`, `#rsync`, `#tools`

---

<a id="item-tech-news-2"></a>
### [Dutch Minister Rejects US MATCH Act Curbs on ASML China Sales](https://www.bloomberg.com/news/articles/2026-11-26/netherlands-plans-to-fight-rollout-of-proposed-us-curbs-on-asml) ⭐️ 8.0/10

Dutch Trade Minister Sjoerd Sjoerdsma told parliament on November 26 that the Netherlands will not accept further U.S. restrictions on ASML&\#x27;s sales to China and opposes the extraterritorial reach of the bipartisan MATCH Act. The Netherlands is coordinating with the European Commission and lobbying jointly with Germany and France to have the provision removed from the upcoming U.S. defense authorization bill. China accounts for roughly 20% of ASML&\#x27;s revenue this year, and Congress is expected to vote on the bill in mid-December with a high likelihood of passage.

telegram · zaihuapd · Nov 26, 14:56

**「Background」** The MATCH Act would require allies including the Netherlands and Japan to adopt stricter semiconductor export controls toward China or face unilateral U.S. restrictions on their equipment makers. ASML is the sole supplier of extreme ultraviolet \(EUV\) lithography systems essential for advanced chip manufacturing, making its export policy a focal point in U.S.-China technology competition.

**「Impact」** If the MATCH Act becomes law, ASML could lose access to its largest non-U.S. market unless the Dutch government complies, directly affecting the company&\#x27;s revenue and the global supply of advanced chipmaking equipment.

**Tags**: `#semiconductor`, `#export-controls`, `#ASML`, `#geopolitics`, `#supply-chain`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Semiconductor exports overtake oil and gas in global trade value for first time](https://www.cnbc.com/2026/11/26/semiconductor-chips-are-the-new-oil-heres-why.html) ⭐️ 9.0/10

Semiconductor exports surpassed oil and gas in global export value for the first time in the first quarter of 2026, reaching about $1.61 trillion versus $1.53 trillion for oil and gas on a four-quarter rolling basis, according to Deutsche Bank analysis of International Trade Centre data.

rss · CNBC Finance · Nov 26, 17:52

**「Background」** The milestone reflects insatiable AI-driven demand for chips amid soaring data center construction, while oil supplies were disrupted by a 77% collapse in daily flows through the Strait of Hormuz following the Iran war, according to the U.S. Energy Information Administration.

**「Impact」** Deutsche Bank suggests the shift could create a &quot;chip dollar&quot; dynamic where Asian semiconductor-surplus nations recycle earnings into U.S. technology stocks and data centers rather than Treasuries, potentially altering global financial flows and keeping yields structurally higher.

**Tags**: `#semiconductors`, `#global trade`, `#macroeconomics`, `#AI`, `#financial markets`

---