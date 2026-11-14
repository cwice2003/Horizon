---
layout: default
title: "Horizon Summary: 2026-11-14 (EN)"
date: 2026-11-14
lang: en
---

> From 20 items, 3 important content pieces were selected

---

**Technology News**
1. [Live full-airband SDR streaming from Orcas Island using dual RTX 4090 GPUs](#item-tech-news-1) ⭐️ 8.0/10
2. [DeepSeek Opens Full-Featured API Suite with Built-in Tool Use](#item-tech-news-2) ⭐️ 8.0/10

**Financial News**
1. [Nvidia CEO Resigns Amid Spy Allegations, Threatening U.S.-China Tech Truce](#item-finance-news-1) ⭐️ 9.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Live full-airband SDR streaming from Orcas Island using dual RTX 4090 GPUs](https://orcasairband.com/) ⭐️ 8.0/10

A live, multi-frequency aviation radio stream from Orcas Island \(KORS\) captures and demodulates the entire 118–137 MHz airband simultaneously using an Ettus B210 SDR and dual NVIDIA RTX 4090 GPUs. The system employs a CUDA-accelerated polyphase channelizer to split the wideband signal into individual channels, demodulate them, detect active transmissions, and discard silent periods. The stream proved immediately useful during a real ground stop at Victoria/Vancouver, letting local pilots monitor ATC communications across all frequencies in real time.

hackernews · mmaunder · Nov 13, 22:04 · [Discussion](https://news.ycombinator.com/item?id=50490593)

**「Background」** Software-defined radio \(SDR\) combined with GPU-accelerated polyphase channelization enables wideband signal processing that was previously impractical on consumer hardware. Earlier hobbyist projects typically monitored one or a few frequencies at a time; this implementation extends the approach to the full aviation band, building on open-source SDR frameworks and CUDA signal-processing libraries.

**「Impact」** Aviation enthusiasts, researchers, and local pilots gain a free, real-time view of all airband traffic in the region, which proved valuable during the Victoria ground stop for situational awareness. The project also serves as a reference implementation for GPU-accelerated wideband demodulation applicable to other spectrum-monitoring tasks.

**「Community discussion」** Commenters noted that many transmissions sound garbled and questioned whether aviation voice remains analog for security or interoperability reasons. One user compared the approach to a KiwiSDR-based project that decodes maritime DSC signals across multiple receivers for vessel triangulation.

**Tags**: `#SDR`, `#GPU-computing`, `#aviation`, `#signal-processing`, `#open-source`

---

<a id="item-tech-news-2"></a>
### [DeepSeek Opens Full-Featured API Suite with Built-in Tool Use](https://mp.weixin.qq.com/s/78KBHc4-4N5b2vfL9SkutQ) ⭐️ 8.0/10

DeepSeek has released a comprehensive API suite that adds integrated tool calling to its existing API endpoints. Developers can now enable parameters to access deep-thinking search, file input, link fetching, OCR, ASR, and TTS capabilities, with the server automatically handling tool orchestration and context stitching. The V4.1-Flash model is supported across three interfaces, and each tool \(Search, Fetch, OCR, ASR, TTS\) can also be called individually. DeepSeek also open-sourced a chat demo \(deepseek-ai/chat-demo\) that supports local deployment and history import.

telegram · zaihuapd · Nov 13, 14:27

**「Background」** DeepSeek previously offered a standard LLM API for text generation. This release extends that API into a platform-style offering by embedding multiple modalities and tool-use capabilities directly into the service layer, reducing the need for developers to build custom orchestration for retrieval-augmented generation and multimodal workflows.

**「Impact」** Developers can now build RAG, document analysis, and voice-enabled applications on DeepSeek without managing separate tool-calling infrastructure, lowering integration complexity and latency for multimodal use cases.

**Tags**: `#DeepSeek`, `#API`, `#LLM`, `#developer-tools`, `#open-source`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Nvidia CEO Resigns Amid Spy Allegations, Threatening U.S.-China Tech Truce](https://www.cnbc.com/2026/11/13/jensen-huang-nvidia-us-china-relations.html) ⭐️ 9.0/10

Nvidia CEO Jensen Huang resigned Thursday and agreed to testify before Congress before Thanksgiving over allegations of an affair with an alleged Chinese spy, prompting analysts to predict tighter U.S. semiconductor export controls ahead of a Trump-Xi summit next week in Shenzhen.

rss · CNBC Finance · Nov 13, 02:56

**「Background」** Washington restricted Nvidia&\#x27;s advanced chip sales to China in 2022, but the Trump administration eased many limits in 2025; the current allegations emerge days after Democrats won the U.S. midterms and as both sides prepare for the APEC leaders&\#x27; meeting Nov. 18-19.

**「Impact」** Analysts warn Congress may pass the MATCH Act and Affiliates Rule to further limit China&\#x27;s access to Dutch and Japanese chip suppliers, while Beijing could retaliate by cutting off rare earths and other critical chipmaking materials.

**Tags**: `#U.S.-China relations`, `#semiconductors`, `#export controls`, `#Nvidia`, `#geopolitics`

---