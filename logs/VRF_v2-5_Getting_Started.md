# Chainlink VRF v2.5 "Getting Started" — Tutorial Validation Log

**Tester:** Harsha Siriki
**Date started:** [2026-07-29]
**Doc page under test:** https://docs.chain.link/vrf/v2-5/getting-started
**Doc source file:** src/content/vrf/v2-5/getting-started.mdx (smartcontractkit/documentation)
**Network:** Base Sepolia Testnet
**Environment:** Remix IDE / MetaMask

**Reference values for Base Sepolia (from docs.chain.link/vrf/v2-5/supported-networks):**

- LINK Token: `0xE4aB69C077896252FAFBD49EFD26B5D171A32410`
- VRF Coordinator: `0x5C210eF41CD1a72de73bF76eC39637bB0d3d7BEE`
- 30 gwei Key Hash: `0x9e1344a1247c8a1785d0a4681a27152bffdb43666ae5bf7d14d24a5efd44bf71`
- Max Gas Limit: 2,500,000
- Minimum Confirmations: 0

**Purpose:** Reproduce this tutorial end-to-end as a first-time reader would, to confirm every step, code sample, address, and external link is accurate and current.

**Findings from this run:** see [`FINDINGS.md`](../FINDINGS.md) — findings are tracked centrally, not duplicated here. This log only records what happened at each step.

---

## Environment Setup

| Item                                    | Value / Status                                                                                                                                                        |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wallet address used                     | `0xfA498F339d311f5b6f8A79c5459F8dE2BABd36e5`                                                                                                                          |
| Testnet ETH source                      | faucets.chain.link/base-sepolia — ❌ Failed (blocked by mainnet LINK requirement, see F002). ✅ Obtained instead via Coinbase Developer Platform Faucet (0.0001 ETH). |
| Testnet LINK source                     | faucets.chain.link/base-sepolia — ✅ Success, 25 LINK. [Tx](https://sepolia.basescan.org/tx/0xc2a42fb4d5fb2a7a474421a2a5d6e2b29e864277c6073eb1f9a52919d2a075c0)       |
| Subscription ID created                 | — (pending: need ETH for gas first)                                                                                                                                   |
| Solidity compiler version used in Remix | — (not yet reached)                                                                                                                                                   |

---

## Step-by-Step Log

For each step: record what the doc says, what you actually did, and the result. Flag anything that didn't match. If a step produces a finding, note the Finding ID (from FINDINGS.md) here rather than describing it in full.

### Step 1 — Create and fund a subscription

- **Doc says:** Fund your wallet with testnet ETH and LINK via faucets.chain.link, then create/fund a subscription.
- **What I did:** Requested Base Sepolia ETH + LINK drip from faucets.chain.link/base-sepolia. LINK succeeded; ETH failed (see F002). Obtained 0.0001 Base Sepolia ETH via the Coinbase Developer Platform Faucet as a workaround.
- **Result:** ⚠️ Partial mismatch, now resolved via workaround — LINK drip succeeded (25 testnet LINK, [tx](https://sepolia.basescan.org/tx/0xc2a42fb4d5fb2a7a474421a2a5d6e2b29e864277c6073eb1f9a52919d2a075c0)). ETH drip **failed** on Chainlink's faucet: "You must hold at least 1 LINK on Ethereum Mainnet to request native tokens." Unblocked via Coinbase Developer Platform Faucet: 0.0001 ETH received, confirmed Success ([tx](https://sepolia.basescan.org/tx/0x847c5e1e103cd1fb16d033d7bb88ce3939a81dc40d086a62a599970f25a1bcb8)).
- **Finding ID (if any):** F002
- **Timestamp:** 2026-07-30 02:19:40 UTC (CDP faucet ETH claim, confirmed on-chain)

### Step 2 — Open VRFD20.sol in Remix

- **Doc says:** Open the contract via the provided Remix link; code should compile as-is for Sepolia.
- **What I did:** Opened VRFD20.sol, reviewed the full source. Verified `@chainlink/contracts@1.5.0` import pin against npm/GitHub — confirmed current (latest published version, and the exact version pinned in the docs repo's own version-overrides.json for tutorial samples).
- **Result:** ✅ Import/version pin matched doc and current registry — no drift found. ⚠️ Contract ships with Ethereum Sepolia's `vrfCoordinator` and `s_keyHash` hardcoded, requiring manual edit to Base Sepolia values before compiling (expected per doc's own comment/guidance, not a bug — but a real trap for a first-time reader deploying to a non-Sepolia network, since the constructor bakes `vrfCoordinator` in at compile time).
- **Finding ID (if any):** None — verified clean on both counts.
- **Timestamp:**

### Step 3 — Deploy with subscription ID

- **Doc says:**
- **What I did:**
- **Result:**
- **Finding ID (if any):**
- **Timestamp:**

### Step 4 — Add deployed contract as approved consumer

- **Doc says:**
- **What I did:**
- **Result:**
- **Finding ID (if any):**
- **Timestamp:**

### Step 5 — Call `rollDice`

- **Doc says:**
- **What I did:**
- **Result:** (transaction hash, gas used, any revert reason)
- **Finding ID (if any):**
- **Timestamp:**

### Step 6 — Call `house`

- **Doc says:**
- **What I did:**
- **Result:**
- **Finding ID (if any):**
- **Timestamp:**

---

## Appendix

![Faucet drip results — ETH failed, LINK succeeded](../screenshots/vrf-v2-5-getting-started/F002-faucet-drip-results.png)
\*Screenshot from Step 1: Base Sepolia ETH drip failed (mainnet LINK requirement, see F002); LINK drip succeeded (25 LINK, [tx](https://sepolia.basescan.org/tx/0xc2a42fb4d5fb2a7a474421a2a5d6e2b29e864277c6073eb1f9a52919d2a075c0)).
