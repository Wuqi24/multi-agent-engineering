# Commit Boundary（提交边界检查）

提交前逐项确认：

- diff 只含允许文件
- 无跨 Phase 偷渡修改
- 文档 commit 与代码 commit 分离
- 无未授权改动（核心身份模型 / 评分 / 决策 / 业务语义 / 验证边界）
- 基线元数据已同步（如核心文件哈希）
- 关键边界文件在 Diff Review 中显式声明 unchanged
