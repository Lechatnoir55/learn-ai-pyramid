# 📐 learn-ai-pyramid — Explain any concept with the Pyramid Principle / 用金字塔原理讲清一个概念

> **One-liner**: 📐 learn-ai-pyramid uses the Pyramid Principle to turn any concept into a concise "conclusion first + logical support" micro-pyramid, helping you explain complex ideas with clarity and structure.
>
> **一句话介绍**：📐 learn-ai-pyramid 用《金字塔原理》把一个概念讲成「结论先行 + 有逻辑支撑」的微金字塔，专治你「看不懂 / 太散 / 语无伦次」的解释焦虑。

---

## 🤔 Sound familiar? / 你有没有过这种时刻

- You want to understand **MCP / RAG / Agent**, bookmark a dozen posts, and your brain is still mush 🫠
- 想搞懂 **MCP / RAG / Agent**，搜了一圈，收藏夹吃灰，脑子还是浆糊 🫠
- You ask AI "what is XX" and get a wall of text — more confused after reading, **info yes, structure no**
- 问 AI「XX 是什么」，它回你一大段，看完更懵——**信息有，结构没有**
- You try to explain it and drift off-topic, forgetting your own point halfway 🐑
- 自己给别人讲，讲着讲着就跑题，最后连自己都忘了中心思想 🐑

**This skill is built to clean up exactly that mess. / 本 skill 就是来收拾这种局面的。**

---

## 🧱 What it actually does / 它到底干了啥

No inspiration, no purple prose — just a hard rule set distilled from *The Minto Pyramid Principle* (Barbara Minto):
不靠灵感，不靠文采，靠一套从《金字塔原理》（芭芭拉·明托）蒸馏出来的**硬规则集**：

- 🔝 **Lead with the answer** — the central idea goes on top; it's a claim, not a metaphor
  **结论先行** —— 中心思想置顶，是断言不是比喻
- 🧩 **Ideas are full sentences** — subject + verb, make people ask "why / how"
  **思想是完整句** —— 有主谓，能让人追问「为什么 / 怎么做」
- 🚫 **No filler layers** — if it collapses after dropping the numbers, cut it
  **禁止废话层** —— 删掉数量词还站不住的，一律砍掉
- 🔽 **Top-down support** — the upper level must be derivable from the lower ones; no orphan points
  **以上统下** —— 上层必须能被下层倒推出来，不许有孤儿要点
- 🗂️ **MECE + logical order** — no overlap, no gaps, sequence that actually makes sense
  **MECE + 逻辑递进** —— 不重叠不遗漏，顺序讲得通

Short **≠ one sentence**; short must still be a complete mini-pyramid.
短，**不等于一句话**；短，也必须是个完整的微金字塔。

---

## 🍱 Four ways to open it / 四种打开方式（菜单任选）

| Mode / 模式 | Use it when you… / 适合你…… |
|---|---|
| ✂️ **Concise / 精简版** | just want the core, fast / 只想快速 get 到核心 |
| 📖 **Detailed / 详细版** | want it unpacked with the full story / 要展开、要来龙去脉 |
| 🧠 **Mindmap / 思维导图** | visual thinker, want the whole picture in one diagram / 视觉型选手，爱一张图看全貌 |
| 🛠️ **How-to / 实操版** | skip the theory, tell me how to actually use it / 别讲虚的，告诉我怎么上手 |
| 🔤 **Jargon / 黑话对照** | intimidated by terms, want plain-language translation / 被术语劝退，想要人话翻译 |

Modes you've already seen won't be re-suggested — keep asking and it goes deeper.
看过的模式不会再推，追着问就往深挖。

---

## ✅ Use me vs ❌ Don't / 用我 vs 别用我

**✅ Great for / 适合**："help me get MCP" / "what is XX" / "your last answer was scattered, rewrite it" / `/learn-ai-pyramid word-embedding`
「帮我搞懂 MCP」「XX 是什么」「你刚才说的太散了，重写」「/learn-ai-pyramid 词向量」

**❌ Not for / 不适合**：industry trends / daily news 📰, writing PRDs / proposals 📝, opinions / book reviews 💬, small talk ☕
要行业趋势/每日新闻 📰、要写 PRD/方案 📝、要观点评论/书评 💬、纯闲聊 ☕

> ⚠️ vs `learn-ai`: that one scrapes X/Twitter and needs a twitterapi.io key, output is prose-style summary; **this skill scrapes no social, needs no key**, and forces pyramid structure. Find `learn-ai` too loose? Switch to this.
> ⚠️ 和 `learn-ai` 的区别：那个会抓 X/Twitter、需要 twitterapi.io 的 key，输出是散文式精简版；**本 skill 不抓社交、不要 key**，输出强制金字塔结构。嫌 `learn-ai` 太散？换我就对了。

---

## 🔍 Sourcing rules (no making stuff up) / 取材规矩（不瞎编）

- 🌐 Only fetches **official web pages** for first-hand definitions; factual claims carry a `[source]`
  🌐 只抓**官方网页**一手定义，事实断言都带 `[来源]`
- 🔑 No API key needed, no social media
  🔑 不需要任何 API key，不碰社交媒体
- 🛑 If sources fall short, it says so — never fakes a layer just to fill the structure
  🛑 资料不够就明说，绝不为了凑结构脑补一层假的

---

Try it with these / 试试这些：

🤖 /learn-ai-pyramid Transformer — the architecture behind GPT and friends; the attention mechanism explained top-down, from one central claim down to the math
🤖 GPT 背后的架构——注意力机制自上而下讲清，从一个中心断言推到公式
🔗 /learn-ai-pyramid LangGraph — how graph-based agent orchestration actually works, with the jargon translated into plain language
🔗 图结构的 Agent 编排到底怎么运转——黑话翻译成人话


Tips / 小贴士：

✂️ You always start with the concise version, then pick deeper modes from the menu at the bottom
✂️ 默认先给精简版，看完再从底部菜单挑更深的模式
🔀 Say「思维导图」「实操」「黑话」(or "mindmap" / "how-to" / "jargon") anytime to switch modes mid-conversation
🔀 对话中随时说「思维导图」「实操」「黑话」即可切换模式
🔍 Follow-up questions on the same concept reuse the already-sourced material — no re-fetching, no drift
🔍 同一概念继续追问会复用已取材的资料——不重新抓取、不跑偏
