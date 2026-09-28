# 3D Artist Skills

Agent skills for creating editable 3D assets from descriptions, photographs,
sketches, concept art, and multiple views.

## Included skill

[create-3d-model](create-3d-model/SKILL.md) guides an agent through proportion
planning, modeling, materials, rendered validation, and delivery of an editable
asset. It defaults to Blender and adapts to another application when requested.

## Install

With Node.js and npm available, run this in your target project:

```sh
npx skills add tarrgor/3D-artist-skills --skill create-3d-model
```

To install specifically for Codex:

```sh
npx skills add tarrgor/3D-artist-skills --skill create-3d-model --agent codex
```

Add `--global` to install for your user instead of the current project. Preview
the available skills without installing:

```sh
npx skills add tarrgor/3D-artist-skills --list
```

See the [official skills CLI documentation](https://github.com/vercel-labs/skills)
for other supported agents and installation options.

## Requirements and use

Installation supplies agent instructions and supporting references. To create
and render actual models, the agent needs access to Blender (through a working
integration or local executable), or another suitable modeling application.
The installer does not install Blender or configure application integrations.

Example request:

> Use create-3d-model to build an editable desk lamp in Blender from these
> reference images. Deliver the .blend file and rendered previews.

## Compatibility

Verified with `skills` CLI 1.7.0: remote discovery and project-local Codex
installation. The skill uses `SKILL.md` with YAML `name` and `description`,
relative reference links, and optional Codex UI metadata in `agents/openai.yaml`.
No npm package or build step is required in this repository.
