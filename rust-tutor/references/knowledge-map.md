# Rust Fine-Grained Knowledge Map

Use this map when choosing the next micro-lesson, checking prerequisites, creating exercises, reviewing code, and updating progress. The curriculum gives the route; this file gives the teachable knowledge points inside each lesson.

## Status Evidence

- `introduced`: the learner has seen the idea and answered a small understanding check.
- `practiced`: the learner used it in a focused exercise with at most minor hints.
- `mastered`: the learner solved a new variation and explained the rule accurately.
- `review`: the learner needs a reminder before this can be used as assumed knowledge.

## Teaching Rules

- Teach at most one new knowledge point, or one very small linked pair, before a check question.
- A task may require only `introduced`, `practiced`, or `mastered` knowledge plus the current point just explained.
- Files may appear in complete scaffolding before they are taught, but seeing or running a file does not mark it learned. Do not ask the learner to explain or edit a project file until its own row has been explained and checked.
- A lesson is complete only when its required knowledge points satisfy the lesson mastery gate in `curriculum.md`.
- Treat each table row as a required micro-lesson for its lesson unless the learner directly verifies it by placement.
- If a learner asks about an advanced topic early, answer briefly and mark it as sidebar knowledge; do not treat it as learned until it has a check or exercise.

## Intro Knowledge Points

