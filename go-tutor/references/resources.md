# Go Learning Resources

Use external resources as supporting material. Do not paste long copyrighted text. Link or summarize briefly, then teach in your own words.

## Priority Order

1. Official Go documentation for language behavior, standard library APIs, modules, tooling, runtime behavior, and security guidance.
2. Exercise-first projects for practice.
3. Community example collections for alternate explanations or drills.
4. Style and best-practice resources for review after the learner can write working code.

## Verification Policy

When answering Go questions, use official Go documentation first whenever precision matters. Verify against official docs or local toolchain output before answering questions about:

- language rules, especially packages, declarations, method sets, interfaces, generics, memory model, `unsafe`, and `cgo`;
- standard library APIs, method signatures, error behavior, context behavior, HTTP, IO, JSON, files, testing, and database APIs;
- module behavior, workspaces, semantic import versioning, publishing, and dependency resolution;
- Go version features and release-note-sensitive behavior;
- `gofmt`, `go vet`, `gopls`, `go doc`, coverage, fuzzing, race detector, and `govulncheck`;
- runtime behavior, profiling, tracing, GC, PGO, scheduling, and concurrency;
- installation and toolchain setup.

For stable beginner concepts, it is acceptable to teach directly, but prefer linking the concept to the relevant official resource. If verification cannot be performed, state that limitation and avoid presenting version-sensitive details as certain.

## Core Resources

| Resource | URL | Use |
| --- | --- | --- |
| Go Documentation | https://go.dev/doc/ | Primary official documentation hub. |
| Go Learn | https://go.dev/learn/ | Official learning entry point for new Go programmers. |
| Go Tutorials | https://go.dev/doc/tutorial/ | Official tutorials for modules, fuzzing, workspaces, vulnerability checks, and common tasks. |
| A Tour of Go | https://go.dev/tour/ | Interactive official intro for syntax, methods, interfaces, and concurrency. |
| Effective Go | https://go.dev/doc/effective_go | Idiomatic naming, formatting, control flow, errors, methods, interfaces, and concurrency guidance. |
| Go Specification | https://go.dev/ref/spec | Precise language rules when needed. Avoid leading beginners here. |
| Go Memory Model | https://go.dev/ref/mem | Precise concurrency memory model rules. Use for advanced concurrency review. |
| Go Modules Reference | https://go.dev/ref/mod | Module, versioning, workspace, and dependency behavior. |
| Standard Library | https://pkg.go.dev/std | API details for `fmt`, `errors`, `io`, `os`, `encoding/json`, `net/http`, `testing`, `sync`, and more. |
| Go Command | https://pkg.go.dev/cmd/go | Tool behavior for `go test`, `go run`, `go build`, modules, coverage, and workspaces. |
| Diagnostics | https://go.dev/doc/diagnostics | Official map for profiling, tracing, execution traces, GC, and related diagnostics. |
| Race Detector | https://go.dev/doc/articles/race_detector | Official guidance for detecting data races. |
| Learn Go with Tests | https://github.com/quii/learn-go-with-tests | Test-first exercise inspiration for beginner and foundations lessons. |
| Go by Example | https://github.com/mmcgrana/gobyexample | Short example inspiration for syntax and standard library drills. |
| Learn Go | https://github.com/inancgumus/learngo | Example and exercise inspiration for structured practice. |
| Exercism Go Track | https://github.com/exercism/go | Practice ideas and review prompts for targeted exercises. |

## Mapping To Curriculum

- G-I0 to G-I1: Go Learn, Go Tutorials, `go version`, `go env`, modules tutorial, and Go command docs.
- G-I2 to G-I4: A Tour of Go, Effective Go basics, and small examples from Go by Example.
- G-I5: `testing` package docs, Learn Go with Tests, and table-driven test examples.
- G-I6: Effective Go error guidance, `errors` and `fmt` package docs, and compiler output from local `go test`.
- G-I7: Dependency-free CLI or text utility inspired by Go Tutorials and Learn Go with Tests.
- G-F0: A Tour of Go methods and pointers, Effective Go methods section.
- G-F1: A Tour of Go interfaces and Effective Go interfaces section.
- G-F2: Official `errors` package docs and Effective Go error guidance.
- G-F3: Go Modules Reference, Go Tutorials, and Effective Go package naming guidance.
- G-F4: `testing` package docs, Go command test flags, examples, benchmarks, and coverage.
- G-F5: Standard library `io`, `bytes`, `strings`, `os`, and dependency injection examples from Learn Go with Tests.
- G-F6: Standard library `os`, `encoding/json`, `net/http`, `context`, and errors.
- G-F7 to G-F9: A Tour of Go concurrency, Effective Go concurrency, `sync`, `context`, Race Detector, and Go Memory Model.
- G-F10: Go Specification type parameters and standard library examples using generics.
- G-F11: Combine official docs and exercise-first resources into a tested CLI, client, or library.
- G-A0: Effective Go and official package documentation conventions.
- G-A1: Go Modules Reference and workspace tutorial.
- G-A2: Go command docs, `gofmt`, `go vet`, `gopls`, coverage, and vulnerability tutorials.
- G-A3: Fuzzing tutorial, `testing` package docs, benchmarks, and coverage docs.
- G-A4: Diagnostics docs, pprof, trace, GC guide, and PGO docs.
- G-A5: Go Memory Model, Race Detector, and official concurrency guidance.
- G-A6: Standard library `net/http`, `context`, `httptest`, and server shutdown docs.
- G-A7: Standard library `database/sql` docs and security guidance for parameterized queries.
- G-A8 to G-A9: Go Specification, `reflect`, `go generate`, `unsafe`, `cgo`, and generics docs.
- G-A10: Vulnerability checking tutorial, release notes, compatibility guidance, and module docs.
- G-A11: Learner-goal-specific official docs plus focused project review.

## Version-Sensitive Guidance

If the answer depends on a current Go version, module behavior, installation step, tooling output, runtime behavior, or API detail, verify against official documentation or the local toolchain output before teaching it as fact.
