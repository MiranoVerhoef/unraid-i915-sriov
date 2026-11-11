# Intel Graphics SR-IOV for Unraid

Community-maintained development fork of [giganode/unraid-i915-sriov](https://github.com/giganode/unraid-i915-sriov), originally based on [zhtengw/unraid-i915-sriov](https://github.com/zhtengw/unraid-i915-sriov). The experimental kernel driver originates from [strongtz/i915-sriov-dkms](https://github.com/strongtz/i915-sriov-dkms).

> **Development status:** This fork is not ready to install. The existing plugin still points to upstream releases and has not yet been migrated to this repository. Do not replace a working SR-IOV installation with this development branch.

## Goals

- Preserve the original Intel SR-IOV Settings page, VF configuration and virtual-machine compatibility.
- Release verified, kernel-specific i915 SR-IOV packages through GitHub Actions.
- Stage a compatible package for the next Unraid kernel **before** an OS reboot.
- Support normal Unraid plugin updates without manual `installpkg` commands.
- Fail safely when an unsupported kernel or a missing package is encountered; never substitute a driver built for another kernel.

## Implementation milestones

1. **Repository baseline:** preserve attribution, add reproducible checks, and isolate work on a development branch.
2. **Driver release integration:** fetch assets and checksums from a configurable release repository; validate matching `uname -r` and verify downloads before installation.
3. **Upgrade preparation:** inspect the kernel version of a pending Unraid OS upgrade and stage its matching package without loading it into the running kernel.
4. **Automated builds:** track official Unraid kernel releases, compile and validate source-compatible driver packages, and publish checksummed assets.
5. **GUI integration:** expose driver readiness, version and errors using the existing settings page; distribute plugin releases via the fork's `.plg` update URL.

## Safety and compatibility

Kernel module builds are experimental. Passing a CI build is not proof of hardware compatibility. Driver updates must not interrupt running GPU workloads without explicit administrator action. Preserve the last working package and settings for recovery.

The plugin and driver build components may have different licenses. Preserve original copyright notices and check the license of every reused component before incorporation.

## Original installation instructions

The currently shipped upstream plugin is available from:
`https://raw.githubusercontent.com/giganode/unraid-i915-sriov/master/i915-sriov.plg`

This fork has **no supported install URL yet**. Its `master` branch remains unchanged until a tested release is ready.
