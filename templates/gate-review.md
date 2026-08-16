# Gate Review

## Verdict

PASS / HOLD / FAIL

## Evidence

- `逐条事实：commit、测试输出、diff、报告；区分事实与推断`

## Risks

- `未阻塞但需跟踪的风险`

## Blocking Issues

- `阻断项；每项给位置/根因/最小修复建议`

## Next Action

- `唯一建议的下一步：进入下一 Phase / 返工 / 转交`

## Reviewer Independence

- `审查者与实现者是否隔离；不默认相信实现者的声明`

## 已完成示例（仅演示，非强制规范）

```text
Verdict: PASS
Evidence:
- pwsh check_markdown.ps1 SKILL.md -> EXIT=0
- 触发词清单 9 项逐项核对通过
Risks:
- 文档类验收依赖人工复核记录
Blocking Issues:
- 无
Next Action:
- 进入 Design Gate
Reviewer Independence:
- 审查由独立会话执行，未参与实现
```
