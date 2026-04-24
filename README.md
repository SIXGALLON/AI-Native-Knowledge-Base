# 🧠 c

> **Let AI become a long-term collaborator on your complex knowledge work,
> not just a one-shot assistant.**
>
> 让 AI 真正嵌入你的知识型工作流,持续参与一项工作,不只是"用一次"。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)]()
[![Language](https://img.shields.io/badge/language-%E4%B8%AD%E6%96%87-red.svg)]()

---

## ✨ 这是什么

AI-Native Knowledge Base一套**让 AI 深度嵌入知识型工作**的方法论 + 可复用的 Claude/CodeBuddy Skill。

你有没有遇到过这些问题？

- 📂 项目文档越堆越多,每次让 AI 协作都要从零讲背景
- 🤷 半年前自己定的规则,现在完全想不起为什么
- 💔 改了某个定义,另一份文档里还是旧名,出错了才发现
- 🧹 文件夹乱成一团:`方案v1.md`、`方案v2.md`、`方案-final.md`、`方案-真的最终.md`
- 😵 AI 每次对话都"失忆",你每次都要重新搭上下文

**这个 skill 帮你一次性解决**。

---

## 🎯 适用场景

### ✅ 适合

- 📝 **学术论文** / 研究项目
- 🏷️ **理想态与评测** / 打标体系
- 📋 **产品 PRD** / 需求文档
- 🔧 **运营 SOP** / 工作手册
- 🎨 **品牌体系** / VI 规范
- 🎓 **培训课程** / 教材体系
- ⚖️ **合规政策** / 法律文档
- 📚 **团队 Wiki** / 公司知识库
- 🌟 **开源项目** 文档
- 🔬 **UX 研究** / 用户调研
- 📊 **数据分析** 报告

### ❌ 不适合

- 📧 一次性任务（一封邮件 / 一个答案）
- 💻 纯代码仓库（用 GitHub README 就够）
- 📔 个人流水账笔记（用 Obsidian / Notion）
- 🎭 已有成熟行业模板的工作（学术期刊 LaTeX / 法定合规格式）

---

## 🚀 快速开始

### 方式 1 · 作为 Claude/CodeBuddy Skill 使用

```bash
# 克隆到你的 skills 目录
# Claude Code:
cd ~/.claude/skills
git clone https://github.com/<user>/ai-native-knowledge-base.git

# CodeBuddy:
cd ~/.codebuddy/skills
git clone https://github.com/<user>/ai-native-knowledge-base.git
```

然后在对话中直接说：

> **"我要做一个 XX 项目,帮我启动"**（从零建库）
>
> **"帮我整理这个文件夹 `<path>`"**（改造已有项目）

Skill 会自动触发,引导你完成结构化。

### 方式 2 · 作为通用 Prompt 使用

复制 [`PROMPT.md`](./PROMPT.md) 粘贴到任何 AI 对话窗口
（Claude / ChatGPT / Gemini / 元宝 / Cursor / ...）。

---

## 🧬 核心理念

### 元模型：所有知识型工作都在回答三个问题

```
关于什么？  →  00-charter/    宪章层
怎么组织？  →  10-<domain>/   领域层
怎么演进？  →  40-process/    过程层
```

其他都是**可选工具**(有规则 → `20-specs/`, 有结构化数据 → `30-resources/`, 有原始材料 → `99-raw/`)。

### 六大不动摇原则

| 原则                             | 一句话                                    |
| -------------------------------- | ----------------------------------------- |
| **Single Source of Truth** | 规则只在一处权威存在,其他引用不复制       |
| **原始 vs 派生分层**       | 原始材料永不改,派生文档持续迭代           |
| **决策留档（ADR）**        | 方向性决策一定写下来,三个月后才知道为什么 |
| **变更日志（changelog）**  | SSoT 变动必登记,可追溯                    |
| **联动检查**               | 改 A 必扫全局引用,不漏 B                  |
| **Inbox 单一入口**         | 散乱输入先分拣,不允许散落                 |

---

## 🎚️ 4 级 AI 嵌入深度

根据项目复杂度和风险,选择合适的"AI 嵌入深度",不要过度治理也不要裸奔。

```
L1 · Assist 辅写         AI 是打字帮手         单次任务
L2 · Remember 留痕       AI 是记忆助手         中期项目
L3 · Operate 运转        AI 是共工             规则化运转
L4 · Guard 守护          AI 是守护者           高风险 / 下游多
```

**自动判别**：skill 会根据对话自动选合适等级,你不需要手动选。

---

## 📖 两种启动模式

### 🌱 Greenfield · 从零搭建

```
你：我要做一个论文项目,投 CHI 2026
 AI：3 个问题问你...
 AI：[自动识别领域 + 判别 Level]
 AI：3 分钟帮你搭好骨架
 AI：给你"下一步 Checklist"
```

[查看完整对话示例 →](references/demos/greenfield-论文.md)

### 🔧 Retrofit · 改造已有项目

```
你：[拖入一个混乱文件夹]
 AI：扫描 + 诊断 + 分类
 AI：出迁移方案 + 对比图
 AI：分批执行（零风险先做,有风险逐项确认）
 AI：永远不真删,可 git reset 回滚
```

[查看完整对话示例 →](references/demos/retrofit-混乱文件夹.md)

---

## 📦 11 个领域 quick-start 包

每个领域都有定制化的目录结构、常见输入分拣、典型 ADR 主题、CLAUDE.md 片段。

| 领域          | 触发关键词                       | Quick-start                       |
| ------------- | -------------------------------- | --------------------------------- |
| 📝 学术论文   | 论文、CHI / NeurIPS / SCI / 投稿 | [→](references/domains/学术论文.md) |
| 🏷️ 理想态与评测 | 评测、打标、理想态、标注         | [→](references/domains/理想态与评测.md) |
| 📋 产品规范   | PRD、需求、产品设计              | [→](references/domains/产品规范.md) |
| 🔧 运营 SOP   | SOP、流程、运营手册              | [→](references/domains/运营SOP.md)  |
| 🎨 品牌体系   | 品牌、VI、design token           | [→](references/domains/品牌体系.md) |
| 🎓 培训课程   | 培训、课件、教材                 | [→](references/domains/培训课程.md) |
| ⚖️ 法律合规 | 合规、政策、条款、监管           | [→](references/domains/法律合规.md) |
| 📚 团队 Wiki  | Wiki、团队知识、onboarding       | [→](references/domains/团队Wiki.md) |
| 🌟 开源项目   | 开源、GitHub、OSS                | [→](references/domains/开源项目.md) |
| 🔬 UX 研究    | UX、用户研究、访谈               | [→](references/domains/UX研究.md)   |
| 📊 数据分析   | 数据分析、BI、报告               | [→](references/domains/数据分析.md) |

---

## 🏗️ 项目结构

```
ai-native-knowledge-base/
├── SKILL.md                    # 方法论完整体 + YAML frontmatter（skill 触发入口）
├── PROMPT.md                   # 轻量版 Prompt（可粘贴到任何 AI）
├── README.md                   # 本文件（GitHub 门面）
├── LICENSE                     # MIT
│
└── references/                 # 参考资料
    ├── CLAUDE.md.template      # AI 协作契约模板
    ├── ADR.template.md         # 决策留档模板
    ├── changelog.template.md   # 变更日志模板
    ├── inbox.README.template.md
    ├── directory.scaffolding.md # 目录脚手架指引
    ├── cross-ref-check.md      # 联动检查机制详解
    ├── retrofit-guide.md       # 已有项目改造指引
    │
    ├── demos/                  # 交互示例
    │   ├── greenfield-论文.md
    │   └── retrofit-混乱文件夹.md
    │
    └── domains/                # 11 个领域 quick-start 包
        ├── 学术论文.md
        ├── 理想态与评测.md
        ├── 产品规范.md
        ├── 运营SOP.md
        ├── 品牌体系.md
        ├── 培训课程.md
        ├── 法律合规.md
        ├── 团队Wiki.md
        ├── 开源项目.md
        ├── UX研究.md
        └── 数据分析.md
```

---

## 💡 一句话判断是否要用

> **"这项工作三个月后还会有人改吗？会不会改错了回退不起？"**
>
> - 会改 + 回退不起 → **L4 · Guard**
> - 会改 + 自己能改回来 → **L3 · Operate**
> - 会有点小改 → **L2 · Remember**
> - 基本不改 → **L1 · Assist** 或干脆别用

---

## 🙋 FAQ

### Q: 和 Notion / Obsidian / Logseq 有什么区别？

这些工具主要是**编辑器**,本 skill 是**方法论 + 协作协议**。它可以与任何编辑器共存（文件本身是 markdown）。区别在于:

- Notion 适合**人写给人看**,但 AI 协作不深
- Obsidian / Logseq 适合**双向链接的个人笔记**,但不适合团队治理
- **本 skill 适合 AI + 人共同演进的长期项目**,本质是让 AI 能持续理解和参与

### Q: 一上来就 6 层目录是不是太重了？

不是。**Level 机制**让你按需使用：

- L1 只需要 2 份文件
- L2 需要 4 份左右
- L3 才启用完整 6 层
- L4 在 L3 基础上加治理流程

AI 会自动判别,不会强塞完整结构给你。

### Q: ADR 听起来很复杂,能不能省？

L1/L2 不需要 ADR。L3 开始需要,但**ADR 模板已经提供**,AI 会主动起草,你只需 review + Accept。

### Q: 和软件工程的 ADR 什么关系？

本方法论**继承**了软件工程 ADR 的传统,但扩展到**所有知识型工作**。软工的 ADR 用于架构决策,本 skill 的 ADR 用于**任何方向性决策**（论文研究问题、产品优先级、评测规则等）。

### Q: 我不用 Claude / CodeBuddy 能用吗？

能。PROMPT.md 可以粘贴到**任何** AI 对话窗口。Skill 形式只是自动化程度更高。

---

## 🤝 贡献

欢迎以下贡献：

- 📖 新增领域包（比如"咨询项目交付"、"标书编制"、"新闻报道"等）
- 🔍 完善 demo（更多真实对话示例）
- 🐛 报告方法论使用中的问题或边界 case
- 🌍 翻译到其他语言

提交 PR 或 issue 到 [GitHub](https://github.com/<user>/ai-native-knowledge-base)。

---

## 📜 许可

MIT License. 自由使用,请保留署名。

---

## 🙏 致谢

- **Anthropic Claude** 团队提出的 Skill 架构
- 软件工程社区的 ADR（Architecture Decision Record）传统
- 在真实项目实践中积累的所有踩坑与校准

---

**作者**：[@warrenixliu](https://github.com/<user>)
**版本**：v2.0.0 · 2026-04-24
**Star ⭐ 支持一下** 如果这个方法论帮到了你。
