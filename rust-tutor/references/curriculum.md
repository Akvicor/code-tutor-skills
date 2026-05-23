# Rust Tutor Curriculum

Use this curriculum as the default learning spine. It is organized into three stages. Use `knowledge-map.md` to split each lesson into fine-grained micro-lessons and to check prerequisites before practice. A lesson's mastery gate depends on the required micro-lessons listed for that lesson in `knowledge-map.md`; do not treat the curriculum topic title as a single large concept.

- `入门` / Intro: become comfortable running, reading, and writing small Rust programs.
- `基础` / Foundations: master ownership, borrowing, errors, modules, traits, tests, and small projects.
- `进阶` / Advanced: understand Rust's broader official documentation map, tooling, async, concurrency, unsafe boundaries, and advanced language features.

Adapt pacing to the learner's goal, but keep the stage order unless placement evidence clearly supports skipping. Skipped lessons are recorded as `verified by placement`, not as fully taught.

## Status Terms

- `unstarted`: no evidence yet.
- `introduced`: explained or attempted once.
- `practiced`: completed at least one exercise with minor help.
- `mastered`: completed an exercise and explained the core rule accurately.
- `review`: should revisit before advancing far.

## Placement

If there is no valid placement result, place the learner with a short readiness check and, when appropriate, a 10 minute diagnostic. A valid placement requires `Overall placement` to be set to a concrete lesson or stage, not empty and not `unplaced`.

1. Use confirmed prior programming experience, Rust language experience, and Rust goal; ask first if any of these are missing or inferred.
2. Check whether they can already read or attempt a tiny Rust function body.
3. If they do not know Rust syntax yet, do not assign a code diagnostic; start at I0 and treat that answer as placement evidence.
4. If they struggle with basic programming, start at I0.
5. If they know programming but not Rust, verify I0-I2 quickly with explanation-first checks and start at I3 or F0 only when the evidence supports it.
6. If they can attempt Rust code, give a tiny function exercise using variables, conditionals, and a vector.
7. If they already know ownership, test borrowing plus `Result` and place at F3-F5.

For experienced developers:

- Combine I0-I2 into fast verification instead of teaching them slowly.
- Fast verification is enough when the learner can create or recognize a Cargo project, run `cargo test`, and explain where `Cargo.toml`, `src/main.rs`, and `src/lib.rs` fit.
- If fast verification passes and Rust ownership is new, set the starting point to F0.
- If the learner demonstrates ownership, borrowing, and `Result`, set the starting point based on the weakest evidence in F3-F5.
- Do not skip the Foundations stage permanently; ownership, borrowing, `Result`, modules, traits, and lifetimes are required.

## Stage 1: 入门

Goal: the learner can install, run, read, and write basic Rust programs and complete a small tested Cargo exercise.

| ID | Topic | Prerequisites | Mastery Gate |
| --- | --- | --- | --- |
| I0 | Toolchain, editor, `rustc`, `cargo` | none | Can report toolchain status, create or inspect a starter Cargo project as scaffolding, and run `cargo check` / `cargo run` without explaining project files yet. |
| I1 | Cargo basics: `Cargo.toml`, binary crate, library crate, `main`, `lib` | I0 | Can explain project layout and run existing `cargo test` without writing Rust logic or test modules. |
| I2 | Values, mutability, shadowing, scalar types, functions, expressions | I1 | After being taught function signatures and both `return` and expression returns, can write pure functions using expressions and return values. |
| I3 | Control flow, loops, simple patterns | I2 | Can transform small input using `if`, loops, and basic pattern matching. |
| I4 | First project: dependency-free number or text utility | I3 | Can complete a runnable Cargo project with deterministic behavior and no external crates. |
| I5 | `String`, `Vec`, simple iteration | I3 | Can build and process a `Vec` or `String` without hard-coded output. |
| I6 | Compiler diagnostics, `Option` and `Result` preview | I5 | Can summarize a compiler error and handle a simple `Option` or `Result`. |
| I7 | Intro recap project: small CLI, text tool, or guessing-game variant with tests | I6 | Can complete a small project with at least 2 tests and explain the code. |

Intro completion evidence:

