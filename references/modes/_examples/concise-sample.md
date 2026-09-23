# 端到端样例：concise 模式

概念：**词袋模型 / Bag of Words**（经典 ML·文本表示，走 Tier 2 源）

> 本样例严格遵循 `modes/concise.md` 的固定 4 行格式。实际对话中可在末尾追加一句「串联已学概念」增强连贯性，属可选，不影响审计。

---

## 1. 取材记录（Step 1）

- 官方源（Tier 2）：scikit-learn 文档 §8.2.3 *The Bag of Words representation*
  URL: https://scikit-learn.org/stable/modules/feature_extraction.html#text-feature-extraction
- 抓到的关键事实（≥ 最小取材量）：
  - 定义：vectorization = tokenizing + counting + normalization；documents described by word occurrences while **completely ignoring the relative position** of words.
  - `CountVectorizer` 同时做 tokenization 与 occurrence counting。
  - 矩阵以稀疏形式存储（scipy.sparse）。
  - 局限：unigrams 无法捕捉短语与词序；未见词在 transform 时被忽略。

---

## 2. 起草稿（Step 3，固定 4 行）

**一句话讲清**：词袋模型是一种只统计词频、完全丢掉词序的文本向量化方法。

**三个事实**：①它先把全部文档去重得到词表；②再把每篇文档变成词表长度的向量，维度值=该词出现次数；③它因此丢掉词序与语法，「我 爱 机器学习」和「机器学习 爱 我」得到完全相同的向量。

**你的行动**：做文本分类时先用 CountVectorizer 把句子转成词频向量，再喂给朴素贝叶斯或线性模型。

来源：[scikit-learn](https://scikit-learn.org/stable/modules/feature_extraction.html#text-feature-extraction)

---

## 3. 审计过程（Step 4，简版 8 项 —— 不展示给用户）

```
R1 yes → 结论句含判断「只统计词频、丢掉词序」，非比喻非定义
R2 yes → 三个事实独立成行、均含主谓
R3 yes → 删数字后「它先把文档去重得词表」仍是可争议判断
R5 yes → 三条同属「三个做法/特征」，单一名词成立
R6 yes → 顺序为结构（建词表→映射向量→代价），非随意排列
R7 yes → 上层是结论非范畴，遗漏不适用
R8 yes → 上层问「是什么」，下层三条属「如何运作」类，类型一致
R4 yes → 下层可倒推上层
```

全 yes → 输出定稿（仅第 2 段 + 来源展示给用户，审计不展示）。

---

## 4. 定稿输出（展示给用户）

**一句话讲清**：词袋模型（Bag of Words）是一种把文本变成向量的方法——只统计每个词在文档里出现了多少次，完全忽略词的顺序和语法。

**三个事实**：①建词表：扫描全部文档去重，得到词表；②映射成向量：每篇文档变成长度=词表大小的向量，维度值=对应词出现次数（或 0/1 表示是否出现）；③代价：词序、语法、上下文全丢——「我 爱 机器学习」和「机器学习 爱 我」得到完全相同的向量。

**你的行动**：做文本分类时先用 CountVectorizer 把句子转成词频向量，再喂给朴素贝叶斯或线性模型。

来源：[scikit-learn](https://scikit-learn.org/stable/modules/feature_extraction.html#text-feature-extraction)
