# ChatGPT Account Migration Manual

> A high-fidelity methodology for manually migrating context, projects,
> conversations, files, preferences, and operational knowledge between
> ChatGPT accounts.

[![Documentation](https://img.shields.io/badge/docs-manual-blue)](MANUAL.md)
[![Language](https://img.shields.io/badge/language-PT--BR-green)](#)
[![Status](https://img.shields.io/badge/status-v1.0-blue)](#)

## Overview

Migrating between ChatGPT accounts is not simply a matter of copying
conversations.

A useful migration must preserve enough information for the destination
account to **continue the work**, including:

- preferences and interaction rules;
- project state;
- decisions and rejected alternatives;
- files and dependencies;
- conversation context;
- negative knowledge;
- cross-project relationships;
- uncertainty and conflicting information.

The central principle of this project is:

> **CONTINUABLE > COPIED**

The objective is not merely to reproduce historical content, but to
preserve enough operational context for work to continue correctly.

---

## 📖 Full manual

The complete step-by-step methodology is available here:

### **[→ Read the Full Migration Manual](MANUAL.md)**

The manual includes:

- account snapshot;
- memory/context extraction;
- project inventory;
- conversation classification;
- file inventory;
- migration capsules;
- project-state reconstruction;
- privacy classification;
- validation procedures;
- coexistence strategy;
- reconciliation with a future data export.

---

## 🧭 Migration model

```text
Account snapshot
      ↓
Memory & inference audit
      ↓
Project inventory
      ↓
PROJECT_STATE
      ↓
Conversation inventory
      ↓
File inventory
      ↓
Destination configuration
      ↓
Bootstrap
      ↓
Project reconstruction
      ↓
Conversation migration
      ↓
Validation
```

---

## 🧩 Templates

Reusable Markdown templates derived from the v1.0 migration manual are
available in the [`templates/`](templates/) directory.

They provide structured artifacts for:

- account profile and portable memory;
- project, conversation, and file inventories;
- project state and migration capsules;
- negative knowledge and cross-project relationships;
- migration manifests and checkpoints;
- validation and Golden Set testing;
- legacy GPT preservation.

> [!WARNING]
> The templates in this repository contain no user-specific data. However,
> completed copies may contain personal, professional, academic, legal,
> financial, or third-party information. Copy the templates to a private
> workspace before filling them in, and do not commit completed migration
> artifacts to this public repository.

The conceptual authority remains the
[full migration manual](MANUAL.md).

---

## 🔎 Provenance

The public template set was extracted and validated against the canonical
v1.0 migration manual.

The extraction report documents source verification, fidelity checks,
privacy review, known manual inconsistencies, and differences from an
earlier non-canonical extraction:

[→ Template Extraction Report v1.0](docs/provenance/TEMPLATE_EXTRACTION_REPORT_v1.0.md)

---

## License

This project is licensed under the
[Creative Commons Attribution 4.0 International License](LICENSE).

You may share and adapt the material, including for commercial purposes,
provided that appropriate attribution is given and changes are indicated.