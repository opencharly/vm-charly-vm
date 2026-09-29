# AGENTS.md — vm-charly-vm

Standalone repo for the `charly-vm` **concept candy** — it owns the VM
kind-authoring `skill:` entities (the `kind: vm` schema, the authoring catalog,
and the cloud-image / bootstrap worked examples) that `charly marketplace
generate` projects into the marketplace corpus as the `/charly-vm:*` skills.
The candy itself ships no install content (a validate-satisfying no-op `plan:`);
the load-bearing content is the sibling `skill:` nodes in `charly.yml`.

Canonical files:

- `charly.yml` — the `charly-vm:` candy entity and its `skill:` entities
  (`arch-cloud-vm`, `cachyos-bootstrap-vm`, `debian-debootstrap-vm`,
  `ubuntu-debootstrap-vm`, `vm`, `vms-catalog`).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — user overview only; never agent guidance.

## Load these skills first (R0)

- `/charly-vm:vm` — the owning `charly vm` command-family skill. VM lifecycle,
  libvirt vs QEMU backends, firmware, GPU passthrough, snapshots. Load before
  editing or troubleshooting the `vm` skill entity.
- `/charly-vm:vms-catalog` — the `kind: vm` authoring reference (`VmSpec`
  fields, the `cloud_image` / `bootc` / `bootstrap` / `iso` / `clone` source
  kinds, the `base_user` adopt pattern). Load before editing a VM-authoring
  claim.
- `/charly-internals:vm-spec` — the `VmSpec` Go type reference and validation
  rules. Load before asserting a field's semantics or default.
- `/charly-internals:skills` — the skill-authoring/skill-maintenance reference
  (where doc content belongs, the projection model). Load before adding or
  changing a `skill:` entity.

## Build / validate / test

- The merge gate is the **org-wide** `charly/pr-validator` (required check
  `validate / validate`, defined in `opencharly/.github`); this repo has **no
  per-repo candy gate** and ships only `.github/workflows/tag-on-merge.yml`.
- Validate the manifest with `charly box validate` at the repo root.
- The `skill:` entities are PROJECTED into the marketplace corpus by
  `charly marketplace generate`; a skill edit is only half-landed until the
  owning repo's corpus is regenerated (see `/charly-internals:marketplace`).

## Modify this repo

- Edit the `skill:` entity in `charly.yml`; the emitted `SKILL.md` under
  `marketplace/**` is generated (DO-NOT-EDIT) and reverted by the next
  regeneration.
- Keep each skill's `description:` and body describing the current schema —
  they are published prose. A schema change belongs in the owning skill in the
  same change that introduces it.
- New behavioural claims belong in the relevant skill body, not in this
  signpost.

## Landing

- The authoritative landing mechanics are `/charly-internals:git-workflow` and
  the umbrella `AGENTS.md` in `opencharly/opencharly`; this signpost does not
  restate them.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time).
