# Agent instructions

Read [README.md](README.md) and [CONTRIBUTING.md](CONTRIBUTING.md) before working here; they define this repository's ownership, build, and validation rules.

## ATTMonk fork

- Commits are `attmonk-ci` (email configured locally or with `ATTMONK_CI_EMAIL`) with no co-author trailers or AI attribution; that overrides the pull request disclosure rule below.
- Pushes, tags and releases go through the `attmonk-ci` GitHub App, never a personal login.
- Commit messages are [Conventional Commits](https://www.conventionalcommits.org): every push to `main` releases automatically when it carries a `feat`, `fix`, `perf`, `revert` or breaking commit. See `RELEASING.md` in [attmonk/silo-plugins](https://github.com/attmonk/silo-plugins). Never push to `upstream` (Silo-Server).
- Keep the plugin ID `silo.attmonk.trakt`. The Silo host refuses `silo.watchprovider.trakt`.

## Writing

Give human-facing prose a final readability pass. Lead with the outcome, use concrete plain language and active voice, and cut filler, stock framing, repetition, and promotional claims. Preserve meaning, evidence, citations, uncertainty, and established terminology. Never rewrite exact quotations, commands, logs, identifiers, API names, or contractual language. Match the audience and use restrained formatting.

## Pull requests

- Never create a pull request unless the developer explicitly asks.
- Use a plain-language Conventional Commit title. In the body, explain the problem before the solution and end with the required AI disclosure, naming the exact model, harness, and tooling used.
- Keep one concern per pull request. If the description needs the word "also" for another change, split it.
- When babysitting a pull request, poll for checks and comments newer than the last push. Verify bot findings against the source, fix real issues, and dismiss false positives with a written reason. Stay quiet when nothing is new, and stop when the latest commit is green.

## ATTMonk CI identity

The organization is `attmonk`. Commits use `attmonk-ci` (email configured locally or with `ATTMONK_CI_EMAIL`);
Git config and the commit hook enforce that identity. The GitHub App keeps ID
5324952 and uses `~/.config/attmonk-github-app/gh`; the old helper path is an
alias for active sessions. Its public identity is `attmonk-ci[bot]`. Keep the existing
App ID, installation, and private key. Workflows require `ATTMONK_CI_APP_KEY`.

Source defaults use ATTMonk identifiers. Existing installations must migrate storage and plugin records together; encrypted stores can retain their derivation context in server environment settings.

## ATTMonk bot attribution and clean history

Use `attmonk-ci <342793482+attmonk-ci[bot]@users.noreply.github.com>` for both
author and committer. Set `attmonk.requireBotAttribution=true` in this checkout
and keep the commit guard enabled. Use Conventional Commits and no co-author
trailers. Pushes, tags, workflow runs and releases use the existing ATTMonk
GitHub App; CI credentials accept `ATTMONK_CI_APPKEY` or `ATTMONK_CI_APP_KEY`.

Keep history limited to clean ATTMonk snapshots and subsequent reviewed work.
Do not merge or push retired histories, branches or tags. Import upstream work
through reviewed patches or source snapshots so retired ancestry is not restored.
Legacy deployment compatibility values belong in local/server environment
configuration, never tracked source. Preserve runtime identities and storage
together when migrating existing installations.
