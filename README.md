# durable-agents

An APM package of durable-agent identity and persistence instructions. The
agent keeps its knowledge, practices, work, status, and decisions in its own
git repository, so it can continue after a session reset.

From the root of your repository, initialize APM if you do not already have an `apm.yml`:

```sh
apm init
```

Add and install the package, then compile the instructions for your agent:

```sh
apm install TobySullivan-AQI/durable-agents
apm compile
```

The install command adds the package to your `apm.yml`. In an existing checkout where the dependency is already declared, run `apm install` to restore it before `apm compile`.

## What the agent does

- Stores knowledge under `knowledge/`, working files under `work/`, and
  practices under `practices/`.
- Reads `work/status.md` and `work/decisions.md` at the start of each session.
- Keeps `work/status.md` current: the current state, open items, and links.
- Records each user decision, correction, or fact in `work/decisions.md` in
  the same turn, with the date, who made it, and the reason.
- Saves research findings under `knowledge/` before it reports them.
- Commits and pushes after each change. With no remote, it commits locally,
  tells the user once, and records that in `work/decisions.md`.