| Lesson | Knowledge Point | Prerequisites | Practice Condition | Mastery Evidence |
| --- | --- | --- | --- | --- |
| I0 | toolchain status: `rustc --version`, `cargo --version` | none | Recognize or run version commands | Can report what toolchain is installed or missing. |
| I0 | Cargo binary project creation | toolchain status | Create or inspect one Cargo binary project as scaffolding | Can find the project directory and understand that Cargo created files to be explained in I1. |
| I0 | `cargo run` and `cargo check` | Cargo binary project creation | Run/check a starter project | Can explain run vs check at a beginner level. |
| I0 | editor feedback and save-run loop | `cargo run` and `cargo check` | Make a tiny edit and rerun/check | Can describe the edit, check, run cycle. |
| I1 | `Cargo.toml` package metadata | Cargo binary project creation | Inspect package name, version, edition | Can say what `Cargo.toml` controls. |
| I1 | binary crate entrypoint `main` | Cargo binary project creation | Read an existing `fn main()` | Can identify where a binary starts. |
| I1 | library crate file `src/lib.rs` | Cargo binary project creation | Inspect provided library code | Can distinguish binary and library files. |
| I1 | `Cargo.lock` lockfile first look | `Cargo.toml` package metadata | Inspect lockfile when it appears | Can say it records exact dependency versions and is not edited by hand in beginner lessons. |
| I1 | comments: `//`, `/* */`, and doc comment preview | binary crate entrypoint `main` | Add or read comments without changing behavior | Can distinguish normal comments from documentation comments at a beginner level. |
| I1 | running existing `cargo test` | `cargo run` and `cargo check` | Run provided tests without editing test code | Can use test output to know pass/fail. |
| I2 | variable binding with `let` | binary crate entrypoint `main` | Fill a simple value binding | Can explain name-to-value binding. |
| I2 | mutability with `mut` | variable binding with `let` | Modify a mutable variable | Can explain immutable by default. |
| I2 | shadowing | variable binding with `let` | Read or write a simple shadowing example | Can distinguish shadowing from mutation. |
| I2 | type annotation and inference | variable binding with `let` | Add or remove an obvious annotation | Can explain when Rust can infer a type in simple code. |
| I2 | scalar integer types | type annotation and inference | Use `i32`, `u32`, or inferred integers | Can choose an integer type in a small function. |
| I2 | booleans, chars, and floats | scalar integer types | Use `bool`, `char`, or `f64` in tiny examples | Can identify these scalar types and avoid mixing them accidentally. |
| I2 | tuple and array basics | scalar integer types | Read or construct a small tuple or fixed array | Can explain fixed-size grouping vs fixed-size list. |
| I2 | function declaration | binary crate entrypoint `main` | Write a simple `fn name(...)` | Can identify name, parameters, and body. |
| I2 | function parameters and return type | function declaration, scalar integer types | Write a pure function with parameters | Can read `fn add(a: i32, b: i32) -> i32`. |
| I2 | expression return value | function parameters and return type | Return the last expression without semicolon | Can explain why no semicolon returns a value. |
| I2 | explicit `return` | function parameters and return type | Read or use early/simple `return` | Can distinguish explicit return from expression return. |
| I2 | `println!`, formatting, and `Debug` output | function declaration | Print values with `{}` or `{:?}` in starter code | Can choose display or debug formatting for simple values. |
| I3 | comparison and logical operators | booleans, chars, and floats | Write a condition with equality, ordering, and/or/negation operators | Can explain the boolean result of a simple expression. |
| I3 | `if` / `else` expressions | expression return value, comparison and logical operators | Choose a value with a condition | Can explain both branches produce compatible values. |
| I3 | `loop`, `while`, and `for` basics | variable binding with `let` | Iterate over a small range or list | Can choose a simple loop form. |
| I3 | ranges and inclusive ranges | `loop`, `while`, and `for` basics | Iterate over `0..n` or `1..=n` | Can predict which numbers are visited. |
| I3 | basic pattern matching preview | `if` / `else` expressions | Read a tiny `match` over simple values | Can describe match arms at a high level. |
| I4 | dependency-free project shape | `cargo run` and `cargo check`, function declaration | Inspect one small Cargo project with no crates | Can identify core logic vs command entrypoint. |
| I4 | deterministic program behavior | `if` / `else` expressions, loop basics | Produce predictable output for fixed input | Can avoid hidden randomness or hard-coded special cases. |
| I4 | beginner assertions with `assert_eq!` | running existing `cargo test`, expression return value | Read or add one assertion in provided code | Can explain expected vs actual in a failing assertion. |
| I4 | `panic!` and `expect` first look | beginner assertions with `assert_eq!` | Read starter code that intentionally stops on invalid setup | Can explain that panic stops the program and is not normal error handling. |
| I5 | `String` creation | variable binding with `let` | Create or receive an owned string | Can distinguish `String` from a string literal at a beginner level. |
| I5 | string concatenation | `String` creation | Build a small output string | Can concatenate without hard-coded output. |
| I5 | string length and simple text methods | `String` creation | Use `len`, `is_empty`, or `push_str` | Can choose a simple string operation. |
| I5 | `Vec` creation | variable binding with `let` | Create a vector of values | Can explain a growable list. |
| I5 | `Vec` indexing and `get` preview | `Vec` creation | Read an element safely in starter code | Can distinguish direct indexing from optional access at a high level. |
| I5 | simple iteration over `Vec` | `Vec` creation, loop basics | Process each item in a vector | Can produce an accumulated result. |
| I6 | reading compiler diagnostics | `cargo check` | Summarize one compiler error | Can identify the key message and location. |
| I6 | `Option` preview | `if` / `else` expressions | Handle `Some` / `None` in starter code | Can represent possible absence. |
| I6 | `Result` preview | `Option` preview | Handle `Ok` / `Err` in starter code | Can represent success or failure. |
| I6 | beginner `unwrap` avoidance | `Result` preview, `panic!` and `expect` first look | Replace or explain one unsafe `unwrap` in starter code | Can say why unchecked `unwrap` is risky outside tiny examples. |
| I7 | intro unit tests | running existing `cargo test`, function declaration | Add or complete simple tests for pure functions | Can run tests and explain what behavior they check. |
| I7 | tested core logic plus thin `main` | dependency-free project shape, intro unit tests | Keep most logic in testable functions | Can explain why CLI glue is separated from pure logic. |
| I7 | intro recap project integration | deterministic program behavior, simple iteration over `Vec`, intro unit tests | Complete a small CLI/text utility or guessing-game variant | Can explain how the learned pieces fit together. |

## Foundations Knowledge Points

