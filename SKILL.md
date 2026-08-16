---
name: multi-agent-engineering
description: Gate 化多 Agent 协作研发工作流：把项目推进拆成 只读审计 → 不变量护栏 → 设计批准 → 分阶段实施 → 独立回归 五道 Gate，并按任务规模缩放（Spike/Bounded/Architectural）。当用户要求"按 Gate 流程推进项目""先做架构审计再动手""建立回归护栏/不变量测试""拆 Agent 协作/交接/审查""风险改动分阶段落地"时使用；适用于 CLI、Web、数据、自动化脚本等任何软件项目，也适用于非代码工程流程。
metadata:
  short-description: "Gate 化多 Agent 协作研发工作流：Audit 到 Regression 五道 Gate，按 Spike/Bounded/Architectural 缩放。"
  version: 0.1.0
  status: beta
---

# Multi-Agent Engineering

把模糊的工程推进变成五道可验证的 Gate：Audit → Invariant → Design → Implementation → Regression。角色是临时任务角色，不是永久 Agent；规则使用通用工程语言，不绑定任何具体项目。

## 何时使用

- 用户要求按 Gate 流程推进项目、先审计再动手、建立回归护栏、拆 Agent 协作/交接/审查
- 任何需要"边界受保护、改动可验证、过程可审计"的工程流程

## When Not To Use

以下情况通常不需要使用本技能：

- 一次性简单修改
- 单文件低风险编辑
- 无跨角色协作需求
- 无长期维护价值
- 无需要验证边界的任务

如果任务规模扩大，可通过 scaling rules 升级进入本流程。

拿不准时默认使用（与 scaling rules 的"拿不准选更重的一路"一致）。

## 流程导航

- `phases/phase-0-audit.md`：只读审计（Audit Gate）
- `phases/phase-1-invariant.md`：架构约束 → 回归测试（Invariant Gate）
- `phases/phase-2-design.md`：设计批准（Design Gate）
- `phases/phase-3-implementation.md`：最小实施（Implementation Gate）
- `phases/phase-4-regression.md`：独立恢复/验证基线（Regression Gate）
- 每阶段包含 Input / Goal / Allowed / Forbidden / Required artifacts / Acceptance

## 流程缩放

- 同一套 Gate，按任务规模减少流程数量，但 Gate 判断不可取消。详见 `rules/scaling.md`
- Spike：Phase 0 → 2 → 3
- Bounded：Phase 0 → 1 → 2 → 3（Phase 3 必须包含完整验证与回归证明）
- Architectural：Phase 0-4 完整
- Spike 路径不是永久绕过流程；如果任务进入实施、长期维护或架构变化，必须升级到 Bounded 或 Architectural

## 角色导航（临时任务角色）

- `roles/auditor.md` · `roles/architect.md` · `roles/implementer.md`
- `roles/reviewer.md` · `roles/regression.md` · `roles/documentation.md`
- 每个角色包含：职责 / 输入 / 输出 / 禁止

## 模板 / 清单 / 规则 / 扩展（按需读取）

- 交接：`templates/task-handoff.md`
- 审查：`templates/gate-review.md`
- 报告：`templates/phase-report.md`
- 前置检查：`checklists/preflight.md`（含 Gate 产物命名约定）
- 回归证明：`checklists/regression-proof.md`
- 提交边界：`checklists/commit-boundary.md`
- 规则：`rules/identity-boundaries.md` · `rules/commit-strategy.md` · `rules/scaling.md` · `rules/escalation.md`
- 可选扩展（核心流程不依赖）：`extensions/audit-history.md` · `extensions/traceability.md` · `extensions/compliance.md`

## 铁律

- 前一 Gate 未 PASS 不进入下一 Phase；HOLD/FAIL 阻断推进
- Input 不完整：Gate 自动 HOLD
- 发现需要改动已冻结边界才能继续：立即 STOP，报告，等确认
- 禁止修改 Phase 0/2 已冻结的项目核心身份模型；禁止改变已批准的评分、决策或业务语义；禁止绕过已有验证边界
- Reviewer 不默认相信实现者；发现者不自行修复并宣布通过
