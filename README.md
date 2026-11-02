# papers-rs

Rust crates of the papers family:

- [`papers-rs`](crates/papers-rs): a Rust port of
  [papers-cli](https://github.com/perrette/papers), the library. papers-cli is
  the reference: papers-rs does what it does, with the same output and the
  same files, so that both work on the same libraries and the same history.
- [`papers-rs-cli`](crates/papers-rs-cli): its command line, `papers-rs`.
- [`latexenc-rs`](crates/latexenc-rs) (library `latexenc`): a port of
  pylatexenc 2.11: the LaTeX parser, LaTeX to text, Unicode to LaTeX.

Used by [Papers Desktop](https://github.com/mathesislab/papers-desktop) and
[papers-review](https://github.com/mathesislab/papers-review). The crates
were developed in papers-desktop and left it with their history.

## Use

```toml
[dependencies]
papers-rs = { git = "https://github.com/mathesislab/papers-rs" }
latexenc-rs = { git = "https://github.com/mathesislab/papers-rs" }
```

`Cargo.lock` pins the commit; `cargo update -p papers-rs` takes the latest.

## The conformance suite

The suite is in papers itself (`design/cases`); `spec/papers` is a git
submodule of perrette/papers, pinned at the commit papers-rs follows. See
[spec/README.md](spec/README.md).

```bash
git submodule update --init spec/papers
cargo build -p papers-rs-cli
python3 spec/papers/design/cases/run.py --papers target/debug/papers-rs --contract-only
```

## Develop

```bash
cargo test --workspace
cargo clippy --workspace --all-targets -- -D warnings
```

## License

MIT. `papers-rs` and `papers-rs-cli` keep the copyright of papers-cli
(Mahé Perrette).
