# Findings Tracker

All documentation gaps, inaccuracies, or issues found across every tutorial validation in this repo. One row per finding. Each row links back to the specific log where it was discovered.

| ID   | Tutorial                                                     | Step                            | Type                                      | Severity | Description                                                                                                                                                                                                                                                                                                                                                                 | Status | Upstream link |
| ---- | ------------------------------------------------------------ | ------------------------------- | ----------------------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | ------------- |
| F001 | [VRF v2.5 Getting Started](logs/VRF_v2-5_Getting_Started.md) | Contract Variables (pre-deploy) | Missing step / underspecified instruction | Minor    | Doc states the tutorial "can run for any supported network" but gives no guidance on which values (coordinator, keyHash, gas limit) to swap or where to find them — reader must independently discover the Supported Networks page and manually map values. No explicit warning that reusing Sepolia's hardcoded coordinator/keyHash on another network will silently fail. | Open   | —             |

---

## Field definitions

- **Type:** Broken link / Stale address / Version mismatch / Missing step / UI drift / Underspecified instruction / Other
- **Severity:** Minor (doesn't block completion, just adds friction) / Moderate (requires outside research to proceed) / Blocking (tutorial cannot be completed as written)
- **Status:** Open / Reported / PR Opened / Fixed / Won't Fix
- **Upstream link:** link to the GitHub issue or PR opened against `smartcontractkit/documentation`, once one exists
