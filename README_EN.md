# AI Coding Governance: A Minimal Set of Rules and Methodology

> From "fix one thing, break three" to "fix one thing, break at most one"

**A behavioral constraint document your AI reads before starting any work on a project.** Four mechanisms, three files, one loop.

![Four mechanisms](assets/fig1-四个机制.png)

---

## What problem it solves

Mid-to-late in a project's life, you change one spot and three others break — and **nobody can tell which change was the original sin**.

The cause is not "the AI got dumber" or "the process wasn't rigorous enough". It's **four missing mechanisms**:

| Root cause | Mechanism | What lands in the repo |
|---|---|---|
| The truth lives only in chat history | Source of truth | `AGENTS.md` / `docs/spec.md` / `docs/adr/` |
| Nobody bounds the blast radius | Boundary | One change ≤ 5 files; beyond that, expand–contract |
| No regression net | Verification | seam + red-before-green + vertical slices |
| Decisions are not remembered | Memory | ADR three-criteria test + glossary |

![Core loop](assets/fig2-核心循环.png)

---

## How to use it (pick one)

### Option 1: rules for the AI only

Rename [`AI编程失控治理-极简规范与方法论.md`](AI编程失控治理-极简规范与方法论.md) to `AI-CODING-RULES.md`, drop it in your project root, and add one line to `AGENTS.md`:

```
Before any work, read AI-CODING-RULES.md in full and treat it as a hard constraint of this project.
```

### Option 2: install the skills (recommended)

This repo ships four skills. Copy them into your skills directory:

```bash
# Claude Code / CodeBuddy / WorkBuddy etc.
cp -r skills/align   ~/.claude/skills/
cp -r skills/build   ~/.claude/skills/
cp -r skills/audit   ~/.claude/skills/
cp -r skills/rescue  ~/.claude/skills/
```

Then just talk naturally to trigger them:

| You say | Skill |
|---|---|
| "align me on this requirement" / "grill me before we start" | `align` |
| "implement this per the spec" / "build it" | `build` |
| "review this change" / "final self-check" | `audit` |
| "track down this error" / "locate this bug" | `rescue` |

### Option 3: read it yourself

Read the document (14-page PDF). Focus on section 1 (the four mechanisms) and the cheat sheet.

---

## The three files

With the skills installed, prepare these three files in your project:

```
AGENTS.md          the project constitution: build/test commands, hard red lines, glossary
docs/spec.md       the current spec: what "done" looks like, acceptance checklist, what's explicitly out of scope
docs/adr/          decision records: written only when all three criteria hit; one paragraph is enough
```

**There is no fourth kind of file.** No progress logs, no architecture panoramas, no README digests.
File count is the primary source of learning cost.

Templates live in [`templates/`](templates/).

---

## The four hard rules

1. **One commit does one thing**
2. **One change touches at most 5 files** — beyond that, use expand–contract (add the new alongside → migrate in batches, green after each → delete the old)
3. **No red test, no implementation changes**
4. **The spec explicitly states what this version does NOT do**

---

## Documents

- 📄 [PDF (14 pages, print-friendly)](AI编程失控治理-极简规范与方法论.pdf) — Chinese
- 📝 [Markdown (source)](AI编程失控治理-极简规范与方法论.md) — Chinese

Note: the full methodology document is currently in Chinese; the four skills under `skills/` are written in Chinese as well but follow the standard `SKILL.md` format and work with any agent that reads skills.

---

## Open-source origins

This is an original synthesis. Every mechanism is distilled from the following **open-source** projects (all MIT-licensed):

| Source | What was adopted |
|---|---|
| [mattpocock/skills](https://github.com/mattpocock/skills) | the grilling method, glossary & ADR three-criteria test (domain-modeling), the seam concept & good/bad tests (tdd), feedback loops (diagnosing-bugs), dual-axis review (code-review), expand–contract (to-tickets) |
| [Fission-AI/OpenSpec](https://github.com/Fission-AI/OpenSpec) | the "truth vs proposal" split of specs / changes, delta-style incremental writing |
| [github/spec-kit](https://github.com/github/spec-kit) | the constitution concept, spec as the single source of truth |
| [sverweij/dependency-cruiser](https://github.com/sverweij/dependency-cruiser) | the idea of machine-checkable dependency boundaries |

**Released under the MIT License.** Keep the attribution when quoting, adapting, or redistributing.

---

**One-sentence summary:** losing control is not a rigor problem — it's a missing-mechanism problem. Add the four mechanisms and "out of control" stops being a thing.
