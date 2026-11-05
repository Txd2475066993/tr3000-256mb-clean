# TR3000 256MB V1 — Clean Firmware

This project builds a clean, device-specific OpenWrt image for the **Cudy TR3000 256MB V1**.

It does not use openwrt.ai, Kiddin9's online build portal, advertising feeds, or third-party app stores.

## Build profile

- Target: `mediatek/filogic`
- Device profile: `cudy_tr3000-256mb-v1`
- Base: official OpenWrt `v25.12.6`
- Image: SquashFS SYSUPGRADE
- UI: LuCI with Shadcn theme (light/dark mode)
- Language: Simplified Chinese
- Proxy UI: OpenClash LuCI app
- LAN address on first boot: `10.0.0.1`

The 256MB device profile is intentionally selected. **Do not replace it with `cudy_tr3000-v1`**, which is a different 128MB target.

## What is included

The standard OpenWrt router base, LuCI, Shadcn theme, Chinese LuCI translations, OpenClash LuCI app, and dependencies required by OpenClash.

Not included: online build-portal components, promotional feeds, third-party package stores, Docker, NAS/file sharing, download managers, AdGuard bundles, or extra proxy applications.

The Mihomo runtime core is not bundled. Install/update it from OpenClash's Version Update page after first boot.

## Build

Pushing the workflow to `main` starts GitHub Actions automatically. A manual run is also available under **Actions → Build TR3000 256MB Clean Firmware → Run workflow**.

On success, download the artifact named `TR3000-256MB-Clean`. It contains:

- `TR3000-256MB-Clean-sysupgrade.bin`
- `TR3000-256MB.manifest`
- `build.config`
- `BUILD-INFO.txt`
- `SHA256SUMS.txt`

## Flash precautions

1. Confirm the router label/hardware is **Cudy TR3000 256MB V1**.
2. Back up your current configuration first.
3. Use only the generated SYSUPGRADE image from the running system's upgrade page.
4. For a clean installation, do not keep old configuration files.
5. After reboot, reconnect to `10.0.0.1`.
6. Do not force an image when the device compatibility check rejects it.

A successful compilation does not guarantee that every KWRT build accepts cross-branch sysupgrade. If the upgrade UI reports a compatibility error, stop and verify the currently installed device profile and upgrade path rather than forcing it.

## Provenance

This is an OpenWrt-based community build for the specified Cudy hardware, **not an official Kiddin9/Kwrt binary**. Upstream package sources and revisions are pinned in the workflow.
