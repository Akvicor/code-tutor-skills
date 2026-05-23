# Go Fine-Grained Knowledge Map

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
| G-I0 | toolchain status: `go version`, `go env` | none | Recognize or run toolchain commands | Can report what Go toolchain is installed or missing. |
| G-I0 | `go run` for a tiny program | toolchain status | Run a provided program | Can explain that `go run` builds and runs. |
| G-I1 | module creation with `go mod init` | toolchain status | Create or inspect `go.mod` | Can explain module name and `go.mod`. |
| G-I1 | `main.go` command file first look | module creation with `go mod init` | Inspect a provided command file | Can say `main.go` is a common filename for a command, while package and function names define behavior. |
| G-I1 | package declaration | module creation with `go mod init` | Read or write `package main` | Can identify the package line. |
| G-I1 | `main` function entrypoint | package declaration | Read an existing `func main()` | Can identify where a command starts. |
| G-I1 | imports | package declaration | Use one standard-library import in starter code | Can explain why imports are listed. |
| G-I1 | `go build` for local binaries | `main` function entrypoint | Build a tiny command | Can distinguish build output from immediate run. |
| G-I1 | comments and doc comments | package declaration | Add `//` comments and read a package or exported-name doc comment | Can distinguish ordinary comments from Go documentation comments. |
| G-I1 | `gofmt` habit | package declaration | Format existing code | Can run or explain formatting. |
| G-I1 | `go.sum` and `go mod tidy` first look | module creation with `go mod init` | Inspect dependency metadata or explain tidy in a starter module | Can say why `go.sum` records module checksums and tidy cleans module files. |
| G-I1 | running existing `go test ./...` | module creation with `go mod init` | Run provided tests without editing test code | Can use test output to know pass/fail. |
| G-I2 | variable declaration with `var` | package declaration | Read or write a simple variable declaration | Can explain name, type, and value. |
| G-I2 | zero values | variable declaration with `var` | Predict default values for simple declarations | Can explain default values for numbers, booleans, strings, and nil-capable types. |
| G-I2 | short declaration `:=` | variable declaration with `var` | Use local inferred variables | Can explain where `:=` is allowed. |
| G-I2 | constant declaration | variable declaration with `var` | Define a simple constant | Can distinguish constants from variables. |
| G-I2 | basic integer types | variable declaration with `var` | Use `int` or a sized integer in a small function | Can choose an integer type for beginner exercises. |
| G-I2 | bool, floats, and type conversion | basic integer types, zero values | Convert or compare simple values without implicit conversion | Can explain that Go does not silently convert numeric types. |
| G-I2 | arithmetic, comparison, and logical operators | bool, floats, and type conversion | Use arithmetic, comparison, and/or/negation operators in tiny functions | Can predict the result type and branch condition. |
| G-I2 | string values and concatenation | variable declaration with `var` | Build a small output string | Can concatenate strings without hard-coded output. |
| G-I2 | function declaration | package declaration | Write a simple `func name(...)` | Can identify name, parameters, and body. |
| G-I2 | parameters and single return value | function declaration, basic integer types | Write a pure function with one return value | Can read `func add(a int, b int) int`. |
| G-I2 | multiple return values | parameters and single return value | Return two values from a small function | Can explain comma-separated return values. |
| G-I2 | variadic functions | parameters and single return value | Read or write a small `...T` parameter | Can explain zero or more arguments of the same type. |
| G-I2 | anonymous functions and closures | function declaration, variable declaration with `var` | Use a small function literal that captures a local value | Can explain captured values at a beginner level. |
| G-I3 | `if` / `else` | arithmetic, comparison, and logical operators, parameters and single return value | Choose a result with a condition | Can explain branch selection. |
| G-I3 | `switch` basics | `if` / `else` | Read or write a small `switch` | Can map cases to outcomes. |
| G-I3 | `for` loop basics | variable declaration with `var` | Iterate over a small range or condition | Can choose a simple loop shape. |
| G-I3 | `range` over collections | `for` loop basics | Use index/value or key/value in a small loop | Can explain what values `range` produces. |
| G-I3 | `defer` first look | function declaration | Read a tiny defer example | Can say deferred calls run near function return. |
| G-I4 | arrays | basic integer types | Read a fixed-size collection | Can explain fixed length. |
| G-I4 | slices | arrays | Create or process a slice | Can explain a flexible view/list. |
| G-I4 | `len`, `cap`, `append`, and `make` | slices | Grow or allocate a slice in starter code | Can explain length vs capacity at a beginner level. |
| G-I4 | maps | slices | Store and look up key-value data | Can use a map for simple counts or lookup. |
| G-I4 | map lookup comma-ok form | maps, multiple return values | Check whether a key exists | Can distinguish missing key from zero value. |
| G-I4 | strings, bytes, and runes | string values and concatenation | Process text in a beginner-safe way | Can avoid confusing bytes and runes in simple cases. |
| G-I5 | `*_test.go` files | function declaration | Read a focused test file | Can identify where tests live. |
| G-I5 | `go test` for a package | `*_test.go` files | Run focused tests | Can interpret pass/fail output. |
| G-I5 | simple table-driven tests | slices, `go test` for a package | Add or complete a small test table | Can explain cases and expected values. |
| G-I5 | test failure messages with `t.Fatalf` or `t.Errorf` | simple table-driven tests | Improve one failing test message | Can report got vs want clearly. |
| G-I6 | error return values | multiple return values | Return `value, error` | Can explain errors as ordinary values. |
| G-I6 | `nil` for no error and nil zero value | error return values, zero values | Check whether error is nil | Can branch on error presence and recognize nil as a zero value for some types. |
| G-I6 | compiler diagnostics | `go test` for a package | Summarize one compiler error | Can identify the key message and location. |
| G-I6 | `fmt` basics | imports, string values and concatenation | Format or print a simple value | Can choose a basic `fmt` function in starter code. |
| G-I6 | avoid panic for normal errors | error return values, `nil` for no error and nil zero value | Replace or explain one panic in recoverable flow | Can say why callers should receive errors for expected failures. |
| G-I7 | dependency-free CLI shape | `main` function entrypoint, `fmt` basics | Inspect or complete a small command package | Can identify command entrypoint and core logic. |
| G-I7 | deterministic text processing | slices, maps, strings, bytes, and runes | Transform fixed input into fixed output | Can avoid hard-coded special cases. |
| G-I7 | tested core logic plus thin `main` | simple table-driven tests, dependency-free CLI shape | Keep core logic testable away from CLI glue | Can explain why tests target functions instead of terminal output. |
| G-I7 | intro project integration | deterministic text processing, simple table-driven tests, error return values | Complete a small CLI/text utility | Can explain how the learned pieces fit together. |

