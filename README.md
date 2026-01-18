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

## Design Principles Across All Labs

- Explicit scope and stated non-goals
- Minimalism over feature sprawl
- Reproducibility and validation
- Evidence-producing controls
- Separation of hygiene, enforcement, and scanning
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

## Status

This index evolves as new labs are added. Existing repositories are considered stable unless explicitly marked otherwise.

---

## Contact & Collaboration

Collaboration and discussion are welcome where appropriate.  
Each repository contains its own scope and contribution guidelines.

This index exists to provide **clarity, alignment, and architectural intent** across the DevSecOps lab ecosystem.
