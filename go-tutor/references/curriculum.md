# Go Tutor Curriculum

Use this curriculum as the default learning spine. It is organized into three stages. Use `knowledge-map.md` to split each lesson into fine-grained micro-lessons and to check prerequisites before practice. A lesson's mastery gate depends on the required micro-lessons listed for that lesson in `knowledge-map.md`; do not treat the curriculum topic title as a single large concept.

- `入门` / Intro: become comfortable installing Go, running programs, writing functions, and testing small packages.
- `基础` / Foundations: master packages, errors, interfaces, standard library composition, testing, and concurrency basics.
- `进阶` / Advanced: understand Go's official documentation map, tooling, diagnostics, services, advanced language features, and production practices.

Adapt pacing to the learner's goal, but keep the stage order unless placement evidence clearly supports skipping. Skipped lessons are recorded as `verified by placement`, not as fully taught.

## Status Terms

- `unstarted`: no evidence yet.
- `introduced`: explained or attempted once.
- `practiced`: completed at least one exercise with minor help.
- `mastered`: completed an exercise and explained the core rule accurately.
- `review`: should revisit before advancing far.

## Placement

If there is no valid placement result, place the learner with a short readiness check and, when appropriate, a 10 minute diagnostic. A valid placement requires `Overall placement` to be set to a concrete lesson or stage, not empty and not `unplaced`.

1. Use confirmed prior programming experience, Go language experience, and Go goal; ask first if any of these are missing or inferred.
2. Check whether they can already read or attempt a tiny Go function body.
3. If they do not know Go syntax yet, do not assign a code diagnostic; start at G-I0 and treat that answer as placement evidence.
4. If they struggle with basic programming, start at G-I0.
5. If they know programming but not Go, verify G-I0 to G-I2 quickly with explanation-first checks and start at G-I3 or G-F0 only when the evidence supports it.
6. If they can attempt Go code, give a tiny function exercise using variables, conditionals, slices, and a table-driven test.
7. If they already know Go basics, test errors, interfaces, testing, and simple concurrency before placing in G-F3 to G-F7.

For experienced developers:

- Combine G-I0 to G-I2 into fast verification instead of teaching them slowly.
- Fast verification is enough when the learner can create or recognize a Go module, run `go test ./...`, and explain where `go.mod`, `package main`, and imports fit.
- If fast verification passes and Go idioms are new, set the starting point to G-F0.
- If the learner demonstrates structs, methods, errors, interfaces, and tests, set the starting point based on the weakest evidence in G-F3 to G-F7.
- Do not skip the Foundations stage permanently; errors, interfaces, package design, testing, and concurrency are required.

## Stage 1: 入门

Goal: the learner can install, run, read, and write basic Go programs and complete a small tested exercise.

| ID | Topic | Prerequisites | Mastery Gate |
| --- | --- | --- | --- |
| G-I0 | Go installation, `go version`, `go env`, `go run` | none | Can show or explain local toolchain status and run a provided tiny Go program without explaining package, import, or entrypoint details yet. |
| G-I1 | Modules, packages, `go mod init`, `main` package, imports, `gofmt` habit | G-I0 | Can create a module, explain `go.mod`, format existing code with `gofmt`, and run existing `go test ./...` without writing business functions or table-driven tests. |
| G-I2 | Variables, constants, basic types, functions, multiple returns | G-I1 | After being taught function declarations and returns, can write pure functions with parameters, return values, and multiple returns. |
| G-I3 | `if`, `switch`, `for`, first look at `defer` | G-I2 | Can transform small input using conditionals and loops and explain when `defer` runs. |
| G-I4 | Arrays, slices, maps, strings, runes | G-I3 | Can choose slices or maps and handle strings without confusing bytes and runes. |
| G-I5 | Basic testing: `*_test.go`, `go test`, simple table-driven tests | G-I4 | Can write and run a table-driven test for one function. |
| G-I6 | Error values, `nil`, compiler diagnostics, `fmt` | G-I5 | Can return and check an error value and summarize a compiler diagnostic. |
| G-I7 | Intro project: dependency-free CLI or text processing tool | G-I6 | Can complete a small `gofmt`-formatted program with deterministic behavior and tests for core logic. |

