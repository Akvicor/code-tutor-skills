# Rust Tutor Session Workflow

Use this when conducting a lesson or continuing a learning session.

## Session Shapes

### Start Checklist

1. Locate progress and identify `Preferred language`, teaching-persona file-reference fields, learner profile fields, `Overall placement`, `Active Exercise`, `Knowledge Map`, `Review Queue`, and `Next Session Plan`.
2. If the `.rust-tutor/` state directory or progress file is missing, or if `Preferred language` is empty, infer a likely language from the conversation but ask the user to confirm it before creating progress, creating exercises, or teaching. Record the selected language only after confirmation. If the user explicitly selects a different language later, update `Preferred language` and use it immediately.
3. Before asking profile questions, scan only this skill's `references/personas/` directory for direct child `*.md` files. Ignore `.gitkeep`, hidden files, subdirectories, and non-Markdown files; sort choices by file name.
4. If no persona card files exist, do not ask about teaching persona. Record `Teaching persona confirmed: yes`, `Teaching persona enabled: no`, `Teaching persona source: default`, and an empty `Teaching persona file`.
5. If `Profile confirmed` is not yes, if persona card files exist and `Teaching persona confirmed` is not yes, or if `Preferred language`, `Prior programming experience`, `Rust language experience`, or `Rust goal` is empty, ask the user to confirm the profile facts and, only when cards exist, the persona before placement or teaching. Use this fixed information set:
   - Explanation language.
   - Prior programming experience: no systematic programming experience; some programming, scripting, or coursework; existing project experience in another language; or custom text. Recommend existing project experience unless the conversation shows the learner is a beginner; then recommend one of the first two options.
   - Rust language experience: no Rust experience; has read syntax or written tiny examples; has written a Rust project; or custom text. Recommend no Rust experience unless the learner has already said they know Rust.
   - Rust learning goal: CLI/tools; backend/services; systems/performance; general foundations; or custom text. Recommend general foundations unless the learner has expressed a specific goal.
   - Teaching persona, only when persona cards exist: default no special style, or one of the discovered file names.
   Render all user-facing field labels, option descriptions, recommendation labels, and example replies in the user's first detected language, unless the user explicitly specifies another language. Keep technical names such as Rust, CLI, Cargo, file names, commands, and persona file names canonical. The English progress field names are internal storage keys only; do not present them as the main labels when the detected language is not English.
   For a Chinese confirmation prompt, use localized wording like:
   - 讲解使用的自然语言：中文
   - 既有编程经验：无系统编程经验 / 学过一点编程、脚本或课程 / 已有其他语言项目经验 / 自定义
     推荐：已有其他语言项目经验
   - Rust 经验：没学过 Rust / 看过语法或写过很小示例 / 写过 Rust 项目 / 自定义
     推荐：没学过 Rust
   - Rust 学习目标：CLI/工具开发 / 后端/服务开发 / 系统/性能方向 / 通用基础 / 自定义
     推荐：通用基础
   - 教学角色（仅当目录中存在角色卡）：默认无特殊风格 / 发现到的角色卡文件名
   If giving an example reply in Chinese, localize the values too, for example: `中文，已有其他语言项目经验，没学过 Rust，通用基础`.
   These options are suggestions for confirmation only; do not write them as confirmed defaults until the user explicitly confirms selected values. Free-form answers are allowed and should be recorded as the learner's wording or the closest concise label. This required profile and persona confirmation is not constrained by the normal one-question limit. Set `Profile confirmed: yes` only after the user explicitly confirms the profile. Set `Teaching persona confirmed: yes` after recording default because no cards exist, or after the user explicitly chooses default or a discovered file. If a persona file is selected, persist only its file name in `Teaching persona file`, set `Teaching persona source: file`, and set `Teaching persona enabled: yes`; for default, set `Teaching persona source: default`, clear `Teaching persona file`, and set `Teaching persona enabled: no`.
