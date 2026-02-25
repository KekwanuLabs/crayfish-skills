# Crayfish Skill Hub

Community skills for [Crayfish](https://github.com/KekwanuLabs/crayfish) — a personal AI assistant that runs on anything from a Raspberry Pi to a workstation.

## What are Skills?

Skills are YAML files that teach your Crayfish new tricks. They combine triggers, tool chains, and prompt templates into reusable automations. No code required.

## Installing Skills

**Via conversation** (Telegram or CLI):
- "What skills are available?" — browse the hub
- "Install morning-briefing" — install by name
- "What skills do I have?" — list installed skills

**Via dashboard**:
- Go to Skills tab > Browse Hub > click Install

**Via URL** (any skill, anywhere):
- Tell your Crayfish: "Install the skill at https://example.com/my-skill.yaml"

## Available Skills

| Skill | Type | Description |
|-------|------|-------------|
| morning-briefing | workflow | Daily morning briefing with email summary and tasks |
| email-triage | workflow | Triage and prioritize unread emails by urgency |
| smart-search | workflow | Search the web and synthesize a clear answer |
| weekly-review | workflow | Weekly review of emails, tasks, and activity |
| focus-mode | prompt | Minimize interruptions and batch notifications |
| quick-capture | workflow | Save a thought, idea, or note to memory |
| meeting-prep | workflow | Prepare for your next meeting with context from email and calendar |
| email-autoresponder | workflow | Draft quick replies to emails that need a response |
| daily-journal | workflow | Evening journal prompt to reflect on your day |
| expense-tracker | workflow | Find receipts and purchase confirmations in your email |
| reminder-set | workflow | Set a reminder and get nudged when it's time |
| day-planner | workflow | Plan your day based on calendar, todos, and email |
| email-followup | workflow | Find emails you sent that never got a reply |
| schedule-finder | workflow | Find free time in your calendar for a new meeting or task |
| news-digest | workflow | Get a quick news summary on any topic |
| email-unsubscribe | workflow | Find newsletters and subscriptions cluttering your inbox |
| contact-recap | workflow | Get a recap of all interactions with a specific person |
| standup-report | workflow | Generate a standup report from yesterday's activity |

## Skill Types

- **workflow** — Runs a sequence of tools, then uses the results to generate a response
- **prompt** — Adds context to the system prompt to change how Crayfish behaves
- **reactive** — Triggers automatically when a specific event happens (new email, etc.)

## Contributing

1. Create a YAML skill file following the format in `skills/`
2. Test it locally by dropping it in your Crayfish `skills/` directory
3. Open a PR adding your skill file to `skills/` and an entry to `index.json`

### Skill YAML Format

```yaml
name: my-skill
version: 1
description: "What this skill does in one sentence"
author: "Your Name"
type: workflow  # workflow, prompt, or reactive
min_tier: trusted

trigger:
  command: "/myskill"           # slash command
  schedule: "0 9 * * 1-5"      # cron expression (optional)
  keywords:                     # natural language triggers (optional)
    - "run my skill"
    - "do the thing"

steps:
  - tool: email_check
    params: {}
    store_as: emails

prompt: |
  Use the results to help the user.
  Emails: {{emails}}
```

### Rules

- No shell execution — skills can only invoke registered Crayfish tools
- Prompts must be under 50KB
- Skills are validated for safety before installation
- Keep it useful for everyday people — this isn't a developer tool

## License

MIT
