# Status

Last reviewed: 2026-11-20 (github-audit pass 02, documentation only; no code was run).

## What works

- Nothing has been verified in this pass.
- The code is short and complete: a constructor with API key checking, and `getNewInvoice` with Unauthorized handling and arbitrary JSON `data`.

## What's broken or unknown

- Not tested against the current BitPay API. The endpoint `https://bitpay.com/api/invoice` and basic-auth key style date from 2014 and may no longer be accepted. **(inference)**
- `mocha` is used by `npm test` but is not in `devDependencies`.
- The single test never calls `done` on an error, so it would time out instead of failing clearly.
- The currency is hard-coded to `BTC` and the invoice price is sent as given.
- `package.json` has an empty `author`.

## What's next

Nothing planned. If revived: check the BitPay API version, add `mocha` as a dev dependency, mock the HTTP call in tests, and make the currency an option.

## Not yet from the standard

- CONTRIBUTING.md
- SECURITY.md
- `.editorconfig`
- `.github` issue and PR templates
- Dependabot
- `ci.yml` with gitleaks
- master to main rename
- CloudEvents catalog
- Product one-pager