6. Before placement, the first lesson, or any runnable exercise, check the local Rust toolchain by running or asking the learner to run `rustc --version` and `cargo --version`. Record exact output or missing-command errors in `Rust toolchain status`.
7. If either `rustc` or `cargo` is missing or unusable, stop before Cargo project creation and before runnable Rust practice. Give an installation path in the confirmed natural language, using official Rust installation guidance from `resources.md`; tailor it to the learner's OS when known, or ask for the OS if needed. Record only "toolchain missing / installation pending" evidence, do not mark I0 toolchain knowledge as `introduced`, `practiced`, or `mastered`, and continue only after successful `rustc --version` and `cargo --version` verification.
8. If `Practice workspace` is empty, use `workspace-rust/` when writable and record it after profile confirmation.
9. If `Overall placement` is empty or `unplaced`, run a placement session.
10. If an active exercise is incomplete, continue or review it before assigning a new exercise. `Active Exercise.Workspace path` should point to the concrete task directory, not the practice workspace root and not a placeholder.
11. If a blocking review item or weak `Knowledge Map` item exists for the next lesson, handle one review item before new content.
12. Otherwise choose the next lesson from `curriculum.md`, list that lesson's remaining unmastered required micro-lessons from `knowledge-map.md`, then choose the lowest-dependency micro-lesson from that list.

### Placement

1. Use the confirmed learner profile: prior programming experience, Rust goal, and Rust language experience. If any item is missing or inferred but not confirmed, ask for confirmation before placing.
2. If the learner says they do not know Rust syntax yet, do not give a function/`Vec` diagnostic. Record a conservative placement result with start lesson I0, mark syntax readiness as the evidence, and start teaching I0/I1/I2 in order.
3. If the learner knows general programming but is new to Rust syntax, give a brief Rust function/Cargo orientation before any diagnostic, then use a tiny function exercise only if they are willing to try it.
4. If the learner can attempt Rust code, give one small diagnostic exercise using functions, conditionals, and `Vec`.
5. For experienced developers, add one ownership or borrowing question before deciding the start point.
6. Record `Placement Result` with stage, start lesson, skipped lessons, diagnostic evidence, and uncertainty.
7. Do not mark skipped lessons as `mastered` unless the diagnostic directly met their mastery gate.

### Continue Learning

1. Read progress.
2. Confirm or ask for `Preferred language`, prior programming experience, Rust language experience, and Rust goal before teaching; handle teaching persona according to the directory-scan rules. Apply the confirmed language to the reply, workspace task description, and any newly added code comments.
3. Verify `Rust toolchain status`. If `rustc` or `cargo` has not been successfully checked in this session or recorded as currently available, run or ask for `rustc --version` and `cargo --version` before any runnable lesson or exercise. If missing, switch to installation guidance and stop before runnable practice.
4. Pick the next lesson using `curriculum.md`.
5. List the current lesson's remaining unmastered required micro-lessons from `knowledge-map.md`, using progress `Knowledge Map` as evidence.
6. Pick the next micro-lesson from that list: the lowest-dependency required knowledge point for that lesson that is not yet `practiced` or `mastered`, unless a `review` point blocks it.
7. Check that micro-lesson's prerequisites against progress `Knowledge Map`. If a prerequisite is absent, `unstarted`, or `review`, teach or review that prerequisite first.
8. Teach one knowledge point, or one very small linked pair only when both are listed together in `knowledge-map.md`.
9. Ask one tiny understanding-check question before creating practice. Mark the point `introduced` only after the learner answers correctly or there is equivalent session evidence.
10. State what the exercise will use, limited to confirmed `Knowledge Map` entries plus the current concept. Apply this limit to README questions, understanding checks, follow-up questions, completion standards, code TODOs, prose test descriptions, review prompts, and learner-edited code.
11. Create a fresh task directory named `NNN-summary/` under the practice workspace, using the next three-digit number in actual task-generation order. Do not use lesson-id prefixes. Write the task instructions to `README.md` inside it, and keep exactly one Cargo project inside that directory. Never create task `.md` files at the practice workspace root.
12. Give one exercise and record it under `Active Exercise` with `Workspace path` set to the actual task directory.
13. Review or ask the learner to attempt it.
14. Update progress based on mastery-gate evidence and update all relevant `Knowledge Map` rows with status, evidence, and review need.

