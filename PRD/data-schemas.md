# Appendix B — Data Tables & Columns

This appendix outlines the data schemas that drive Ethproofs V3’s user interface tables, ensuring a robust foundation for displaying and analyzing zk proving data. It details direct database fields, indirect relationships, UI-specific columns, and proposed extensions for entities like **teams, zkVMs, proof systems, provers, blocks, and proofs**. By defining clear, auditable, and extensible data structures, this schema supports transparent benchmarking, verifiable metrics, and seamless integration with research workflows—aligning with Ethproofs’ mission to accelerate Ethereum’s real-time proving roadmap.

---

## B.1 Teams

Defines the schema for team-related data, capturing identity and metadata for proving teams. Includes direct database fields (e.g., Team Name, GitHub Org), indirect relationships (e.g., linked zkVMs, provers, proofs), and UI-specific columns to ensure clear, auditable presentation of contributions.

**Direct fields (from `teams`)**
- Team ID (`id`)
- Team Name (`name`)
- GitHub Org (`github_org`)
- Twitter Handle (`twitter_handle`)
- Website (`website_url`)
- Logo (`logo_url`)
- Created At (`created_at`)
- Storage Quota Bytes (`storage_quota_bytes`)
- Telegram ID (`telegram_id`)

**Indirect fields (via relationships)**
- **zkVMs** → from `zkvms.team_id`
- **Provers** → from `provers.team_id`
- **Proofs Submitted** → from `proofs.team_id`

---

## B.2 zkVMs

Outlines the structure for zkVMs: core attributes, versions, proof systems, and verifiability. Includes indirect relationships and UI enhancements (e.g., verifiability badges) to support transparent benchmarking.

**Direct fields (from `zkvms`)**
- zkVM ID (`id`)
- Name (`name`)
- Team ID (`team_id`)
- Precompiles (`precompiles`)
- Frontend (`frontend`)
- Created At (`created_at`)

**Indirect fields (via relationships)**
- **Versions** → from `zkvm_versions.zkvm_id`
- **Security Metrics** → from `zkvm_security_metrics.zkvm_id`
- **Performance Metrics** → from `zkvm_performance_metrics.zkvm_id`
- **Daily Stats** → from `zkvm_daily_stats.zkvm_id`
- **Benchmarks** → from `benchmarks.zkvm_id`
- **Proofs** → via `proofs.zkvm_id`
- **Teams** → via `teams.id = zkvms.team_id`

**Additional UI columns (from refined sheet)**
- Team Affiliation (dropdown from `teams`)
- Latest Version (text / join from `zkvm_versions`)
- ISA (enum: RISC-V, Cairo, …)
- Active / Coming Soon / All (derived from proof activity)
- Internal Ethproofs Audit Status (manual flag)
- Proof System (FK → `proof_systems`)
- In-Browser Verification Available (bool)
- Mainnet Capable (bool)
- Parallelizable Proving (bool)
- Continuations (enum: Full, Basic)
- Date Added (derived timestamp)
- Latest Update (derived timestamp)
- Open Source: CPU Prover (enum/license)
- Repo URL: CPU Prover (link)
- Open Source: GPU Prover (enum/license)
- Repo URL: GPU Prover (link)
- Open Source: Verifier (enum/license)
- Repo URL: Verifier (link)

**Proposed additions (UI/DB)**
- Verifiability badges (Verifier-WASM available, Browser-verify enabled, Reproducible benchmarks)
- Attribution links (papers, PRs, repos) per metric → new `zkvm_attributions` table

---

## B.3 Proof Systems *(new table — populated from zkVM onboarding form)*

Specifies the schema for proof systems: cryptographic primitives, commitment schemes, recursion features. Includes indirect relationships and proposed UI additions for transparency.

