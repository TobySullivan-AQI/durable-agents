# AGENTS.md — maintaining this package

This file is hand-authored for agents (and humans) who maintain this repo.
It is **not** the compiled consumer output that `apm compile`/`apm install`
would normally generate — see "Do not compile" below.

## What this repo is

`durable-agents` is an APM producer package (single-plugin shape, per the
[APM producer docs](https://microsoft.github.io/apm/producer/)). Its
capability is the "durable agent" identity instruction: an always-on
instruction telling any agent that installs this package to persist its
knowledge, practices, and working state as files committed to its own repo,
rather than losing them at the end of a session.

The published primitive lives at
[`.apm/instructions/durable-agent.instructions.md`](.apm/instructions/durable-agent.instructions.md).
That file is the source of truth — edit it, not any generated output.

## How consumers use this package

Consumers add this package directly by git path/URL (e.g.
`apm install TobySullivan-AQI/durable-agents` or a full git URL) and run
`apm install`. There is no build/release step on our side: `apm install`
reads straight from `.apm/` in this repo at install time.

## Do not compile, install, or commit generated output here

Because this repo is only ever consumed via a direct git reference, we do
**not**:

- run `apm compile` or `apm install` in this repo, or
- commit any compiled/generated output (`AGENTS.md` generated banners,
  `.github/`, `.claude/`, `.cursor/`, `apm.lock.yaml`, `apm_modules/`, etc.)

Keep this repo as pure, uncompiled source. Use `apm compile --validate` (and
`apm compile --dry-run` if you want to preview placement) to check changes —
neither writes files — before committing.

## Making changes

1. Add or edit primitives under `.apm/<type>/` (currently just
   `.apm/instructions/`).
2. Run `apm compile --validate` to confirm the manifest and primitives are
   well-formed.
3. Keep `apm.yml` metadata (`name`, `version`, `description`, `repository`,
   `keywords`, `type`) accurate — it's what shows up for downstream
   consumers and in `plugin.json` if this is ever packed.
4. Commit and push directly to the current branch (including `main`)
   unless told otherwise.