- Creates and runs Cargo projects.
- Writes basic functions, loops, conditionals, and tests.
- Reads common compiler errors at a high level.
- Knows ownership is the next central Rust topic.

## Stage 2: 基础

Goal: the learner can write clear, tested Rust libraries or CLIs using Rust's core ownership and type-system model.

| ID | Topic | Prerequisites | Mastery Gate |
| --- | --- | --- | --- |
| F0 | Ownership: move, `Copy`, `Clone`, `Drop` | I7 or placement | Can predict moves and fix a moved-value error without cloning blindly. |
| F1 | Borrowing: `&T`, `&mut T`, aliasing, mutability | F0 | Can choose shared or mutable references and explain the exclusivity rule. |
| F2 | Slices and reference-oriented function signatures | F1 | Can design signatures over strings and slices without unnecessary ownership. |
| F3 | Structs, methods, associated functions, `impl` | F2 | Can model a domain type with methods and tests. |
| F4 | Enums, `Option`, `match`, `if let` | F2 | Can represent absence or state with enums instead of sentinel values. |
| F5 | `Result`, `?`, recoverable errors, avoiding `unwrap` | F4 | Can propagate errors and keep `unwrap` out of library logic. |
| F6 | Collections: `String`, `Vec`, `HashMap`, ownership in collections | F2, F4 | Can build and query collections without fighting lifetimes unnecessarily. |
| F7 | Modules, packages, crates, visibility, paths | F5 | Can split code into modules with a clear public API. |
| F8 | Testing: unit tests, integration tests, test organization | F7 | Can test core logic separately from IO or CLI glue. |
| F9 | Traits and generics: bounds, derive, common traits | F5 | Can write a generic function or type constrained by traits. |
| F10 | Lifetimes as relationships between references | F1, F9 | Can explain a lifetime annotation as a relationship, not storage duration. |
| F11 | Closures and iterators | F6, F9 | Can rewrite a loop as an iterator pipeline and know when not to. |
| F12 | File IO and CLI basics with the standard library | F5, F8 | Can read input, report IO errors, and test core logic separately. |
| F13 | Foundations project: mini grep, config parser, or log analyzer | F12 | Can complete a small library or CLI with tests, modules, `Result`, and rustfmt/Clippy checks. |

Foundations completion evidence:

- Explains value moves, shared borrows, and mutable borrows.
- Designs function signatures with owned values and references intentionally.
- Uses `Result` and `Option` for normal error and absence cases.
- Splits a small project into modules and tests it.
- Reads most of The Rust Programming Language's main-line chapters with confidence.

## Stage 3: 进阶

Goal: the learner has a broad, accurate map of Rust's official ecosystem and knows when advanced tools and language features are appropriate.

| ID | Topic | Prerequisites | Mastery Gate |
| --- | --- | --- | --- |
| A0 | Cargo advanced: workspaces, profiles, features, `cargo install`, publishing concepts | F13 | Can explain workspaces, features, and release/debug profiles at a project-design level. |
| A1 | Tooling: rustfmt, Clippy, rust-analyzer, `cargo fix` | F8 | Can run or explain each tool and when it should be used. |
| A2 | Editions and migration: Rust 2021/2024, Edition Guide, `cargo fix --edition` | A1 | Can explain edition compatibility and the migration workflow. |
| A3 | rustdoc: `///`, `//!`, doc tests, `cargo doc`, API docs | F8 | Can document a public API and include a passing doc test. |
| A4 | Smart pointers: `Box`, `Rc`, `Arc`, `RefCell`, `Mutex` | F10 | Can choose a pointer type based on ownership, sharing, and mutability. |
| A5 | Concurrency: threads, channels, `Send`, `Sync`, shared state | A4 | Can write or review a small threaded program without data races. |
| A6 | Async Rust: `Future`, `async`/`.await`, runtimes, tasks, streams map | A5 | Can explain why async needs a runtime and where async differs from threads. |
| A7 | Trait objects and dynamic dispatch: `dyn Trait`, object safety, tradeoffs | F9 | Can choose static or dynamic dispatch and explain the cost and flexibility tradeoff. |
| A8 | Advanced traits and types: associated types, supertraits, fully qualified syntax, newtype | A7 | Can read and write code using associated types or fully qualified syntax. |
| A9 | Advanced patterns: refutable/irrefutable, destructuring, guards, binding modes | F4 | Can use complex patterns correctly and identify where refutable patterns are allowed. |
| A10 | Macros: `macro_rules!`, derive/procedural macro concepts, when to avoid macros | F9 | Can explain what macros generate and when a function or trait is simpler. |
| A11 | Unsafe and FFI overview: raw pointers, `unsafe fn`, unsafe traits, C ABI, safe wrappers | A4 | Can identify the unsafe boundary and describe the obligation it creates. |
| A12 | Rust Reference and Rustonomicon navigation | A11 | Can choose the right official reference for precise rules or unsafe details. |
| A13 | Final capstone: multithreaded web server, async CLI/server, or library plus CLI | A3, A5 | Can complete a documented, tested project using multiple advanced topics. |

