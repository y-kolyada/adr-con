# ADR Library

---

## ✅ Status: Active

**AI Model:** GPT-5.4

**AI Studio:** VS Code

**Documentation:**

- [README.md](./README.md)

---

**TOC:**

- [ADR Library](#adr-library)
  - [✅ Status: Active](#-status-active)
  - [1. Purpose](#1-purpose)
  - [2. File Roles](#2-file-roles)
  - [3. Reserved Number Ranges](#3-reserved-number-ranges)

---

## 1. Purpose

The `./` folder is the canonical numbered ADR library for this repository.

Use this folder for durable ADRs that fit one of the reserved architectural domains in the ADR taxonomy, including repository-wide process, software architecture, language-specific development practice, infrastructure, AI, containerization, operating systems, and monitoring.

---

## 2. File Roles

- [adr-005-ai-agile-and-context-driven-development.md](./adr-005-ai-agile-and-context-driven-development.md) — workflow ADR for treating documentation as operational context in AI-assisted delivery

## 3. Reserved Number Ranges

Canonical ADRs in `./` use reserved number ranges:

- `000-029` — software development process, project governance, and documentation process
- `030-099` — reserved
- `100-149` — language-independent architecture, design, and testing
- `150-199` — reserved
- `200-249` — TypeScript and JavaScript
- `250-299` — Python
- `300-399` — reserved
- `400-499` — AWS
- `500-599` — Azure
- `600-629` — GCP
- `630-649` — Ansible
- `650-669` — Puppet
- `670-699` — Terraform
- `700-709` — Bash
- `710-729` — PowerShell
- `730-799` — CI/CD, GitOps, and delivery automation
- `800-849` — working with AI
- `850-869` — Docker
- `870-899` — Kubernetes
- `900-919` — Linux
- `920-939` — Windows
- `940-959` — monitoring
- `960-999` — reserved

These numbers are separate from step-based implementation document numbers.
