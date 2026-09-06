# alphagov/accessible-autocomplete context
> refreshed 2026-09-06 | upstream default: main @ fb3e243

## Identity & policies
- upstream: alphagov/accessible-autocomplete, default branch main, primary language JavaScript (Preact), English-first (yes)
- CLA/DCO: none (CONTRIBUTING has no CLA/DCO requirement)
- AI-assisted PR policy: unstated (no AI mention in CONTRIBUTING)
- signed commits required: no
- PR template: none (repo .github has no PR template; org alphagov/.github has none either) -> pipeline fallback body
- external tracker: github

## Conventions (verified from merged PRs)
- branch naming: mixed; recent merged PRs use descriptive kebab (fix-html-injection-ajax-example, fix-chrome-headless-ci, add-netlify-redirect-for-examples)
- commit style: plain imperative, no conventional-commit prefix
- test command: `npm test` (standard lint + karma browser tests + wdio webdriver tests); CI runs build + karma + standard + check-staged + wdio
- CI: GitHub Actions (test.yaml, integration_tests.yaml, saucelabs.yaml). saucelabs only runs for same-repo PRs (not forks). test.yaml + integration_tests.yaml run on forks.
- maintainers: owenatgov, romaricpascal, NickColley, domoscargin, selfthinker, edwardhorsford, tvararu, querkmachine
- repo mostly dormant: last merged PR Dec 2025 (#784, #780); before that Dec 2024. Many open PRs from 2024-2025 unmerged.

## Maintainer picture
- active maintainers: owenatgov, romaricpascal (recent committers)
- response latency: slow; issues get maintainer comments but fixes rarely merged quickly

## Issue-area health
- Many open issues (179). Most are complex a11y/design discussions or feature requests.
- Maintainer-engaged issues reviewed: #790 (ARIA discussion), #789 (focus overflow, needs a11y input), #781 (Chrome CI, already fixed by merged #784), #718 (iPhone tap-out, no solution), #605 (Dragon, hard to test), #587/#586/#432/#472 (design questions), #495 (defaultValue regression, complex), #466 (docs correct), #498 (complex a11y).
- No clearly-actionable small maintainer-engaged issue survives -> run repo-audit matrix.

## Gap ledger (dedupe — READ FIRST, never re-pick)
- (empty on first refresh)

## Mined gaps (discovered, not yet attempted)
- (to be filled by repo-audit)
