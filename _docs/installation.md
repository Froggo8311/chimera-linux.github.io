---
layout: book
title: Installation
section: 2
---

This section describes how to install Chimera in different scenarios.

**Please note that Chimera is in a pre-alpha state.** The system is not
yet suitable for production or daily driving.

## System requirements

Chimera is supported on various types of computers. The documentation is
going to cover those that are officially supported and have binary package
repositories.

You will need the following:

| Architecture | Requirements                                        |
|--------------|-----------------------------------------------------|
| `x86_64`     | Any UEFI or BIOS-based 64-bit computer              |
| `ppc64le`    | POWER8 or better (OpenPOWER, PowerVM)               |
| `aarch64`    | UEFI devices supported by mainline kernel, or below |
| `riscv64`    | UEFI devices supported by mainline kernel, or below |

In general, for a console-based system, you will need at least 128MB
or more RAM for the system to be truly usable. A graphical desktop will
need more, depending on the desktop (1GB is recommended for GNOME installs).

### AArch64 devices

In addition to generic UEFI targets supported by mainline kernel, there
are also devices with device-specific images, typically using U-Boot.

Currently, officially supported are the following:

* 64-bit Raspberry Pi (3/4 and variants such as 400 and compute modules)
* PINE64 Pinebook Pro
* MNT Reform 2 with i.MX8MQ SOM

You will need to obtain the correct image for these. The list is subject
to expansion.

### RISC-V devices

This is similar to AArch64.

Officially supported are the following:

* SiFive HiFive Unmatched
* Qemu virtual machines (with and without OpenSBI)

This list is also subject to expansion.

## Downloading system media

All system media are available [here](https://repo.chimera-linux.org/live).
In general you will want to pick those with the latest date.

In general, for all architectures the following is available:

* Live images in ISO format
* Device-specific images if available
* Root filesystem tarballs

### Live ISOs

For generic computers, this is usually preferred. Use these if you are not
installing on a device that requires device-specific media, such as all
Intel or AMD `x86_64` computers, most POWER architecture systems, and
supported AArch64/RISC-V systems with UEFI.

### Device-specific images

Use these if your device is explicitly supported.

### Root filesystem tarballs

As a bit of a special case, Chimera also provides root file system tarballs.
This is a small, pre-packaged Chimera installation. The following flavors
are always available:

* Bootstrap tarballs (bootstrapped from the `base-bootstrap` metapackage)
  are suitable for setting up small containers that you can add more
  software into, e.g. with Docker. They only contain a bare userland
  and `apk`.
* Minimal tarballs (bootstrapped from the `base-minimal` metapackage) are
  suitable for setting up bare bootable systems. They do not contain a
  kernel or a bootloader, but they do contain an init system suite,
  a `getty` and user management tools.
* Core tarballs (bootstrapped from `base-core` metapackage) are larger and
  contain packages suitable for most deployments. Like minimal tarballs
  they do not contain a kernel or a bootloader, but they do contain
  programs such as those for manipulating filesystems and networks.

They are handy for chroot-style installations that are fully manual, mostly
to save time bootstrapping with `apk` from scratch.

In addition to this, tarball counterpart for every device-specific image
is available. You can use these for manual installation on such devices,
or you can create device images using Chimera's `mkimage.sh` using these.

## Verifying system media

In each media bundle, the `sha256sums.txt` file contains SHA256 checksums
of every file. Use this to check that your downloaded file is not corrupt.

## Installing

Proceed to the section relevant to you.
