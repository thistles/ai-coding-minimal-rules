# 变更记录

本项目遵循 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/) 约定。

## [V1.2] - 2026-10-07

- 新增英文版规范文档：`AI-CODING-RULES_EN.md` 与 `AI-CODING-RULES_EN.pdf`（14 页，与中文版 V1.1 内容对齐）
- 新增英文版机制图：`assets/fig1-four-mechanisms-en`、`assets/fig2-core-loop-en`（PNG + SVG）及渲染导出工具 `assets/figures-en.html`
- 双版 README 文档链接更新为按语言区分

## [V1.1] - 2026-10-06

首个公开整理版本。

- 主文档《AI 编程失控治理：极简规范与方法论》：四个机制、四步循环（align / build / audit / rescue）、速查卡、给 AI 的执行摘要
- 四个技能：`skills/align`、`skills/build`、`skills/audit`、`skills/rescue`（标准 SKILL.md 格式）
- 三份模板：`templates/AGENTS.md`、`templates/spec.md`、`templates/adr`
- 14 页 PDF 版（适合打印）与两张机制图（PNG + SVG）

### 相对 V1.0 的变更

- 补上 audit 之后的闭环：审查报告不再悬空，明确审查后的处理路径——规范轴硬违规直接修、坏味道交由用户判断、规格轴范围蔓延要真删（见 `skills/audit`「完成后」一节）
