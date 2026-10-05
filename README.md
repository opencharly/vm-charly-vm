# vm-charly-vm

Home of the `charly-vm` concept candy and the **VM kind-authoring skills** for
[charly](https://github.com/opencharly/charly) — the `kind: vm` schema, the VM
authoring catalog, and the cloud-image / bootstrap worked examples, projected
into the marketplace corpus as the `/charly-vm:*` skills.

This repo ships **no installable content**: the `charly-vm` candy is a
documentation-only node whose `plan:` is a validate-satisfying no-op. What it
owns is the family's `skill:` entities — sibling nodes in the same `charly.yml`
— which `charly marketplace generate` renders into the standalone
[opencharly/marketplace](https://github.com/opencharly/marketplace) corpus.

## Skills this repo owns

| Skill | Covers |
|---|---|
| `/charly-vm:vm` | The `charly vm` command family: build / create / start / stop / ssh / console, libvirt vs QEMU backends, BIOS vs UEFI firmware, virtio-gpu, GPU passthrough, snapshots. |
| `/charly-vm:vms-catalog` | The `kind: vm` authoring reference — `VmSpec` fields, the `cloud_image` / `bootc` / `bootstrap` / `iso` / `clone` source kinds, the `base_user` adopt pattern. |
| `/charly-vm:arch-cloud-vm` | The canonical `source.kind: cloud_image` worked example (Arch cloud image, BIOS, virtio-gpu, resource sizing). |
| `/charly-vm:cachyos-bootstrap-vm` | A `source.kind: bootstrap` VM built with `pacstrap` inside a privileged builder. |
| `/charly-vm:debian-debootstrap-vm` | A `source.kind: bootstrap` Debian VM built with `debootstrap`. |
| `/charly-vm:ubuntu-debootstrap-vm` | A `source.kind: bootstrap` Ubuntu VM built with `debootstrap`. |

## What a VM entity looks like

A VM is a name-first `kind: vm` node in a project's `charly.yml` — the entity
describes only the VM's shape (disk, RAM, SSH, cloud-init, libvirt); the deploy
that uses it carries the authorization:

```yaml
# the ENTITY (shape only — no disposable:)
my-vm:
  vm:
    source:
      kind: cloud_image
      distro: arch
      url: https://fastly.mirror.pkgbuild.com/images/latest/Arch-Linux-x86_64-cloudimg.qcow2
      base_user: arch
    disk_size: 40G
    ram: 8G
    cpu: 4
    ssh: {port: 2224, key_source: generate}

# the DISPOSABLE DEPLOY a bed or automation drives (create/destroy authorization)
my-vm-bed:
  vm:
    from: my-vm
    disposable: true
```

Drive it with the `charly vm` verbs (`charly vm build my-vm`, `charly vm create
my-vm-bed`, `charly vm ssh my-vm-bed`) or apply layers in-guest with
`charly deploy add vm:my-vm-bed`. The full field-by-field reference is
`/charly-vm:vms-catalog`; the Go types are `/charly-internals:vm-spec`.

## Layout

- `charly.yml` — the `charly-vm` concept candy plus the family's `skill:`
  entities (`arch-cloud-vm`, `cachyos-bootstrap-vm`, `debian-debootstrap-vm`,
  `ubuntu-debootstrap-vm`, `vm`, `vms-catalog`).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- [`opencharly/marketplace`](https://github.com/opencharly/marketplace) — the generated skill corpus.
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder.
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella.
