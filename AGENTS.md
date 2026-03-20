<!-- Maintenance: Update when tasks, hooks, or project scope changes. -->
<!-- Audience: All docs under docs/ and this file are written for coding agents (LLMs), not humans. Use direct instructions, not tutorials or explanations of concepts the agent already knows. Apply this rule when creating or updating any documentation. -->

## Build, Test, and Development Commands

- Use Task ([Taskfile.yml](Taskfile.yml)) as the default interface; run `task` to list all tasks, `task --summary <name>` for details
- `task build` / `task test` / `task lint` / `task fmt` / `task check` — primary workflow; `task check` runs formatting check, Clippy, tests, `cargo doc`, and build (see [docs/tooling.md](docs/tooling.md))
- Rust-native equivalents work without Task: `cargo build`, `cargo test`, `cargo fmt --all`, `cargo clippy --workspace --all-targets --all-features --locked -- -D warnings` (same as `task lint`; Clippy levels from `Cargo.toml` `[lints]`, thresholds from `clippy.toml`, groups from crate attributes in `src/main.rs`)
- Prefer `cargo add` / editing `Cargo.toml` for dependencies; run `cargo build` or `task build` after manifest changes
- Toolchain is pinned via [rust-toolchain.toml](rust-toolchain.toml): **nightly** with `rustfmt` and `clippy` so [rustfmt.toml](rustfmt.toml) can use unstable formatting options

## Git Conventions

- When asked to commit without a specific format, follow Conventional Commits: `<type>(<scope>): <imperative summary>`
- Never use `--no-verify` when committing or pushing; fix the underlying hook failure instead

## Documentation Scope

- Keep this file limited to always-on repository rules.
- Read `docs/coding.md` before writing or modifying any Rust code.
- Read `docs/testing.md` before writing or modifying tests.
- Read `docs/tooling.md` when working with build, CI, hooks, or adding tools.
- Read `docs/review.md` when performing code review.
- Read `docs/adr/` only when historical rationale matters.
