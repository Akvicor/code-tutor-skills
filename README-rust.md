# Rust Tutor

`rust-tutor` 是 `code-tutor-skills` 仓库中的本地 Codex skill，用来把 Codex 变成可持续记录进度的 Rust 编程老师。它会读取学习进度，判断下一节课，讲解知识点，给练习，review 代码，并把结果写回本地进度文件。

## 如何使用

### Codex

在支持 Codex skills 的环境里，显式调用 Rust 学习 skill：

```text
使用 $rust-tutor 继续我的 Rust 学习
```

也可以提出更具体的请求：

```text
使用 $rust-tutor 给我做 Rust placement 诊断
```

```text
使用 $rust-tutor 继续上次的练习
```

```text
使用 $rust-tutor review 我在 workspace-rust/ 里的 Rust 代码
```

```text
使用 $rust-tutor 解释 ownership，并给我一个小练习
```

### Claude Code

安装到 Claude Code 后，可以直接调用：

```text
/rust-tutor
```

也可以用自然语言触发，例如：

```text
继续我的 Rust 学习
```

Claude Code 安装方式见 [README.md](README.md)。

## 学习流程

Rust 课程分为三个阶段：

- 入门：环境、Cargo、基础语法、控制流、集合初识、编译器诊断、小项目
- 基础：所有权、借用、切片、struct/enum、`Result`、collections、modules、tests、traits、lifetimes、iterators、IO、综合项目
- 进阶：Cargo 进阶、工具链、Edition、rustdoc、smart pointers、concurrency、async、高级 trait/pattern/macro、unsafe/FFI、Reference/Rustonomicon、final capstone

第一次学习时，进度里的 `Overall placement` 默认为 `unplaced`，所以 skill 会先做 placement readiness check，然后再决定从哪一课开始。进入 placement 或第一课前，skill 必须先检查 `rustc --version` 和 `cargo --version`；如果工具链缺失，会先按用户系统引导安装，不会创建需要运行的 Cargo 练习。完全不会 Rust 语法时，会从 I0/I1/I2 开始讲，不会直接要求写代码诊断题。

## 进度保存

`.rust-tutor/` 是本地学习状态目录，不是 `rust-tutor` skill 本体的一部分。
首次使用时，如果本地状态目录不存在或语言偏好还没有配置，skill 可以根据对话推断希望使用的自然语言，但必须先询问确认；确认后再从模板创建进度文件并创建练习工作区。

开始学习前，skill 会用固定模板一次确认自然语言、编程基础、Rust 基础和学习目标；编程基础、Rust 基础和学习目标会提供默认选项，也允许用户自定义。确认问题会按首次检测到的用户语言展示字段名、选项、推荐值和示例回复，除非用户另行指定语言。如果 `rust-tutor/references/personas/` 里存在用户放入的 `.md` 角色卡，确认问题中还会包含角色选择。目录为空时不会询问角色。这些信息明确确认后才会进入 placement 或正式教学。

Rust 默认进度文件：

```text
.rust-tutor/progress.md
```

Rust 练习工作区：

```text
workspace-rust/
```

练习、复习、小结和项目任务都会放入新的独立任务目录。目录名使用实际任务生成顺序的三位序号和英文摘要，不加 `i` 或 `g` 前缀；说明写在目录内 `README.md`：

```text
workspace-rust/
  000-toolchain/
    README.md
    hello_cargo/
  001-cargo-basics/
    README.md
```

每个任务目录的 `README.md` 必须先写当前任务工作路径，再写本节知识点和讲解，然后列出本任务可见项目文件/目录的一句话用途并标明需要读取、运行、编辑或暂时忽略，最后写任务要求和描述。README 问题、理解检查、完成标准、代码 TODO、测试说明和用户需要编写或修改的代码只能使用本节知识点和进度中 `Knowledge Map` 已记录的知识点；未学文件可以作为完整脚手架出现，但不能要求用户解释或修改。

小结问题和小结代码项目也必须先核对 `Knowledge Map` 与当前小结 `README.md` 已讲解知识点；如果问题、TODO、starter code 或测试说明需要未学知识点，必须先在当前小结中讲解并列入知识点。

课程会按 `references/knowledge-map.md` 拆成细粒度知识点来教：先讲一个知识点，做一个理解检查，再给对应练习。用户临时问到的超前内容只作为旁路知识，除非经过检查或练习，不会被当成已经学会。

每次学习或 review 后，skill 会更新：

- 用户语言偏好 `Preferred language`
- 教学角色文件引用 `Teaching persona`
- 已确认的编程基础、Rust 基础和学习目标
- 当前阶段和课程
- placement 结果
- active exercise
- 细粒度知识点 `Knowledge Map`
- 每节课掌握状态
- 项目进度
- review queue
- session log
- 下一次学习计划

如果当前工作区没有 `.rust-tutor/progress.md`，`rust-tutor` 会尝试使用：

```text
${CODEX_HOME:-~/.codex}/memories/rust-tutor/progress.md
```

如果仍然没有可写位置，Codex 会在回复里给出需要保存的进度更新。

## 语言偏好

`rust-tutor` 会把用户确认后的语言写入进度文件的 `Preferred language`。首次运行或该字段为空时，skill 可以推断语言，但必须先询问确认再继续。之后教学回复、练习说明、写入 `workspace-rust/` 的任务描述，以及新生成的代码注释都会使用这个语言。

Rust 关键字、标识符、crate 名、命令、文件名、编译器诊断和现有代码注释会保持原样，除非用户明确要求翻译或改写。

## 教学角色

`rust-tutor` 可以记录一个可选教学角色，只影响自然语言语气，不影响课程顺序、知识点门槛、理解检查、练习难度、代码、命令、编译器诊断或 review 证据。

Rust 角色卡目录：

```text
rust-tutor/references/personas/*.md
```

只有该目录直属的 `.md` 文件会被识别；`.gitkeep`、隐藏文件、子目录和非 Markdown 文件会被忽略。角色卡选项按文件名排序展示，角色卡 ID 就是文件名，例如 `sakuya.md`。仓库不提供默认角色卡内容；如果目录中没有 `.md` 文件，tutor 不会询问角色，并使用默认无特殊风格。

项目根目录的 `persona-cards/` 保存了可选角色卡模板，不会被 `rust-tutor` 自动扫描。想启用某个模板时，复制到 Rust 角色卡目录：

```bash
cp persona-cards/sakuya.md rust-tutor/references/personas/
cp persona-cards/flandre.md rust-tutor/references/personas/
```

用户选择角色卡后，进度文件只保存文件名，不复制完整角色卡。每次教学前，tutor 会读取 `references/personas/<file>`；如果文件被删除或不可读，会停止角色扮演。有其他角色卡时会重新询问选择，否则回退默认无特殊风格。

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

## 官方文档优先

对于 Rust 精确事实问题，`rust-tutor` 会优先使用 Rust 官方文档或本地工具链输出。特别是这些问题需要验证后再回答：

- 语言规则、所有权、借用、生命周期、traits、patterns、macros、unsafe、FFI
- 标准库 API、方法签名、trait 实现、错误类型
- Cargo、workspace、features、profiles、build scripts、发布流程
- Edition 和迁移
- rustfmt、Clippy、rust-analyzer、rustc、编译器诊断
- async/runtime 行为、crate 版本敏感 API
- 安装和工具链配置

## 目录结构

```text
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

.rust-tutor/
  progress.md
workspace-rust/
  000-toolchain/
    README.md
    hello_cargo/
```
