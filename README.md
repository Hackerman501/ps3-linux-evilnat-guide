# Linux on a PS3 with Evilnat CFW 4.93

A community guide to installing Petitboot and booting a compatible Linux distribution on a PlayStation 3 running Evilnat Custom Firmware (CFW).

> [!WARNING]
> **This process can result in data loss or leave your console in a difficult-to-recover state. Back up your data and your console's internal flash (NAND or NOR) before making changes. Proceed only if you understand the risks.**
>
> This guide is provided for informational purposes. It is not an official Sony or Evilnat support document. You are responsible for any changes you make to your console.

## Contents

- [Before you start](#before-you-start)
- [Limitations](#limitations)
- [1. Get Petitboot](#1-get-petitboot)
- [2. Install Petitboot](#2-install-petitboot)
- [3. Open Petitboot](#3-open-petitboot)
- [4. Prepare a Linux USB drive](#4-prepare-a-linux-usb-drive)
- [5. Boot Linux](#5-boot-linux)
- [6. Install Linux](#6-install-linux)
- [7. Boot Linux after installation](#7-boot-linux-after-installation)
- [Troubleshooting and recovery notes](#troubleshooting-and-recovery-notes)
- [References](#references)

## Before you start

You will need:

- A PS3 running a compatible version of Evilnat CFW.
- A USB drive formatted as FAT32 for the Petitboot installer.
- A separate USB drive containing a Linux distribution compatible with the PS3's PowerPC platform.
- A USB keyboard. A USB mouse may also be useful.
- A reliable backup of your important data and your console's NAND or NOR flash.

The PS3 uses a PowerPC-based Cell processor. A normal x86-64 PC Linux image will not work. Check the distribution's documentation for PS3 support and the appropriate PowerPC architecture before writing an image.

## Limitations

Linux on the PS3 is a hobbyist setup and has significant hardware limitations:

- There is no generally available, fully supported RSX graphics driver comparable to a modern PC GPU driver.
- Desktop graphics and video playback generally lack the GPU acceleration expected on a modern computer.
- The Cell processor architecture and available software limit compatibility and performance.
- Storage speed, particularly over USB, may be limited.
- The PS3 controller may not work in Petitboot or after Linux starts. Keep a USB keyboard and, if needed, a USB mouse connected.

A PS3 running Linux is better suited to experimentation, lightweight tasks, or learning than to modern desktop workloads.

## 1. Get Petitboot

The Petitboot files referenced by this guide are available in the Petitboot directory of Evilnat's XAI Plugin repository:

**[Evilnat XAI Plugin — Petitboot](https://github.com/xXEvilnatXx/xai_plugin/tree/main/Petitboot)**

Make sure you choose the correct file for your setup and follow any instructions that accompany it. Do not use files from an untrusted re-upload when the upstream source is available.

## 2. Install Petitboot

1. Copy the required Petitboot file to a USB drive formatted as FAT32.
2. Insert the drive into the **rightmost USB port** on the PS3 (when viewed from the front).
3. On the PS3, open **Network → CFW Tools → OtherOS → Install Petitboot**.
4. Follow the on-screen instructions. Do not turn off the console while the operation is running.

Menu names can vary between CFW builds. If the menu or option is missing, stop and check the documentation for your exact Evilnat release rather than selecting an unrelated option.

## 3. Open Petitboot

1. Start with the console powered off in standby.
2. Press and hold the power button to turn the console on.
3. Release the button after the second beep, when the Petitboot menu appears.

If this does not open Petitboot on your console, consult the relevant CFW documentation before repeatedly trying different button combinations.

## 4. Prepare a Linux USB drive

Choose a Linux distribution with explicit support for the PS3 or compatible 64-bit PowerPC (`ppc64`) hardware. Start with the distribution list on PS3 DevWiki:

**[PS3 DevWiki — Distributions](https://www.psdevwiki.com/ps3/Distributions)**

Use the image and instructions provided by the distribution's maintainers. On Windows, Rufus is one possible image-writing tool, but the correct writing method depends on the image format. Follow the distribution's instructions rather than assuming every ISO can be written and booted in the same way.

After writing the image:

1. Safely eject the USB drive from your computer.
2. Connect the Linux drive to a USB port on the PS3.
3. Connect a USB keyboard to another port.

## 5. Boot Linux

1. Start Petitboot using the steps above.
2. Wait for Petitboot to detect available boot entries.
3. Select the entry corresponding to the USB drive's live environment. Depending on the image, it may begin with `live:/`.
4. Follow the selected distribution's instructions to start its live environment.

The label and appearance of boot entries vary by distribution. If the expected entry does not appear, check the image, USB drive, and distribution-specific instructions.

## 6. Install Linux

The exact installation steps depend on the chosen distribution. Read its installation documentation carefully before selecting a target disk.

| Target | Important considerations |
| --- | --- |
| Internal PS3 drive | Installing to the internal drive may require repartitioning or reformatting the drive and can erase existing data. Do not proceed without a verified backup. |
| External USB drive | May avoid changing the internal drive, depending on the distribution and installation method. USB storage is generally slower, and compatibility depends on the image and installer. |

**Do not assume an external installation is automatically safe or that an internal installation is reversible.** Confirm which disk the installer is about to modify before proceeding.

## 7. Boot Linux after installation

After a successful installation, the referenced route for selecting OtherOS is:

**CFW Tools → OtherOS → Set OtherOS Boot Flag**

Then restart the console and use the supported Petitboot startup method to select the installed Linux system. Options and behavior may vary with the CFW version and installation.

## Troubleshooting and recovery notes

### Recovery Mode opens Linux instead

Some setups with Petitboot installed have been reported to start Linux when attempting to enter PS3 Recovery Mode. This is not a behavior to rely on or assume is harmless. If recovery access matters, read the current CFW/Petitboot guidance before installing.

### Back up NAND or NOR first

A flash backup is important before modifying OtherOS or boot-related settings. Recovery options differ between NAND and NOR consoles. Reformatting the internal drive is not a universal recovery method and does **not** replace a valid flash backup, especially on NAND systems.

Do not attempt to flash a backup unless you know it matches your console and understand the process.

### Keyboard and controller do not work

Keep a USB keyboard attached when using Petitboot and Linux. The PS3 controller may not be supported in these environments, so do not rely on it for navigation.

### Linux does not boot

Confirm that the image supports the PS3/PowerPC architecture, that it was written according to the distribution's instructions, and that Petitboot detects the drive. A Linux image for a standard x86-64 PC is not compatible.

## References

- [Evilnat XAI Plugin — Petitboot files](https://github.com/xXEvilnatXx/xai_plugin/tree/main/Petitboot)
- [PS3 DevWiki — Linux distributions](https://www.psdevwiki.com/ps3/Distributions)
- [r/ps3homebrew](https://www.reddit.com/r/ps3homebrew/)

## Disclaimer

This is an independent community guide. Links to third-party projects are provided for reference; their maintainers control those resources and their contents. Procedures and compatibility can change. Verify the instructions against the documentation for your specific console, CFW version, and Linux distribution before proceeding.