Intro completion evidence:

- Creates and runs Go modules.
- Writes basic functions, loops, conditionals, slices, maps, and tests.
- Reads common compiler errors at a high level.
- Understands errors are values and that package/test design is the next core path.

## Stage 2: 基础

Goal: the learner can write clear, tested Go packages or CLIs using idiomatic errors, interfaces, standard library composition, and basic concurrency.

| ID | Topic | Prerequisites | Mastery Gate |
| --- | --- | --- | --- |
| G-F0 | Structs, methods, pointers | G-I7 or placement | Can model a small domain type with methods and explain when a pointer receiver is needed. |
| G-F1 | Interfaces, composition, implicit implementation | G-F0 | Can define a small interface at the consumer boundary and explain implicit satisfaction. |
| G-F2 | Idiomatic errors: wrapping, `errors.Is`, `errors.As` | G-I6, G-F0 | Can wrap and inspect errors without string matching or panics. |
| G-F3 | Packages, visibility, module dependencies | G-F1, G-F2 | Can split code into packages with a clear exported API and minimal dependencies. |
| G-F4 | Table-driven tests, subtests, examples, benchmarks | G-I5 | Can write subtests and choose tests, examples, or benchmarks appropriately. |
| G-F5 | `io.Reader` / `io.Writer`, dependency injection, standard library composition | G-F1, G-F4 | Can test IO-heavy code by injecting readers or writers instead of using global state. |
| G-F6 | Files, JSON, HTTP client, standard library practice | G-F2, G-F5 | Can build a small standard-library workflow with errors and tests around core logic. |
| G-F7 | Goroutines, channels, `select` | G-F4 | Can write a small concurrent pipeline and explain channel ownership and closing. |
| G-F8 | `context`, cancellation, timeout | G-F7 | Can pass `context.Context` through call boundaries and stop work on cancellation. |
| G-F9 | `sync`, mutex, WaitGroup, atomic, race detector | G-F7 | Can protect shared state and use the race detector to validate a concurrent exercise. |
| G-F10 | Generics basics: type parameters, constraints, when not to use them | G-F1 | Can write a simple generic function and explain when an interface or concrete type is simpler. |
| G-F11 | Foundations project: tested CLI, HTTP client, or small library | G-F6, G-F9 | Can complete a focused project with tests, idiomatic errors, packages, and `gofmt`/`go vet` checks. |

Foundations completion evidence:

- Uses structs, methods, interfaces, and packages intentionally.
- Handles errors as values and wraps errors when callers need context.
- Tests core logic with table-driven tests and subtests.
- Composes standard library interfaces such as `io.Reader` and `io.Writer`.
- Writes basic concurrent code and validates shared-state code with the race detector when feasible.

## Stage 3: 进阶

Goal: the learner has a broad, accurate map of Go's official ecosystem and knows when advanced tools and language features are appropriate.

