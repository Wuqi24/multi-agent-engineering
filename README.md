[English](README.md) | [简体中文](README.zh-CN.md)

# multi-agent-engineering

> Beta v0.1.0 · Personal Codex Skill · Gate-based Multi-Agent Engineering Workflow

**One-liner: turn code changes from "just do it" into five verifiable Gates — Read-Only Audit → Invariant Guardrails → Design Approval → Staged Implementation → Independent Regression — scaled by task size, so AI changes are safe and auditable.**

---

## Positioning

### What It Is

- **Lightweight engineering workflow guardrails**: doesn't write project code; only turns the change process into verifiable Gates
- **An executable collaboration workflow for AI**: six temporary roles + handoff templates + Gate acceptance; process has artifacts, not just chat history
- **Generic**: works for CLI / Web / Data / automation scripts, and non-code engineering workflows
- **Scaled by size**: Spike / Bounded / Architectural — small tasks aren't crushed by process
- **Pure Markdown**: zero dependencies, auditable, versionable, portable

### What It Is Not

- ✗ Not an agent orchestration framework — no Agent Registry, DAG, or Orchestrator
- ✗ Not a task manager — doesn't replace issue / todo
- ✗ Not a code generator — doesn't write features; only constrains how changes are made
- ✗ Not a security scanner — use [skillspector-scan](https://github.com/Wuqi24/skillspector-scan) for skill security review

### Why Use It

**Problem**: AI changes code directly; boundaries get broken, regression is hard to verify, and multi-role collaboration depends on chat history.

**Solution**: Gate the engineering process — every Gate has explicit Input / Allowed / Forbidden / Artifacts / Acceptance. Incomplete input auto-HOLDs; Gates cannot be skipped.

---

## Five Gates

| Gate | Name | Goal | Key Constraint |
|---|---|---|---|
| Phase 0 | Audit | Read-only audit; current state & risks | No code changes |
| Phase 1 | Invariant | Freeze architecture boundaries as verifiable constraints | Test protection, no refactor |
| Phase 2 | Design | Design first; produce an approved plan | No implementation before approval |
| Phase 3 | Implementation | Minimal changes within frozen boundaries | No scope creep |
| Phase 4 | Regression | Independently restore / verify the baseline | No product behavior changes |

## Scaling

| Path | Flow | When |
|---|---|---|
| Spike | P0 → P2 → P3 | Small experiment, single file, no long-term maintenance |
| Bounded | P0 → P1 → P2 → P3 | Small feature, localized change |
| Architectural | P0 → P4 (full) | Data model / identity / core boundary changes |

Scaling only reduces the number of phases, never the Gate checks. Spike is not a permanent bypass — upgrade is required when entering implementation, long-term maintenance, or architectural change.

## Six Roles

Temporary task roles, not permanent agents: **Auditor / Architect / Implementer / Reviewer / Regression / Documentation**. Each has its own responsibilities, inputs, outputs, and prohibitions with no overlapping boundaries (Auditor is read-only, Architect designs only, Implementer never expands scope, Reviewer stays independent, Regression never changes product behavior, Documentation never claims unverified facts).

---

## Quick Start

### Install

```powershell
git clone https://github.com/Wuqi24/multi-agent-engineering.git "$HOME\.codex\skills\multi-agent-engineering"
```

Restart Codex to activate. You can also download the zip from [Release](https://github.com/Wuqi24/multi-agent-engineering/releases) and extract it into your skills directory.

### Example Triggers

- "Run this project through the Gate workflow"
- "Do a read-only architecture audit before touching anything"
- "Add regression guardrails / invariant tests for this module"
- "Split the work across agents; produce a handoff plan first"
- "Land risky changes in stages"

---

## Directory Structure

```text
multi-agent-engineering/
├── SKILL.md            # Entry point & trigger conditions (<300 lines)
├── agents/             # Agent configuration
├── roles/              # Six role definitions
├── phases/             # Five Gate definitions
├── templates/          # handoff / gate-review / phase-report
├── checklists/         # preflight / regression-proof / commit-boundary
├── rules/              # identity-boundaries / commit-strategy / scaling / escalation
└── extensions/         # audit-history / traceability / compliance (optional)
```

---

## Version History

| Version | Date | Notes |
|---|---|---|
| 0.1.0 | 2026-08-16 | Beta: a general engineering workflow distilled from skillspector-scan evolution; first standalone release |

## Disclaimer

Personal, beta-quality skill provided AS-IS, without any express or implied warranty. Review before install; the author is not liable for any direct or indirect loss.
