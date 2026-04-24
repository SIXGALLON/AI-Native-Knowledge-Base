# 目录脚手架生成指引（v2）

> 用户触发 skill 并确定 Level + 领域后,AI 按本指引创建骨架。

---

## 一、按 Level 的最小骨架

### L1 · Assist（最少 2 个文件）

```bash
touch CLAUDE.md
touch <项目名>.md   # 或者 10-主文档.md
```

**CLAUDE.md** 简化版：只写项目名、目的、交互原则。
**主文档**：所有内容都在这里。

### L2 · Remember

```bash
mkdir -p 00-charter 10-<domain> 40-process/inbox
touch CLAUDE.md README.md
touch 00-charter/01-项目背景与目标.md
touch 00-charter/02-核心概念词表.md
touch 10-<domain>/00-总则.md
touch 40-process/inbox/README.md
```

启用：inbox 分拣 + 概念词表。

### L3 · Operate（完整体系）

L2 基础上添加：

```bash
mkdir -p 20-specs 30-resources 99-raw 40-process/decisions
touch 20-specs/00-总览.md
touch 20-specs/10-操作手册.md
touch 30-resources/00-架构说明.md
touch 40-process/decisions/ADR-0001-引入知识库体系.md
touch 40-process/rule-history.md
```

启用：ADR + changelog + 联动检查。

### L4 · Guard

L3 基础上添加：

```bash
mkdir -p 40-process/impact-assessments
touch 40-process/impact-assessments/README.md
touch 40-process/governance-health.md   # 定期健康度检查
```

启用：影响评估强制 + 健康度月检。

---

## 二、按领域的特化（11 种）

### 理想态与评测

```bash
mkdir -p 10-ideal-response/20-场景分型 10-ideal-response/90-案例库/good 10-ideal-response/90-案例库/bad
touch 10-ideal-response/00-总则.md
touch 30-resources/10-labels.csv
touch 30-resources/11-labels-changelog.md
```

### 学术论文

```bash
mkdir -p 10-chapters 30-resources/figures 30-resources/tables
touch 10-chapters/00-大纲.md
touch 10-chapters/01-intro.md
touch 10-chapters/02-related-work.md
touch 10-chapters/03-method.md
touch 10-chapters/04-experiments.md
touch 10-chapters/05-discussion.md
touch 10-chapters/06-conclusion.md
touch 30-resources/references.bib
touch 30-resources/11-references-changelog.md
touch 20-specs/00-写作规范.md   # 字数 / 期刊要求 / 图表规范
```

### 产品规范 / PRD

```bash
mkdir -p 10-specs/20-modules 10-specs/90-examples
touch 10-specs/00-总则.md
touch 30-resources/10-requirements.csv
touch 30-resources/11-requirements-changelog.md
touch 20-specs/10-用户画像.md
touch 20-specs/20-优先级矩阵.md
```

### 运营 SOP

```bash
mkdir -p 10-workflows/20-steps 10-workflows/90-cases
touch 10-workflows/00-总则.md
touch 30-resources/10-checklist.csv
touch 30-resources/11-checklist-changelog.md
```

### 品牌体系

```bash
mkdir -p 10-brand-system/20-assets 10-brand-system/90-gallery
touch 10-brand-system/00-品牌内核.md
touch 30-resources/10-tokens.json
touch 30-resources/11-tokens-changelog.md
touch 20-specs/00-应用守则.md
```

### 培训课程

```bash
mkdir -p 10-curriculum/20-modules 10-curriculum/90-assessments
touch 10-curriculum/00-课程大纲.md
touch 30-resources/10-lessons.csv
touch 30-resources/11-lessons-changelog.md
```

### 法律合规

```bash
mkdir -p 10-policies/20-domains 10-policies/90-cases
touch 10-policies/00-总则.md
touch 30-resources/10-clauses.csv
touch 30-resources/11-clauses-changelog.md
touch 20-specs/00-监管框架.md
```

### 团队 Wiki

```bash
mkdir -p 10-topics 10-topics/onboarding 10-topics/faq
touch 10-topics/00-索引.md
touch 20-specs/00-编辑规范.md
```

### 开源项目

```bash
mkdir -p 10-docs/20-guides 10-docs/90-examples
touch 10-docs/00-overview.md
touch 10-docs/CONTRIBUTING.md
touch 20-specs/00-代码规范.md
# 还需要根目录的 README.md / LICENSE / CODE_OF_CONDUCT.md
```

### UX 研究

```bash
mkdir -p 10-studies 30-resources/interviews 30-resources/personas
touch 10-studies/00-研究框架.md
touch 30-resources/10-participants.csv
touch 30-resources/11-participants-changelog.md
```

### 数据分析报告

```bash
mkdir -p 10-findings 30-resources/datasets 30-resources/charts
touch 10-findings/00-总览.md
touch 30-resources/10-data-index.csv
touch 30-resources/11-data-changelog.md
touch 20-specs/00-分析方法论.md
```

---

## 三、AI 执行时的动作清单

创建骨架后 AI 应：

1. **复制模板到对应文件**
   - `references/CLAUDE.md.template` → `./CLAUDE.md`(按 Level 裁剪)
   - `references/ADR.template.md` → `40-process/decisions/ADR-0001-*.md`
   - `references/changelog.template.md` → `30-resources/11-*-changelog.md`
   - `references/inbox.README.template.md` → `40-process/inbox/README.md`

2. **填充 Charter**
   - `01-项目背景与目标.md` 根据用户描述起草
   - `02-核心概念词表.md` 留空骨架（对话中逐步补）

3. **写 ADR-0001**（L3+）
   - 背景：为什么结构化
   - 选项对比：平铺 / 其他结构 / 本方法论
   - 决策：采用 ai-native-knowledge-base + 理由

4. **给用户"下一步 Checklist"**
   - 你需要提供什么原始材料
   - 你需要定义哪些维度
   - 第一个可落地的产出是什么

---

## 四、不要做的事

- ❌ 一次性把所有模板都填"示例数据"——留空骨架更有价值
- ❌ 替用户决定领域的切分——必须对齐后再做
- ❌ 把原始材料放派生目录——始终 `99-raw/` 或 `40-process/inbox/`
- ❌ 跳过 ADR-0001——建库本身是一个值得留档的决策
- ❌ 强行上 L4——按判别逻辑走,不是越重越好

---

## 五、最终验证

```
<project>/
├── CLAUDE.md          ✓ 从模板复制并填充(按 Level 裁剪)
├── README.md          ✓ 存在（可以只写"见 CLAUDE.md"）
├── 00-charter/        ✓ 2 份文档已起草
├── 10-<domain>/       ✓ 领域特化骨架
├── 20-specs/          ✓（如启用）
├── 30-resources/      ✓（如启用）
├── 40-process/
│   ├── inbox/         ✓ README 从模板复制
│   ├── decisions/     ✓ ADR-0001 已起草（L3+）
│   └── rule-history.md ✓ 空文件也 OK
└── 99-raw/            ✓ 空目录等原始材料（如启用）
```

**检查要点**：
- `CLAUDE.md` 里所有 `<>` 占位符都填了真实内容
- ADR-0001 的决策内容是**真实的**（不是模板 dummy）
- 每个 `00-*.md` 都有至少一段有意义的文字
- 不相关的层 / 字段已删除（不要留空模板凑数）
