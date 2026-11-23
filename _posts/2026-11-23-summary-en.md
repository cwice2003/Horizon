---
layout: default
title: "Horizon Summary: 2026-11-23 (EN)"
date: 2026-11-23
lang: en
---

> From 21 items, 3 important content pieces were selected

---

**Technology News**
1. [O&\#x27;Reilly Radar: Silicon Valley&\#x27;s Mechanism Design Crisis](#item-tech-news-1) ⭐️ 8.0/10
2. [OpenAI Examines Perplexity-Intelligence Link in Language Models](#item-tech-news-2) ⭐️ 8.0/10

**Technology Blog**
1. [When in Doubt, Flail About: Rapid Experimentation Under Uncertainty](#item-tech-blog-1) ⭐️ 5.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [O&\#x27;Reilly Radar: Silicon Valley&\#x27;s Mechanism Design Crisis](https://www.oreilly.com/radar/what-happened-to-silicon-valley/) ⭐️ 8.0/10

An O&\#x27;Reilly Radar article argues that Silicon Valley&\#x27;s structural problems arise from mechanism design choices that optimize for shareholder value rather than human flourishing. The analysis frames the issue as a question of what game the tech industry ought to be playing, using mechanism design and game theory to examine the fundamental optimization targets of tech capitalism. The piece garnered significant engagement on Hacker News with 476 points and 275 comments.

hackernews · greenyouse · Nov 22, 19:20 · [Discussion](https://news.ycombinator.com/item?id=50602947)

**「Background」** Mechanism design, sometimes called reverse game theory, asks what rules should govern a system to achieve desired outcomes rather than analyzing outcomes from given rules. The article applies this framework to Silicon Valley&\#x27;s incentive structures, suggesting that current corporate governance mechanisms were designed to maximize financial returns for shareholders, a paradigm reinforced by decades of financialization and zero-interest-rate policy that enabled massive capital deployment.

**「Impact」** The analysis suggests that without redesigning the underlying incentive mechanisms — such as corporate governance models, venture capital fund structures, and executive compensation — regulatory or cultural interventions will have limited effect on outcomes like AI safety, labor practices, or market concentration. Readers involved in startup governance, policy, or technical leadership may need to evaluate whether their organizational mechanisms align with stated human-centered goals.

**「Community Discussion」** Commenters highlighted the article&\#x27;s core question — &quot;What game ought we to be playing?&quot; — with several arguing that the zero-interest-rate era allowed companies to grow to &quot;grotesque proportions&quot; and that current AI-driven cost-cutting reflects a reversion to shareholder-value optimization. Others noted a cultural shift from technical builders to &quot;VC influencers&quot; and referenced Milton Friedman&\#x27;s shareholder primacy doctrine as a root cause.

**Tags**: `#technology-industry`, `#silicon-valley`, `#mechanism-design`, `#capitalism`, `#human-flourishing`

---

<a id="item-tech-news-2"></a>
### [OpenAI Examines Perplexity-Intelligence Link in Language Models](https://openai.com/index/perplexity-and-intelligence/) ⭐️ 8.0/10

OpenAI published a blog post exploring the correlation between perplexity — a measure of next-token prediction surprise — and model intelligence in large language models. The piece examines how lower perplexity \(better compression of training data\) corresponds to stronger reasoning capabilities, using a common held-out evaluation set to compare models including GPT-5.6 Sol and Microsoft&\#x27;s MAI-2 Base. The analysis revives a foundational metric for LLM progress amid increasing reliance on reinforcement learning and complex benchmarks.

hackernews · acossta · Nov 22, 17:06 · [Discussion](https://news.ycombinator.com/item?id=50601525)

**「Background」** Perplexity quantifies a model&\#x27;s uncertainty when predicting the next token: a perfect predictor achieves perplexity of 1, while a random predictor&\#x27;s perplexity equals the vocabulary size. The idea that compression \(low prediction loss\) equates to intelligence dates back to at least a 2008 paper arguing that extracting world models from raw data is measured by prediction rate. Recent LLM development has shifted toward reinforcement learning and specialized benchmarks, making the cross-entropy loss baseline a simpler, long-standing reference point.

**「Impact」** Microsoft has joined OpenAI&\#x27;s evaluation framework, reporting MAI-2 Base&\#x27;s log-perplexity of 0.819 on the same held-out set, placing it near GPT-5.6 Sol. This cross-vendor adoption suggests perplexity may become a standardized pre-training progress metric, giving developers a simpler, comparable baseline amid proliferating and often convoluted reasoning benchmarks.

**「Community Discussion」** Commenters debated whether cross-entropy loss remains the core driver of intelligence given the rise of RL, with some finding the clear perplexity-intelligence trend surprising. A 2008 paper was cited arguing the compression-intelligence link is fundamental, while others noted GPT-4.5&\#x27;s absence from the chart and questioned whether o1 marked the true start of reasoning models.

**Tags**: `#LLM evaluation`, `#perplexity`, `#OpenAI`, `#scaling laws`, `#model intelligence`

---

## Technology Blog

<a id="item-tech-blog-1"></a>
### [When in Doubt, Flail About: Rapid Experimentation Under Uncertainty](https://seangoedecke.com/when-in-doubt-flail-about/) ⭐️ 5.0/10

rss · Sean Goedecke · Nov 23, 00:00

**「Background」** The author argues that when engineers face unclear situations without clear guidance, cautious waiting is typically counterproductive; instead, rapid experimentation—termed &quot;flailing&quot;—is the fastest way to gain understanding and become useful, despite feeling like repeated failure from the inside.

**「Solution」** The method involves three principles: try many different approaches to maximize contact with reality, pay extremely careful attention to feedback from both people and system metrics, and ruthlessly abandon any plan not generating positive signals. The author identifies three contexts where this applies: product flailing \(testing features around a core idea until traction emerges, as with GitHub Models where AI inference via Actions tokens became the seed for &quot;Continuous AI&quot;\), engineering flailing \(making speculative changes to complex, opaque systems rather than exhaustively analyzing them first, aided now by AI agents that can generate multiple refactor candidates\), and organizational flailing \(attempting various interventions—automation, task ownership, long-term proposals—when team dynamics are broken and no one can articulate the fix\). The psychological key is recognizing that the uncomfortable sensation of flailing is normal and should be treated as a positive signal, not a warning, provided one remains sensitive to feedback and drops failing plans instantly.

**「Takeaway」** Effective engineering under uncertainty requires embracing the discomfort of rapid, feedback-driven trial-and-error across product, technical, and organizational domains, treating the feeling of &quot;flailing&quot; as a sign of productive exploration rather than incompetence.

**Tags**: `#engineering-strategy`, `#decision-making`, `#organizational-dynamics`, `#experimentation`, `#career-advice`

---