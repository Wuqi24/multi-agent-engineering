# Preflight（只读审计最小集）

逐项检查：

- 项目结构与关键文件
- 数据流分层与边界（事实/证据/解释/排序/决策，按项目实际）
- 高冲突文件与单文件瓶颈
- 可并行与必须串行的任务
- Token/Context 重复读取点
- ROI 排序（哪些值得做、哪些不值得）

## Gate Artifact Naming Convention

每个 Gate 输入必须具备：

- 明确文件名
- 来源 Phase
- 生成时间
- 状态（PASS/HOLD/FAIL）

Input 不完整：自动 HOLD。
