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

| Item                                    | Value / Status                                |
| --------------------------------------- | --------------------------------------------- |
| Wallet address used                     |                                               |
| Testnet ETH source                      | faucets.chain.link/base-sepolia — worked? Y/N |
| Testnet LINK source                     | faucets.chain.link/base-sepolia — worked? Y/N |
| Subscription ID created                 |                                               |
| Solidity compiler version used in Remix |                                               |

---

## Step-by-Step Log

For each step: record what the doc says, what you actually did, and the result. Flag anything that didn't match. If a step produces a finding, note the Finding ID (from FINDINGS.md) here rather than describing it in full.

### Step 1 — Create and fund a subscription

- **Doc says:** [paraphrase the instruction]
- **What I did:**
- **Result:** ✅ Matched doc / ⚠️ Partial mismatch / ❌ Broken
- **Finding ID (if any):**
- **Timestamp:**

### Step 2 — Open VRFD20.sol in Remix

- **Doc says:**
- **What I did:**
- **Result:**
- **Finding ID (if any):**
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

(Screenshots, full error text, transaction hashes, block explorer links)
