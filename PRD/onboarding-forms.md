# Appendix A — Onboarding Forms

Onboarding is the first gate to credibility. Ethproofs can only serve as a trusted research tool if every datapoint is clean, well-formatted, and verifiable from the start. Appendix A defines the structured **Admin Dashboard** user forms for **Teams**, **zkVMs**, and **Provers**. These forms enforce consistency in data entry, capture explicit attribution for every claim, and set clear expectations for contributors (e.g., staging milestones). By standardizing inputs and version control from the outset, Ethproofs ensures its data tables remain reproducible, auditable, and useful to researchers tracking real-time proving progress.

---

## A.1 New Team Onboarding Form

The Team onboarding form collects the baseline identity and attribution details needed to onboard a research or engineering team into Ethproofs. Because Ethproofs acts as a credibility layer for the proving ecosystem, each team must provide sufficient documentation and commit to staging requirements before being listed in production. Structured inputs (URLs, attribution links, audit status) ensure that all claims are traceable and administrators can enforce guardrails consistently.

### A.1.1 Team Identity
- **Team Name** (Short answer, required)  
- **Team Website** (URL, required)  
- **GitHub Organization** (URL, required)  
- **Twitter/X Handle** (optional)  
- **Logo Upload** (.svg; background = transparent, fill = black, required)

### A.1.2 Attribution & Docs
- **Primary Contact Email** (required)  
- **Documentation URL** (Notion/Docs/Whitepaper, optional)  
- **Research Papers / References** (Paragraph, optional — list links separated by commas)

---

## A.2 New zkVM Onboarding Form

**Purpose:** Document core architecture, features, and provenance of zkVMs. Expands significantly beyond Ethproofs V2 and consolidates information previously scattered across sources like Awesome-zkVM and the prooflab / Conner Swann zkVM Spreadsheet.

### A.2.1 zkVM Identity
- **zkVM Name** (required)  
- **Team Affiliation** (dropdown, required)  
- **Latest Version** (required)

### A.2.2 Eligibility Agreement, Part I
*(Each item requires a checkbox attestation + documentation URL)*
- **Mainnet Capable**  
- **Parallelizable Proving**  
- **Continuations & Recursion** (chunking/sharding)  
- **GPU Proving** (with exposed Metal/CUDA code)

### A.2.3 Eligibility Agreement, Part II
**Open-source disclosures** (license + repo URL required):
- **CPU Prover**  
- **GPU Prover**  
- **Verifier**

### A.2.4 Security & Audit (“Pizza Ratings”)
For each, contributor must attest to status and provide documentation:
- **Protocol Soundness** (tiers: not fully audited, fully audited, formally verified)  
- **Implementation Audit** (tiers: not fully audited, fully audited, formally verified)  
- **EVM STF Bytecode Audit** (tiers: not fully audited, fully audited, formally verified)  
- **Bounties** (tiers: ≤$64k, $64k–$1M, ≥$1M)  
- **Security Target (bits)** (tiers: ≤100 bits, 100–128 bits, ≥128 bits)  
- **Quantum Security** (curve vs. hash/lattice-based)  
- **Verification Time** (≥16ms, <16ms, <1ms)  
- **Proof Size** (≥512KiB, <512KiB, <32KiB)

### A.2.5 Core Components

#### A.2.5.1 ISA
**Instruction Set Architecture:** The fundamental “language” of the VM, defining all its basic operations and how they interact with data. *(check one)*
- RISC-V  
- Cairo  
- MIPS  
- Wasm  
- Other (Short answer, required)  
**Link to documentation** verifying this claim. (Short answer, URL, required)

#### A.2.5.2 ISA Extensions / Profile
> **Note:** Consider combining this with the ISA section for ISAs that have standard extension sets (e.g., RISC-V, MIPS). For ISAs like Cairo where extensions don’t apply, mark **N/A**.