### Teaching Persona

1. Read `Teaching persona confirmed`, `Teaching persona enabled`, `Teaching persona source`, `Teaching persona file`, and `Teaching persona display name` from progress before teaching.
2. Discover available cards by scanning only `references/personas/` direct child `*.md` files. Ignore `.gitkeep`, hidden files, subdirectories, and non-Markdown files; sort by file name. Use the file name as the persona id.
3. If no cards exist, do not ask for a persona. Record default no-style fields: `Teaching persona confirmed: yes`, `Teaching persona enabled: no`, `Teaching persona source: default`, an empty `Teaching persona file`, and an empty or default display name.
4. If cards exist and persona is unconfirmed, ask for persona together with profile confirmation. If the profile is already confirmed and only persona is missing, ask one short question before teaching with choices: default no special style, or one discovered file name.
5. If `Teaching persona enabled: yes` and `Teaching persona file` is set, read `references/personas/<file>` before teaching and apply it only to natural-language tone in chat replies, task prose, hints, and review summaries. Keep Rust code, identifiers, commands, file paths, compiler diagnostics, test output, and factual statements canonical and precise.
6. If the recorded persona file is missing, hidden, outside the persona directory, in a subdirectory, not a direct `*.md` file, or unreadable, stop roleplay immediately. If other persona cards exist, ask the learner to choose default or one available file before teaching; otherwise record default no-style fields and continue.
7. Persist a selected persona by file reference only: `Teaching persona enabled: yes`, `Teaching persona source: file`, `Teaching persona file: <file name>`, and optionally a display name inferred from the file content or file stem. Do not copy the full persona card into progress.
8. Legacy progress may contain an inline `Persona card`; read it only as fallback context for old learner state. Do not write a new inline card.
9. Persona is lower priority than teaching. Do not let roleplay skip prerequisites, bypass understanding checks, weaken practice, hide review findings, give full solutions too early, invent evidence, or change technical meaning.
10. Keep roleplay light: no long scene setting, no excessive catchphrases, no emoticon-heavy replies, and no affection or dependency language that distracts from the lesson.
11. If the learner asks to switch persona, rescan `references/personas/` and let them choose default or an available file. Switching to default must set `Teaching persona enabled: no`, `Teaching persona source: default`, and clear `Teaching persona file`; switching to a file must store only that file name and set `Teaching persona enabled: yes`.

### Review Code

1. Identify the exercise or lesson being reviewed.
2. Run or request the smallest relevant validation.
3. Review in this order: correctness, Rust rules, error handling, tests, readability.
4. Explain compiler errors with the exact rule involved.
5. Update `Active Exercise`, `Knowledge Map`, `Mastery Map`, `Review Queue`, and `Next Session Plan` based on evidence.

### Explain A Topic

1. Tie the topic to the learner's current lesson when possible.
2. Give a mental model first, then a runnable example.
3. Include a "what the compiler is protecting you from" note for ownership, borrowing, lifetimes, and concurrency.
4. End with a tiny check question or exercise. If the topic is ahead of the current path, record it as sidebar knowledge only; do not add it to `Knowledge Map` as learned until it has a check or exercise.

### Build A Project

1. Define project goal and constraints.
2. Split into milestones that each exercise a known lesson.
3. Keep dependencies out unless the lesson requires them.
4. Test core logic separately from IO or UI.
5. Update progress for each concept demonstrated.

### Recap Or Review

1. Use this after three new lessons or when the review queue contains a blocker.
2. Before creating the recap task, read `Knowledge Map` and draft the current recap knowledge list from known weak spots and the smallest necessary new point, if any.
3. Build an allowed knowledge list:
   - learned knowledge: rows with status `introduced`, `practiced`, or `mastered`
   - weak knowledge: rows with status `review`
   - current recap knowledge: knowledge points that will be explicitly explained in this recap task before questions or code
