# CodeQualitySkill 使用说明

> 适用文件：`CodeQualitySkill.md`（v2.0.0，Skill 名称 `code-quality-guard`）
> 配套模板：`code_review_template.md`（第 0–6 章：评审注意事项 / 关于代码 / 自动检查 / 设计 / 代码编写质量 / 代码审查清单 / 跟踪调查）

这份 Skill 有四种用法，按投入从小到大排列。

---

## 用法一：在对话里直接引用（最快，不用安装）

在 WorkBuddy、Cursor、Claude Code 等工具的对话中，把文件和要审的代码一起交给 AI：

```
按照 @CodeQualitySkill.md 和 @code_review_template.md，
评审 src/payment/ 目录下的代码，填写评审模板，
并修复其中 Blocker、Critical、Major 级的问题。
```

适合偶尔用一次，或者先试试效果。

---

## 用法二：装成 WorkBuddy 的 Skill（推荐，之后自动生效）

WorkBuddy 识别"一个目录 + 目录里的 `SKILL.md`"这种结构。把 Skill 文件和评审模板放进同一个目录即可。

### 2.1 安装位置

| 级别 | 目录 | 生效范围 |
|------|------|----------|
| 用户级（推荐） | `~/.workbuddy/skills/code-quality-guard/` | 所有项目 |
| 项目级 | `<项目根目录>/.workbuddy/skills/code-quality-guard/` | 仅当前项目，可随代码库共享给团队 |

### 2.2 安装命令

```bash
mkdir -p ~/.workbuddy/skills/code-quality-guard
cp /Users/janeyang/WorkBuddy/AI4SE/CodeQualitySkill.md ~/.workbuddy/skills/code-quality-guard/SKILL.md
cp ~/Downloads/code_review_template.md ~/.workbuddy/skills/code-quality-guard/
```

### 2.3 安装记录（2026-11-17 已执行）

**安装结果：成功。** 安装在用户级目录，对所有项目都有效：

```
~/.workbuddy/skills/code-quality-guard/
├── SKILL.md                   ← 由 CodeQualitySkill.md 复制而来（约 34 KB）
└── code_review_template.md    ← 评审模板（约 6 KB）
```

**执行与核对：**

1. 创建目录 `~/.workbuddy/skills/code-quality-guard/`（安装前该目录不存在，不会覆盖旧版本）。
2. 复制两个文件。
3. 用 `diff` 比对：复制后的 `SKILL.md` 与原文件一致；文件开头的名称 `code-quality-guard` 和触发词描述都在。

**安装后改动了一处：**

在安装版 `SKILL.md` 的输入说明里，写明了评审模板的具体位置，保证默认能直接找到它：

```
默认使用本 SKILL 同目录下的 code_review_template.md
（即 ~/.workbuddy/skills/code-quality-guard/code_review_template.md）
```

> ⚠️ 因此安装版比工作区的 `/Users/janeyang/WorkBuddy/AI4SE/CodeQualitySkill.md` 多这一行。以后修改 Skill 时，记得两份一起改（或改完后重新执行 2.2 的命令，再补回这一行）。

**尚未验证：** 当前会话还没加载这个 Skill，需要新开一个会话才能确认能否自动触发。

### 2.4 如何触发

新开一个会话后，说下面这类话就会触发：

- "帮我评审一下 `src/xxx` 的代码，填一下评审表"
- "提交前做个代码质量检查"
- "检查这段代码有没有坏味道"

触发词写在 `SKILL.md` 开头的 `description` 里（代码评审、code review、坏味道、code smell、代码质量、重构、vibe coding 自检、提交前检查、填写评审表），可以按团队习惯增删。

**确认是否已加载：** 在新会话里问"有哪些可用的 skill"，列表里应该有 `code-quality-guard`。

---

## 用法三：写代码时就预防问题（VIBE Coding 场景）

前两种用法是写完再审。要想 AI 一开始就少写坏味道，把 `CodeQualitySkill.md` **附录 C** 那段约束提示复制到项目的规则文件里：

| 工具 | 放在哪里 |
|------|----------|
| Cursor | 项目根目录的 `.cursorrules`，或 `.cursor/rules/*.mdc` |
| Claude Code / Codex | 项目根目录的 `CLAUDE.md` 或 `AGENTS.md` |
| WorkBuddy | 项目的 `.workbuddy/rules` |
| GitHub Copilot | `.github/copilot-instructions.md` |

这样每次生成代码都会遵守函数长度、异常处理、禁止写死密钥等约束，写完还会自动附上自查结果。

---

## 用法四：交给人工评审

把 AI 填好的评审表作为附件随 PR 一起提交，人工评审只需要做三件事：

1. 抽查第 2 章：自动检查的结果是不是真的运行出来的，有没有"未知"项。
2. 逐条确认第 5 章的问题清单和修复状态。
3. 重点看末尾"给人工评审者的关注点"那几条业务和架构问题，再在第 6 章签结论。

---

## 推荐的日常流程

```
写需求 → AI 带着附录 C 的约束写代码 → 提交前让 AI 按 Skill 自审并修复
      → 生成填好的评审表 → 人工复核（重点看关注点）→ 第 6 章签结论 → 合并
```

---

## 按团队情况调整

- **阈值**：改 `SKILL.md` 第 4 节，比如函数行数、覆盖率要求。
- **严格程度**：对话里说明"用 prototype 模式"，原型代码就只拦截最严重的两级问题（Blocker、Critical）。
- **检查工具**：项目已有 SonarLint、ESLint 等配置时会优先使用。本地没装的工具，对应项会填"未知"，不会编造结果。
- **评审模板**：替换安装目录下的 `code_review_template.md`；如果检查项有增删，同步更新 `SKILL.md` 的附录 A。
