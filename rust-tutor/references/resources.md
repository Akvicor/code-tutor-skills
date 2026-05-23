# Rust Learning Resources

Use external resources as supporting material. Do not paste long copyrighted text. Link or summarize briefly, then teach in your own words.

## Priority Order

1. Official Rust documentation for language behavior and standard library APIs.
2. Exercise-first projects for practice.
3. Community guides for alternate explanations or broader curricula.
4. Style and best-practice resources for review after the learner can write working code.

## Verification Policy

When answering Rust questions, use official Rust documentation first whenever precision matters. Verify against official docs or local toolchain output before answering questions about:

- language rules, especially ownership, borrowing, lifetimes, traits, patterns, macros, unsafe, and FFI;
- standard library APIs, method signatures, trait implementations, and error types;
- Cargo behavior, workspaces, features, profiles, publishing, and build scripts;
- edition behavior and migration steps;
- rustfmt, Clippy, rust-analyzer, rustc flags, and compiler diagnostics;
- async/runtime behavior or crate-version-sensitive APIs;
- installation and toolchain setup.

For stable beginner concepts, it is acceptable to teach directly, but prefer linking the concept to the relevant official resource. If verification cannot be performed, state that limitation and avoid presenting version-sensitive details as certain.

## Core Resources

| Resource | URL | Use |
| --- | --- | --- |
| The Rust Programming Language | https://doc.rust-lang.org/book/ | Primary conceptual reference for the core path. |
| Rust by Example | https://doc.rust-lang.org/rust-by-example/ | Short runnable examples for a topic. |
| Rustlings | https://github.com/rust-lang/rustlings | Small official exercises, useful for practice and review. |
| Rust Standard Library | https://doc.rust-lang.org/std/ | API details for `String`, `Vec`, `HashMap`, IO, threads, etc. |
| Cargo Book | https://doc.rust-lang.org/cargo/ | Cargo workspaces, profiles, features, publishing, and build behavior. |
| rustdoc Book | https://doc.rust-lang.org/rustdoc/ | Documentation comments, doc tests, and API docs. |
| Edition Guide | https://doc.rust-lang.org/edition-guide/ | Edition differences and migration workflow. |
| rustc Book | https://doc.rust-lang.org/rustc/ | Compiler options and diagnostics when needed. |
| Error Index | https://doc.rust-lang.org/error_codes/error-index.html | Detailed explanations for specific compiler errors. |
| Rust Reference | https://doc.rust-lang.org/reference/ | Precise language rules when needed. Avoid leading beginners here. |
| Rustonomicon | https://doc.rust-lang.org/nomicon/ | Advanced unsafe Rust reference. Use as orientation, not as beginner material. |
| Async Book | https://rust-lang.github.io/async-book/ | Async Rust concepts and ecosystem map. |
| 100 Exercises To Learn Rust | https://github.com/mainmatter/100-exercises-to-learn-rust | Structured exercise sequence for longer practice. |
| Comprehensive Rust | https://google.github.io/comprehensive-rust/ | Classroom-style explanations and review material. |
| Rust API Guidelines | https://rust-lang.github.io/api-guidelines/ | API design feedback after traits/modules are introduced. |
| rust-skills | https://github.com/leonardomso/rust-skills | Optional Rust coding checklist and best-practice inspiration. |

## Mapping To Curriculum

- I0-I1: Rust Learn, The Book chapter 1, Cargo basics, Rustlings setup.
- I2-I3: The Book chapters 2 and 3, Rust by Example basics.
- I4-I6: Early deterministic Cargo exercises and Rustlings intro exercises.
- I7: The Book guessing game can be used here after basic diagnostics and `Option`/`Result` preview.
- F0-F2: The Book chapter 4, Rustlings ownership and borrowing exercises.
- F3-F4: The Book chapters 5 and 6.
- F5: The Book chapter 9, Rust by Example error handling.
- F6: The Book chapter 8 and standard library collection docs.
- F7: The Book chapter 7.
- F8: The Book chapter 11.
- F9-F10: The Book chapter 10.
- F11: The Book chapter 13.
- F12-F13: The Book chapter 12 and standard library IO docs.
- A0: The Book chapter 14 and Cargo Book.
- A1: Official rustfmt, Clippy, rust-analyzer, `cargo fix`, and rustc documentation.
- A2: Edition Guide and current edition notes.
- A3: rustdoc Book plus The Book documentation/test examples.
- A4: The Book chapter 15.
- A5: The Book chapter 16.
- A6: The Book async chapter and Async Book; verify current runtime details before teaching.
- A7: The Book chapter 18.
- A8-A10: The Book chapter 20 advanced features plus Rust Reference when precision is needed.
- A11-A12: Rust Reference and Rustonomicon overview for unsafe and FFI boundaries.
- A13: The Book final project plus learner-goal-specific official docs.

## Version-Sensitive Guidance

If the answer depends on a current Rust version, crate version, installation step, or runtime API, verify against official documentation or the local toolchain output before teaching it as fact.
