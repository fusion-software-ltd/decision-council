# Decision Council

Assemble AI advisors to debate decisions, cross-examine reasoning, and produce scored recommendations.

**By Fusion Software** · [fusionsoftware.com/decisioncouncil](https://fusionsoftware.com/decisioncouncil)

---

## What it does

Decision Council convenes a panel of five AI advisors — Optimist, Pessimist, Devil's Advocate, Pragmatist, and Behaviourist — to analyse any significant decision. Each advisor scores the decision independently, then the Chair orchestrates cross-examination where scores diverge, runs a consensus danger check, and synthesises a scored recommendation.

Handles three decision types:
- **Directional** — "Should we do this?" → PROCEED / DEFER / PASS / MODIFY
- **Comparative** — "Which option?" → Ranked with rationale
- **Binary** — "Go or no-go?" → YES / NO with conviction level

You can also define your own advisors — customer segments, stakeholders, competitors, team roles — or mix them with the pre-built analytical lenses.

## Installation

### Cowork (recommended)
1. Open the Claude Desktop app → Cowork tab
2. Click **Customize** in the left sidebar
3. Click **Browse plugins** or upload the plugin folder directly

### Claude Code
```bash
claude --plugin-dir ./decision-council
```

## Commands

| Command | Description |
|---|---|
| `/decision-council:convene [question]` | Convene a full council session (5 advisors, cross-examination, full synthesis) |
| `/decision-council:debrief` | Post-session debrief — dashboard, challenge, record decision, feedback |
| `/decision-council:quick [question]` | Quick 3-advisor panel for lower-stakes decisions |
| `/decision-council:configure` | Adjust panel composition, thresholds |
| `/decision-council:status` | Show current configuration and advisor track record |
| `/decision-council:pre-mortem` | Run a pre-mortem on the last recommendation — what does the failure story look like? |
| `/decision-council:dashboard` | Generate a visual HTML decision dashboard you can save and share |
| `/decision-council:pro` | Browse Pro features — specialist advisors, decision vault, apps, adaptive learning |

## First use

On your first `/decision-council:convene`, the Chair will ask 3–4 setup questions to configure your panel. This takes about 2 minutes and only happens once per project.

## Examples

```
/decision-council:convene Should I invest $10K in a global tracker fund, or hold cash given current market conditions?
```

```
/decision-council:quick Should we launch the feature this sprint or defer to next quarter?
```

```
/decision-council:convene Which of these three pricing models should we adopt: freemium, flat-rate, or usage-based?
```

## How it works

1. **Disclaimer** — delivered at the start of every session (non-negotiable)
2. **Research** — Chair searches for relevant current data
3. **Interview** — 2–4 questions to understand the decision
4. **Independent analysis** — each advisor analyses the decision independently
5. **Cross-examination** — where scores diverge by 30+ points, advisors challenge each other
6. **Consensus check** — flags dangerous agreement
7. **Synthesis** — scored recommendation with scenarios, conflicts, and next actions
8. **Memory update** — track record saved for future sessions

## Important notice

Decision Council helps you think through decisions more rigorously. It does not provide financial, legal, medical, or professional advice. You are solely responsible for all decisions you make. See the full disclaimer delivered at the start of each session.

## Version

1.18.0 — Two-command architecture (convene + debrief). Debrief is top-level agent with full AskUserQuestion. Platform limitation: subagents cannot use AskUserQuestion. 18 files.

## License

Proprietary. © Fusion Software Ltd.

[Source on GitHub](https://github.com/fusion-software-ltd/decision-council)
