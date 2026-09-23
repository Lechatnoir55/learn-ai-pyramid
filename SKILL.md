---
name: learn-ai-pyramid
agent_created: true
version: 2.2.0
allowed-tools: Read, Glob, Grep, WebSearch, WebFetch
description: >
  用《金字塔原理》的结构规则讲解一个概念：先给「结论先行」的微金字塔简答，
  再按菜单出详细版 / 思维导图 / 实操版 / 黑话对照。信息源只用官方网页，
  不抓社交媒体、不需要任何 API key。何时调用：用户说「帮我搞懂 XX」「XX 是什么」
  「解释一下 XX」「/learn-ai-pyramid XX」（助记：pyr = pyramid），或明确抱怨某段解释太散、看不懂、不成结构。
  何时不调用：要行业趋势或每日新闻、要观点评论或书评、要写 PRD 或方案、
  用户明确只要一句话且拒绝展开、纯闲聊。触发信号：搞懂 / 解释 / 是什么 /
  讲清楚 / 扫盲 / 语无伦次 / 看不懂 / explain / what is / ELI5 / mindmap。
---

# learn-ai-pyramid — 用金字塔原理讲清一个概念

用《金字塔原理》（芭芭拉·明托）蒸馏出的规则集，强制约束讲解输出的结构。
治的就是「一句话、语无伦次」——**短不等于一句话，短也必须是个完整的微金字塔**。

## 治理不变量（常驻，任何模式、任何时候都不得违反）

```
1. 结论先行 —— 单一中心思想置顶，是断言不是比喻、不是定义
2. 思想是完整句 —— 有主谓，能引发「为什么/怎么做」，不是名词标签
3. 禁止缺乏思想的句子 —— 删掉数量词后必须仍是个可争议的判断
4. 以上统下 —— 上层必须能由下层倒推得出，不许有孤儿要点
5. 归类分组 + 逻辑递进 —— 同组须能用单一名词概括；顺序须属时间/结构/程度
6. MECE + 纵向问答 —— 不重叠不遗漏；下层类型由上层疑问词锁定
```

## 何时启动

- `/learn-ai-pyramid <concept>`（助记：pyr = pyramid）
- 「帮我搞懂 MCP」「MCP 是什么」「解释一下 Computer Use」
- 「XX 这个概念怎么理解」
- 「你刚才说的太散了 / 看不懂 / 语无伦次」——用本 skill 重写

## 何时不启动（重要）

- 要**行业趋势、每日新闻、竞品扫描** → 不是本 skill（本 skill 讲概念，不讲行情）
- 要**写 PRD、方案、报告** → 用专门的写作 skill
- 要**观点评论、书评** → 不启动
- 用户**明确只要一句话**且拒绝展开 → 说明「一句话讲不出结构，我给个三行的微金字塔」，
  用户坚持再照办
- 纯闲聊 → 不启动

> ⚠️ 与 `learn-ai` 的区别：那个会抓 X/Twitter 且需要 twitterapi.io 的 key，
> 输出是散文式精简版。本 skill **不抓社交、不要 key**，输出强制金字塔结构。
> 用户若想要社交讨论视角，用 `learn-ai`；若嫌 `learn-ai` 输出散，用本 skill。

## 工作流

### Step 0：配置（不打断用户）

读 `~/.learn-ai-pyramid/config.json`。**文件不存在就直接用默认值，不要停下来问**：

```
language: zh        default_mode: concise
```

用户后续可用指令改（见「可调指令」）。

### Step 1：取材

读 `references/source-discipline.md`，用 WebSearch / WebFetch 抓**官方网页**。

- **官方术语优先**：先查 `assets/official-sources.md` 路由表——命中官网就 WebFetch 对应一手页面；
  概念超出那 5 个网址，才回退通用 WebSearch。
- **不调用任何 API，不需要 key，不抓社交媒体。**
- 最小取材量：1 个定义 + 2–4 条可支撑关键句的事实 + （如有争议）1 条反方出处。
- 不够 → 照抄 `source-discipline.md` 里的降级话术，**不许脑补**。

### Step 2：选模式

首次默认 **concise**。用户点菜单则切到对应模式。

| 模式 | 文件 |
|---|---|
| 精简版 | `references/modes/concise.md` |
| 详细版 | `references/modes/detailed.md` |
| 思维导图 | `references/modes/mindmap.md` |
| 实操版 | `references/modes/howto.md` |
| 黑话对照 | `references/modes/jargon.md` |

### Step 3：起草（Pass 1）

读 `references/pyramid-rules.md` 对应档位的规则，再读该模式的 `modes/<mode>.md`，**照它起草**。
**首次起草建议先看 `references/modes/_examples/concise-sample.md`**——它是端到端成品样例（取材→草稿→审计→定稿）。
起草时只想内容，不要边写边审计。

### Step 4：审计（Pass 2）—— 不可跳过

把草稿冻结，照 `references/pyramid-audit.md` 逐条判定：

| 模式 | 档位 |
|---|---|
| concise | 简版 8 项 |
| howto / jargon | 中版 12 项 |
| detailed / mindmap | 全版 16 项 |

**有任意 no → 按「修补动作」重写该段 → 重新审计 → 全 yes 才输出。**
审计过程与草稿**一律不展示给用户**。

### Step 5：输出 + 菜单

输出通过后，在末尾拼菜单：**列出 3 个用户还没看过的模式**。
用户已经看过的模式不再出现，全部看过则不再给菜单。

```
---
还想深挖？1) 详细版　2) 思维导图　3) 黑话对照
直接说序号或名字就行。
```

## 可调指令

| 用户说 | 动作 |
|---|---|
| 「思维导图」「白板」 | 切 `mindmap` 模式 |
| 「详细点」「展开讲」 | 切 `detailed` 模式 |
| 「怎么上手」「实操」 | 切 `howto` 模式 |
| 「黑话」「术语」 | 切 `jargon` 模式 |
| 「默认出详细版」 | 改 `~/.learn-ai-pyramid/config.json` 的 `default_mode` |
| 「用英文」「双语」 | 改 `language` |
| 换了新概念 | 回到 Step 1 重新取材 |

## 边界情况

- **概念太新、资料太少** → 用降级话术，不要为了凑金字塔结构而脑补一层。
  宁可少一层，也不要塞一层假的。
- **概念本身有争议** → concise 加「先说问题」行（替代旧的「冲突」行）；detailed 的「当下在讨论什么」必须拆正方/反方两组（R7）。
- **mindmap 打开失败** → 只返回文件路径，让用户手动打开。
- **用户追问的模式素材不足** → 明说「这部分没搜到可靠来源」，而不是硬凑。

## 文件索引

```
SKILL.md                          本文件：路由 + 治理不变量 + 两遍流程
references/pyramid-rules.md       规则集 R1-R11 + P1-P6（蒸馏自《金字塔原理》）
references/pyramid-audit.md       审计清单：简版 8 / 中版 12 / 全版 16
references/source-discipline.md   取材纪律 + 降级话术
references/modes/*.md             五个输出模式
assets/official-sources.md        官方术语源路由表（Tier 1 优先：5 个官网 → WebSearch 兜底）
references/modes/_examples/concise-sample.md  端到端成品样例（concise 模式：取材→草稿→审计→定稿）
```
