# Ethproofs — Product Requirements Document (PRD)

---

## Purpose of this Document

This Product Requirements Document (PRD) defines the **vision, features, and success metrics** for Ethproofs — a public-good platform to track and accelerate progress in zk proving for Ethereum.

The PRD serves five purposes:

1. **Clarify Vision** — align stakeholders on Ethproofs’ goals and scope.  
2. **Define Requirements** — outline user needs, features, and technical specifications.  
3. **Guide Development** — provide the basis for roadmap planning.  
4. **Set Success Criteria** — establish measurable outcomes for evaluation.  
5. **Facilitate Communication** — ensure all stakeholders understand priorities and expectations.

---

## Roadmap Phases

|             | **phase 0**<br>*early adopters* | **phase 1**<br>*delayed proving* | **phase 2**<br>*mandatory proofs* | **phase 3**<br>*enshrined proofs* |
|-------------|---------------------------------|----------------------------------|-----------------------------------|-----------------------------------|
| **timeline** | <span style="color:blue">2025</span> | <span style="color:blue">2026</span> | <span style="color:blue">2027</span> | <span style="color:blue">2028</span> |
| **proving**  | <span style="color:red">altruistic</span> | <span style="color:red">altruistic</span> | <span style="color:green">rational</span> | <span style="color:green">rational</span> |


*Ethproofs is currently in **pre-Phase 0**, before reliable altruistic proving is established.*

---

## 1. Overview

**Ethproofs** is a neutral, research-driven platform that tracks, benchmarks, and validates zk proofs for Ethereum’s Layer 1 (L1). It provides a dashboard, proof explorer, and open data schemas to support the community’s journey from pre-Phase 0 through enshrined zk-proofs.  

### Ethproofs’ role
- Enable **client-side verification** today.  
- Support the race for **real-time proving of execution blocks**.  
- Support the evolution toward future proving across **consensus, data, and privacy** layers as needed.  

### North-star targets
- ≤ **10s proving latency** (P99 of mainnet blocks).  
- ≤ **$100k opex** per L1 EL proving cluster.
- ≤ **10kW power** per L1 EL proving cluster.
- ≥ **128-bit security** profile.  
- ≤ **300KiB proof size**, no trusted setup.  
- Fully open-sourced and formally verified code.  

### 1.1 Current Traction
- **Ecosystem adoption**: 6 zkVMs and 9 provers onboarded (+4 in progress).  
- **Proof volume**: 100k+ Ethereum blocks proved.  
- **Verification**: in-browser verification live for 2 zkVMs (expanding to 4).  
- **Automation**: status bots enforce accountability for missed proofs.  
- **Performance gains**: 5× latency reduction and 15× cost reduction in the past year.  
- **Community**: active researcher & developer feedback loops.  

### 1.2 Next Steps
- **Robust Documentation** — comprehensive definitions and metrics.  
- **Structured Onboarding** — detailed, auditable data for zkVMs, proof systems, and provers.  
- **Contributor Guardrails** — 100 consecutive verified proofs required in staging before production access.  

### 1.3 Target Users
- **Provers** — benchmark performance, submit proofs, and compete transparently.  
- **zkVM Developers** — showcase readiness for real-time proving.  
- **Researchers & Community** — monitor ecosystem progress via neutral data.  
- **Ethereum Foundation Teams** — use Ethproofs benchmarks for L1 security studies and incentive design.  

---

## 2. Product & UI Principles

Ethproofs emphasizes **neutrality, verifiability, and accessibility**.  

### Core Principles
- **North Star First** — highlight progress toward real-time proving.  
- **Phase-Aware Growth** — anticipate evolution from altruistic to rational incentives.  
- **Credibility with Guardrails** — explicit contributor expectations and visible audit states.  
- **Verified vs Reported** — clear separation of verifiable and self-reported data.  
- **Minimalist UI** — standardized shadcn/ui components, data-first design.  
- **Modular & Scalable** — support new metrics and entities over time.  

### Key UI Elements
- **Persistent Navigation** — sidebar for global sections; right-hand docs drawer for inline definitions and provenance.  
- **Interactive Tables** — clustering, filtering, row comparison, CSV export.  
- **Consistent Interaction Patterns** — provenance surfaced at point-of-use; filters and comparison tools uniform across all data types.  
- **Branding** — minimal and data-first (Lock Sans fonts, Tailwind zinc grayscale, green accents).  
- **Responsive Behavior** — clean layouts across desktop and mobile.  

---

## 3. Verification & QA

Ethproofs enforces credibility through **strict verification guardrails**:

- **In-Browser Verification** — WASM verifiers required for all proof submissions.  
- **Open Source Status** — provers/zkVMs tagged for verifier, CPU prover, GPU prover.  
- **Attribution & Provenance** — every claim linked to papers, PRs, repos, or commits.  
- **Audit Workflow** — automated checks + manual review; clear contributor states:  
  - `Under Audit` — default for new/updated data.  
  - `Audited by Ethproofs` — confirmed and verified.  
- **Staging Milestones** — 100 consecutive clean proofs before production listing.  

---

## 4. Technical Notes

Ethproofs’ stack is optimized for **speed, reproducibility, and low maintenance**:

- **Framework**: Next.js (App Router + TypeScript).  
- **UI**: shadcn/ui with Tailwind CSS (minimal overrides).  
- **Charts**: Recharts for proving metrics visualization.  
- **State & Data**: API-driven, lightweight client-side state, public endpoints for proofs/zkVMs/provers/blocks.  
- **Engineering Principles**:  
  - Minimal styling customizations.  
  - Uniform interaction models.  
  - Extensible schemas for evolving metrics.  

---

## 5. Success Metrics

Success is measured by **researcher trust and ecosystem adoption**, not design polish.  

### Usability
- ≤ 5s to locate proof details.  
- ≥ 70% provers onboard without admin help.  
- ≥ 80% of metrics with inline definitions.  

### Reliability
- ≥ 95% uptime for proof ingestion & bots.  
- ≤ 10s delay for proof submission updates.  
- CSV exports always reflect filters/sorting.  

### Credibility
- 100% of production proofs have in-browser verification.  
- All unverifiable claims flagged as “Reported.”  
- All active zkVMs/provers display audit states.  

### Adoption & Impact
- ≥ 3 EF research teams reference Ethproofs annually.  
- ≥ 5 external teams integrate Ethproofs API.  
- Continuous quarter-over-quarter contributor growth.  

---

## 6. Long-Term Vision

Ethproofs’ initial focus is **real-time proving of execution blocks** (leanExecution). Long-term, it will expand to support:

- **leanExecution** — SNARK-friendly ISA (e.g., RISC-V).  
- **leanConsensus (“Beacon Chain 2.0”)** — post-quantum secure consensus with SNARKified attestations.  
- **leanData (“Blobs 2.0”)** — post-quantum secure data availability with aggregatable hash-based proofs.  
- **Client-Side Proving** — enabling end users to generate and verify proofs locally, fostering decentralization, improving resilience, and reducing reliance on centralized infrastructure.  
- **Privacy Proving** — transparency and auditability for user-facing privacy systems.  

**Outcome:** Ethproofs becomes the **benchmarking and credibility hub** for zk proving across execution, consensus, data, client-side proving, and privacy — accelerating Ethereum’s path to decentralization and scalability.  

---

*This PRD is a living document. Contributions, feedback, and corrections are welcome via issues and PRs.*
