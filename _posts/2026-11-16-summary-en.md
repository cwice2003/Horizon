---
layout: default
title: "Horizon Summary: 2026-11-16 (EN)"
date: 2026-11-16
lang: en
---

> From 23 items, 3 important content pieces were selected

---

**Technology News**
1. [MacBook Pro Tandem OLED Displays Show 480–960 Hz PWM Flicker Instead of DC Dimming](#item-tech-news-1) ⭐️ 8.0/10
2. [Meituan Open-Sources LongCat-2.5 Trained on Huawei Ascend Chips](#item-tech-news-2) ⭐️ 8.0/10

**Financial News**
1. [Lutnick resisted chip crackdown as sons&\#x27; firm cut Nvidia stake](#item-finance-news-1) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [MacBook Pro Tandem OLED Displays Show 480–960 Hz PWM Flicker Instead of DC Dimming](https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/) ⭐️ 8.0/10

The new MacBook Pro models with tandem OLED displays use pulse-width modulation \(PWM\) at 480 Hz and 960 Hz across most usable brightness levels instead of the expected DC dimming, according to measurements published by MacAnorak. The dual-layer OLED panels appear to run both layers at 480 Hz, 180 degrees out of phase, producing an effective 960 Hz flicker when both layers are active. This behavior affects users who are sensitive to display flicker, including those with concussion history or photophobia, and contradicts the assumption that OLED would eliminate PWM-related strain.

hackernews · MacAnorak · Nov 15, 13:15 · [Discussion](https://news.ycombinator.com/item?id=50506719)

**「Background」** Tandem OLED stacks two organic light-emitting layers to increase brightness and longevity while maintaining per-pixel contrast. Earlier OLED laptops and phones often used DC dimming at higher brightness and switched to PWM only at very low levels; Apple&\#x27;s previous mini-LED MacBook Pros employed PWM at roughly 480 Hz. The shift to tandem OLED was expected to reduce or remove PWM in the normal working range, but the reported measurements show the opposite.

**「Impact」** Flicker-sensitive users report eye strain, headaches, and reduced concentration when using the affected MacBook Pro models, and no software toggle exists to force DC dimming at typical brightness. Professionals who rely on long editing or coding sessions may need to test the display in person or consider external monitors with verified DC dimming.

**「Community Discussion」** Hacker News commenters debate whether the dual-layer phase relationship creates an effective 960 Hz signal that is less harmful or whether the 480 Hz fundamental remains problematic; some users with concussion experience note that any screen flicker aggravates symptoms, while others call for more research on PWM sensitivity prevalence.

**Tags**: `#display-technology`, `#pwm`, `#macbook-pro`, `#oled`, `#accessibility`

---

<a id="item-tech-news-2"></a>
### [Meituan Open-Sources LongCat-2.5 Trained on Huawei Ascend Chips](https://the-decoder.com/meituan-releases-a-1-6-trillion-parameter-agent-model-that-never-touched-an-nvidia-gpu/) ⭐️ 8.0/10

Meituan has released LongCat-2.5, a 1.6-trillion-parameter multimodal agent model with 48 billion active parameters per token, under an MIT license. The company states the model was trained entirely on Huawei Ascend accelerators without using NVIDIA GPUs. LongCat-2.5 accepts text, image, and video inputs and is designed for autonomous, multi-step coding tasks. On Terminal Bench v2.1 it scores 88.4, close to Claude Opus 5&\#x27;s 89.1.

telegram · zaihuapd · Nov 15, 11:08

**「Background」** LongCat-2.5 follows Meituan&\#x27;s earlier LongCat releases and targets the growing category of coding agents that can execute extended, multi-step programming workflows. The claim of training a trillion-parameter-scale model solely on domestic Chinese hardware reflects ongoing efforts to reduce reliance on NVIDIA GPUs amid export restrictions.

**「Impact」** Developers and organizations can now experiment with a permissively licensed, near-state-of-the-art coding agent that runs on non-NVIDIA hardware, potentially lowering barriers to deploying large-scale agent workflows on Huawei Ascend infrastructure.

**Tags**: `#large-language-models`, `#ai-hardware`, `#open-source-ai`, `#coding-agents`, `#china-tech`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Lutnick resisted chip crackdown as sons&\#x27; firm cut Nvidia stake](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 8.0/10

Commerce Secretary Howard Lutnick resisted intelligence-backed pressure to restrict a Singapore firm suspected of smuggling Nvidia AI chips to China while his sons&\#x27; firm, Cantor Fitzgerald, cut its reported Nvidia stake by nearly half — from 3.5 million shares worth $652 million in September 2025 to 1.78 million shares worth $310 million by March 2026 — according to CNBC analysis of securities filings.

rss · CNBC Finance · Nov 15, 19:58

**「Background」** Lutnick received classified warnings about Nvidia CEO Jensen Huang&\#x27;s ties to a suspected Chinese spy before Huang resigned amid a spy probe, and Treasury Secretary Scott Bessent said other agencies had favored sanctioning the Singapore firm for months but Commerce controls the entity list that imposes such restrictions.

**「Impact」** The episode raises conflict-of-interest questions for the cabinet official overseeing export controls while his family&\#x27;s firm holds financial ties to the chipmaker at the center of U.S.-China tech competition.

**Tags**: `#semiconductors`, `#export-controls`, `#ethics`, `#Nvidia`, `#China-trade`

---