# Interview Hub Plugin

A proof-of-concept Claude Code plugin that packages domain-specific skills for the [Interview Hub](https://github.com/lcarera/interview_hub) project.

This plugin gives Claude contextual knowledge about the Interview Hub codebase so it can guide you through common workflows without you having to explain the project's conventions each time.

## Skills included

| Skill | Trigger | What it does |
|-------|---------|--------------|
| `add-email-type` | Auto + `/add-email-type` | Walks through adding a new email notification type to the async email system |
| `create-migration` | `/create-migration` only | Generates a sequentially-numbered Supabase migration file |
| `pr-check` | `/pr-check` only | Runs backend + frontend tests locally before creating a PR |
| `prod-debug` | Auto + `/prod-debug` | Guides production debugging on Cloud Run (logs, secrets, common errors) |

**Auto** means Claude will invoke the skill automatically when it detects a relevant request (e.g., "add a welcome email" or "check the prod logs"). Skills marked with **only** require an explicit slash command.

## Installation

### Via CLI

```bash
# Add this repo as a marketplace source
claude plugin marketplace add lcarera/interview_hub_plugin

# Install the plugin
claude plugin install interview-hub@interview_hub_plugin
```

### Via Desktop App

1. Open **Customize** > **Personal plugins**
2. Click **+ Create plugin** > **Add marketplace**
3. Enter `lcarera/Interview-Hub-Plugin` (or the full repo URL)

The plugin's skills will appear under the **Skills** section in the Customize panel.

## Creating your own plugin

If you want to create your own Claude Code plugin, install the [plugin-dev](https://github.com/anthropics/claude-plugins-official) plugin. It includes skills and agents for scaffolding plugins, writing skills, creating hooks, and validating your plugin structure:

```bash
claude plugin marketplace add anthropics/claude-plugins-official
claude plugin install plugin-dev
```

## Plugin structure

```
Interview-Hub-Plugin/
├── .claude-plugin/
│   ├── plugin.json          # Plugin manifest
│   └── marketplace.json     # Marketplace index
├── skills/
│   ├── add-email-type/
│   │   └── SKILL.md
│   ├── create-migration/
│   │   └── SKILL.md
│   ├── pr-check/
│   │   └── SKILL.md
│   └── prod-debug/
│       └── SKILL.md
└── README.md
```
