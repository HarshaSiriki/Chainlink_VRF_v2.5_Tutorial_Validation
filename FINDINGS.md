# Findings Tracker

All documentation gaps, inaccuracies, or issues found across every tutorial validation in this repo. One row per finding. Each row links back to the specific log where it was discovered.

| ID   | Tutorial                                                     | Step                            | Type                                                    | Severity      | Description                                                                                                                                                                                                                                                                                                               | Status                          | Upstream link |
| ---- | ------------------------------------------------------------ | ------------------------------- | ------------------------------------------------------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- | ------------- |
| F001 | [VRF v2.5 Getting Started](logs/VRF_v2-5_Getting_Started.md) | Contract Variables (pre-deploy) | ~~Missing step / underspecified instruction~~ Retracted | ~~Minor~~ N/A | ~~Doc gives no guidance on which values to swap for other networks.~~ **Retracted on verification:** the page explicitly states "For a full reference of the addresses, key hashes and fees for each network, see VRF Supported Networks," directly linking to the correct page. Initial read of the page was incomplete. | Retracted — not a valid finding | —             |

---

## Field definitions

- **Type:** Broken link / Stale address / Version mismatch / Missing step / UI drift / Underspecified instruction / Other
- **Severity:** Minor (doesn't block completion, just adds friction) / Moderate (requires outside research to proceed) / Blocking (tutorial cannot be completed as written)
- **Status:** Open / Reported / PR Opened / Fixed / Won't Fix
- **Upstream link:** link to the GitHub issue or PR opened against `smartcontractkit/documentation`, once one exists
