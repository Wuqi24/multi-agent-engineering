# Commit Strategy

- 一个 Phase 一个责任边界：Gate 产物（文档/契约）与实现（代码/测试）分 commit
- 文档 commit 与代码 commit 分离：`docs:` / `contracts:` 与 `feat:` / `test:` 不混装
- 禁止跨 Phase 偷渡修改：Phase N 的改动不得夹带 Phase N+1 的内容
- 小步提交：单 commit 只做一件事，信息可追溯
- 提交前跑 `checklists/commit-boundary.md` 检查
- 缩放不影响提交纪律：即使走 Spike，改动仍需独立可追溯 commit
