# Omni Studio Engine

Omni Studio Engine is an AI digital product delivery skill for turning Figma designs into production web products with design-system extraction, pixel-level implementation, responsive behavior, interaction polish, and deployment.

It is designed for:

- SaaS products
- Dashboards
- Landing pages
- Web3 products
- AI products
- Design-led marketing or product sites

## What It Does

- Reads Figma designs and design assets
- Extracts design tokens and reusable components
- Builds a maintainable component system
- Implements pages with pixel-level fidelity
- Adds responsive rules, animation, and interaction
- Reviews visual details section by section
- Deploys the finished project

## Codex Installation

Copy the skill folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R omni-studio-engine ~/.codex/skills/
```

Restart Codex, then use:

```text
Use Omni Studio Engine

Figma:
<figma-url>

目标：
将整个项目开发并部署上线

要求：
- 100%还原
- 保持设计系统一致
- 自动生成组件库
- 自动部署
```

## Other AI Agents

For Claude Code, Cursor, Windsurf, Gemini CLI, or another agent, provide the contents of:

- `omni-studio-engine/SKILL.md`
- `omni-studio-engine/references/pixel-review.md`
- `omni-studio-engine/references/implementation.md`
- `omni-studio-engine/references/deployment.md`

Use this instruction:

```text
First read omni-studio-engine/SKILL.md. When needed, read the reference files.
Follow Omni Studio Engine to implement the Figma design as a production-ready product:
design tokens, component system, pixel-level layout, responsive rules, animation, QA, and deployment.
```

## Repository Structure

```text
omni-studio-engine/
  SKILL.md
  agents/
    openai.yaml
  references/
    deployment.md
    implementation.md
    pixel-review.md
```

## Philosophy

This is not a generic Figma-to-code converter. It is a disciplined delivery process for AI-assisted product work: read the design, build the system, implement from top to bottom, review carefully, iterate until the details are right, and ship maintainable code.
