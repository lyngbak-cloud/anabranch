# How to contribute

Howdy! Usual good software engineering practices apply. Write
tests. Write comments. Follow standard Rust coding practices where
possible. Use `cargo fmt` and `cargo clippy` to tidy up formatting.

There are soft spots in the code, which could use cleanup,
refactoring, additional comments, and so forth. Let's try to raise the
bar, and clean things up as we go. Try to leave code in a better shape
than it was before.

## Pre-commit hook

We have a sample pre-commit hook in `pre-commit.py`.
To set it up, run:

```bash
ln -s ../../pre-commit.py .git/hooks/pre-commit
```

This will run following checks on staged files before each commit:
- `rustfmt`
- checks for Python files, see [obligatory checks](/docs/sourcetree.md#obligatory-checks).

There is also a separate script `./run_clippy.sh` that runs `cargo clippy` on the whole project
and `./scripts/reformat` that runs all formatting tools to ensure the project is up to date.

If you want to skip the hook, run `git commit` with `--no-verify` option.

## Submitting changes

1. Get at least one +1 on your PR before you push.

   For simple patches, it will only take a minute for someone to review
it.

2. Don't force push small changes after making the PR ready for review.
Doing so will force readers to re-read your entire PR, which will delay
the review process.

3. Always keep the CI green.

   Do not push, if the CI failed on your PR. Even if you think it's not
your patch's fault. Help to fix the root cause if something else has
broken the CI, before pushing.

*Happy Hacking!*

## Sign-off

Every commit carries a Developer Certificate of Origin sign-off, added with
`git commit -s`, which certifies the terms at https://developercertificate.org.
Pull requests with unsigned commits are not merged.

## Upstream

Anabranch continues neondatabase/neon. A fix that applies to the upstream tree
is also sent there as a pull request, and upstream commits that apply here are
cherry-picked with their authorship intact.

## Continuous integration

Pull requests run the Rust checks and tests in `.github/workflows/rust.yml`.
Image builds run on `main` and on tags. A maintainer approves the first
workflow run of a new contributor.
