[English](README.en.md) | [简体中文](README.md)

# multi-agent-engineering 中文文档
> 测试版 v0.1.0 · 个人自制 Codex Skill · Gate 化多 Agent 协作研发工作流

**一句话定位：把软件的改动从"直接动手"变成"五道可验证的 Gate"——只读审计 → 不变量护栏 → 设计批准 → 分阶段实施 → 独立回归，按任务规模缩放，让 AI 改得安全、改得可审计。**

---

## 定位

### 这是什么

- **轻量工程流程护栏**：不替项目写代码，只把改动过程变成可验证的 Gate
- **AI 可执行的协作流程**：六个临时角色 + 交接模板 + Gate 验收，过程有载体、不靠聊天记录
- **通用**：适用于 CLI / Web / 数据 / 自动化脚本等软件项目，也适用于非代码工程流程
- **按规模缩放**：Spike / Bounded / Architectural 三档，小任务不被流程压垮
- **纯 Markdown**：零依赖、可审计、可版本化、可移植

### 这不是什么

- ❌ 不是 Agent 编排框架——不建 Agent Registry、DAG、Orchestrator
- ❌ 不是任务管理系统——不替代 issue / todo
- ❌ 不是代码生成器——不替 AI 写功能，只约束"怎么改"
- ❌ 不是安全扫描器——技能安全审查请用 [skillspector-scan](https://github.com/Wuqi24/skillspector-scan)

### 为什么用它

**问题**：AI 直接改代码，边界易被破坏、回归难验证、多角色协作只能靠聊天记录。

**方案**：把工程推进 Gate 化——每道 Gate 有明确的 Input / Allowed / Forbidden / Artifacts / Acceptance，改动可验证、过程可审计、交接有模板。Input 不完整自动 HOLD，Gate 不可跳过。

---

## 五道 Gate

| Gate | 名称 | 目标 | 关键约束 |
|---|---|---|---|
| Phase 0 | Audit | 只读审计，产出现状与风险 | 不修改代码 |
| Phase 1 | Invariant | 把架构边界固化为可验证约束 | 测试保护，不重构 |
| Phase 2 | Design | 设计先行，产出批准方案 | 未批准不实施 |
| Phase 3 | Implementation | 最小修改，守住冻结边界 | 不做范围外改动 |
| Phase 4 | Regression | 独立恢复/验证基线 | 不改产品行为 |

## 规模缩放

| 路径 | 流程 | 适用 |
|---|---|---|
| Spike | P0 → P2 → P3 | 小实验、单文件、无长期维护 |
| Bounded | P0 → P1 → P2 → P3 | 小功能、局部修改 |
| Architectural | P0 → P4（完整） | 数据模型/身份/核心边界变化 |

缩放只减少流程数量，不取消 Gate 判断；Spike 不是永久绕过，进入实施/维护/架构变化时必须升级。

## 六角色

临时任务角色，不是永久 Agent：**Auditor / Architect / Implementer / Reviewer / Regression / Documentation**。每个角色都有职责、输入、输出与禁止事项，边界不重叠（Auditor 只读、Architect 只设计、Implementer 不扩范围、Reviewer 独立、Regression 不改产品行为、Documentation 不宣称未验证事实）。

---

## 快速上手

### 安装

```powershell
git clone https://github.com/Wuqi24/multi-agent-engineering.git "$HOME\.codex\skills\multi-agent-engineering"
```

重启 Codex 后生效。也可以从 [Release](https://github.com/Wuqi24/multi-agent-engineering/releases) 下载 zip 解压到技能目录。

### 触发示例

- "按 Gate 流程推进这个项目"
- "先做只读架构审计再动手"
- "给这个模块建立回归护栏/不变量测试"
- "拆 Agent 协作，先出交接方案"
- "风险改动分阶段落地"

---

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

---

## 版本历史

| 版本 | 日期 | 说明 |
|---|---|---|
| 0.1.0 | 2026-08-16 | 测试版：基于 skillspector-scan 演进提炼的通用工程流程，首次独立发布 |

## 责任声明

本 Skill 为个人自制测试版本，按"现状"提供，不提供任何明示或暗示的保证。使用者应自行审查其内容与适用性；因使用本 Skill 造成的任何直接或间接损失，作者不承担责任。安装/使用前请自行做安全审查。
