# Property OS workspace

This repo is a Clawnify **bundle**: a list of five app repos and three agents
that together run a property business from the first enquiry to the work
order. Apps are **referenced by repo** and never copied here; each keeps its
own verification pin and update path. Layout:

- `clawnify.json` — the root manifest: `bundle.apps[]` by repo (with the
  display `name` each member gets at install), `bundle.agents[]` by path
  with a `required` flag, `deploy.prompts`. `workspace.org` is `null`
  because this repo is a template; it is bound to an org at install.
- `agents/<name>/` — the bundle's agents (AGENT.md, skills/, flows/).
- `apps/<slug>/` — each member as a git submodule pinned at its verified
  commit. Read-only here: install ignores these folders, and member changes
  go upstream to the member repo.
- `docs/` — the getting-started narrative.

## Editing rules

- **Fix a member upstream.** There is no copy of OpenProperty here to edit. A
  generic improvement is a PR to `clawnify/OpenProperty`; re-verification
  advances the pin every install uses.
- **Bundle-level work belongs here:** `agents/*`, `docs/`, the root manifest.
- **Never commit `.env` files or `.clawnify/` folders.** Never echo tokens.
- This repo never knows about an org. Do not `clawnify link` or `clawnify org
  use` inside it.

## Installing by hand

Inside a workspace bound to the target org, deploy each member from its repo,
then the agents from this repo:

```bash
clawnify deploy --from clawnify/OpenProperty
clawnify deploy --from clawnify/OpenCRM
clawnify deploy --from clawnify/OpenChannels
clawnify deploy --from clawnify/OpenDataRoom
clawnify deploy --from clawnify/OpenRenderStudio
clawnify deploy agents/sales                     # required
clawnify deploy agents/resident agents/studio    # optional, plan permitting
```

Then read `docs/GETTING-STARTED.md` with the agent.

Docs: https://docs.clawnify.com/llms.txt
