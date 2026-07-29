# Chainlink Docs Validation

Independent, hands-on validation of Chainlink developer documentation tutorials — reproducing each guide end-to-end as a first-time reader would, and logging exactly what matches, what doesn't, and why.

## Why this exists

Documentation that looks correct on the page doesn't always hold up when you actually follow it — versions drift, external UIs change, steps assume context the reader doesn't have. This repo is a record of me running Chainlink's tutorials step by step, on live testnets, and documenting the process transparently: what the doc says, what I actually did, and the result.

## Scope

| Tutorial | Doc source | Status |
|---|---|---|
| [Getting Started with Chainlink VRF v2.5](https://docs.chain.link/vrf/v2-5/getting-started) | [smartcontractkit/documentation](https://github.com/smartcontractkit/documentation) | In progress |

More tutorials may be added over time.

## How to read the logs

Each tutorial has its own validation log (e.g. `VRF_Tutorial_Validation_Log.md`) with:
- **Environment Setup** — network, wallet, subscription details used for the run
- **Step-by-Step Log** — what the doc instructs vs. what actually happened at each step, with timestamps
- **Findings Summary** — a table of anything that didn't match: broken links, stale addresses, version mismatches, missing instructions, or UI drift
- **Follow-Up Actions** — links to any issues or PRs opened against Chainlink's documentation repo as a result

## Contributing findings upstream

Where a genuine gap or inaccuracy is found, it's reported or fixed directly against Chainlink's own docs repository, following their [Contributing guide](https://github.com/smartcontractkit/documentation/blob/main/CONTRIBUTING.md), rather than just noted here. Links to any resulting issues/PRs are included in the relevant log's Follow-Up Actions section.

## About

Maintained by Harsha Siriki as part of hands-on Web3 documentation practice.
- [GitHub](https://github.com/HarshaSiriki)
- [Medium](https://medium.com/@harsha.siriki)
