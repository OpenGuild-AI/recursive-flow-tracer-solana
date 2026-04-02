# ◆ Recursive Flow Tracer — Solana

> Trace money flows across the Solana network.
> Not just transactions — **behavior, structure, and hidden relationships.**

---

## ⚡ What this is

A **recursive on-chain analysis engine** that maps how SOL and tokens move between wallets.

You start with a single address → the system expands outward → builds a **directed flow graph** of capital movement.

This is not a block explorer.

This is **flow intelligence**.

---

## 🔍 Core Capabilities

* **Recursive traversal**

  * Follow inflows, outflows, or both
  * Configurable depth (1–5 levels)
* **Graph-based modeling**

  * Wallet → edges → value transfer
  * Parent-child propagation logic
* **SOL + token analysis**

  * Native transfers
  * SPL token flows (mint-aware)
* **Heuristic filtering**

  * Min SOL threshold
  * Top-N expansion per level (anti-explosion control)
* **Real-time processing**

  * Queue-based scanning engine
  * Rate-limited API calls (Helius)
* **Multiple views**

  * 🌳 Tree (hierarchical flow)
  * 📊 Flat table (aggregated metrics)
  * ↓ Top funders (external capital sources)
* **Export layer**

  * JSON graph dump
  * Human-readable report

---

## 🧠 Why it matters

Most tools show *what happened*.
This shows **how money actually propagates**.

Use cases:

* Wallet clustering
* Funding source detection
* Airdrop / farming patterns
* Wash trading / circular flows
* Early-stage alpha detection
* Investigating suspicious activity

---

## 🏗 Architecture Overview

```text
Root Wallet
   ↓
Fetch Transactions (Helius API)
   ↓
Normalize Transfers
   ↓
Aggregate Inflows / Outflows
   ↓
Filter (SOL threshold + direction)
   ↓
Enqueue Next Wallets
   ↓
Repeat (BFS-like traversal)
```

Key design decisions:

* **Breadth-first traversal** → controlled expansion
* **Top-15 per level** → prevents combinatorial explosion
* **Stateful graph model** → avoids duplicate scans
* **Delay-based rate limiting** → API-safe

---

## ⚙️ Configuration

| Parameter    | Description               |
| ------------ | ------------------------- |
| Start Wallet | Root address              |
| API Key      | Helius RPC                |
| Max Depth    | Recursion depth           |
| Min SOL      | Filter noise              |
| Direction    | Inflows / Outflows / Both |
| Delay        | Rate limiting (ms)        |

---

## 🚀 Quick Start

1. Open the app:

   *

2. Insert:

   * Wallet address
   * Helius API key

3. Configure:

   * Depth (start with 2–3)
   * Min SOL (e.g. `0.01`)

4. Click:

   ```
   ▶ Trace starten
   ```

---

## 📊 Output Interpretation

### Tree View

* Shows **causal flow hierarchy**
* Each node:

  * Depth
  * Flow direction
  * SOL magnitude
  * Scan status

### Flat Table

* Aggregated metrics:

  * Total inflow/outflow
  * Transaction count
  * Degree (connections)

### Top Funders

* External wallets not in graph
* Ranked by:

  * Total SOL contributed
  * Frequency

---

## ⚠️ Constraints & Tradeoffs

* **RPC dependency (Helius)**
* **Rate limiting required**
* **Depth > 3 → exponential growth risk**
* Token valuation ≠ USD normalization (yet)

---

## 🧩 Future Improvements (realistic roadmap)

* Wallet clustering heuristics
* Graph visualization (D3 / WebGL)
* Token pricing normalization
* ML-based anomaly detection
* Persistent storage (indexed DB / backend)
* Multi-root comparative analysis

---

## 🧪 Known Edge Cases

* Wrapped SOL vs native SOL ambiguity
* Program wallets vs user wallets
* Spam / dust transactions
* Token decimals inconsistencies

---

## 🧭 Strategic Insight

This tool becomes significantly more powerful when:

* Combined with labeling datasets
* Used iteratively (multi-root tracing)
* Integrated into a broader intelligence pipeline

---

## 📜 License

MIT — use it, fork it, break it, improve it.

---

## ◆ Final Note

If you treat wallets as identities, you’ll miss everything.

Treat them as **flow nodes in a system** —
then patterns emerge.
