# Phase 1 — Invariant Gate

## Input

- Phase 0 Audit Report；已确认风险与边界清单
- 来源：Audit Gate

## Goal

把关键架构约束固化为回归测试（护栏）。

## Allowed

- 只加测试与测试文档

## Forbidden

- 改核心逻辑、改评分/决策/业务语义、删既有测试

## Required artifacts

- 不变量 ↔ 测试映射；护栏测试；独立验证结果（非代码项目护栏见 Non-code Project Invariants）

## Acceptance

- 护栏在真实目标上通过（或失败项可分类且与产品行为无关）

## Non-code Project Invariants

当项目不是传统代码项目时，Invariant Gate 仍然存在；护栏形式按项目类型选择。

### 1. Executable Artifact（CLI / Script / Application）

- 优先：自动化测试、机检脚本、CI 检查

### 2. Document / Configuration Artifact

- 优先：检查清单、结构校验、人工复核记录

### 3. Mixed Artifact

- 组合：自动检查 + 文档约束 + Review checklist

明确：Invariant 不等于测试代码。Invariant 是"未来变化不能破坏的可验证约束"。

Acceptance 示例：

- 可执行产物：机检脚本退出码为 0，且新增规则有对应检查项
- 文档产物：检查清单逐项可复核，关键约束有明确验收人与复核记录
- 混合产物：自动检查通过 + 文档约束无漂移 + Review checklist 完成
