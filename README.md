# Planning-Docs

`Planning-Docs` is the source-of-truth repository for planning, product, architecture, and internal technical documentation for Companion, TheCube.

This repo is intentionally plain Markdown. It complements, but does not replace, the public documentation site in `Companion-TheCube.github.io`.

## Structure

- [Project](project/README.md): product direction, project plan, overview, and roadmap.
- [Components](components/README.md): internal docs for Core, servers, Bluetooth manager, launcher, and hardware.
- [Apps](apps/README.md): app platform guidance, manifest reference, and example-runtime docs.
- [Specs](specs/README.md): requirements and API specification drafts.
- [Governance](governance/README.md): community, terms, and privacy/data documentation.
- [Artifacts](artifacts/README.md): external artifacts, diagrams, and known documentation-access gaps.
- [Source Map](source-map.md): provenance for every markdown file in this repo.

## Relationship To Other Repos

- `Companion-TheCube.github.io` remains the public-facing docs site.
- `Companion-TheCube---Core` is the implementation source for the desktop runtime.
- `Companion-TheCube-Server` is the cloud/server API prototype.
- `Companion-TheCube-AppServer` is the app catalog/distribution service prototype.
- `AppExample-*` repositories are the source for app packaging and runtime examples.

## Authoring Rules

- Keep filenames lowercase and kebab-case.
- End synthesized or cleaned docs with a `## Sources` section.
- Mark draft or incomplete areas explicitly.
- Update [source-map.md](source-map.md) whenever new docs are added or source assumptions change.

## Open-item notation

- `Decision needed:` a choice still needs to be made.
- `Open question:` a factual or product question is still unanswered.
- `Needs verification:` the current statement is based on incomplete, draft, or conflicting sources.

## Current Status

This first pass consolidates Google Drive planning docs, local repo READMEs, and current implementation notes into one standalone repository. Some non-Google-Docs artifacts remain blocked by current Drive tooling and are recorded under [Artifacts](artifacts/README.md).

## Open Items

- `Decision needed:` confirm the long-term split between what stays in `Planning-Docs` and what migrates into `Companion-TheCube.github.io`.
- `Open question:` identify the exact Google Drive folder ID and complete non-Google-Docs artifact inventory.
- `Needs verification:` several child docs are based on draft planning sources or partial implementations rather than finalized contracts.

## Sources

- Local repo inventory under `/home/andrew/Documents/projects/Companion, TheCube`
- Implementation plan used for this repository bootstrap