Advanced completion evidence:

- Explains the purpose and risks of Rust's advanced features.
- Uses Cargo, rustdoc, Clippy, rustfmt, rust-analyzer, and edition tooling appropriately.
- Chooses pointer, concurrency, and async models based on ownership and runtime needs.
- Understands unsafe as an explicit contract boundary, not a performance shortcut.
- Completes a capstone with tests and documentation.

## Projects

Use one project or recap after every 3 to 5 lessons. Every stage must end with a project.

| ID | Stage | When | Project | Required Evidence |
| --- | --- | --- | --- | --- |
| P-I | 入门 | After I7 | Small CLI or text utility | Cargo project, deterministic behavior, at least 2 tests. |
| P-F1 | 基础 | After F2 | Borrowing lab over strings and slices | Avoids unnecessary clones and explains signatures. |
| P-F2 | 基础 | After F5 | Result-driven parser or config reader | Uses `Result`, `?`, and avoids `unwrap` in library logic. |
| P-F3 | 基础 | After F13 | Mini grep, log analyzer, or small library + CLI | Modules, tests, IO separated from core logic, rustfmt/Clippy checked. |
| P-A1 | 进阶 | After A5 | Concurrent worker, thread pool, or channel pipeline | Uses threads/channels/shared state safely and explains model. |
| P-A2 | 进阶 | After A13 | Final capstone | Documented, tested, and demonstrates multiple advanced topics. |

## Remediation Rules

- If the learner uses `clone` to silence ownership errors, return to F0-F2 with a smaller example.
- If the learner uses `unwrap` outside prototypes, return to F5.
- If the learner cannot explain a signature with references, return to F1-F2 before lifetimes.
- If the learner overuses lifetimes on owned data, teach F10 with relationship examples.
- If iterator code becomes unreadable, allow a loop and discuss tradeoffs.
- If advanced topics cause confusion, return to the smallest Foundations topic that blocks understanding.

## Topic Selection

Choose the next lesson by this order:

1. Placement if `Overall placement` is empty or `unplaced`.
2. Any incomplete `Active Exercise`.
3. Any missing or `review` fine-grained `Knowledge Map` item that blocks the current topic.
4. Any `review` lesson that blocks the current topic.
5. The current lesson if its mastery gate is not satisfied.
6. The next unpracticed micro-lesson for the current lesson from `knowledge-map.md`.
7. A stage project, consolidation project, or recap when 3 to 5 new lessons have been practiced.
8. The lowest-numbered `unstarted` required lesson in the current stage.
9. Goal-specific tracks after A13, such as embedded, WebAssembly, backend services, CLI tooling, systems programming, game development, or GUI.

## Advancement Rules

- Do not advance from a lesson until the learner has evidence for that lesson's mastery gate.
- Do not mark a lesson `mastered` until each required `knowledge-map.md` row for that lesson is at least `practiced`, unless the row was directly verified by placement evidence.
- Do not mark a stage complete until its stage project is complete.
- If the learner passes tests but cannot explain the target rule, mark `practiced` or `review`, not `mastered`.
- If the learner needs heavy hints, keep the same lesson active and add a review item.
- If placement skips a lesson, mark it as verified by placement only when the diagnostic directly tested the lesson's mastery gate.
- Required Foundations topics must not be permanently skipped: ownership, borrowing, `Result`, modules, traits, and lifetimes.