**Direct fields (from `proof_systems`)**
- Proof System ID (`id`)
- Proof System Name (`name`)
- Team Affiliation (`team_id`)
- Latest Version (string)
- Internal Ethproofs Audit Status (manual flag)
- Active / Coming Soon / All (derived from usage)
- Dual License: Proof System (bool)
- Open Source: Proof System (enum/license)
- zkVMs (list of linked zkVMs)
- Used By (count of zkVMs using it)
- Verifier Language (Rust, Solidity, etc.)
- Memory Model (Stack-based, Register-based, etc.)
- Field/Curve (e.g., BabyBear, BLS12-381)
- Field Size (bits)
- Commitment Scheme (FRI, IPA, …)
- Hash Function (Blake2, Blake3, etc.)
- Conjectures (list)
- Optimizations (list: lookup, contiguity, etc.)
- Proof Aggregation Support (enum: None, Basic, Full)
- Recursion Support (enum: None, Full IVC, Full PCD)

**Indirect fields (via relationships)**
- Associated zkVM Versions → `zkvm_versions.proof_system_id`
- Associated zkVMs → via `zkvm_versions.zkvm_id`
- Implementations (Provers) → `provers.proof_system_id`
- Verifier / Prover Programs → from `programs.proof_system_id`
- Benchmarks → from `benchmarks.proof_system_id`
- Proofs Using This System → from `proofs.proof_system_id`
- Daily Stats → from `proof_daily_stats.proof_system_id`
- Attributions → from `attributions.entity_type = 'proof_system'`
- OSS Status History → from `oss_status.entity_type = 'proof_system'`
- Verification Assets → from `verification_assets.entity_type = 'proof_system'`

---

## B.4 Provers

Defines the structure for prover data: implementation details, hardware specs, open-source status, and UI signals (e.g., staging gate status) for credible, auditable tracking.

**Direct fields (from `provers`)**
- Prover ID (`id`)
- Name (`name`)
- Team ID (`team_id`)
- zkVM ID (`zkvm_id`)
- API Auth Tokens (`api_auth_tokens`)
- Is Active (`is_active`)
- Created At (`created_at`)

**Indirect fields (via relationships)**
- Machines → from `machines.prover_id`
- Clusters → from `clusters.prover_id`
- Proofs → from `proofs.prover_id`
- Daily Stats → from `prover_daily_stats.prover_id`
- zkVMs → via `zkvms.id = provers.zkvm_id`
- Teams → via `teams.id = provers.team_id`

**Additional UI columns (from refined sheet)**
- Latest Version
- Active / Coming Soon / All (derived)
- zkVM using (join)
- Proof System using (join)
- Binaries Available (bool)
- CPU (clock speed, cores, etc.)
- RAM (amount)
- GPU Model / VRAM
- Hardware Acceleration (ASIC, FPGA, GPU, etc.)
- Prover Distribution (single-threaded, multi-threaded, cluster, etc.)
- Dual License: Prover (bool)
- Repo URL: Prover
- Open Source: Verifier (enum/license)
- Dual License: Verifier (bool)
- Repo URL: Verifier
- Open Source: GPU Acceleration (enum/license)
- Dual License: GPU Acceleration (bool)
- Repo URL: GPU Acceleration

**Proposed additions (UI/DB)**
- Open-source status (CPU prover, GPU prover) → new fields or `prover_oss_status` table  
- In-browser verification participation → boolean / refs to package  
- **Staging gate** → require 100 clean Ethproofs blocks on staging  
  - `provers.state ∈ {Draft, Staging, Under Audit, Verified, Production}`  
  - `provers.staging_clean_count`, `provers.staging_required = 100`

---

## B.5 Blocks

Schema for Ethereum L1 blocks, annotated with gas usage, proof metrics, and RTP indicators. Includes relationships to proofs and UI columns for researcher workflows.

**Direct fields (from `blocks`)**
- Block ID (`id`)
- Block Number (`block_number`)
- Slot (`slot`)
- Timestamp (`timestamp`)
- Gas Used (`gas_used`)
- Transaction Count (`transaction_count`)
- Parent Hash (`parent_hash`)
- Proposer / Miner (`proposer`)
- Created At (`created_at`)

