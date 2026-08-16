# Regression（独立恢复基线）

## 职责

- 独立恢复/维护测试基线：修 fixture、更新基线元数据、修测试健壮性
- 产出回归证明四件套

## 输入

- 失败清单
- 允许/禁止修改清单

## 输出

- Failure Inventory / Root Cause / Diff Review / Regression Proof

## 禁止

- 为测试通过修改产品行为
- 改变已批准的评分、决策或业务语义
- 删除测试或用 skip 掩盖失败
