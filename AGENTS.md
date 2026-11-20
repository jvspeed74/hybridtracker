## Commands

| Purpose                                                   | Command                                                               |
|-----------------------------------------------------------|-----------------------------------------------------------------------|
| Build                                                     | `cargo build --workspace`                                             |
| Test                                                      | `cargo test --workspace`                                              |
| Count the `todo!()` sites left, in library code and tests | `cargo clippy --workspace --tests -- -W clippy::todo`                 |
| Run only the scaffolded tests                             | `cargo test --workspace -- --ignored`                                 |
| Format check                                              | `cargo fmt --all --check`                                             |
| Lint, with warnings denied                                | `cargo clippy --workspace --all-targets --locked -- -D warnings`      |
| Documentation build, with warnings denied                 | `RUSTDOCFLAGS="-D warnings" cargo doc --workspace --no-deps --locked` |
| Enable the pre-commit hook, once per clone                | `git config core.hooksPath .githooks`                                 |

---

## Commits and pull requests

**Pull requests.**

- Never commit to `main`. Every change reaches it through a pull request.
- The body follows [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md), with its sections in order.
  `gh pr create --body` does not apply the template.
- Pull requests are squash-merged, so the pull request title becomes the commit on `main`. Write the title as a commit
  message, in the format below.

**Commit messages** follow [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/):

    <type>(<scope>): <description>

| Type       | Reach for it when                                                                      |
|------------|----------------------------------------------------------------------------------------|
| `feat`     | The change adds behavior the specification requires that did not exist before.         |
| `fix`      | The change corrects defective behavior (i.e., a bug).                                  |
| `refactor` | The change restructures code without altering user-facing behavior.                    |
| `test`     | The change adds or corrects tests only.                                                |
| `docs`     | The change touches documentation or comments only.                                     |
| `build`    | The change affects `Cargo.toml`, dependencies, the toolchain, or the workspace layout. |
| `chore`    | The change is maintenance that fits no other type (e.g., `.gitignore`, tooling).       |
| `perf`     | The change improves a measured resource cost without user-facing observable behavior.  |
| `style`    | The change alters formatting only, such as `cargo fmt` output.                         |
| `ci`       | The change touches continuous-integration configuration only.                          |

- **Breaking change:** put `!` after the scope and add a `BREAKING CHANGE:` footer.