| ID | Topic | Prerequisites | Mastery Gate |
| --- | --- | --- | --- |
| G-A0 | Effective Go: naming, package design, API design | G-F11 | Can review a small API for naming, package boundaries, and exported documentation. |
| G-A1 | Modules advanced: workspaces, versioning, publishing | G-F3 | Can explain workspaces, semantic import versioning, and module release basics. |
| G-A2 | Tooling: `gofmt`, `go vet`, `gopls`, `go doc`, coverage, `govulncheck` | G-F4 | Can run or explain each tool and when it should be used. |
| G-A3 | Fuzzing, benchmarks, coverage, golden tests | G-F4 | Can add a bounded fuzz target or benchmark and interpret the result. |
| G-A4 | Diagnostics: pprof, trace, GC guide, PGO | G-F11 | Can choose a diagnostic tool for CPU, memory, trace, or profile-guided optimization questions. |
| G-A5 | Go memory model, race detector, concurrency patterns | G-F9 | Can explain happens-before at a practical level and avoid data races in a small example. |
| G-A6 | `net/http` server, middleware, graceful shutdown | G-F6, G-F8 | Can build a small HTTP server with timeouts, cancellation, tests, and graceful shutdown. |
| G-A7 | `database/sql`, transactions, prepared statements, SQL injection avoidance | G-F6, G-F8 | Can write a small data-access function using context, transactions, and parameters safely. |
| G-A8 | Reflection, code generation, `unsafe`/`cgo` overview | G-A0, G-A2 | Can identify when reflection or generation is appropriate and describe unsafe boundaries. |
| G-A9 | Advanced generics: constraints, `comparable`, API tradeoffs | G-F10 | Can read and review a generic API and explain the complexity tradeoff. |
| G-A10 | Security, vulnerability checking, release notes, compatibility | G-A2 | Can use vulnerability and release information to review dependency and upgrade risk. |
| G-A11 | Final capstone: documented and tested CLI, web service, or library | G-A0, G-A2, plus selected advanced lessons relevant to the capstone | Can complete a documented, tested project demonstrating multiple advanced topics. |

Advanced completion evidence:

- Explains the purpose and risks of Go's advanced features.
- Uses official tooling, diagnostics, coverage, vulnerability checks, and documentation appropriately.
- Chooses concurrency, context, package, and API designs based on maintainability and correctness.
- Treats `unsafe` and `cgo` as explicit boundary tools, not shortcuts.
- Completes a capstone with tests and documentation.

## Projects

Use one project or recap after every 3 to 5 lessons. Every stage must end with a project.

| ID | Stage | When | Project | Required Evidence |
| --- | --- | --- | --- | --- |
| G-P-I | 入门 | After G-I7 | Small CLI or text utility | Go module, deterministic behavior, tests for core logic. |
| G-P-F1 | 基础 | After G-F2 | Structs, methods, and errors lab | Pointer receivers and error wrapping explained. |
| G-P-F2 | 基础 | After G-F5 | IO-driven parser or formatter | Uses `io.Reader`/`io.Writer`, table-driven tests, and idiomatic errors. |
| G-P-F3 | 基础 | After G-F11 | Tested CLI, HTTP client, or small library | Packages, tests, standard library composition, `gofmt`, and `go vet`. |
| G-P-A1 | 进阶 | After G-A6 | HTTP service or concurrent worker | Context, graceful shutdown or cancellation, tests, and race-aware design. |
| G-P-A2 | 进阶 | After G-A11 | Final capstone | Documented, tested, and demonstrates multiple advanced topics. |

## Remediation Rules

- If the learner hard-codes output or only tests happy paths, return to G-I5 or G-F4 with a smaller table-driven test.
- If the learner uses panics for normal failures, return to G-I6 and G-F2.
- If interfaces are defined on the provider side without a need, revisit G-F1 with consumer-side examples.
- If package boundaries become circular or vague, return to G-F3.
- If concurrent code leaks goroutines, races, or closes channels from the wrong owner, return to G-F7 to G-F9.
- If generics make the code harder to read, allow a concrete type or interface and discuss tradeoffs.

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
9. Goal-specific tracks after G-A11, such as backend services, CLIs, distributed systems, observability, Kubernetes tooling, WebAssembly, embedded, or performance.

## Advancement Rules

- Do not advance from a lesson until the learner has evidence for that lesson's mastery gate.
- Do not mark a lesson `mastered` until each required `knowledge-map.md` row for that lesson is at least `practiced`, unless the row was directly verified by placement evidence.
- Do not mark a stage complete until its stage project is complete.
- If the learner passes tests but cannot explain the target rule, mark `practiced` or `review`, not `mastered`.
- If the learner needs heavy hints, keep the same lesson active and add a review item.
- If placement skips a lesson, mark it as verified by placement only when the diagnostic directly tested the lesson's mastery gate.
- Required Foundations topics must not be permanently skipped: errors, interfaces, packages, tests, standard library composition, and concurrency.
