# Go Exercise And Review Rubric

Use this when creating, grading, or revising practice.

## Exercise Design

A good Go Tutor exercise has:

- One main concept.
- One current fine-grained knowledge point from `knowledge-map.md`, unless the map explicitly groups a tiny linked pair.
- A small input and output.
- A clear completion standard.
- At least one test or manual check.
- A reason to use the target Go feature.
- Learner-completed code that uses only fine-grained knowledge already recorded in `Knowledge Map` plus the current concept just taught.
- A fresh task directory containing exactly one code project.

Avoid exercises that require third-party modules unless the current lesson explicitly introduces dependencies.

Use the learner's `Preferred language` for every natural-language part of the exercise: task title, requirements, completion standard, hints, workspace README or notes, prose test descriptions, and newly added code comments. If a teaching persona is confirmed and enabled, apply it lightly to natural-language prose and hints only. Keep Go identifiers, package names, commands, expected output literals, and compiler/test diagnostics in their canonical form, and never let persona style change requirements or grading.

## Workspace Layout

- Treat `workspace-go/` as the practice root only.
- Put each newly generated exercise, review, recap, consolidation, or project task in a fresh `workspace-go/NNN-summary/` directory. `NNN` is the next three-digit number in actual task-generation order; `summary` is a short lowercase English topic summary.
- Do not use `i` or `g` prefixes and do not map directory numbers to lesson ids.
- Write task instructions to `workspace-go/NNN-summary/README.md`; do not create task `.md` files in the practice root.
- The README must have exactly this top-level order: current task workspace path, knowledge points with explanations, task requirements and description.
- Create exactly one Go module or package root inside the task directory, not beside it.
- `Active Exercise.Workspace path` must be the concrete task directory path, never the practice root and never a placeholder.

## Prerequisite Fit

- Teach before practice: explain the required syntax or command shape and show a runnable example before assigning the exercise.
- Check understanding before practice: ask one tiny question and mark the current point `introduced` only after there is evidence.
- Required learner edits, README questions, understanding checks, follow-up questions, completion standards, code TODOs, prose test descriptions, and review prompts must not depend on unintroduced syntax, APIs, test structure, package/module concepts, Go idioms, or project-file roles.
- Starter code and generated project files may contain not-yet-taught scaffolding only when it is complete, marked as context, and not something the learner must edit or explain.
- Seeing, running, or generating a file does not make its purpose learned. Ask about `go.mod`, `go.sum`, `main.go`, `package main`, `func main`, imports, or `*_test.go` only after the matching `Knowledge Map` point has been explained and checked.
- G-I1 exercises should focus on module/package layout, `gofmt`, and running existing tests; do not ask the learner to implement Go functions or write table-driven tests until those topics have been taught.
- If an exercise needs new knowledge, first teach that knowledge in the same lesson and list it under "练习会用到".
- Before assigning an exercise, inspect `Knowledge Map`; absent or `unstarted` knowledge must be introduced first, and `review` knowledge must be reviewed before it becomes required learner-edited code.
- If a curriculum lesson contains several knowledge points, split it into several tasks instead of combining them into one large exercise.

## Project File Notes

- Every task README must include a short project-file note for each visible project file or directory, such as `go.mod`, `go.sum`, `main.go`, package directories, `*_test.go`, or generated binaries when relevant.
- Each note must say whether the learner should read, run, edit, or ignore the file for now.
- Notes for untaught files must be one-sentence context only and must not become questions, requirements, or evidence until taught.

## Recap Knowledge Gate

Recap and review tasks must use the same prerequisite rules as code exercises:

- Before generating recap concept questions or recap code projects, build the allowed knowledge list from `Knowledge Map` rows with status `introduced`, `practiced`, or `mastered`, plus knowledge points explicitly explained in the current recap README.
- Check every concept question, follow-up question, README requirement, completion standard, code TODO, learner-edited starter-code line, and prose test description against that allowed list.
- If any item needs a knowledge point outside the allowed list, teach it first in the current recap and add it to the README knowledge points before using it in a question or code task.
- Knowledge marked `review` may appear only as the review target after a short reminder or explanation; do not require it together with unrelated new knowledge.
- Untaught surrounding code is allowed only as complete scaffolding that the learner does not modify and does not need to understand to answer the question or complete the task.

## Placement Exercise Fit

- Do not use a syntax-heavy diagnostic for a learner who says they do not know Go syntax yet. Start with G-I0/G-I1/G-I2 teaching and record that answer as placement evidence.
- Use placement code exercises only when the learner can already read or attempt a tiny Go function body.
- If a learner knows programming but not Go, give a minimal Go function/module/testing orientation before asking them to try a diagnostic.

## Exercise Template

Every task directory must include a `README.md` with this top-level order:

```text
# <Task title>

## Current Task Workspace

workspace-go/NNN-summary/

## Knowledge Points

- <Knowledge point>: <short explanation>

## Project Files

- <Path>: <one-sentence purpose and whether to read, run, edit, or ignore for now>

## Task Requirements

<Task description>

- <Requirement>
- <Completion standard>
```

Do not leave `NNN-summary` in the actual generated README; replace it with the concrete task path.

```text
练习：...

要求：
- ...

起始代码：
```go
...
```

完成标准：
- Run `go test ./...` inside the task's single Go module or package root, or use the listed manual checks when no Go validation applies.
- Learner can explain ...

练习会用到：
- 已学：...
- 本节新知识：...

提示策略：
1. ...
2. ...
```

## Difficulty Levels

- Level 1: Fill in one function body.
- Level 2: Choose function signatures and write tests.
- Level 3: Refactor code to use a Go idiom correctly.
- Level 4: Build a small package, CLI milestone, or service slice.

Default to Level 1 or 2 for a new topic. Use Level 3 or 4 for consolidation.

## Review Rubric

Grade with evidence:

| Area | Good Evidence | Needs Review |
| --- | --- | --- |
| Correctness | Tests pass and edge cases are handled | Hard-coded output or missed edge cases |
| Errors | Returns, wraps, and checks errors intentionally | Panics or string-matches errors for normal failures |
| Interfaces | Interfaces are small and placed near consumers | Large provider-side interfaces or unnecessary abstraction |
| Packages | Names and exported APIs are clear | Circular dependencies, vague package names, or leaked internals |
| Idiom | Simple names, `gofmt`, standard library patterns | Over-engineered or copied from another language |
| Testing | Core logic has table-driven tests or focused tests | Only manual runs or no checks |
| Concurrency | Goroutine lifetime, channel closing, and shared state are clear | Goroutine leaks, data races, or unclear ownership |

## Diagnostic Teaching

When the learner hits a compiler error, failed test, panic, or race:

1. Quote or summarize the key line.
2. Name the Go rule, API contract, or concurrency principle involved.
3. Show the value, error, goroutine, or data flow causing the symptom.
4. Apply the smallest fix.
5. Explain when that fix is appropriate and when it hides a design issue.

## Mastery Decisions

- Mark `mastered` only when the learner can solve a small new variation and explain the rule.
- Mark `introduced` only after explanation plus an understanding check.
- Mark `practiced` when code works with minor hints.
- Mark `review` when the learner needed heavy hints, guessed through compiler errors, passed tests without explaining the fix, or used non-idiomatic patterns that block the lesson goal.
- Do not punish syntax mistakes if the conceptual explanation is sound.

## Solution Policy

- Do not give full solutions before an attempt unless the user explicitly asks.
- If the learner is stuck, give the next smallest useful hint.
- After showing a solution, ask for a short explanation or a modification to verify understanding.
