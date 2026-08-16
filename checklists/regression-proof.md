# Regression Proof（回归证明四件套）

提交前必须输出：

1. Failure Inventory：失败项 / 类型 / 是否产品问题
2. Root Cause：现象 / 原因 / 最小修复 / 风险
3. Diff Review：修改文件 / 新增 / 删除 / 未触碰；关键边界显式声明 unchanged
4. Regression Proof：护栏测试 + 既有测试均可运行

禁止：为测试通过修改产品行为；删除测试；skip 掩盖。