## Foundations Knowledge Points

| Lesson | Knowledge Point | Prerequisites | Practice Condition | Mastery Evidence |
| --- | --- | --- | --- | --- |
| G-F0 | struct declaration | G-I7 or placement | Define fields for a small domain type | Can model grouped data. |
| G-F0 | struct literals and field names | struct declaration | Construct values clearly | Can explain positional avoidance and field-name readability. |
| G-F0 | methods | struct declaration, function declaration | Add a method to a struct | Can explain receiver syntax. |
| G-F0 | pointer basics | methods, zero values | Read address and dereference examples | Can explain that pointers refer to existing values and may be nil. |
| G-F0 | pointer receiver | methods, pointer basics | Mutate or avoid copying through receiver | Can choose value vs pointer receiver in a simple case. |
| G-F1 | interface declaration | methods | Define a small consumer-side interface | Can explain implicit implementation. |
| G-F1 | small consumer-side interfaces | interface declaration | Move an interface to the package that consumes it | Can avoid provider-side abstractions without a need. |
| G-F1 | composition | interface declaration | Combine behavior without inheritance | Can avoid oversized interfaces. |
| G-F1 | nil interface pitfalls | interface declaration, pointer basics | Read a typed-nil interface example | Can explain why interface nil checks can be surprising. |
| G-F2 | error wrapping | error return values | Add context to an error | Can use wrapping without string matching. |
| G-F2 | sentinel and custom error types | error wrapping | Define or compare a small reusable error | Can choose sentinel or typed errors based on caller needs. |
| G-F2 | `errors.Is` / `errors.As` | error wrapping, sentinel and custom error types | Inspect wrapped errors | Can choose the right inspection tool. |
| G-F2 | error messages and caller context | error wrapping | Add context once without duplicate noise | Can write lower-case, useful error messages and avoid panics. |
| G-F3 | exported names | package declaration | Expose a small API | Can explain uppercase export. |
| G-F3 | package naming and doc comments | exported names, comments and doc comments | Name and document one small package/API | Can write concise package and exported-name docs. |
| G-F3 | package boundaries | exported names | Split code into packages | Can avoid circular or vague packages. |
| G-F3 | module dependencies and `go mod tidy` | `go.sum` and `go mod tidy` first look, package boundaries | Add or remove one dependency in a controlled exercise | Can keep module metadata consistent. |
| G-F4 | subtests | simple table-driven tests | Add named cases with `t.Run` | Can read failing subtest output. |
| G-F4 | examples and benchmarks | `go test` for a package | Choose test vs example vs benchmark | Can explain which tool answers which question. |
| G-F4 | coverage basics | subtests | Run or interpret package coverage | Can explain statement coverage as a signal, not proof. |
| G-F4 | test helpers and cleanup | subtests | Use a helper or cleanup in a focused test | Can keep tests readable without hiding assertions. |
| G-F5 | `io.Reader` | interface declaration | Accept input via reader | Can test IO without global state. |
| G-F5 | `io.Writer` | interface declaration | Write output via writer | Can inject output for tests. |
| G-F5 | dependency injection with interfaces | `io.Reader`, `io.Writer`, small consumer-side interfaces | Pass dependencies through parameters or structs | Can avoid hard-coded files, network, or stdout in core logic. |
| G-F5 | standard library composition with `bytes` and `strings` | dependency injection with interfaces | Test IO code with in-memory readers/writers | Can choose test doubles from the standard library. |
| G-F6 | file IO with `os` and `io` | G-F5, error wrapping | Read or write files with error handling | Can keep filesystem boundaries thin and test core logic. |
| G-F6 | JSON encoding and decoding | file IO with `os` and `io` | Marshal or unmarshal a small struct | Can handle JSON errors and field tags at a beginner level. |
| G-F6 | HTTP client with `net/http` | JSON encoding and decoding, error return values | Fetch or parse a response in a small client | Can close response bodies and propagate errors. |
| G-F6 | testing standard-library workflows | HTTP client with `net/http`, dependency injection with interfaces | Test parsing or client logic without brittle live network calls | Can isolate core logic from IO/network setup. |
| G-F7 | goroutines | function declaration | Start one bounded goroutine | Can explain goroutine lifetime at a high level. |
| G-F7 | channels and closing | goroutines | Pass values safely | Can explain who closes the channel. |
| G-F7 | `select` basics | channels and closing | Wait on more than one channel in a small example | Can explain which case runs and why default can busy-loop. |
| G-F7 | goroutine leak awareness | channels and closing | Fix or explain one blocked goroutine | Can identify a missing receive, send, close, or cancellation path. |
| G-F8 | `context.Context` as a parameter | G-F7 | Thread context through call boundaries | Can explain why context is normally the first parameter. |
| G-F8 | cancellation and timeout | `context.Context` as a parameter, `select` basics | Stop work when context is done | Can use `ctx.Done()` in a loop or select. |
| G-F8 | deadline-aware IO boundaries | cancellation and timeout, HTTP client with `net/http` | Attach context to an HTTP request or similar boundary | Can explain timeout vs cancellation at a practical level. |
| G-F9 | `sync.WaitGroup` | goroutines | Wait for bounded goroutines | Can add and done without racing or hanging. |
| G-F9 | `sync.Mutex` | goroutines, pointer basics | Protect shared state | Can explain lock scope and avoid copying mutexes. |
| G-F9 | atomics first look | `sync.Mutex` | Read or use a simple atomic counter | Can explain that atomics are specialized tools, not default synchronization. |
| G-F9 | race detector | `sync.Mutex`, `go test` for a package | Run or explain `go test -race` for concurrent code | Can use race reports to find unsafe shared access. |
| G-F10 | type parameters | interface declaration | Write a simple generic function | Can identify a type parameter list and uses. |
| G-F10 | constraints and type sets | type parameters | Constrain a small generic helper | Can explain what operations the constraint permits. |
| G-F10 | `comparable` basics | constraints and type sets, maps | Use or read a comparable constraint for map keys | Can explain equality requirement at a beginner level. |
| G-F10 | when not to use generics | type parameters, interface declaration | Compare concrete, interface, and generic designs | Can choose the simplest readable API. |
| G-F11 | foundations project planning | G-F6, G-F9 | Split a CLI, HTTP client, or small library into packages and tests | Can list core logic, IO/network boundaries, and validation commands. |
| G-F11 | foundations project integration | foundations project planning, package boundaries, error wrapping | Complete a focused project | Can explain how packages, errors, IO, tests, and concurrency fit together. |
| G-F11 | `gofmt` and `go vet` project check | foundations project integration | Run or explain formatting and vet checks | Can use tool feedback without broad unrelated rewrites. |
| G-F11 | project recap and review queue cleanup | foundations project integration | Review weak items after project completion | Can identify which concepts are mastered and which need review. |