**Indirect fields (via relationships)**
- Proofs for Block → from `proofs.block_id`
- Fastest / Avg Proof Metrics (derived) → aggregates over `proofs` by `block_id`
- Linked Teams / Provers / zkVMs via Proofs → `proofs.team_id`, `proofs.prover_id`, `proofs.zkvm_id`

**Additional UI columns (from CSV)**
- Blobs (EIP-4844 blob count)
- Block Size (bytes) → `blocks.size_bytes` (or derived)
- Cost per Mgas → derived metric at block level (avg/min over proofs)
- Cost per Proof → derived (avg/min over proofs for the block)
- Epoch → `blocks.epoch` (if stored)
- Etherscan URL → `blocks.block_explorer_url` (derived/link)
- Gas Limit → `blocks.gas_limit`
- Gas Used → `blocks.gas_used`
- Num Proofs → count from `proofs` by `block_id`
- Proof → UI link to latest/fastest proof detail
- Proof Status → aggregate status (e.g., “verified”, “has proofs”, “missing”)
- Slot → `blocks.slot`
- Timestamp → `blocks.timestamp`
- TXs → `blocks.transaction_count`

**Proposed additions (UI/DB)**
- RTP progress indicators per block (e.g., fastest proof vs ~10s target)
- Compare blocks (2–3 side-by-side): cached aggregates for latency/cost
- Provenance badge if **all** proofs for the block have browser verification enabled

---

## B.6 Proofs

Schema for individual proof records: latency, cost, cycles, reproducibility; relationships to blocks, provers, zkVMs; and UI flags for browser verification.

**Direct fields (from `proofs`)**
- Proof ID (`id`)
- Block ID (`block_id`)
- Prover ID (`prover_id`)
- zkVM ID (`zkvm_id`)
- zkVM Version ID (`zkvm_version_id`)
- Team ID (`team_id`)
- Program ID (`program_id`)
- Status (`status`)
- Proving Time (ms) (`proving_ms`)
- Total Time (ms) (`total_ms`)
- Verification Status (`verification_status`)
- Created At (`created_at`)

**Indirect fields (via relationships)**
- Blocks → `blocks.id = proofs.block_id`
- Provers → `provers.id = proofs.prover_id`
- zkVMs → `zkvms.id = proofs.zkvm_id`
- zkVM Versions → `zkvm_versions.id = proofs.zkvm_version_id`
- Teams → `teams.id = proofs.team_id`
- Programs (verifier/prover binaries) → `programs.id = proofs.program_id`
- Daily Stats → `proof_daily_stats.proof_id`

**Additional UI columns (from CSV)**
- Proof Number → UI label (maps to `proofs.id` or external identifier)
- Block Number → join `blocks.block_number`
- Cost per Mgas → derived (cost model over proofs/gas)
- Cost per Proof → derived/recorded
- Cycles → measured/recorded metric (perf)
- Proof Size → `proofs.size_bytes` (or equivalent)
- Proving Time → maps to `proving_ms` (UI: humanized)
- Total Time to Prove → maps to `total_ms` (UI: humanized)
- Provers Used → list/join from `provers.name` (for multi-prover workflows)
- zkVMs Used → list/join from `zkvms.name` (for multi-zkVM workflows)

**Proposed additions (UI/DB)**
- **Browser verification gating:** submission requires verifier assets present (WASM npm, VK, public inputs schema)  
  - `proofs.browser_verify_available` (bool)  
  - `proofs.browser_verified_at` (timestamp)
- Attribution links for cost/latency (papers, PRs, commits) → `attributions` helper table
- Provenance flags: `is_measured` vs `is_claimed`, with source references
- **Reproducibility checksum** (inputs/config hash) for reruns
