# 官方术语源（Tier 1 优先）

解释**官方术语**时，按本表优先用 WebFetch 去对应官网取一手定义；**概念超出本表覆盖范围**，再回退 `source-discipline.md` 的通用 WebSearch 流程。

> 设计原则（来自用户指令）：
> 1. 问「官方术语」→ 优先去下面 5 个官网找。
> 2. 问的 AI 概念不在这 5 个网址里 → 才去 WebSearch 找别的站。

## 路由决策树

1. 概念名是否带某个厂家的产品名？→ 命中对应源（见下表）。
2. 是通用底层概念（Agent / Tool / LLM / Function-calling / Agent loop）？
   → 命中多个源，**各取一手定义并列对比**，不要只信一家。
3. 概念不属于任何阵营（非 AI 概念、或极新未见术语）？→ 回退 WebSearch（见 `source-discipline.md`）。

## 源清单与优先映射

| # | 源 | 覆盖范畴 | 优先用于 |
|---|---|---|---|
| 1 | **OpenAI API Docs**<br>`https://developers.openai.com/api/docs` | OpenAI API 全体系：文本生成、Responses API、Assistants(已退)、Agent SDK、MCP servers、Function calling、Computer use、Code interpreter、RAG/File search、Embeddings、Fine-tuning、Reasoning models(o-series)、Realtime API、Moderation、结构化输出、Prompt caching、Batch | 任何以 OpenAI 产品/API 命名的术语（Responses API、GPT Actions、o3/o-series、Codex、ChatKit、Sora、Agent Builder），及通用 Agent/tool/computer-use 在 OpenAI 语境下的定义 |
| 2 | **LangChain Docs**<br>`https://docs.langchain.com/oss/python/langchain/overview` | LangChain `create_agent`、LangGraph、Deep Agents、smolagents、middleware/harness、providers 集成（OpenAI/Anthropic/Google…）、LangSmith observability | LangChain / LangGraph / Deep Agents / smolagents 相关术语，及「Agent = Model + Harness」类框架定义 |
| 3 | **Hugging Face Agents Course**<br>`https://huggingface.co/learn/agents-course/unit0/introduction` | Agent 基础（Tools/Thoughts/Actions/Observations）、LLM 机制（messages、special tokens、chat templates）、function-calling、smolagents/LangGraph/LlamaIndex、fine-tuning for function-calling、observability/evaluation、benchmark/leaderboard | Agent 入门概念（Thought/Action/Observation、agent loop）、LLM 底层机制、function-calling |
| 4 | **Claude Academy**<br>`https://academy.claude.com/` | Claude 产品生态（Claude.ai / Code / Cowork / Platform）、4D Framework、4 Properties of AI、AI Fluency、next-token prediction、working memory、steerability、context limits | Claude/Anthropic 专属概念、AI 能力边界心智模型（4 Properties、working memory、steerability）、4D 协作框架 |
| 5 | **Microsoft AI Decision Framework Glossary**<br>`https://microsoft.github.io/Microsoft-AI-Decision-Framework/docs/glossary.html` | Agent、Agentic engineering、ACI、MCP、A2A、RAG、Copilot 全家桶、Foundry、Shadow AI、Agent risk tiers、Vibe coding、Harness、Orchestration、BYOK/BYOM；**标注 GA/Preview/Retiring 状态 + 「勿架构于营销词」警告** | Microsoft/Azure AI 生态术语、MCP/A2A/RAG 的厂商中立定义、治理类（Shadow AI、Agent risk tiers）、「哪些是营销词/已废弃」鉴别 |

## Tier 2 — 经典机器学习 / 统计 / 数学概念（**跳过上表，直接来这里**）

> **2026-09-04 实测教训**：上面 5 个官网覆盖的是 AI·Agent 术语，**不覆盖经典 ML / 统计概念**。
> 朴素贝叶斯、PCA、词向量、SVM、聚类这类**不要去翻那 5 个官网**，会白跑一轮
> （已验证：Microsoft glossary 里既没有 `embedding` 也没有 `word vector` 词条）。直接按下表取：

| # | 源 | 覆盖范畴 | 优先用于 |
|---|---|---|---|
| 6 | **scikit-learn 官方文档**<br>`https://scikit-learn.org/stable/modules/` | 全部经典 ML 算法的官方定义、公式、参数、复杂度，**以及官方明说的局限** | 朴素贝叶斯、PCA、聚类、线性模型、集成学习等一切 sklearn 实现的概念。**局限类断言优先引它**（如 PCA 只中心化不缩放、NB 是 bad estimator） |
| 7 | **Stanford NLP 项目页**<br>`https://nlp.stanford.edu/projects/` | GloVe、CoreNLP、情感分析等 Stanford NLP 产出 | GloVe、依存句法等 Stanford 系方法 |
| 8 | **arXiv 原论文 abstract 页**<br>`https://arxiv.org/abs/<id>` | 算法一手出处、确切标题/作者/年份、论文自述的卖点 | Word2Vec `1301.3781`、BERT `1810.04805`、Transformer `1706.03762`。**先取 abstract 页**，比二手解读可靠 |
| 9 | **权威综述 / 教材页** | 概念之间的关系、学界共识与争议 | 「当下在讨论什么」段的正反方出处；如 Information Fusion 2023《Beyond word embeddings: A survey》 |

**路由决策树补 1 步**（插在原文第 2 步之后）：

```
2.5 概念是经典 ML / 统计 / 数学（朴素贝叶斯、PCA、词向量、SVM、聚类、回归…）？
    → 走 Tier 2，不要翻 Tier 1 的那 5 个官网。
```

## 抓取纪律（与 source-discipline.md 一致）

- WebFetch 一个 docs 站时，**优先抓概念页 / glossary 子页**；若首页只列目录，顺着相关链接再抓。
- 每个事实性断言仍须带 `[来源](url)`（来自实际抓到的页面，禁止编造）。
- **「营销词 vs 真术语」**：Microsoft glossary 已显式标注哪些词是 marketing-only / Retiring（如 Autopilot、Vibe coding、Plugin 已弃用）。讲到这类词时，必须指出其状态，不要当成稳定术语去架构。
- 同一概念多源冲突时，并列各方定义并指明阵营，不替用户下唯一结论。
- 仍遵守 `source-discipline.md` 的降级话术与硬规则（不许脑补、不许素材堆砌冒充思想）。
