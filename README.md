# Terraform State Migration Kit
### Moving backends without downtime or drift.

> **Architecture Principle:** State is the absolute source of truth. Moving it requires deterministic physics, not copy-paste.

## 📚 Canonical Architecture Reference  
This repository contains the migration sequences and `moved` block patterns for zero-downtime state transfers.

**The continuously maintained architectural specification lives here:** 👉 [https://www.rack2cloud.com/modern-infrastructure-iac-strategy-guide/](https://www.rack2cloud.com/modern-infrastructure-iac-strategy-guide/)

---

## The Accidental Destruction Trap
A common failure occurs when engineers attempt to manually copy state files or change the `backend` block without performing the proper initialization sequence. The consequence is Terraform losing the link to real-world resources, resulting in a "Plan: 50 to add, 50 to destroy" scenario.

## Safe Migration Checklist

| Operation | Risk Level | Required Tooling / Command |
| :--- | :--- | :--- |
| **Backend Change** | 🔴 High | `terraform init -migrate-state` |
| **Module Refactor** | 🟠 Medium | `moved` blocks (Terraform 1.1+) |
| **Resource Rename** | 🟠 Medium | `terraform state mv` |
| **Provider Update** | 🟡 Low | `terraform init -upgrade` |

---
**Star this repo for safe IaC operations.** *Maintained by [Rack2Cloud](https://www.rack2cloud.com)*
