# AGENTS.md

Guidance for AI agents working in this repo. Humans: see [README.md](README.md).

## What this is

`bitpay-invoice-generator` 0.1.2: one class that creates BitPay invoices. Three commits, all on 2014-12-16. Dormant.

## Stack

- Plain JavaScript (ES5), CommonJS, no build step.
- Runtime dependencies: bluebird ^2.3.11, superagent ^0.21.0.
- Tests: mocha (invoked as `mocha`, but not listed in `package.json`, so it must be installed separately).
- Era-appropriate runtime is Node 0.10 **(inference)**.

## Layout

- `index.js` the whole library
- `test/invoice_generator.js` one spec that calls the live BitPay API
- `docs/STATUS.md` current state of the repo

## Commands

- Install: `npm install`
- Test: `npm test` runs `mocha -R spec test/`. It needs a real `BITPAY_API_KEY` in the environment and network access, and the test never fails cleanly without them. Not verified on a current toolchain.

## Rules

- Add or update tests with every change.
- Never commit secrets (API keys included). Use environment variable names only.
- Use Conventional Commits.
- Keep `docs/STATUS.md` current.

## Agents may and may not

- May: improve docs, add tests, open PRs on a branch.
- May not: archive the repo, publish to npm, rewrite git history, or call the live BitPay API with Steven's credentials, without Steven.
