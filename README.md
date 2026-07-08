# agent-skills

## Installing

Install available skills from this repository with:

```bash
npx skills add https://github.com/WSH95/agent-skills
```

To install one skill directly, use the GitHub shorthand with the skill
name:

```bash
npx skills add WSH95/agent-skills@<skill-name>
```

## Skills

- [statusline-designer](#statusline-designer-use-case) - design and customize the Claude Code terminal status line through a local web UI.

### Use Case

#### statusline-designer Use Case

![statusline-designer demo](https://raw.githubusercontent.com/WSH95/statusline-designer-dev/main/docs/status-bar-composer-demo.gif)

Invoke it whenever a user wants to set up, change, redesign, or add fields to their Claude Code status line (statusline / bottom bar). It opens a local web designer with a live terminal preview, then generates the status-line script and wires it into settings.json.

Example interactions:

- "design my status line"
- "show git branch and context % in my status bar"
- "add the 5-hour usage limit and session cost to my statusline"

## License

MIT. See [LICENSE](LICENSE).