Provide definition *(check one)*:
- RV32IM  
- RV64IMA  
- MIPS32e2  
- Other (Short answer, required)  
**Link to documentation** verifying this claim. (Short answer, URL, required)

#### A.2.5.3 Proving Frontend
**Proving Frontend:** The programming language the programmer expresses their business logic in, which then gets compiled down into the VM’s supported ISA for constrained execution. *(check one)*
- ASM / Assembly  
- C  
- C++  
- Cairo  
- Circom  
- Go  
- Lurk  
- PIL  
- Rust  
- Wasm  
- Other (Short answer, required)  
**Link to documentation** verifying this claim. (Short answer, URL, required)

#### A.2.5.4 Precompiles
**Precompiles** (Built-ins, Chiplets, Accelerate etc.): Specialized, pre-built functions for complex tasks (like cryptography) that boost efficiency and reduce proof overhead. *(check all that apply)*
- Bitwise Ops  
- Blake2  
- Blake3  
- BLS12-381 Pairing  
- BN254 Pairing  
- ECDSA  
- Ed25519  
- Generic MSM  
- Jubjub ops  
- Keccak  
- KZG Verification  
- Merkle Operations  
- NTT/FTT  
- P-256 / secp256r1  
- Pallas / Vesta (Pasta) ops  
- Poseidon  
- Poseidon2  
- Range Checks  
- secp256k1  
- Schnorr (secp256k1)  
- SHA256  
- Other (Short answer, required)  
**Link to documentation** verifying this claim. (Short answer, URL, required)

### A.2.6 Proof System, Basic Information
- **Proof System Name** (required)  
- **Latest Version** (required)  
- **Open Source License + Repo URL** (required)

### A.2.7 Proof System, Core Components

#### A.2.7.1 Proof System Type
*(check one, required)*
- Hash-based  
- Lattice-based  
- STARK  
- SNARK  
- Bulletproofs  
- Other (Short answer, required)  
**Link to documentation** verifying this claim. (Short answer, URL, required)

#### A.2.7.2 Trusted Setup
*(check one, required)*
- None  
- Conditional  
- Universal  
- Circuit-specific  
- Inherited  
- Other (Short answer, required)  
**Link to documentation** verifying this claim. (Short answer, URL, required)

#### A.2.7.3 Arithmetization
**Arithmetization:** The process of turning an execution trace into an algebraic statement (polynomial equations) that can be verified. *(check one, required)*
- AIR  
- AIR (core)  
- AIR (plonky2)  
- AIR (plonky3)  
- AIR (Starky)  
- AIR (Winterfell)  
- eAIR  
- CCS  
- GKR  
- PLONK  
- PLONK (wrap)  
- Plonkish  
- R1CS  
- Other (Short answer, required)  
**Link to documentation** verifying this claim. (Short answer, URL, required)

#### A.2.7.4 Backends
**Backends:** The proof system (typically an IOP + PCS) used for prover–verifier checks. *(check one, required)*
- ALI  
- Breakdown  
- DEEP-FRI  
- Groth16  
- IPA  
- Plonky3  
- PSE-Halo2 (KZG)  
- Spartan  
- Winterfell  
- Zeromorph  
- Other (Short answer, required)  
**Link to documentation** verifying this claim. (Short answer, URL, required)

#### A.2.7.5 Verifier
**Verifiers:** Programs that verify given a proof and public inputs. *(check one, required)*
- Rust  
- Solidity  
- Wasm  
- Other (Short answer, required)  
**Link to documentation** verifying this claim. (Short answer, URL, required)

#### A.2.7.6 Memory Model
*(check one, required)*
- Stack-based  
- Register-based  
- Harvard  
- Von Neumann  
- Other (Short answer, required)  
**Link to documentation** verifying this claim. (Short answer, URL, required)

#### A.2.7.7 Field/Curve
*(check one, required)*
- BabyBear  
- KoalaBear  
- BLS12-381  
- BN254  
- Goldilocks  
- Mersenne31  
- Other (Short answer, required)  
**Link to documentation** ver