## Advanced Knowledge Points

| Lesson | Knowledge Point | Prerequisites | Practice Condition | Mastery Evidence |
| --- | --- | --- | --- | --- |
| G-A0 | Effective Go naming | G-F11 | Review package, interface, and function names | Can make names shorter and clearer without losing meaning. |
| G-A0 | API design and exported surface | Effective Go naming, package boundaries | Review a small public API | Can reduce unnecessary exported names and preserve compatibility. |
| G-A0 | documentation as API contract | API design and exported surface, package naming and doc comments | Improve package and exported-name docs | Can explain behavior, errors, and concurrency expectations. |
| G-A0 | idiomatic simplicity review | Effective Go naming | Replace clever code with clearer code in a small example | Can justify boring, maintainable Go. |
| G-A1 | module versioning and semantic import versioning | G-F3 | Explain v0/v1/v2+ module paths | Can describe how major versions affect import paths. |
| G-A1 | Go workspaces with `go.work` | module versioning and semantic import versioning | Inspect or create a small workspace | Can explain local multi-module development. |
| G-A1 | publishing modules | module versioning and semantic import versioning | Describe tags and module discovery | Can explain release steps without needing to publish. |
| G-A1 | dependency compatibility and replace directives | Go workspaces with `go.work`, module dependencies and `go mod tidy` | Use or review a local replace in a controlled example | Can explain why replace directives should not leak accidentally. |
| G-A2 | `go vet` workflow | G-F4 | Run or explain vet checks | Can distinguish vet warnings from compiler errors. |
| G-A2 | `gopls` editor support | G-F4 | Explain diagnostics, completion, and navigation | Can use editor feedback as a learning aid. |
| G-A2 | `go doc` and documentation lookup | package naming and doc comments | Find docs for a package, type, or function | Can use local docs before guessing APIs. |
| G-A2 | coverage and `govulncheck` workflow | G-F4, module dependencies and `go mod tidy` | Run or explain coverage and vulnerability checks | Can explain what each tool does and does not prove. |
| G-A2 | `go install` for tools and commands | module dependencies and `go mod tidy` | Install or explain a versioned command | Can distinguish installing a command from adding a library dependency. |
| G-A3 | benchmarks with `testing.B` | examples and benchmarks | Add or run a small benchmark | Can avoid measuring setup as the main result. |
| G-A3 | fuzzing with `testing.F` | G-F4 | Add a bounded fuzz target | Can explain seed corpus and failure minimization at a high level. |
| G-A3 | golden tests | G-F4 | Compare output to a checked-in expected result | Can update golden data deliberately and review diffs. |
| G-A3 | coverage-driven test review | coverage basics | Use coverage to find untested branches | Can add meaningful tests rather than chasing 100 percent mechanically. |
| G-A4 | CPU and memory pprof | G-F11 | Capture or interpret a basic profile | Can choose CPU vs heap profiling for a question. |
| G-A4 | execution trace | G-F9 | Explain when trace is useful | Can choose trace for scheduling, blocking, and latency questions. |
| G-A4 | GC guide and memory pressure | CPU and memory pprof | Read a simple allocation profile and GC concept | Can connect allocation rate to GC cost at a practical level. |
| G-A4 | PGO overview | CPU and memory pprof | Explain profile-guided optimization workflow | Can describe when PGO is worth the operational cost. |
| G-A5 | practical happens-before | G-F9 | Explain ordering in a mutex/channel example | Can connect synchronization to visibility. |
| G-A5 | concurrency patterns: worker pools and pipelines | practical happens-before, G-F7 | Build or review a bounded pipeline | Can explain cancellation, ownership, and backpressure. |
| G-A5 | advanced race detector use | race detector | Use race output to find a shared-state bug | Can identify the conflicting accesses. |
| G-A5 | memory model navigation | practical happens-before | Look up a precise memory model question | Can choose the official memory model for exact rules. |
| G-A6 | `net/http` server handlers | G-F6, G-F8 | Build a small handler | Can separate handler glue from business logic. |
| G-A6 | middleware and routing shape | `net/http` server handlers | Compose one middleware around a handler | Can explain request/response flow. |
| G-A6 | server timeouts and graceful shutdown | `net/http` server handlers, cancellation and timeout | Add timeouts or shutdown with context | Can explain shutdown sequence at a high level. |
| G-A6 | HTTP server tests with `httptest` | `net/http` server handlers, subtests | Test a handler without a live server | Can assert status, headers, and body clearly. |
| G-A7 | `database/sql` connections and context | G-F6, G-F8 | Read or write a small query function | Can pass context and handle query errors. |
| G-A7 | transactions | `database/sql` connections and context | Use begin, commit, and rollback in a small workflow | Can explain rollback on failure. |
| G-A7 | prepared statements and parameters | `database/sql` connections and context | Use query parameters instead of string concatenation | Can explain SQL injection avoidance. |
| G-A7 | repository boundary testing strategy | transactions, dependency injection with interfaces | Decide what to unit test vs integration test | Can explain why real DB behavior often needs integration tests. |
| G-A8 | reflection basics | G-A0, G-A2 | Read or write a tiny `reflect` example | Can explain loss of compile-time type information. |
| G-A8 | code generation with `go generate` | reflection basics | Explain or run a generator in a controlled example | Can distinguish generated code from handwritten API. |
| G-A8 | `unsafe` overview | reflection basics | Identify unsafe pointer boundary in a tiny example | Can explain what checks are bypassed. |
| G-A8 | cgo overview | `unsafe` overview | Read a C boundary sketch | Can describe build, portability, and ownership concerns. |
| G-A9 | advanced constraints and approximation elements | G-F10 | Read a non-trivial constraint | Can explain permitted underlying types at a high level. |
| G-A9 | generic API readability review | advanced constraints and approximation elements | Review a generic API for complexity | Can simplify when constraints obscure intent. |
| G-A9 | `comparable` and map/set API design | `comparable` basics | Design a small set or lookup helper | Can explain equality requirements and tradeoffs. |
| G-A9 | generics compatibility and documentation | generic API readability review | Document type parameter behavior | Can explain constraints to callers clearly. |
| G-A10 | vulnerability checking with `govulncheck` | G-A2 | Run or explain vulnerability scanning | Can distinguish reachable vulnerability reports from dependency presence. |
| G-A10 | release notes and compatibility review | G-A1 | Review an upgrade or release note | Can identify behavior, API, and security risk. |
| G-A10 | dependency and supply-chain hygiene | vulnerability checking with `govulncheck`, module versioning and semantic import versioning | Review dependency changes | Can explain why minimal dependencies reduce maintenance risk. |
| G-A10 | security review checklist | release notes and compatibility review, G-A6 | Review inputs, auth boundaries, secrets, and logging at a high level | Can identify common production risks without overclaiming security. |
| G-A11 | capstone scope and design | G-A0, G-A2 | Select a CLI, web service, or library capstone | Can define scope, milestones, and risk. |
| G-A11 | capstone implementation integration | capstone scope and design | Build across multiple advanced lessons | Can explain major design choices and tradeoffs. |
| G-A11 | capstone tests, docs, and release checks | capstone implementation integration, coverage and `govulncheck` workflow | Add validation appropriate to the project | Can show tests, docs, formatting, vet, and security-check evidence. |
| G-A11 | final review and learning map handoff | capstone tests, docs, and release checks | Summarize mastered topics and follow-up areas | Can identify next independent learning tracks. |
