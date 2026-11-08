# Task Specification Template

> 提示：在由 Engineer Agent 编写代码之前，PM Agent 或开发者必须按此模版完成任务 Grooming。

## 1. Goal (目标) 
- [用 1-2 句话清晰定义本任务完成后要达到的最终状态]

## 2. Acceptance Criteria (可客观化验的验收标准) 
- [ ] [标准 1：必须是具备二元结果（YES/NO）的明确陈述，如：运行 `uv run pytest tests/test_auth.py` 全绿通过]
- [ ] [标准 2：如：POST `/api/v1/login` 在密码错误时返回 HTTP 401 及标准错误 JSON]
- [ ] [标准 3：如：未授权用户访问 `/dashboard` 自动重定向至 `/login`]

## 3. Out of Scope (排除范围) 
- [明确本次改动绝不能涉及的内容，防止 Agent 盲目扩展或做额外假设]
- 例如：暂不实现 OAuth 2.0 第三方登录（留待后续 Issue）
- 例如：暂不进行 CSS 样式细化与 UI 动画调整

## 4. Constraints (约束条件)
- **Tech Stack & Libraries**: 仅使用 `pyproject.toml` 中已有的依赖，未经许可不得引入新包。
- **File Boundaries**: 修改范围原则上限制在 `src/services/` 目录下。
- **Quality Gate**: 必须提供对应的 pytest 测试用例，且保证通过率 100%。
