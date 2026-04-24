# 联动检查（Cross-Ref Check）· §6.4 核心机制详解

> 本项目最重要的防错机制。每次改动 SSoT 或核心概念后，AI **必须主动执行全局扫描**。

---

## 为什么需要联动检查

知识库在迭代中最常见的坏死：

- 改了 A 处，B 处还在引用旧版
- 删了一个文件，有 5 个地方还在链接
- 改名了一个概念，文档里半数还是旧名
- 派生物（Excel / 图）没同步更新

只靠人眼 review 100% 会漏。必须用工具化扫描。

---

## 什么时候必须执行

| 改动类型 | 是否必扫 |
|---|---|
| 改 SSoT 数据（CSV / JSON） | ✅ 必扫 |
| 改核心概念定义（词表条目） | ✅ 必扫 |
| 改名 / 删除标签、维度、文件 | ✅ 必扫 |
| 修订评分规则 / 阈值 | ✅ 必扫 + 打分影响评估 |
| 合并 / 拆分标签 | ✅ 必扫 + changelog + ADR |
| 新增一个维度文件 | ✅ 必扫（检查必读清单 / 总则索引 / README 是否要更新） |
| 修错别字 / 调整排版 | ❌ 不需要 |
| 补 TODO / 补注释 | ❌ 不需要 |
| 只改一处小幅内容扩充 | ❌ 不需要 |

---

## 标准扫描流程

### Step 1 · 列出要搜的 pattern

```
旧概念名 / 旧文件名 / 旧标签名 / 旧变量名
```

通常包括：
- 精确字符串（`"C2·该问不问"`）
- 带路径形式（`"10-信息密度.md"` / `"10-信息密度"`）
- 可能变体（带点号、带前后缀、空格差异）

### Step 2 · 全局搜索

使用工具：
- VS Code / Cursor：Ctrl+Shift+F
- Bash：`grep -rn "pattern" .`
- 本 skill 环境：`search_content` 工具

### Step 3 · 分类匹配结果

每一条命中，判断是：

| 类型 | 处置 |
|---|---|
| **活引用**（规则文档、理想态文档、操作手册的当前描述）| 必须改 |
| **历史陈述**（ADR 里"当初为什么这么定"、changelog 里的变更记录）| 保留，不改 |
| **原始素材**（`99-raw/` 下的文件）| 保留，只读 |
| **注释 / 示例代码** | 具体判断（通常要更新） |

### Step 4 · 并发执行所有改动

**重要**：在一轮工具调用里并发发出所有 `replace_in_file`，不要一条一条改。

### Step 5 · 最终校验

改完后**再扫一次**旧 pattern，确认：

- 只剩历史陈述匹配
- 无遗漏的活引用

---

## 扫描范围（按改动类型）

### 改了维度 / 理想态文档（如 `10-<domain>/11-xxx.md`）

必扫：
- `CLAUDE.md`（必读清单）
- `10-<domain>/00-总则.md`（索引表）
- `10-<domain>/20-scenarios/*.md`（场景文件的链接）
- `20-rules/00-总览.md`（引用到 What 层）
- `30-assets/*-changelog.md`（之前是否提到过）
- `40-process/decisions/ADR-*.md`（历史陈述保留）

### 改了 SSoT 数据（如 `30-assets/10-labels.csv`）

必扫：
- `20-rules/`（所有规则文档）
- `10-<domain>/`（所有维度/场景文件的标签引用）
- 相关 `*-changelog.md` （追加一条）
- 所有 `_反例.md` / `case.md`（打标示例）

### 改了核心词表条目（`00-charter/02-核心概念词表.md`）

必扫：**整个项目**（核心词表是 SSoT 中的 SSoT）

### 改了 CLAUDE.md 的分拣表 / 必读清单

必扫：
- `40-process/inbox/README.md`（是否和新规则一致）
- 最新 ADR（是否有提到不同做法）

---

## 报告模板（扫完后 AI 给出的交付）

```markdown
## 联动检查报告

### 改动对象
- <改了什么 SSoT>

### 全局搜索结果
共 N 处匹配：

| 文件 | 行号 | 处置 |
|---|---|---|
| `path/to/file.md` | L12 | ✅ 已更新为新值 |
| `path/to/other.md` | L45 | ✅ 已更新 |
| `40-process/decisions/ADR-0001.md` | L34 | 🔒 保留（历史陈述）|
| `99-raw/original.csv` | - | 🔒 保留（只读）|

### 派生物同步
- [ ] `30-assets/10-labels.xlsx` 需重新生成 → 已完成 ✅
- [ ] `CLAUDE.md §必读清单` 需更新 → 本次不涉及

### 最终校验
再次搜索旧 pattern，剩余 3 处全部为历史陈述（ADR / changelog）。**无遗漏**。
```

---

## 常见失误 & 对策

| 失误 | 症状 | 对策 |
|---|---|---|
| 只搜文件名不搜概念名 | 概念被引用的地方漏改 | 搜 pattern 时同时加文件名和概念名两套 |
| 历史陈述也被改掉 | ADR 变成"当初就决定 X" 但实际是后来改的 | 识别历史陈述类文档，保留描述性原文 |
| 只改一批不扫第二轮 | 漏改，用户事后发现 | Step 5 必须再扫一次 |
| 派生物忘了重生 | Excel 和 CSV 不一致 | 列明派生物清单，每次改 SSoT 都重新生成 |
| 引用路径深的文件漏搜 | 嵌套目录下的 .md 没被搜到 | 用递归搜索，不要只搜顶层 |

---

## 工具化建议

如果项目足够大（50+ 文件），可以写一个检查脚本：

```python
# 伪代码：联动检查
def cross_ref_check(old_pattern, new_pattern, excluded_dirs=None):
    hits = grep_r(old_pattern, excluded=excluded_dirs or [])
    active = []
    historical = []
    for hit in hits:
        if is_adr_or_changelog(hit.file) or is_raw(hit.file):
            historical.append(hit)
        else:
            active.append(hit)
    return active, historical
```

运行后 AI 自动列出 active 那组给 owner 看。

---

## 核心原则

**"改 A 不扫 B"是知识库第一大死法**。每次改动都问自己：

1. 这个改动会影响多少其他地方？（列出来）
2. 历史陈述哪些要保留？（ADR / changelog / raw）
3. 派生物需要重新生成吗？
4. 必读清单要调整吗？

四个问题答完再动手。
