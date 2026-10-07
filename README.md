# AI 编程失控治理：一套极简规范与方法论

> 从"改一处错三处"到"改一处只错一处"

**给AI 项目启动时先读的行为约束文档。**四个机制 ·三份文件 · 一条循环。

**[English README](README_EN.md)** ｜ 版本 V1.1（[变更记录](CHANGELOG.md)） ｜ MIT License

![四个机制](assets/fig1-四个机制.png)

---

## 它解决什么问题

项目迭代到中后期，改一处代码，坏三处，而且**说不清哪处是原罪**。

原因不是"AI 变笨了"，也不是"流程不够严谨"，而是**缺四个机制**：

| 根因 | 机制 | 落地物 |
|---|---|---|
| 真相只在对话里 | 真相源 | `AGENTS.md` / `docs/spec.md` / `docs/adr/` |
| 改动范围没人定 | 边界 | 一次改动 ≤ 5 文件，超了走扩展-收缩 |
| 没有回归网 | 验证 | seam + 先红后绿 + 竖切片 |
| 决策不被记住 | 记忆 | ADR 三条判据 + 术语表 |

![核心循环](assets/fig2-核心循环.png)

---

## 怎么用（三选一）

### 方式一：只给AI 用

把 [`AI编程失控治理-极简规范与方法论.md`](AI编程失控治理-极简规范与方法论.md) 改名`AI-CODING-RULES.md` 放项目根目录，然后在 `AGENTS.md` 加一行：

```
开始任何工作前，先完整阅读 AI-CODING-RULES.md，并把它当作本项目的硬约束执行。
```

### 方式二：装技能（推荐）

本仓库自带四个技能，拷进你的skills 目录：

```bash
# Claude Code / CodeBuddy / WorkBuddy 等
cp -r skills/align   ~/.claude/skills/
cp -r skills/build   ~/.claude/skills/
cp -r skills/audit   ~/.claude/skills/
cp -r skills/rescue  ~/.claude/skills/
```

装完说人话即可触发：

| 说| 触发 |
|---|---|
| "帮我对齐一下这个需求" / "开工前先拷问" | `align` |
| "按 spec 实现这个功能" / "造一下" | `build` |
| "审查一下这次改动" / "收尾自查" | `audit` |
| "排查这个报错" / "这个 bug 定位一下" | `rescue` |

### 方式三：人读

通读文档（14 页 PDF / 8 页 Markdown），重点看第一节（四个机制）和速查卡。

---

## 三份文件

装完技能，在项目里准备这三份：

```
AGENTS.md          项目宪法：构建命令、测试命令、不可越界的红线、术语
docs/spec.md       本版规格：做完长什么样、验收清单、这一版明确不做什么
docs/adr/          决策记录：三条判据全中才写，一个段落就够
```

**没有第四类文件。**进展日志、架构全景图、README 摘要——一律不写。
文件数量是学习成本的主要来源。

模板见 [`templates/`](templates/)。

---

## 四条硬规则

1. **一个 commit 只做一件事**
2. **一次改动不超过 5 个文件**，超过走扩展-收缩（先加新的 → 分批挪 → 再删旧的）
3. **没有红灯测试，不许改实现**
4. **spec 里明确写"这一版不做什么"**

---

## 文档

- 📄 [PDF（14 页，适合打印）](AI编程失控治理-极简规范与方法论.pdf)
- 📝 [Markdown（源文件）](AI编程失控治理-极简规范与方法论.md)

---

## 开源来源

本项目为原创整理，全部机制提炼自以下**开源**项目（均MIT 许可）：

| 来源 | 采纳了什么 |
|---|---|
| [mattpocock/skills](https://github.com/mattpocock/skills) | 拷问方法（grilling）、术语表与 ADR 三判据（domain-modeling）、seam 概念与好/坏测试（tdd）、反馈回路（diagnosing-bugs）、双轴审查（code-review）、扩展-收缩（to-tickets） |
| [Fission-AI/OpenSpec](https://github.com/Fission-AI/OpenSpec) | specs / changes 分离的"真相 vs 提案"思想、delta 增量写法 |
| [github/spec-kit](https://github.com/github/spec-kit) | constitution（项目宪法）概念、spec 作为唯一真相 |
| [sverweij/dependency-cruiser](https://github.com/sverweij/dependency-cruiser) | 依赖边界的机器可校验思路 |

**本项目以 MIT 许可发布。**引用、改写、二次分发请保留出处。

---

**一句话总结：**失控不是流程不严谨，是缺机制。四个机制补上，失控就不成立。