| Lesson | Knowledge Point | Prerequisites | Practice Condition | Mastery Evidence |
| --- | --- | --- | --- | --- |
| F0 | ownership and move | Intro completion | Predict a moved value | Can explain who owns a value after assignment or call. |
| F0 | `Copy` vs move | ownership and move | Compare integers and `String` | Can predict when old binding remains usable. |
| F0 | `Clone` as explicit duplication | ownership and move | Fix one case with or without clone | Can explain why clone is or is not appropriate. |
| F0 | `Drop` and end-of-scope cleanup | ownership and move | Trace when a value is no longer usable | Can connect ownership to cleanup without manual free. |
| F1 | shared borrow `&T` | ownership and move | Read without taking ownership | Can choose a shared reference. |
| F1 | mutable borrow `&mut T` | shared borrow `&T`, mutability with `mut` | Mutate through one reference | Can explain exclusivity. |
| F1 | aliasing rule: many readers or one writer | mutable borrow `&mut T` | Fix a small borrow conflict | Can state why simultaneous read/write borrows are rejected. |
| F1 | reference scope and non-lexical lifetime intuition | aliasing rule: many readers or one writer | Move a use earlier or later to satisfy the borrow checker | Can see when a borrow is no longer used. |
| F2 | string slices `&str` | shared borrow `&T`, `String` creation | Accept text without taking ownership | Can choose `&str` for read-only text input. |
| F2 | slice signatures | shared borrow `&T`, `Vec` creation | Accept `&[T]` in a function | Can avoid unnecessary ownership in signatures. |
| F2 | slicing syntax and bounds | string slices `&str`, slice signatures | Read or create a simple slice | Can explain that slices borrow part of existing data. |
| F2 | ownership-oriented API choice | slice signatures, ownership and move | Choose `String`, `&str`, `Vec<T>`, or `&[T]` for a small function | Can justify ownership vs borrowing in a signature. |
| F3 | struct declaration | function declaration | Define fields for a small domain type | Can model grouped data. |
| F3 | struct update and field init shorthand | struct declaration | Build a value from existing fields | Can read or write common struct initialization forms. |
| F3 | methods and `impl` | struct declaration, shared borrow `&T` | Add a method to a struct | Can explain `self`, `&self`, or `&mut self`. |
| F3 | associated functions | methods and `impl` | Add a constructor-like `new` | Can distinguish `Type::new()` from `value.method()`. |
| F4 | enum declaration | struct declaration | Represent a small finite state | Can choose enum over sentinel values. |
| F4 | enum data variants | enum declaration | Store data inside variants | Can explain that variants may carry different fields. |
| F4 | `match` with enums | enum declaration, basic pattern matching preview | Handle all variants | Can explain exhaustive matching. |
| F4 | `Option` in real APIs | enum declaration, `Option` preview | Return or handle absence without sentinel values | Can choose `Option` for possibly missing data. |
| F4 | `if let` and `let...else` | `match` with enums, `Option` in real APIs | Simplify one single-pattern branch | Can choose between full `match`, `if let`, and `let...else`. |
| F5 | `Result` return type | `Result` preview, function return-value syntax | Return recoverable errors | Can avoid `unwrap` in library logic. |
| F5 | `?` propagation | `Result` return type | Propagate an error | Can explain early return on `Err`. |
| F5 | custom error messages with `expect` boundaries | `panic!` and `expect` first look, `Result` return type | Keep `expect` only at deliberate outer boundaries or tests | Can explain why library code returns errors instead of panicking. |
| F5 | error type choice: strings, `io::Error`, or enum preview | `?` propagation | Pick an error shape for a small function | Can explain the caller's needs when choosing an error type. |
| F6 | `Vec<T>` ownership in collections | `Vec` creation, ownership and move | Push, iterate, and return owned values | Can predict moves into and out of vectors. |
| F6 | `HashMap<K, V>` basics | `Vec<T>` ownership in collections | Count, insert, or look up values | Can use a map for key-value lookup. |
| F6 | borrowing keys and values from collections | `HashMap<K, V>` basics, shared borrow `&T` | Read from a collection without moving values | Can explain why lookup often returns references. |
| F6 | `entry` API preview | `HashMap<K, V>` basics | Update a count or default value | Can recognize when `entry` avoids repeated lookup. |
| F7 | modules and visibility | `Result` return type | Split a small module | Can explain `mod`, `pub`, and paths. |
| F7 | `use` paths and aliases | modules and visibility | Import names without confusing ownership | Can explain absolute vs relative paths at a beginner level. |
| F7 | package, crate, and module vocabulary | `Cargo.toml` package metadata, modules and visibility | Identify package/crate/module in one project | Can use the terms without mixing them up. |
| F7 | module file layout | modules and visibility | Split code into `mod.rs` or same-name files following current style | Can place files so the compiler finds modules. |
| F8 | unit tests | function declaration | Write focused tests for pure logic | Can run and interpret `cargo test`. |
| F8 | test modules and `#[cfg(test)]` | unit tests, modules and visibility | Put unit tests beside the code under test | Can explain why test modules are compiled for tests. |
| F8 | integration tests in `tests/` | F7, unit tests | Add one integration test after module layout is known | Can explain crate-level testing from outside the library. |
| F8 | test organization and fixtures | integration tests in `tests/` | Choose unit vs integration placement | Can keep IO or setup out of core logic tests when possible. |
| F9 | trait declaration and implementation | methods and `impl` | Define or implement a small behavior | Can explain a trait as a shared interface. |
| F9 | common derives: `Debug`, `Clone`, `PartialEq`, `Eq` | trait declaration and implementation | Derive traits needed for printing or tests | Can explain why a derive is needed in a specific example. |
| F9 | generic functions and structs | trait declaration and implementation | Write a small generic helper | Can identify a type parameter and where it is used. |
| F9 | trait bounds and `where` clauses | generic functions and structs | Constrain a generic function by behavior | Can explain why a bound is required. |
| F10 | lifetime elision intuition | shared borrow `&T`, trait bounds and `where` clauses | Read simple reference signatures without writing lifetimes | Can explain that many lifetimes are inferred. |
| F10 | explicit lifetime relationships | lifetime elision intuition | Add a lifetime to relate input and output references | Can explain a lifetime annotation as a relationship, not storage duration. |
| F10 | struct fields with references | explicit lifetime relationships, struct declaration | Read or write a struct that borrows data | Can explain why the borrowed data must outlive the struct. |
| F10 | avoiding unnecessary lifetime annotations | explicit lifetime relationships | Replace over-annotated owned data examples | Can identify when owned values do not need lifetimes. |
| F11 | closure syntax and capture | function declaration, ownership and move | Use a closure in a small transformation | Can explain when a closure captures by borrow or move at a high level. |
| F11 | iterator adapters: `map`, `filter`, `collect` | simple iteration over `Vec`, closure syntax and capture | Rewrite a simple loop as an iterator pipeline | Can explain each adapter in a short chain. |
| F11 | `iter`, `iter_mut`, and `into_iter` | iterator adapters: `map`, `filter`, `collect`, ownership and move | Choose the right iteration ownership mode | Can predict whether items are borrowed, mutably borrowed, or moved. |
| F11 | readability tradeoffs for iterators | iterator adapters: `map`, `filter`, `collect` | Compare loop and iterator versions | Can choose clarity over cleverness. |
| F12 | CLI args with `std::env::args` | `Result` return type, modules and visibility | Parse simple command arguments | Can keep argument parsing separate from core logic. |
| F12 | file IO with `std::fs` | CLI args with `std::env::args`, `?` propagation | Read or write a text file with errors | Can propagate IO errors instead of panicking. |
| F12 | environment variables with `std::env` | CLI args with `std::env::args` | Read optional configuration from env | Can model missing env values as `Result` or `Option`. |
| F12 | stderr and process exit boundaries | file IO with `std::fs`, custom error messages with expect boundaries | Report errors from `main` or a thin runner | Can separate user-facing error reporting from library logic. |
| F13 | foundations project planning | F12, F8 | Break a mini grep/config parser/log analyzer into modules | Can list core logic, IO, CLI, and tests separately. |
| F13 | foundations project integration | foundations project planning, modules and visibility, `Result` return type | Complete a small library or CLI across modules | Can explain how ownership, `Result`, modules, and tests fit together. |
| F13 | rustfmt and Clippy project check | foundations project integration | Run or explain formatting and lint checks | Can use tool feedback without broad unrelated rewrites. |
| F13 | project recap and review queue cleanup | foundations project integration | Review weak items after project completion | Can identify which concepts are mastered and which need review. |

