# charly-vm — retired

> **RETIRED — this repo publishes nothing.** All 6 `vm`-family skills live in the
> repo that holds the code, plugin or config each one documents (the table below).
> Nothing is authored, built, deployed or consumed here: a change to a `vm`-family
> skill is a change at its destination repo, in the same pull request as the entity it
> documents.

**This repo no longer authors a skill.** It was the `charly-vm` concept candy: a `true`-no-op `plan:` and 6 `skill:` entities, with the prose in `.agents/skills/`.
Under `AGENTS.md` Part II #5 a skill lives in the repo whose code,
plugin or config it describes — and this repo holds none of them (measured before the
change: **0 `.go`, 0 `.cue`, no `candy/` directory**) — so 6 of them moved, byte-identically,
to the repo that does:

| Skill | Now authored in | The entity that owns it |
|---|---|---|
| `arch-cloud-vm` | [`opencharly/distro-arch`](https://github.com/opencharly/distro-arch) | the `box/arch` entity it documents |
| `cachyos-bootstrap-vm` | [`opencharly/distro-cachyos`](https://github.com/opencharly/distro-cachyos) | the `box/cachyos` entity it documents |
| `debian-debootstrap-vm` | [`opencharly/distro-debian`](https://github.com/opencharly/distro-debian) | the `box/debian` entity it documents |
| `ubuntu-debootstrap-vm` | [`opencharly/distro-ubuntu`](https://github.com/opencharly/distro-ubuntu) | the `box/ubuntu` entity it documents |
| `vm` | [`opencharly/plugin-vm`](https://github.com/opencharly/plugin-vm) | the `command:vm` provider and the libvirt renderer |
| `vms-catalog` | [`opencharly/spec`](https://github.com/opencharly/spec) | the `vm.yml` / VmSpec CUE schema |

**The addresses did not change.** Every skill keeps its `vm` family at its
destination node, so `/charly-vm:<skill>` still resolve — they are simply authored
where the entity is implemented. The move is the rule `AGENTS.md` Part II #5 states, tracked
in [opencharly/opencharly#600](https://github.com/opencharly/opencharly/issues/600).

## What remains here

| Property | Value |
|---|---|
| Layer / candy | `charly-vm` (drained concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | nothing — 0 `skill:` entities |
| Service / port | none |

Do not compose, reference or edit this repo: the skills, their routing nodes and their
prose all live at the destinations above, and this repo's retirement is tracked in
[opencharly/opencharly#600](https://github.com/opencharly/opencharly/issues/600).