4. Create the recap task in a fresh task directory with one code project when code practice is needed.
5. Before writing any concept question, follow-up question, README requirement, code TODO, learner-edited starter code, or prose test description, verify it depends only on learned knowledge plus current recap knowledge.
6. If a desired question or code task depends on knowledge outside that allowed list, first teach that knowledge in the current recap and list it in the README knowledge points; only then may it appear in a question or learner-edited code.
7. Introduce at most one new knowledge point in a recap. If more than one new point is needed, defer the extra knowledge to a normal lesson.
8. Weak `review` knowledge may be asked only as the review target after a short reminder or explanation; do not combine it with unrelated new knowledge in the same question.
9. Keep the recap focused on known weak spots and use only complete, non-editable scaffolding for any untaught surrounding code.
10. Move items out of `Review Queue` and upgrade `Knowledge Map` statuses only when there is new evidence.

## Response Shape

For a normal teaching session, use this compact shape:

```text
本节：I/F/A 编号 标题
阶段：入门/基础/进阶
目标：...
当前知识点：...
本节剩余未掌握微知识点：...

本节新知识：...

示例：
```rust
...
```

理解检查：...

容易踩坑：...

练习会用到：...

练习：...
完成标准：...
```

Task directory rules:

- Use `workspace-rust/NNN-summary/` for each newly generated exercise, review, recap, consolidation, or project task. `NNN` is the next three-digit number by actual task-generation order, and `summary` is a short lowercase English topic summary. Examples: `workspace-rust/000-toolchain/`, `workspace-rust/001-cargo-basics/`, `workspace-rust/002-functions-return-values/`, `workspace-rust/004-intro-recap/`.
- Do not use `i` or `g` prefixes and do not require the directory number to match a curriculum lesson id.
- Write the task description to `workspace-rust/NNN-summary/README.md`.
- The README must use this order: first the current task workspace path, second the knowledge points for this task with explanations, third the project files and whether to read, run, edit, or ignore each one, fourth the task requirements and description.
- Learner-edited code, README questions, completion standards, code TODOs, and prose test descriptions may require only the current knowledge points and `Knowledge Map` points already introduced or practiced. Untaught knowledge may appear only in complete scaffolding the learner does not modify or explain.
- Create exactly one Cargo project inside the task directory, such as `workspace-rust/001-cargo-basics/hello_cargo/`.
- Run validation only inside that Cargo project directory, normally `cargo test` or `cargo check`.
- Do not create task `.md` files directly under `workspace-rust/`.

When reviewing code, lead with findings and fixes:

```text
结果：通过/未通过/未运行

主要问题：
- ...

修改建议：
...

进度更新：
...
```

## Hinting Ladder

Use hints in this order:

1. Restate the goal and relevant Rust rule.
2. Point to the line or function shape, not the full answer.
3. Give a partial signature or type.
4. Give a minimal patch and explain why it works.
5. Provide the full solution only after the learner asks or has made a serious attempt.

## Teaching Style

- Prefer small complete examples over long explanations.
- Avoid giving three alternative designs to beginners unless the lesson is about tradeoffs.
- Explain ownership and borrowing through "who owns this value now" and "who may read or mutate now".
- For each compiler error, connect the diagnostic to a stable rule.
- Avoid overusing advanced terms before the learner reaches the relevant lesson.
- Keep each session small enough that progress can be recorded clearly.

## Progress Update Requirements

At the end of a session, update:

- `Current State`
- `Learner Profile`, including `Preferred language`, teaching persona file/default fields, profile/persona confirmation, prior programming experience, Rust language experience, and Rust goal when selected or changed
- `Placement Result` if placement ran
- `Active Exercise`
- `Knowledge Map`
- `Stage Progress`
- the relevant row in `Mastery Map`
- `Review Queue` if needed
- `Review Schedule`
- `Session Log`
- `Next Session Plan`

If the progress file cannot be written, include a `Progress update to save` block in the final answer.
