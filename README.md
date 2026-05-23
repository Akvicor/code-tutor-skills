# Code Tutor Skills

`code-tutor-skills` 是一个面向 Codex / Claude Code 的编程学习 skill 集合。每个 skill 负责一门语言，并提供各自独立的课程、练习规则、进度模板和本地练习工作区。

## Skills

| Skill | 语言/方向 | 说明 | 文档 |
| --- | --- | --- | --- |
| `rust-tutor` | Rust | Rust 编程老师：记录进度、安排课程、讲解概念、布置练习、review 代码 | [README-rust.md](README-rust.md) |
| `go-tutor` | Go | Go 编程老师：记录进度、安排课程、讲解概念、布置练习、review 代码 | [README-go.md](README-go.md) |

## 获取仓库

```bash
git clone https://github.com/Akvicor/code-tutor-skills.git
cd code-tutor-skills
```

## Codex

Codex 支持项目本地 skills 和个人 skills。项目本地 skills 适合随项目一起使用；个人 skills 适合在多个项目间复用。

在仓库根目录执行项目本地安装：

```bash
mkdir -p .agents/skills
cp -R rust-tutor .agents/skills/rust-tutor
cp -R go-tutor .agents/skills/go-tutor
```

在仓库根目录执行个人安装：

```bash
mkdir -p "$HOME/.agents/skills"
cp -R rust-tutor "$HOME/.agents/skills/rust-tutor"
cp -R go-tutor "$HOME/.agents/skills/go-tutor"
```

调用方式：

```text
使用 $rust-tutor 继续我的 Rust 学习
使用 $go-tutor 继续我的 Go 学习
```

也可以提出更具体的请求：

```text
使用 $rust-tutor review 我在 workspace-rust/ 里的 Rust 代码
使用 $go-tutor 给我做 Go placement 诊断
```

只安装 `rust-tutor/` 和 `go-tutor/` skill 本体；不要把 `.rust-tutor/`、`.go-tutor/`、`workspace-rust/` 或 `workspace-go/` 本地状态目录作为 Codex skill 安装。

## Claude Code

Claude Code 支持项目本地 skills 和个人 skills。项目本地 skills 适合随项目一起使用；个人 skills 适合在多个项目间复用。

在仓库根目录执行项目本地安装：

```bash
mkdir -p .claude/skills
cp -R rust-tutor .claude/skills/rust-tutor
cp -R go-tutor .claude/skills/go-tutor
```

在仓库根目录执行个人安装：

```bash
mkdir -p ~/.claude/skills
cp -R rust-tutor ~/.claude/skills/rust-tutor
cp -R go-tutor ~/.claude/skills/go-tutor
```

调用方式：

```text
/rust-tutor
/go-tutor
```

也可以用自然语言触发：

```text
继续我的 Rust 学习
继续我的 Go 学习
```

只安装 `rust-tutor/` 和 `go-tutor/` skill 本体；不要把 `.rust-tutor/`、`.go-tutor/`、`workspace-rust/` 或 `workspace-go/` 本地状态目录作为 Claude Code skill 安装。

## 本地状态目录

学习过程中生成的进度保存在对应的隐藏目录中；练习代码保存在可见的同级 workspace 中。它们都是本地状态，不是 skill 本体：

```text
.rust-tutor/
.go-tutor/
workspace-rust/
workspace-go/
```

Rust 与 Go 的课程、练习和进度互不共享。

首次运行某个学习 skill 时，如果对应隐藏状态目录不存在，或进度文件里的 `Preferred language` 还没有配置，skill 可以根据对话推断自然语言，但必须先请用户确认，确认后才能写入进度并开始教学。练习 workspace 缺失时会按默认路径直接创建。档案和角色确认后、placement 或第一课前，skill 必须先检查本机 Rust 或 Go 工具链；如果缺失，会先引导安装，不会创建需要运行的练习。

开始学习前，skill 还必须用固定模板一次确认用户希望使用的自然语言、编程基础、目标语言基础和学习目标；编程基础、目标语言基础和学习目标会提供默认选项，也允许用户自定义。确认问题会按首次检测到的用户语言展示字段名、选项、推荐值和示例回复，除非用户另行指定语言。这些信息不能只靠推断写入为已确认状态。只有用户明确确认后，才能写入 `Profile confirmed: yes`。

