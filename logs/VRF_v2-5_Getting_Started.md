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
| Subscription ID created                 | `24963885066942085575241868055782773595381668348941839345025195320832983598589` (not yet funded)                                                                      |
| Solidity compiler version used in Remix | — (not yet reached)                                                                                                                                                   |

---

## Step-by-Step Log

For each step: record what the doc says, what you actually did, and the result. Flag anything that didn't match. If a step produces a finding, note the Finding ID (from FINDINGS.md) here rather than describing it in full.

### Step 1 — Create and fund a subscription

- **Doc says:** Fund your wallet with testnet ETH and LINK via faucets.chain.link, then create/fund a subscription.
- **What I did:** Requested Base Sepolia ETH + LINK drip from faucets.chain.link/base-sepolia. LINK succeeded; ETH failed (see F002). Obtained 0.0001 Base Sepolia ETH via the Coinbase Developer Platform Faucet as a workaround. Created a VRF subscription via vrf.chain.link (Base Sepolia).
- **Result:** ⚠️ Partial mismatch, now resolved via workaround — LINK drip succeeded (25 testnet LINK, [tx](https://sepolia.basescan.org/tx/0xc2a42fb4d5fb2a7a474421a2a5d6e2b29e864277c6073eb1f9a52919d2a075c0)). ETH drip **failed** on Chainlink's faucet: "You must hold at least 1 LINK on Ethereum Mainnet to request native tokens." Unblocked via Coinbase Developer Platform Faucet: 0.0001 ETH received, confirmed Success ([tx](https://sepolia.basescan.org/tx/0x847c5e1e103cd1fb16d033d7bb88ce3939a81dc40d086a62a599970f25a1bcb8)). Subscription created successfully: `24963885066942085575241868055782773595381668348941839345025195320832983598589`. **Not yet funded with LINK** — pending.
- **Finding ID (if any):** F002
- **Timestamp:** 2026-07-30 02:19:40 UTC (CDP faucet ETH claim, confirmed on-chain)

### Step 2 — Open VRFD20.sol in Remix

- **Doc says:** Open the contract via the provided Remix link; code should compile as-is for Sepolia.
- **What I did:** Opened VRFD20.sol, reviewed the full source. Verified `@chainlink/contracts@1.5.0` import pin against npm/GitHub — confirmed current (latest published version, and the exact version pinned in the docs repo's own version-overrides.json for tutorial samples).
- **Result:** ✅ Import/version pin matched doc and current registry — no drift found. ⚠️ Contract ships with Ethereum Sepolia's `vrfCoordinator` and `s_keyHash` hardcoded, requiring manual edit to Base Sepolia values before compiling (expected per doc's own comment/guidance, not a bug — but a real trap for a first-time reader deploying to a non-Sepolia network, since the constructor bakes `vrfCoordinator` in at compile time).
- **Finding ID (if any):** None — verified clean on both counts.
- **Timestamp:**

### Step 3 — Deploy with subscription ID

- **Doc says:** Compile VRFD20.sol, deploy passing your subscription ID to the constructor.
- **What I did:** Edited `vrfCoordinator` and `s_keyHash` to Base Sepolia values (`0x5C210eF41CD1a72de73bF76eC39637bB0d3d7BEE` / `0x9e1344a1247c8a1785d0a4681a27152bffdb43666ae5bf7d14d24a5efd44bf71`) before compiling. Compiled successfully. Deployed via Remix, Browser Extension environment, Base Sepolia (chain 84532), passing subscription ID `24963885066942085575241868055782773595381668348941839345025195320832983598589` to the constructor.
- **Result:** ✅ Success — "1 Transaction mined and execution completed."
  - Tx hash: `0xf7cadd7f2a005988bfbbb8c7e7565138f9a101bc38270c60ef5be51ae40fb9c8`
  - Contract address: `0xAc2ecDcCcEC23859F9b3f622063e44873c0173f4`
  - Block: 44807518
  - Gas used: 1,788,507
  - Deployer: `0xfA498F339d311f5b6f8A79c5459F8dE2BABd36e5`
  - Decoded constructor input confirmed correct subscription ID passed
  - Note: this consumed a meaningful portion of the 0.0001 ETH balance — worth tracking remaining balance before attempting `rollDice`
- **Finding ID (if any):** None — deploy worked cleanly once the network-specific values were corrected per F001/doc guidance.
- **Timestamp:** Jul-29-2026 11:35:30 PM UTC-04

### Step 4 — Add deployed contract as approved consumer

- **Doc says:** In the Subscription Manager, add the deployed contract address as an approved consumer; fund the subscription.
- **What I did:** Funded subscription `24963...598589` with testnet LINK via vrf.chain.link. Added `0xAc2ecDcCcEC23859F9b3f622063e44873c0173f4` as an approved consumer.
- **Result:** ✅ Success — confirmed indirectly: the subsequent `rollDice` call (Step 5) no longer reverted at gas estimation, which had failed specifically due to missing consumer registration / subscription funding. No standalone tx hash captured for this step in isolation.
- **Finding ID (if any):** F003 — see FINDINGS.md. Getting Started does flag funding upfront via its section heading, but defers the actual funding steps to a separate page whose internal ordering (Add Consumer before Fund) doesn't match the order a Getting Started reader actually needs.
- **Timestamp:**

### Step 5 — Call `rollDice`

- **Doc says:** Call `rollDice(address)` with your wallet address; this submits a VRF request.
- **What I did:** Retried `rollDice` in Remix after completing Step 4.
- **Result:** ✅ Success — "1 Transaction mined and execution completed."
  - Tx hash: `0x988f32bae63b4c9a9518ecca40582170cd8513a1ab7daebbba7ef95aec2fc2d3`
  - Block: 44832807, gas used: 240,025
  - Log from VRF Coordinator (`0x5C210eF4...d7BEE`) containing this session's keyHash and contract address — consistent with `RandomWordsRequested`
  - Log from the deployed contract (`0xAc2ecDcCcEC...c0173f4`) containing the wallet address — consistent with `DiceRolled`
  - **Environment note (not a Chainlink docs finding):** `from` on this tx was `0xC066ac5D...37a8B8c`, not the tracked wallet directly — the transaction appears to have been routed through a MetaMask smart-account relay/batch (`to: 0xdb9B1e94...47dB3`), bundling the call rather than sending it as a plain 1:1 EOA transaction. This is a MetaMask account-abstraction behavior unrelated to the tutorial content itself, but worth knowing if reading raw transaction data and expecting a direct sender match.
- **Finding ID (if any):** None.
- **Timestamp:** Jul 30 2026 13:51:42 (-04:00 UTC)

### Step 6 — Call `house`

- **Doc says:** Call `house(address)` to retrieve the assigned house once the random roll has been fulfilled.
- **What I did:** Called `house(0xfA498F339d311f5b6f8A79c5459F8dE2BABd36e5)` in Remix.
- **Result:** ✅ Success — returned `"Targaryen"` (no revert). Confirms `fulfillRandomWords` had already been called by the VRF Coordinator by the time this was checked, completing the full request → fulfillment → read cycle.
- **Finding ID (if any):** None.
- **Timestamp:**

---

## Run Summary

**Outcome:** The VRF v2.5 Getting Started tutorial was successfully reproduced end to end on Base Sepolia: subscription created and funded, contract deployed with corrected network-specific values, consumer registered, rollDice requested, and house returned a valid result (Targaryen) after fulfillment.

**Findings produced:** 2 open (F002 — undocumented mainnet-LINK requirement on Chainlink's own faucet; F003 — minor ordering mismatch and missing screenshots on the linked subscription-management page), 1 retracted on verification (F001). Note: F003 was itself revised after an initial overstatement was caught and corrected — see FINDINGS.md.

---

## Appendix

![Faucet drip results — ETH failed, LINK succeeded](../screenshots/vrf-v2-5-getting-started/F002-faucet-drip-results.png)
\*Screenshot from Step 1: Base Sepolia ETH drip failed (mainnet LINK requirement, see F002); LINK drip succeeded (25 LINK, [tx](https://sepolia.basescan.org/tx/0xc2a42fb4d5fb2a7a474421a2a5d6e2b29e864277c6073eb1f9a52919d2a075c0)).
