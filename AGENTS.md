`durable-agents` is an APM producer package (single-plugin shape, per the
[APM producer docs](https://microsoft.github.io/apm/producer/)).

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

1. Add or edit primitives under `.apm/<type>/`
2. Run `apm compile --validate` to confirm the manifest and primitives are
   well-formed.
3. Keep `apm.yml` metadata (`name`, `version`, `description`, `repository`,
   `keywords`, `type`) accurate — it's what shows up for downstream
   consumers and in `plugin.json` if this is ever packed.
4. Increment the package version number, following SemVer. Respect conventions
   for pre-release (v0) version. Never move up a version level (0.0.x -> 0.1.0,
   or 0.x.y -> 1.0.0) unless explicitly instructed to do so.
