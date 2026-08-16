# multi-agent-engineering

> 状态：测试版（v0.1.0）· 个人自制 Codex Skill

Gate 化多 Agent 协作研发工作流：把项目推进拆成 **只读审计 → 不变量护栏 → 设计批准 → 分阶段实施 → 独立回归** 五道 Gate，并按任务规模缩放（Spike / Bounded / Architectural）。适用于 CLI、Web、数据、自动化脚本等软件项目，也适用于非代码工程流程。

## 核心模型

五道 Gate，每道都有 Input / Goal / Allowed / Forbidden / Artifacts / Acceptance：

| Gate | 名称 | 目标 | 关键约束 |
|---|---|---|---|
| Phase 0 | Audit | 只读审计，产出现状与风险 | 不修改代码 |
| Phase 1 | Invariant | 把架构边界固化为可验证约束 | 测试保护，不重构 |
| Phase 2 | Design | 设计先行，产出批准方案 | 未批准不实施 |
| Phase 3 | Implementation | 最小修改，守住冻结边界 | 不做范围外改动 |
| Phase 4 | Regression | 独立恢复/验证基线 | 不改产品行为 |

Input 不完整时 Gate 自动 HOLD；Gate 不可跳过。

## 规模缩放

| 路径 | 流程 | 适用 |
|---|---|---|
| Spike | P0 → P2 → P3 | 小实验、单文件、无长期维护 |
| Bounded | P0 → P1 → P2 → P3 | 小功能、局部修改 |
| Architectural | P0 → P4（完整） | 数据模型/身份/核心边界变化 |

缩放只减少流程数量，不取消 Gate 判断；Spike 不是永久绕过，进入实施/维护/架构变化时必须升级。

## 角色

六种临时任务角色（不是永久 Agent）：Auditor / Architect / Implementer / Reviewer / Regression / Documentation。每个角色都有职责、输入、输出与禁止事项，边界不重叠。

## 安装

```powershell
# 复制到技能目录（Windows）
Copy-Item -Recurse multi-agent-engineering "$env:USERPROFILE\.codex\skills\multi-agent-engineering"
```

重启 Codex 后生效。

## 使用

当任务满足以下任一信号时使用：

- 用户要求按 Gate 流程推进项目、先审计再动手
- 需要建立回归护栏/不变量测试
- 拆 Agent 协作、交接、审查
- 风险改动需要分阶段落地

## 目录结构

```text
multi-agent-engineering/
├── SKILL.md            # 入口与触发条件（<300 行）
├── agents/             # Agent 配置
├── roles/              # 六角色定义
├── phases/             # 五 Gate 定义
├── templates/          # handoff / gate-review / phase-report
├── checklists/         # preflight / regression-proof / commit-boundary
├── rules/              # identity-boundaries / commit-strategy / scaling / escalation
└── extensions/         # audit-history / traceability / compliance（可选扩展）
```

## 版本历史

| 版本 | 日期 | 说明 |
|---|---|---|
| 0.1.0 | 2026-08-16 | 测试版：基于 skillspector-scan 演进提炼的通用工程流程，首次独立发布 |

## 责任声明

本 Skill 为个人自制测试版本，按"现状"提供，不提供任何明示或暗示的保证。使用者应自行审查其内容与适用性；因使用本 Skill 造成的任何直接或间接损失，作者不承担责任。发布/修改前请自行做安全审查。
