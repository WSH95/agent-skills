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

Grok Build discovers these skills after `npx skills add` (it scans
`~/.agents/skills` and `~/.claude/skills`). Run them as
`/paper-polish-standalone` or `/paper-review-standalone`.


## Skills

- [statusline-designer](#statusline-designer-use-case) - design and customize the Claude Code terminal status line through a local web UI.
- [paper-polish-standalone](#paper-polish-standalone-use-case) - multi-pass polishing of a finished paper draft (structure, clarity, claim calibration, concision, title check) returning a before/after revision report — no project setup required.
- [paper-review-standalone](#paper-review-standalone-use-case) - mock peer review of a finished paper draft through five reviewer lenses plus an evidence-cited area-chair meta-review — no project setup required.
- [openmausbot-launcher](#openmausbot-launcher-use-case) - operate a headless OpenMausBot bot team from your agent host: start and stop the server, import or write a team package, bind engines, brief the lead bot, watch the delegation chain, relay its questions and your answers, reconcile the repository, clean up, report.

### Use Case

#### statusline-designer Use Case

![statusline-designer demo](https://raw.githubusercontent.com/WSH95/statusline-designer-dev/main/docs/status-bar-composer-demo.gif)

Type `/statusline-designer` whenever you want to set up, change, redesign, or add fields to your Claude Code status line (statusline / bottom bar). It opens a local web designer with a live terminal preview, then generates the status-line script and wires it into settings.json. The skill is user-invoked: it runs only when you ask for it by name.

Example interactions:

- `/statusline-designer` - open the designer, and apply whatever you build
- `/statusline-designer` again later - it re-hydrates your current layout so you can tweak it
- `python3 ~/.claude/skills/statusline-designer/scripts/open_designer.py` - the same end-to-end flow with no agent involved; Apply to Terminal keeps the designer open for more tweaking, Apply & Close applies and shuts it down

#### paper-polish-standalone Use Case

Use paper-polish-standalone to line-edit a finished academic paper draft without any project setup: upload the PDF (or paste the text), confirm scope and a concision target, and receive a revision report of numbered before/after comparisons covering structure, clarity and flow, claim calibration, concision, a mechanical sweep, and a title check.

Example interactions:

- Upload a paper PDF and ask: polish this draft with paper-polish-standalone.
- We are one page over the limit — tighten the paper by 15%.
- Proofread the methods section and calibrate its claims.

#### paper-review-standalone Use Case

Use paper-review-standalone for a mock peer review of a finished academic paper draft without any project setup: upload the PDF (or paste the text), optionally answer a few calibration questions (venue, paper type, contributions, worries), and receive one report containing five structured lens reviews plus an area-chair meta-review that rules on every major weakness with cited evidence and ranks the must-fix items.

Example interactions:

- Upload a paper PDF and ask: run paper-review-standalone before I submit.
- What would reviewers say about this draft at CoRL?
- Red-team this paper and give me the top five must-fix items.

#### openmausbot-launcher Use Case

Use openmausbot-launcher when you have, or want, an OpenMausBot bot team and would rather drive it from your agent host - Claude Code, Codex CLI, Grok Build, OpenClaw, Hermes Agent or DeepSeek Harness - than from the desktop app. The skill is user-invoked: it runs only when you ask for it by name. It needs a separately installed `openmausbot` 0.1.56 (the headless server, on `PATH` or named by `OMB_BIN`), Node 24, and a git project with a test command; every bot turn runs a real coding CLI on your own subscriptions. Setting a project up starts with `doctor`; the operator's own instructions are the skill's `SKILL.md`, and `README.md` inside the skill is the entry point for the person installing it.

Example interactions:

- `/openmausbot-launcher do T10 in ~/proj` - on first use it sets the project up (doctor, server, import, bind, facts), then briefs the lead and watches the chain until it settles or needs you.
- `/openmausbot-launcher write a team package for reviewing pull requests` - an interview, one question at a time; a summary you confirm; then the `.openmaus.json` file, validated offline before you import it.
- `/openmausbot-launcher status --project ~/proj` - one snapshot of the team and its open runs, no bot turn spent.
- `/openmausbot_launcher status` in an OpenClaw Telegram chat - the same from a phone; `$openmausbot-launcher <request>` in Codex.

## License

MIT. See [LICENSE](LICENSE).
