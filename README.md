# Things 3 Skill for Claude

A [Claude Skill](https://support.anthropic.com/en/articles/11147530-how-do-i-create-and-manage-claude-s-skills) that generates clickable import links for [Things 3](https://culturedcode.com/things/) directly from your conversations.

Drop a briefing, meeting notes, or anything on your mind — Claude generates a clean HTML preview of the proposed tasks. One click and everything imports into Things automatically via the `things:///json` URL scheme.

## What it does

- **Generates Things 3 import links** from any conversation that produces actionable tasks
- **Supports the full Things data model**: projects with headings, to-dos with checklists, tags, areas, deadlines
- **Adapts to your workspace**: learns your areas, projects, and tags on first use
- **Respects tag inheritance**: won't duplicate tags already carried by parent areas or projects
- **Follows productivity best practices** (inspired by the [FU-Master methodology](https://productivewithapurpose.com/2019/05/21/the-fu-master-productivity-checklist-using-things3/)): deadlines over scheduling, Anytime by default, next actions only
- **Splits large task lists** (15+) into multiple logical links
- **Delivers as HTML** with a clean dark-themed preview — click to import in Safari

## Install

1. Download [`things-todo.skill`](./things-todo.skill)
2. In Claude, go to **Settings → Skills**
3. Drop the `.skill` file to install it

## Setup

On first use, Claude will ask you to share your Things 3 structure:

- **Areas** — your ongoing life/work buckets (e.g. Work, Home, Side Projects)
- **Active projects** — projects currently in progress
- **Tags** — your tag list, including emojis if your tag names contain them (names must match exactly)

Claude stores this in memory so you only need to do it once. Update anytime by saying "update my Things tags" or "j'ai un nouveau projet".

## Usage

Just talk to Claude as usual. The skill triggers automatically when:

- You ask for a todo list, task plan, or next steps
- A conversation lands on concrete actions
- You say things like "send this to Things", "make a task list", "crée les tâches"

Claude will generate an HTML file — open it in Safari and click the import button.

### Example

> **You:** I just had a client call about the website redesign. We need to finalize the wireframes by next Friday, get copy from Sarah, and schedule a review meeting with the team.

> **Claude:** → New project in **Work** · 3 tasks
>
> - Finalize wireframes · deadline March 21
> - Request copy from Sarah
> - Schedule team review meeting
>
> *[generates HTML file with import link]*

## How it works

The skill uses the [Things 3 JSON URL scheme](https://culturedcode.com/things/support/articles/2803573/) (`things:///json?data=...`) to create import links. It:

1. Structures tasks as JSON following the Things schema
2. URL-encodes the payload
3. Wraps it in a clean HTML page with task preview
4. Delivers via `present_files` for you to open in Safari

## Limitations

- `things:///` links don't work inside the Claude chat interface — hence the HTML file delivery
- Tags must already exist in your Things app to be applied (Things ignores unknown tags silently)
- Very large task sets (30+) may hit URL length limits — the skill splits them automatically

## Credits

Built with [Claude Skills](https://support.anthropic.com/en/articles/11147530-how-do-i-create-and-manage-claude-s-skills) by [@viktorvuka](https://viktorvuka.fr).

## License

MIT