教学角色是可选的轻量表达风格，只影响自然语言语气，不影响课程顺序、知识点门槛、理解检查、练习难度、代码、命令、编译器诊断或 review 证据。每个 tutor 只从自身的 `references/personas/` 目录动态读取用户放入的直属 `*.md` 角色卡；如果目录里没有 `.md` 文件，skill 不会询问角色，会记录默认无特殊风格。

项目根目录的 `persona-cards/` 保存了可选角色卡模板，不会被 tutor 自动扫描。用户想启用某个角色时，把对应 `.md` 文件复制到目标 skill 的 `references/personas/` 目录：

```bash
cp persona-cards/sakuya.md rust-tutor/references/personas/
cp persona-cards/flandre.md rust-tutor/references/personas/
cp persona-cards/sakuya.md go-tutor/references/personas/
cp persona-cards/flandre.md go-tutor/references/personas/
```

首次 placement 会先做 readiness check；如果学习者还不会对应语言的基础语法，skill 会从入门工具链和基础语法课开始讲，不会直接要求写代码诊断题。

练习 workspace 是总根目录；每次生成练习、复习、小结或项目任务时，都创建新的 `NNN-summary/` 目录，并在目录内使用 `README.md` 写任务说明。`NNN` 按实际任务生成顺序递增，使用三位补零；目录名不加 `i` 或 `g` 前缀，也不要求对应课程 ID。

```text
workspace-rust/
  000-toolchain/
    README.md
    hello_cargo/
  001-cargo-basics/
    README.md

workspace-go/
  000-installation/
    README.md
  001-modules-packages/
    README.md
    hello/
```

每个任务目录的 `README.md` 必须先写当前任务工作路径，再写本节知识点和讲解，然后列出本任务可见项目文件/目录的一句话用途并标明需要读取、运行、编辑或暂时忽略，最后写任务要求和描述。进度文件会维护 `Knowledge Map`，记录细粒度知识点的 `unstarted`、`introduced`、`practiced`、`mastered`、`review` 状态、证据和复习需求；新任务的 README 问题、理解检查、完成标准、代码 TODO、测试说明和用户需编辑代码只能要求当前知识点和已经学过的知识点。未学文件可以作为完整脚手架出现，但不能要求用户解释或修改。

小结和复习也遵守同一规则：生成小结问题、追问、代码 TODO、用户需要修改的 starter code 或测试说明前，必须先核对 `Knowledge Map` 中已经学过的知识点和当前小结 `README.md` 中已经讲解的知识点。发现未学知识点时，必须先在当前小结里讲解并写入知识点，再用于提问或代码任务。

每门课还包含 `references/knowledge-map.md`，用于把 curriculum 中的一节课拆成更小的知识点。skill 应按“讲一个知识点 → 做理解检查 → 给练习 → review → 记录证据”的节奏推进；用户临时问到的超前内容只作为旁路知识，除非经过检查或练习，不会自动成为后续练习的已学前置知识。

## 角色卡

角色卡不会复制进进度文件。用户选择角色后，进度只保存文件名，例如 `Teaching persona file: sakuya.md`；每次教学前再读取对应文件。角色卡不能覆盖教学规则：skill 仍会按知识地图推进，不会因为角色设定跳过检查、提前给完整答案或伪造掌握证据。

推荐角色卡格式：

```markdown
# 角色名称

## 身份定位

## 称呼与自称

## 性格特点

## 说话风格

## 教学边界

## 示例表达
```

## Skill 文件结构

```text
persona-cards/
  sakuya.md
  flandre.md

rust-tutor/
  SKILL.md
  agents/openai.yaml
  references/
    curriculum.md
    exercise-rubric.md
    knowledge-map.md
    personas/
      .gitkeep
    progress-template.md
    resources.md
    session-workflow.md

go-tutor/
  SKILL.md
  agents/openai.yaml
  references/
    curriculum.md
    exercise-rubric.md
    knowledge-map.md
    personas/
      .gitkeep
    progress-template.md
    resources.md
    session-workflow.md
```

`rust-tutor/` 和 `go-tutor/` 是 skill 本体；`.rust-tutor/` 和 `.go-tutor/` 只是本地进度状态，`workspace-rust/` 和 `workspace-go/` 只是本地练习代码。
