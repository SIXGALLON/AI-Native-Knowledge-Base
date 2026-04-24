# Changelog

All notable changes to this skill will be documented in this file.

Format follows [Keep a Changelog](https://keepachangelog.com/).

---

## [2.0.0] - 2026-04-24

### Changed
- **完全重写**：从"评测项目为原型"的思维切换为"所有知识型工作的通用元模型"
- **目录从 6 层必选 → 3 层必选 + 3 层可选**（`20-specs/` / `30-resources/` / `99-raw/` 按需启用）
- **`20-rules/` 重命名为 `20-specs/`**（规范层）,更普适
- **`30-assets/` 重命名为 `30-resources/`**（资源层）,包含结构化数据、文献库、tokens 等

### Added
- **4 级 AI 嵌入深度**（L1 Assist / L2 Remember / L3 Operate / L4 Guard）
  - 用"AI 嵌入深度"作为判别轴,不再是"人数"
  - 自动判别机制 + 升级触发信号
- **Retrofit 改造模式**：对已有项目做诊断 → 方案 → 分批迁移的完整流程
- **11 个领域 quick-start 包**：学术论文、理想态与评测、产品规范、运营 SOP、品牌体系、培训课程、法律合规、团队 Wiki、开源项目、UX 研究、数据分析
- **交互示例 demos**：完整对话展示 Greenfield 和 Retrofit 两种模式
- **AI 交互原则**（§零）：7 条行为准则确保自然交互
- **ANTI-PATTERNS 章节**：明确说明什么时候不该用本 skill
- **元模型三问**：将方法论抽象为"关于什么 / 怎么组织 / 怎么演进"

### Improved
- 交互风格从"说教式"改为"主动式"（AI 不讲方法论,只讲项目）
- 术语白话化（"SSoT" → "只在一处定义"）
- 治理机制包装为价值描述（"我帮你起草"而非"规则要求"）

---

## [1.0.0] - 2026-04-24

### Initial Release
- 6 层必选目录结构
- 6 条核心原则（SSoT / 分层 / ADR / changelog / 联动检查 / inbox）
- 7 个领域适配表
- CLAUDE.md / ADR / changelog / inbox / scaffolding / cross-ref-check 六份模板
