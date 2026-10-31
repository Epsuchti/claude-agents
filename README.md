# claude-agents

A Claude Code plugin marketplace with one plugin, `workflow`. It contains five agents (planner, designer,
implementer, fixer, tester) and a `workflow` skill that routes tasks between them.

## Install
In Claude Code:
```
/plugin marketplace add <git-url-or-local-path-of-this-repo>
/plugin install workflow@claude-agents
```
To update, pull or push this repo, then run `/plugin marketplace update claude-agents`.

## What a project provides
The agents are generic. Each project gives them:
- `AGENTS.md` or `CLAUDE.md` with the binding rules, the environment setup and the test commands. The
  implementer, fixer and tester read it first.
- `docs/tasks/`, where the planner writes its plan files.
- `docs/design/`, optional, for the designer.

A project agent with the same name in `.claude/agents/` overrides the plugin's agent for that project.

## Models
| Agent | Model |
|---|---|
| planner | opus |
| implementer | opus |
| designer | fable |
| fixer | sonnet |
| tester | haiku |

Change the `model:` line in the agent file to use another model.

## Token notes
- The `description` lines stay in every session's context, so keep them to one sentence.
- An agent's body loads only when it's spawned. Keep the rules that steer behaviour; they save far more than
  they cost.
