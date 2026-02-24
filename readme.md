## 项目内容

学习 Code Agent 相关的技巧，比如 rules、skills、Vibe Coding。

也许会提供一些经过测试的模板。


## 作用目录

需要将 rules、skills 放到下面的目录。

```
# 项目级
project/.cursor/rules/
  react-patterns.mdc       # Rule with frontmatter (description, globs)
  api-guidelines.md        # Simple markdown rule
  AGENTS.md				  # Global instructions
  frontend/                # Organize rules in folders
    AGENTS.md              # Frontend-specific instructions
    components.md
  backend
    AGENTS.md              # Backend-specific instructions
    
# 用户级（猜测，未实践）
~/.cursor/skills
~/.codex/skills
```

## rules

rules 就是一些提示词，用来约束 AI 的回复。

## skills

对工作流的封装。

每个 skill 必须有一个 SKILL.md

### 示例

- 目录结构

  ```
  .cursor/
  └── skills/
      └── deploy-app/
          ├── SKILL.md
          ├── scripts/
          │   ├── deploy.sh
          │   └── validate.py
          ├── references/
          │   └── REFERENCE.md
          └── assets/
              └── config-template.json
  ```

- SKILL.md

  ```
  ---
  name: my-skill
  description: Short description of what this skill does and when to use it.
  ---
  # My Skill
  Detailed instructions for the agent.
  ## When to Use
  - Use this skill when...
  - This skill is helpful for...
  ## Instructions
  - Step-by-step guidance for the agent
  - Domain-specific conventions
  - Best practices and patterns
  - Use the ask questions tool if you need to clarify requirements with the user
  ```

- skill.md 支持属性

  | Field                      | Required | Description                                                  |
  | :------------------------- | :------- | :----------------------------------------------------------- |
  | `name`                     | Yes      | Skill identifier. Lowercase letters, numbers, and hyphens only. Must match the parent folder name. |
  | `description`              | Yes      | Describes what the skill does and when to use it. Used by the agent to determine relevance. |
  | `license`                  | No       | License name or reference to a bundled license file.         |
  | `compatibility`            | No       | Environment requirements (system packages, network access, etc.). |
  | `metadata`                 | No       | Arbitrary key-value mapping for additional metadata.         |
  | `disable-model-invocation` | No       | When `true`, the skill is only included when explicitly invoked via `/skill-name`. The agent will not automatically apply it based on context. |