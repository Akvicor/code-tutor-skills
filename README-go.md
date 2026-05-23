# Go Tutor

`go-tutor` 是 `code-tutor-skills` 仓库中的本地 Codex skill，用来把 Codex 变成可持续记录进度的 Go 编程老师。它会优先参考 Go 官方文档，结合练习驱动的学习方式，按入门、基础、进阶三阶段教学，给练习，review 代码，并把结果写回本地进度文件。

## 如何使用

### Codex

在支持 Codex skills 的环境里，显式调用 Go 学习 skill：

```text
使用 $go-tutor 继续我的 Go 学习
```

也可以提出更具体的请求：

```text
使用 $go-tutor 给我做 Go placement 诊断
```

```text
使用 $go-tutor 继续上次的练习
```

```text
使用 $go-tutor review 我在 workspace-go/ 里的 Go 代码
```

```text
使用 $go-tutor 解释 interface，并给我一个小练习
```

### Claude Code

安装到 Claude Code 后，可以直接调用：

```text
/go-tutor
```

也可以用自然语言触发，例如：

```text
继续我的 Go 学习
```

Claude Code 安装方式见 [README.md](README.md)。

## 学习流程

Go 课程分为三个阶段：

- 入门：Go 安装、modules、packages、`gofmt` 习惯、基础语法、控制流、集合、基础 testing、errors、小项目
- 基础：structs、methods、pointers、interfaces、errors、packages、table-driven tests、`io.Reader`/`io.Writer`、文件/JSON/HTTP、concurrency、context、sync、generics、综合项目
- 进阶：Effective Go、modules 进阶、tooling、fuzzing/benchmarks/coverage、diagnostics、memory model、HTTP server、`database/sql`、reflection/code generation/unsafe/cgo、advanced generics、security、final capstone

第一次学习时，进度里的 `Overall placement` 默认为 `unplaced`，所以 skill 会先做 placement readiness check，然后再决定从哪一课开始。进入 placement 或第一课前，skill 必须先检查 `go version` 和 `go env`；如果工具链缺失，会先按用户系统引导安装，不会创建需要运行的 Go 练习。完全不会 Go 语法时，会从 G-I0/G-I1/G-I2 开始讲，不会直接要求写代码诊断题。

## 进度保存

`.go-tutor/` 是本地学习状态目录，不是 `go-tutor` skill 本体的一部分。
首次使用时，如果本地状态目录不存在或语言偏好还没有配置，skill 可以根据对话推断希望使用的自然语言，但必须先询问确认；确认后再从模板创建进度文件并创建练习工作区。

开始学习前，skill 会用固定模板一次确认自然语言、编程基础、Go 基础和学习目标；编程基础、Go 基础和学习目标会提供默认选项，也允许用户自定义。确认问题会按首次检测到的用户语言展示字段名、选项、推荐值和示例回复，除非用户另行指定语言。如果 `go-tutor/references/personas/` 里存在用户放入的 `.md` 角色卡，确认问题中还会包含角色选择。目录为空时不会询问角色。这些信息明确确认后才会进入 placement 或正式教学。

Go 默认进度文件：

```text
.go-tutor/progress.md
```

Go 练习工作区：

```text
workspace-go/
```

练习、复习、小结和项目任务都会放入新的独立任务目录。目录名使用实际任务生成顺序的三位序号和英文摘要，不加 `i` 或 `g` 前缀；说明写在目录内 `README.md`：

```text
workspace-go/
  000-installation/
    README.md
  001-modules-packages/
    README.md
    hello/
```

每个任务目录的 `README.md` 必须先写当前任务工作路径，再写本节知识点和讲解，然后列出本任务可见项目文件/目录的一句话用途并标明需要读取、运行、编辑或暂时忽略，最后写任务要求和描述。README 问题、理解检查、完成标准、代码 TODO、测试说明和用户需要编写或修改的代码只能使用本节知识点和进度中 `Knowledge Map` 已记录的知识点；未学文件可以作为完整脚手架出现，但不能要求用户解释或修改。

小结问题和小结代码项目也必须先核对 `Knowledge Map` 与当前小结 `README.md` 已讲解知识点；如果问题、TODO、starter code 或测试说明需要未学知识点，必须先在当前小结中讲解并列入知识点。

课程会按 `references/knowledge-map.md` 拆成细粒度知识点来教：先讲一个知识点，做一个理解检查，再给对应练习。用户临时问到的超前内容只作为旁路知识，除非经过检查或练习，不会被当成已经学会。

每次学习或 review 后，skill 会更新：

- 用户语言偏好 `Preferred language`
- 教学角色文件引用 `Teaching persona`
- 已确认的编程基础、Go 基础和学习目标
- 当前阶段和课程
- placement 结果
- active exercise
- 细粒度知识点 `Knowledge Map`
- 每节课掌握状态
- 项目进度
- review queue
- session log
- 下一次学习计划

如果当前工作区没有 `.go-tutor/progress.md`，`go-tutor` 会尝试使用：

```text
${CODEX_HOME:-~/.codex}/memories/go-tutor/progress.md
```

如果仍然没有可写位置，Codex 会在回复里给出需要保存的进度更新。

## 语言偏好

`go-tutor` 会把用户确认后的语言写入进度文件的 `Preferred language`。首次运行或该字段为空时，skill 可以推断语言，但必须先询问确认再继续。之后教学回复、练习说明、写入 `workspace-go/` 的任务描述，以及新生成的代码注释都会使用这个语言。

Go 关键字、标识符、package 名、命令、文件名、编译器诊断和现有代码注释会保持原样，除非用户明确要求翻译或改写。

## 教学角色

`go-tutor` 可以记录一个可选教学角色，只影响自然语言语气，不影响课程顺序、知识点门槛、理解检查、练习难度、代码、命令、编译器诊断或 review 证据。

Go 角色卡目录：

```text
go-tutor/references/personas/*.md
```

只有该目录直属的 `.md` 文件会被识别；`.gitkeep`、隐藏文件、子目录和非 Markdown 文件会被忽略。角色卡选项按文件名排序展示，角色卡 ID 就是文件名，例如 `sakuya.md`。仓库不提供默认角色卡内容；如果目录中没有 `.md` 文件，tutor 不会询问角色，并使用默认无特殊风格。

项目根目录的 `persona-cards/` 保存了可选角色卡模板，不会被 `go-tutor` 自动扫描。想启用某个模板时，复制到 Go 角色卡目录：

```bash
cp persona-cards/sakuya.md go-tutor/references/personas/
cp persona-cards/flandre.md go-tutor/references/personas/
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

对于 Go 精确事实问题，`go-tutor` 会优先使用 Go 官方文档或本地工具链输出。特别是这些问题需要验证后再回答：

- 语言规则、packages、method sets、interfaces、generics、memory model、`unsafe`、`cgo`
- 标准库 API、方法签名、错误行为、`context`、HTTP、IO、JSON、files、testing、database APIs
- modules、workspaces、semantic import versioning、发布和依赖解析
- Go version features、release notes、runtime 行为
- `gofmt`、`go vet`、`gopls`、`go doc`、coverage、fuzzing、race detector、`govulncheck`
- profiling、trace、GC、PGO、安装和工具链配置

## 目录结构

```text
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

.go-tutor/
  progress.md
workspace-go/
  000-installation/
    README.md
  001-modules-packages/
    README.md
```
