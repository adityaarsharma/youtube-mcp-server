# Contributing to YouTube Marketing Skills

Contributions welcome — especially niche-specific templates, reference guide improvements, and new sub-skills for underserved channel types.

## What to Contribute

### Add a channel template
The `skills/youtube-marketing/templates/` folder has configs for different channel archetypes. If you have data for a niche not covered (e-commerce, gaming, finance, tech reviews), add a template file following the existing pattern.

### Improve a reference guide
The `skills/youtube-marketing/references/` folder has focused knowledge guides. If you have a published study or benchmark that's missing, add it with a source citation.

### Add a sub-skill
The `skills/youtube-marketing/sub-skills/` folder has 21 command files. If there's a workflow missing for YouTube creators, propose it as an issue first.

### Fix or improve an existing skill
All `.md` files are plain Markdown — edit and PR.

## Guidelines

- **Sub-skills**: Under 200 lines, self-contained, includes output format template
- **Reference guides**: Under 200 lines, focused on one topic, all data cited with source + year
- **Templates**: Channel-specific constants only — products, links, publish time, audience
- **No hardcoded credentials or API keys** anywhere in the repo
- **Naming**: kebab-case for all files (`my-skill.md`, not `MySkill.md`)

## Steps

1. Fork the repo
2. Create a branch: `git checkout -b add-gaming-template`
3. Make your change
4. Open a PR with a clear title and 1-2 sentence description of what you added

## Issues

Use GitHub Issues for:
- Bug reports (skill output is wrong or missing)
- Feature requests (new commands, new templates)
- Data updates (a benchmark in a reference guide is outdated)

Label your issue: `bug`, `enhancement`, `new-template`, or `data-update`.
