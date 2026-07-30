# Chainlink Docs Validation

Independent, hands-on validation of Chainlink developer documentation tutorials — reproducing each guide end-to-end as a first-time reader would, and logging exactly what matches, what doesn't, and why.

## Why this exists

Documentation that looks correct on the page doesn't always hold up when you actually follow it — versions drift, external UIs change, steps assume context the reader doesn't have. This repo is a record of me running Chainlink's tutorials step by step, on live testnets, and documenting the process transparently: what the doc says, what I actually did, and the result.

## Scope

| Tutorial                                                                                    | Doc source                                                                          | Status    |
| ------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | --------- |
| [Getting Started with Chainlink VRF v2.5](https://docs.chain.link/vrf/v2-5/getting-started) | [smartcontractkit/documentation](https://github.com/smartcontractkit/documentation) | Completed |

More tutorials may be added over time.

## Highlights

Validating the VRF v2.5 Getting Started guide surfaced a real, reproducible gap: Chainlink's own testnet faucet silently blocks the ETH drip for users with no LINK held on Ethereum Mainnet, with no warning in the tutorial or on the faucet page. Filed as [smartcontractkit/documentation#4011](https://github.com/smartcontractkit/documentation/issues/4011). Full evidence in [`FINDINGS.md`](FINDINGS.md).

## How to read this repo

- **[`FINDINGS.md`](FINDINGS.md)** — the master tracker. Every documentation gap, inaccuracy, or issue found across all tutorials, in one table, regardless of which tutorial it came from.
- **`logs/`** — one file per tutorial, containing the environment setup and step-by-step walkthrough (what the doc says vs. what actually happened, with timestamps). Each step links to a Finding ID in `FINDINGS.md` if it produced one.

Example: `logs/VRF_v2-5_Getting_Started.md` documents the full run of the [VRF v2.5 Getting Started guide](https://docs.chain.link/vrf/v2-5/getting-started); any issues it turned up are recorded as F001, F002, etc. in `FINDINGS.md`.

## Contributing findings upstream

Where a genuine gap or inaccuracy is found, it's reported or fixed directly against Chainlink's own docs repository, following their [Contributing guide](https://github.com/smartcontractkit/documentation/blob/main/CONTRIBUTING.md), rather than just noted here. Links to any resulting issues/PRs are tracked in the **Upstream link** column of [`FINDINGS.md`](FINDINGS.md).

## About

Maintained by Harsha Siriki as part of hands-on Web3 documentation practice.

- [GitHub](https://github.com/HarshaSiriki)
- [Medium](https://medium.com/@harsha.siriki)
