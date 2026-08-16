# Workflow Scaling Rules

同一套 Gate，按任务规模缩放流程数量；**Gate 判断永远不可取消**。

## Spike

- 适用：小实验、单文件、无长期维护
- 流程：Phase 0 → Phase 2 → Phase 3
- 说明：跳过不变量护栏与独立回归门；结果以结论/一次性产物交付

## Bounded Change

- 适用：小功能、局部修改（不触及核心身份与语义）
- 流程：Phase 0 → Phase 1 → Phase 2 → Phase 3
- 说明：可以省独立 Phase 4；但 **Phase 3 必须包含完整验证、回归证明、结果记录**，不能理解为跳过验证

## Architectural Change

- 适用：数据模型变化、身份变化、核心边界变化
- 流程：Phase 0 → 1 → 2 → 3 → 4（完整）

## 规则

- 缩放只能减少流程数量，不能取消 Gate 判断
- 拿不准时选更重的一路
- 中途发现隐藏复杂度只能升级路径（Spike → Bounded → Architectural），不能降级
