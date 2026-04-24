# 领域包 · 运营 SOP / 手册

## 推荐 Level

L3 为主。SOP 天生需要规则化沉淀,但一般不到 L4。

## 启动问用户

1. 这套 SOP 给谁执行？（客服 / 运营 / 合作伙伴）
2. 有多少个核心流程要覆盖？
3. 出错了代价多大？（影响用户体验 / 影响收入 / 影响合规）

## 定制化目录

```
10-workflows/
  ├── 00-总则.md              流程总体框架
  ├── 10-<流程1>.md            每个流程一份
  ├── 11-<流程2>.md
  ├── 20-steps/                详细步骤
  └── 90-cases/                典型案例
      ├── good/
      └── bad/

20-specs/
  ├── 00-服务标准.md           SLA / 响应时间 / 质量红线
  └── 10-话术规范.md

30-resources/
  ├── 10-checklist.csv          检查项清单（SSoT）
  └── 11-checklist-changelog.md
```

## 常见输入分拣

| 输入 | 处置 |
|---|---|
| 用户投诉 / 客诉 | inbox/cases/ → 分析后可能更新 SOP |
| 团队反馈（执行卡点）| inbox/feedback/ |
| 异常 case 汇总 | → `90-cases/bad/` |
| 流程优化提议 | 建 ADR |
| 新业务场景 | 建新流程文件 |

## 典型 ADR

- ADR-0001：SOP 体系化决策
- ADR-0002：某流程重构
- ADR-0003：服务标准调整（如 SLA 变更）

## CLAUDE.md 片段

```markdown
## 项目专属约定

- `30-resources/10-checklist.csv` 是检查项真源
- 服务标准以 `20-specs/00-服务标准.md` 为准
- 每月过一次客诉 case,判断是否触发 SOP 修订

## 输入分拣

| 类型 | 处置 |
|---|---|
| 客诉 / 异常 | inbox/cases/ |
| 执行反馈 | inbox/feedback/ |
| 流程变更 | 建 ADR |
```
