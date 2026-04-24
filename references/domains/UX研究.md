# 领域包 · UX 研究 / 用户调研

## 推荐 Level

L2-L3。研究项目本身是中期项目,积累多份研究后适合 L3。

## 启动问用户

1. 研究类型？（访谈 / 问卷 / 可用性测试 / 民族志 / 混合）
2. 这是独立研究还是系列研究？
3. 研究结论会给谁用？（产品团队 / 对外发表 / 内部决策）

## 定制化目录

```
10-studies/
  ├── 00-研究框架.md            研究问题 / 方法论
  ├── 10-<study-1>/
  │   ├── 00-研究计划.md
  │   ├── 10-受访者.md
  │   ├── 20-资料整理.md
  │   ├── 30-分析.md
  │   └── 40-发现与建议.md
  ├── 11-<study-2>/ ...
  └── 90-cross-study-insights.md   跨研究洞察

20-specs/
  ├── 00-研究伦理.md            隐私 / 知情同意 / 数据保护
  └── 10-访谈 / 问卷规范.md

30-resources/
  ├── 10-participants.csv         受访者库（SSoT,脱敏）
  ├── 11-participants-changelog.md
  ├── interviews/                  访谈录音 / 转录
  ├── personas/                    用户画像
  └── journey-maps/                用户旅程图

99-raw/                         原始数据
  ├── recordings/                 录音
  ├── transcripts/                原始转录
  └── survey-data/                问卷原始数据
```

## 常见输入分拣

| 输入 | 处置 |
|---|---|
| 访谈录音 / 转录 | `99-raw/recordings/` 和 `transcripts/` |
| 受访者信息 | `30-resources/10-participants.csv`（脱敏）|
| 编码 / 分析笔记 | 对应 study 的 `20-资料整理.md` |
| 业务方需求 | inbox/ → 可能触发新 study |
| 研究方法调整 | 建 ADR |

## 典型 ADR

- ADR-0001：研究框架确定
- ADR-0002：某研究的方法选择
- ADR-0003：编码体系调整
- ADR-0004：伦理审查结果

## 特有机制

### 受访者隐私保护（强制）

- 所有涉及身份的字段脱敏（P001 / P002 而非真名）
- 录音文件有加密或访问控制
- `99-raw/` 下内容不能被 push 到远程（加 .gitignore）

### 编码一致性

多人编码时,定期做一致性检查(Kappa 或类似),记录到 ADR。

## CLAUDE.md 片段

```markdown
## 项目专属约定

- 所有用户数据在 30-resources/ 和 10-studies/ 里都是脱敏版本（P001...）
- `99-raw/recordings/` **绝不 push 到远程**（已在 .gitignore）
- 引用受访者必用脱敏 ID,不用真名

## 输入分拣

| 类型 | 处置 |
|---|---|
| 原始录音 / 数据 | 99-raw/ |
| 访谈笔记 | 对应 study 的资料整理 |
| 跨研究洞察 | 90-cross-study-insights.md |
| 方法调整 | 建 ADR |
```
