# LokumKernel SM8850 Source Notes

This repository is the Android common kernel source branch used by the
LokumKernel_SM8850 release tooling for Xiaomi Pandora-class SM8850 devices.

## Expected workspace layout

The production build is orchestrated from the sibling `lokum-release` repository
in the `LokumKernel-SM8850` GitHub organization. The build workspace is expected
to contain:

```text
kernel_platform/common          # this repository
kernel_platform/KernelSU-Next   # sibling repo; drivers/kernelsu symlink target
kernel_platform/susfs4ksu       # SUSFS upstream/reference source
LokumKernel-SM8850/lokum-release
```

`drivers/kernelsu` is intentionally a relative symlink to
`../../KernelSU-Next/kernel`. This keeps KernelSU Next updateable as a separate
pinned source instead of vendoring its full history into the common kernel tree.

## Current production pins

- Firmware base: Xiaomi Pandora `OS3.0.309.0.WBLCNXM`
- Kernel release string: `6.12.23-android16-5-LokumKernel`
- KernelSU Next branch/commit: `pandora/gki-2025-09-ksunext-dev-susfs` / `985f8bcb`
- SUSFS source commit: `75a613850178234c6c7595d1db8211716a011a2e`
- SUSFS version: `v2.1.0`
- Boot image partition size: `100663296` bytes

## Build and release

Use the release repo, not ad-hoc commands, for production artifacts:

```bash
LokumKernel-SM8850/lokum-release/scripts/release.sh
```

Generated `boot.img`, AnyKernel3 zip files, logs, and checksums are not tracked
in this source repository. They belong in the release repo `out/` directory and
in GitHub Releases after runtime validation.