## Advanced Knowledge Points

| Lesson | Knowledge Point | Prerequisites | Practice Condition | Mastery Evidence |
| --- | --- | --- | --- | --- |
| A0 | Cargo profiles: dev, release, and custom profile basics | F13 | Inspect or explain profile differences | Can describe why release builds optimize differently. |
| A0 | Cargo features and optional dependencies | F13 | Read or sketch a feature flag | Can explain feature unification at a practical level. |
| A0 | Cargo workspaces | F13 | Inspect or create a tiny workspace layout | Can explain shared target and member crates. |
| A0 | `cargo install` and publishing concepts | F13 | Explain install vs dependency and publish prerequisites | Can describe crate publishing without needing to publish. |
| A1 | rustfmt workflow | F8 | Run or explain `cargo fmt` | Can keep formatting separate from semantic changes. |
| A1 | Clippy workflow | F8 | Run or explain `cargo clippy` | Can distinguish useful lint feedback from style preference. |
| A1 | rust-analyzer editor support | F8 | Explain diagnostics, completion, and go-to-definition | Can use editor feedback as a learning aid. |
| A1 | `cargo fix` and mechanical fixes | Clippy workflow | Explain or run a safe mechanical fix in a controlled case | Can review automatic changes before accepting them. |
| A2 | Rust editions and compatibility | A1 | Identify the edition in `Cargo.toml` | Can explain editions do not split the ecosystem. |
| A2 | Edition Guide navigation | Rust editions and compatibility | Find a migration rule or change note | Can use the guide for edition-specific questions. |
| A2 | `cargo fix --edition` workflow | Rust editions and compatibility, `cargo fix` and mechanical fixes | Describe the migration sequence | Can explain why tests should run before and after migration. |
| A3 | doc comments: `///` and `//!` | F8, comments: `//`, `/* */`, and doc comment preview | Document a public item or module | Can choose item-level vs module-level docs. |
| A3 | `cargo doc` and API documentation | doc comments: `///` and `//!` | Build or inspect generated docs | Can explain how public API docs are produced. |
| A3 | doc tests | doc comments: `///` and `//!`, unit tests | Add a compiling example in documentation | Can explain docs as executable examples. |
| A3 | public API examples and hidden setup | doc tests | Keep documentation examples focused and valid | Can use doc examples without leaking irrelevant setup. |
| A4 | `Box<T>` for heap allocation and recursive types | F10 | Use or explain a boxed value | Can identify when indirection is needed. |
| A4 | `Rc<T>` shared ownership | `Box<T>` for heap allocation and recursive types | Read a single-thread shared ownership example | Can explain reference counting without mutation. |
| A4 | `Arc<T>` shared ownership across threads | `Rc<T>` shared ownership | Read a thread-safe shared ownership example | Can distinguish `Rc` from `Arc`. |
| A4 | `RefCell<T>` interior mutability | `Rc<T>` shared ownership, borrowing rules | Mutate through runtime borrow checks in a small example | Can explain runtime borrow panic risk. |
| A4 | `Mutex<T>` protected shared mutability | `Arc<T>` shared ownership across threads, `RefCell<T>` interior mutability | Protect shared state with locking | Can explain lock scope and poisoning at a high level. |
| A5 | spawning threads with `std::thread` | A4 | Spawn and join one thread | Can explain thread lifetime and join. |
| A5 | message passing with channels | spawning threads with `std::thread` | Send values between threads | Can explain producer, receiver, and channel close. |
| A5 | shared-state concurrency with `Arc<Mutex<T>>` | `Mutex<T>` protected shared mutability | Update shared state safely | Can explain why both `Arc` and `Mutex` are needed. |
| A5 | `Send` and `Sync` intuition | shared-state concurrency with `Arc<Mutex<T>>` | Read compiler feedback about thread safety | Can explain at a high level what may cross or be shared between threads. |
| A6 | `Future` and `async`/`.await` model | A5 | Read a tiny async function | Can explain that futures are polled and need execution. |
| A6 | runtimes and tasks | `Future` and `async`/`.await` model | Explain why Tokio or another runtime appears in examples | Can distinguish async task scheduling from OS threads. |
| A6 | async IO and cancellation intuition | runtimes and tasks | Read an async IO or timeout sketch | Can explain why blocking calls are avoided in async code. |
| A6 | streams and async ecosystem map | runtimes and tasks | Identify stream-like async sequences | Can navigate common async concepts without treating them as core syntax. |
| A7 | trait objects with `dyn Trait` | F9 | Store heterogeneous values behind a trait object | Can explain dynamic dispatch at a high level. |
| A7 | object safety basics | trait objects with `dyn Trait` | Read why a trait cannot be made into an object | Can identify common object-safety blockers. |
| A7 | static vs dynamic dispatch tradeoffs | trait objects with `dyn Trait`, generic functions and structs | Compare generic and `dyn` designs | Can choose based on flexibility, code size, and call cost. |
| A8 | associated types | trait bounds and `where` clauses | Read or write a trait with an associated type | Can explain when the implementor chooses the type. |
| A8 | supertraits | associated types | Require one trait from another | Can explain inherited behavior requirements. |
| A8 | fully qualified syntax | associated types | Disambiguate a method or associated item | Can read `<Type as Trait>::item` syntax. |
| A8 | newtype pattern | trait declaration and implementation | Wrap a type to add behavior or control API | Can explain why a wrapper is preferable to type aliasing. |
| A9 | refutable and irrefutable patterns | `match` with enums | Classify pattern positions | Can identify where a pattern may fail. |
| A9 | destructuring structs, enums, tuples, and slices | refutable and irrefutable patterns | Pull values out with patterns | Can keep destructuring readable and correct. |
| A9 | match guards and binding modes | destructuring structs, enums, tuples, and slices | Add a guard or binding in a match arm | Can explain why guard conditions do not affect exhaustiveness in the same way. |
| A9 | advanced `let`, parameters, and loop patterns | refutable and irrefutable patterns | Read patterns outside `match` | Can identify which pattern forms are allowed in each position. |
| A10 | `macro_rules!` by example | F9 | Read or write a tiny declarative macro | Can explain pattern-to-expansion at a high level. |
| A10 | derive and procedural macro concepts | `macro_rules!` by example | Identify generated code boundaries | Can describe derive, attribute, and function-like macro categories. |
| A10 | macro hygiene and diagnostics intuition | `macro_rules!` by example | Read a macro error without panic | Can separate call-site code from expanded code conceptually. |
| A10 | when to avoid macros | derive and procedural macro concepts | Replace an unnecessary macro with a function or trait | Can explain the maintenance tradeoff. |
| A11 | raw pointers and unsafe blocks | A4 | Read a tiny unsafe pointer example | Can identify what the compiler stops checking. |
| A11 | `unsafe fn` and unsafe traits | raw pointers and unsafe blocks | Explain caller and implementor obligations | Can describe the safety contract. |
| A11 | FFI and C ABI overview | `unsafe fn` and unsafe traits | Read an `extern "C"` boundary sketch | Can identify ABI and ownership boundary questions. |
| A11 | safe wrappers around unsafe code | FFI and C ABI overview | Review where unsafe is contained | Can explain why the public API should enforce invariants. |
| A12 | Rust Reference navigation | A11 | Find a precise language rule | Can choose the Reference for syntax or semantic details. |
| A12 | Rustonomicon navigation | safe wrappers around unsafe code | Find unsafe-code guidance | Can choose the Nomicon for unsafe invariants and pitfalls. |
| A12 | Standard Library docs navigation | A3 | Inspect trait, type, or method docs | Can use docs to confirm signatures and examples. |
| A12 | official book and example-source triangulation | Rust Reference navigation, Standard Library docs navigation | Compare TRPL, Rust By Example, and docs for a topic | Can choose the right official source for learning vs exact rules. |
| A13 | capstone scope and design | A3, A5 | Select a multithreaded server, async tool, or library plus CLI | Can define scope, milestones, and risk. |
| A13 | capstone implementation integration | capstone scope and design | Build across multiple advanced lessons | Can explain major design choices and tradeoffs. |
| A13 | capstone tests and documentation | capstone implementation integration, doc tests | Add tests and docs appropriate to the project | Can show validation evidence beyond manual runs. |
| A13 | final review and learning map handoff | capstone tests and documentation | Summarize mastered topics and follow-up areas | Can identify next independent learning tracks. |
