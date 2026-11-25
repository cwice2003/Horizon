---
layout: default
title: "Horizon Summary: 2026-11-25 (EN)"
date: 2026-11-25
lang: en
---

> From 20 items, 3 important content pieces were selected

---

**Technology News**
1. [Active Intrusion Campaign Targets Check Point Servers via V8 PRNG Weakness](#item-tech-news-1) ⭐️ 8.0/10
2. [PrismML Releases Ternary Bonsai 2.5 27B: 2-Bit Quantized Model for Local Coding](#item-tech-news-2) ⭐️ 8.0/10
3. [VMware vCenter Critical Auth Bypass CVE-2026-123903 Patched](#item-tech-news-3) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Active Intrusion Campaign Targets Check Point Servers via V8 PRNG Weakness](https://www.greynoise.io/blog/check-point-security-management-servers-intrusion-campaign) ⭐️ 8.0/10

GreyNoise reports an active intrusion campaign targeting Check Point security management servers, exploiting a weakness in Node.js V8&\#x27;s Math.random\(\) to forge administrative session cookies. Attackers scan for vulnerable servers, collect multiple session identifiers from the loginSrp1 endpoint, and reconstruct the PRNG internal state to recover the signing key. The campaign appears to leverage CVE-2026-16232 as an initial access vector, though it remains unclear whether all affected organizations had their management servers exposed to the internet. GreyNoise&\#x27;s analysis indicates this is a real-world attack against widely deployed enterprise security infrastructure.

hackernews · louiereederson · Nov 24, 16:32 · [Discussion](https://news.ycombinator.com/item?id=50630594)

**「Background」** The attack exploits a known weakness in V8&\#x27;s Math.random\(\) implementation, which uses a predictable pseudo-random number generator \(PRNG\) unsuitable for cryptographic purposes. Check Point&\#x27;s security management servers use this function to generate session identifiers \(sid\) for signed cookies, allowing an attacker who observes enough outputs to recover the PRNG state and forge valid admin sessions. CVE-2026-16232, a vulnerability in Check Point&\#x27;s HFS \(HTTP File Server\) component, is suspected as the initial entry point for the campaign.

**「Impact」** Organizations running Check Point security management servers with internet-accessible management interfaces should immediately verify whether they are affected, apply any available patches for CVE-2026-16232, and rotate all administrative session keys. The attack demonstrates that cryptographic secrets derived from Math.random\(\) can be practically recovered, requiring developers to replace such usages with cryptographically secure random generators.

**「Community Discussion」** Commenters debate whether the root cause lies in applications misusing Math.random\(\) or in the V8 engine providing a non-cryptographic PRNG by default. Some note the initial access vector remains unclear, with questions about whether all compromised organizations had their management servers directly exposed to the internet. Others warn that AI-assisted exploitation will lower the barrier for such attacks.

**Tags**: `#security`, `#vulnerability`, `#intrusion`, `#check-point`, `#prng`

---

<a id="item-tech-news-2"></a>
### [PrismML Releases Ternary Bonsai 2.5 27B: 2-Bit Quantized Model for Local Coding](https://prismml.com/news/bonsai-2-5-27b) ⭐️ 8.0/10

PrismML has released Ternary Bonsai 2.5 27B, a 2-bit \(ternary\) quantized model that achieves frontier-like coding benchmark scores while running at 22–25 tokens per second on consumer Mac hardware with 128k context. The model is distributed as a Q2 GGUF and fits in 24 GB RAM on a Mac Mini M5 Pro, making it practical for agentic coding workflows. Community reports indicate SWE-bench Verified performance comparable to Opus 4.6 \(released February 2026\), though the benchmark&\#x27;s representativeness is debated. The release advances extreme quantization at the 27B parameter scale for local inference.

hackernews · b0m · Nov 24, 20:08 · [Discussion](https://news.ycombinator.com/item?id=50633922)

**「Background」** Ternary quantization reduces model weights to three values \(−1, 0, +1\), enabling roughly 2-bit storage per parameter and dramatically lowering memory bandwidth requirements. Prior Bonsai versions established that ternary quantization could preserve reasoning capabilities at smaller scales; Bonsai 2.5 extends this to 27B parameters with a 128k context window. The SWE-bench Verified benchmark evaluates models on real-world software engineering tasks from popular Python repositories.

**「Impact」** Developers can now run a 27B-parameter coding model with 128k context entirely on a Mac Mini M5 Pro \(24 GB RAM\) at interactive speeds, enabling local agentic coding without cloud API costs or latency. The 22–25 tok/s generation rate supports multi-step coding agents, and the 128k context allows whole-repository context in a single session. Users should verify task-specific performance, as SWE-bench Verified may not fully represent general coding ability.

**「Community Discussion」** Commenters report real-world speeds of 22–25 tok/s on Mac Mini M5 Pro with 24 GB RAM and confirm 128k context fits in memory. One user notes SWE-bench Verified scores matching Opus 4.6 but questions whether this reflects benchmark saturation, underlying benchmark drift, or genuine frontier-like capability in small models with a ~6-month lag. Another requests direct comparisons to equivalently quantized Qwen 3.8B or other 1B–10B models. A self-reported long-horizon benchmark shows Bonsai 2.5 completing tasks in 29% less time with 17% fewer steps than Bonsai 2, though both pass 5 of 8 tests.

**Tags**: `#LLM quantization`, `#local inference`, `#coding benchmarks`, `#ternary quantization`, `#agentic coding`

---

<a id="item-tech-news-3"></a>
### [VMware vCenter Critical Auth Bypass CVE-2026-123903 Patched](https://thehackernews.com/2026/11/vmware-vcenter-hit-by-another-critical.html) ⭐️ 8.0/10

Broadcom released patches for 23 vulnerabilities across VMware products, including a critical authentication bypass in vCenter Directory Service \(vmdir\) tracked as CVE-2026-123903 with a CVSS score of 9.8. The flaw allows any attacker with network access to vCenter to bypass authentication entirely and gain unauthorized system access. This vulnerability was actively exploited as a zero-day days before the patch release, according to The Hacker News.

telegram · zaihuapd · Nov 24, 14:50

**「Background」** VMware vCenter Server is the centralized management platform for vSphere environments, and its Directory Service \(vmdir\) handles authentication and identity management. Authentication bypass vulnerabilities in vmdir are particularly severe because they can grant full administrative control over virtualized infrastructure without requiring credentials. Broadcom acquired VMware in late 2023 and has since taken over security advisory publications.

**「Impact」** Organizations running unpatched vCenter instances face immediate risk of complete compromise; administrators should apply the Broadcom security updates immediately and verify that no unauthorized access occurred during the zero-day exploitation window.

**Tags**: `#security`, `#vulnerability`, `#vmware`, `#vcenter`, `#authentication-bypass`

---