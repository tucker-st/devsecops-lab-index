# DevSecOps Lab Index

This repository serves as a **single authoritative index** for my DevSecOps and cloud security labs hosted on my professional GitHub account.

The purpose of this index is to:
- clearly describe the **intent and scope** of each lab
- show how individual repositories fit into a **cohesive DevSecOps learning and control model**
- avoid duplication, over-claiming, or tool sprawl

Each repository demonstrates a **specific capability or control**, not a generic demo environment.

---

## How to Read This Index

The labs are organized by **capability layers**, not by tools.

Each repository answers one question:
> “What DevSecOps or security capability does this demonstrate?”

This mirrors how mature environments are designed and assessed.

---

## Capability Layers

### 1. Platform & Operational Foundations

These repositories demonstrate **operational discipline** that underpins secure cloud, container, and CI/CD environments.

#### RHCSA (RHEL 10) Practice Repository
- Linux system administration under realistic constraints
- Persistence, reboot validation, and service correctness
- SELinux and firewall enforcement by default
- Exam-style pressure and validation

Purpose:
> Establishes the operational baseline required for secure infrastructure and DevSecOps workflows.

Repository:  
https://github.com/tucker-st/rhcsa-ex200

---

### 2. Platform Hygiene & Change Visibility

These repositories focus on **lifecycle awareness, drift detection, and change evidence**, not scanning or enforcement.

#### Docker Image Hygiene
- Captures Docker image state before and after updates
- Pulls existing images with explicit change visibility
- Produces reproducible diff artifacts and logs
- Supports operational hygiene and evidence generation

Purpose:
> Demonstrates container image lifecycle hygiene and change visibility as a reusable DevSecOps control.

Explicit non-goals:
- Vulnerability scanning
- SBOM generation
- Policy enforcement

Repository:  
https://github.com/tucker-st/docker-image-hygiene

---

### 3. Cloud Security Foundations

These repositories establish **security-first cloud baselines** with explicit scope and guardrails.

#### AWS Cloud Security Foundations
- IAM fundamentals and least-privilege patterns
- Logging and visibility
- Network security basics
- Shared responsibility model

Purpose:
> Provides a disciplined entry point into AWS security without console-driven shortcuts.

Repository:  
https://github.com/tucker-st/aws-cloud-security-foundations

---

### 4. Secure Kubernetes & Platform Foundations

These repositories focus on **correct, auditable platform setup**, not feature completeness.

#### AWS EKS Secure Foundations
- Single-region, security-first EKS deployment
- IRSA with OIDC
- Secure add-ons via Helm
- Observability and operational readiness

Purpose:
> Demonstrates how to stand up a Kubernetes control plane with security and auditability as first-class concerns.

Repository:  
https://github.com/tucker-st/aws-eks-secure-foundations

---

### 5. Infrastructure as Code Controls

These repositories emphasize **guardrails, structure, and change awareness** in IaC.

#### Secure IaC Foundations
- Terraform structure and state safety
- Change impact awareness
- Secure defaults
- Automation with intent

Purpose:
> Treats Infrastructure as Code as an operational control surface, not just a deployment mechanism.

Repository:  
https://github.com/tucker-st/secure-iac-foundations

---

### 6. RMF & Compliance Operations

These repositories translate governance into **practical, day-to-day workflows**.

#### RMF Operational Playbooks
- Continuous monitoring practices
- POA&M lifecycle management
- Audit and inspection readiness
- Operational compliance guidance

Purpose:
> Bridges formal RMF requirements with real operational execution.

Repository:  
https://github.com/tucker-st/rmf-operational-playbooks

---

### 7. Supply Chain & Image Assurance

These repositories focus on **assessment and assurance artifacts** for container images.  
They are intentionally separate from hygiene, change visibility, and policy enforcement.

#### Docker Image Assurance
- Generates Software Bill of Materials (SBOM)
- Performs container image vulnerability assessment
- Produces structured, reviewable artifacts suitable for CI pipelines
- Uses containerized tooling to avoid local dependency sprawl

Purpose:
> Demonstrates container image assessment and assurance workflows without enforcing policy or blocking deployments.

Explicit non-goals:
- Image pull hygiene or change tracking (handled separately)
- Admission control or policy enforcement
- Signature enforcement or provenance guarantees

Repository:  
https://github.com/tucker-st/docker-image-assurance

---

### 8. Enforcement & Policy (Planned)

This capability layer represents **future work** focused on **policy enforcement and decision points** in DevSecOps pipelines and platforms.

Items in this section are **not yet implemented**.  
They are listed to show **architectural intent**, not delivery commitments.

The goal is to demonstrate how **enforcement builds on hygiene and assurance**, rather than replacing them.

#### Policy & Enforcement Foundations (Planned)
Conceptual and practical exploration of enforcement mechanisms, intentionally kept separate from foundations and assessment.

Potential focus areas:
- Policy-as-code concepts applied after evidence is produced
- Admission control patterns (e.g., allow / deny decisions)
- CI/CD gating based on explicit criteria
- Clear distinction between **visibility**, **assessment**, and **enforcement**

Design intent:
> Enforcement should be applied deliberately, with full awareness of upstream hygiene and assurance signals.

Explicit non-goals (at this stage):
- Full enterprise policy engines
- Turnkey “one-click” enforcement frameworks
- Broad compliance claims

This layer is planned to **consume artifacts** produced by:
- Platform hygiene controls
- Image assurance workflows
- Infrastructure and identity foundations

No repository currently exists for this layer.


## Design Principles Across All Labs

- Explicit scope and stated non-goals
- Minimalism over feature sprawl
- Reproducibility and validation
- Evidence-producing controls
- Separation of hygiene, assessment, and enforcement
- Operational realism over tutorial convenience

---

## What This Index Is Not

- Not a monolithic “all-in-one” lab
- Not a collection of unrelated demos
- Not a vulnerability scanning showcase
- Not a certification cram site

Each repository is intentionally **composable**, allowing controls to be layered without coupling.

---

## Intended Audience

- Security engineers transitioning to cloud and DevSecOps
- Platform and infrastructure engineers operating in regulated environments
- ISSOs and security professionals modernizing legacy practices
- Reviewers seeking evidence of operational judgment, not just tooling familiarity

---

## Planned / Not Yet Implemented (Roadmap)

This section captures **intent** and **direction** only. Items listed here may change as requirements, time, and learning priorities evolve. Nothing in this section should be interpreted as a committed delivery schedule.

### Policy & Guardrails (Planned)
- Admission / enforcement concepts (kept separate from foundations)
- Minimal policy examples focused on clarity over completeness

### Evidence & Reporting (Planned)
- Structured outputs that can be archived as pipeline artifacts
- Simple reporting formats that support operational review

---

## Status

This index evolves as new labs are added. Existing repositories are considered stable unless explicitly marked otherwise.

---

## Contact & Collaboration

Collaboration and discussion are welcome where appropriate.  
Each repository contains its own scope and contribution guidelines.

This index exists to provide **clarity, alignment, and architectural intent** across the DevSecOps lab ecosystem.
