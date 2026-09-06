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
- #229 (onConfirm selected value is undefined on blur, 🐛 bug, open since 2017) IS a clearly-actionable small maintainer-engaged bug: edwardhorsford commented "onConfirm shouldn't be undefined." Picked this cycle.

## Gap ledger (dedupe — READ FIRST, never re-pick)
- 2026-09-06 issue #229 (onConfirm(undefined) on blur when no option selected) — pr-opened — fix: guard onConfirm in handleComponentBlur to only fire when a valid option is selected (selected !== null && selected >= 0). Deduped: no open/closed/merged upstream PR covers #229 / onConfirm-blur / undefined. lukekarrys' fork commit 5594661 (never merged) is a related but different approach (only run onConfirm if no query or new query). Verified live on upstream main fb3e243: handleComponentBlur calls onConfirm(options[selected]) with selected=-1/null -> onConfirm(undefined). Repro via Node script (bug present before, gone after; positive cases preserved). Lint (standard) clean. Local karma cannot run in this aarch64 env (puppeteer Chrome is x86_64, no root to install arm64) -> fork CI runs the suite.

## Mined gaps (discovered, not yet attempted)
- 2026-09-06 clean-code handleSpace inconsistency: when showAllValues + menu closed + empty query, space opens the menu but does not set selected:0/focused:0 (handleDownArrow does). Repro: press space with empty query + showAllValues -> menu opens, no option focused, second space does nothing. Not deduped yet. status: proposed
- 2026-09-06 clean-code double event.preventDefault() in handleDownArrow (~line 320) — cosmetic, not worth a PR alone. status: dropped(cosmetic)
- 2026-09-06 a11y HTML attribute errors (#790): role="combobox" on input is valid ARIA 1.2; aria-expanded on input is questionable — verify against spec before pursuing. status: proposed
