
<h1 align="center">EZ Flash Junior Kernel Mod</h1>

<p align="center">
  <strong>Kernel Reverse Engineering. Firmware Patching. Cartridge Development.</strong>
</p>

<p align="center">
  Nintendo Game Boy · Game Boy Color · Cartridge Firmware
</p>

<p align="center">
  <img src="https://img.shields.io/badge/platform-Game%20Boy%20%2F%20Game%20Boy%20Color-A63A55?style=flat-square">
  <img src="https://img.shields.io/badge/category-Cartridge%20Firmware-A63A55?style=flat-square">
  <img src="https://img.shields.io/badge/license-AGPL--3.0-555555?style=flat-square">
  <img src="https://img.shields.io/badge/architecture-SM83-333333?style=flat-square">
</p>

## Overview

EZ Flash Junior Kernel Mod is an open-source reverse-engineering and modification project for the EZ-Flash Junior flash cartridge.

The cartridge uses an internal menu and operating-system firmware known as the kernel. This software runs on the Game Boy CPU architecture and manages cartridge initialization, microSD access, ROM selection, save operations, and system configuration.

The project analyzes the original kernel binary and introduces additional functionality through independently developed patches and firmware modifications.

It supports multiple original kernel versions, including:

- 1.04e (FW4)
- 1.05e-0731 (FW5)
- 1.05e-0918 (FW5)

The modified kernel is loaded from the cartridge's microSD card as `ezgb.dat`. The standard kernel modification process does not require rewriting the console firmware or permanently flashing the handheld.

## Technical Architecture

The project operates at the cartridge firmware level.

Its architecture consists of several technical layers.

### Kernel Binary

The original EZ-Flash Junior kernel is distributed as a compiled binary.

The project provides reverse-engineered disassembly, symbol annotations, and reconstruction tools for analyzing its internal functionality.

### SM83 Processor Environment

The kernel executes on the Game Boy's SM83 processor.

The implementation interacts with cartridge hardware, memory banking, storage operations, and the console's launch process.

### Firmware Patching

Individual features are implemented as patches against specific kernel versions.

The patching workflow includes:

- Binary disassembly.
- Function identification.
- Code injection.
- Address verification.
- IPS patch generation.
- Reassembly and validation.

### Cartridge Hardware Interface

The project investigates the cartridge's hardware communication mechanisms, including:

- FPGA control registers.
- SD sector access.
- Memory banking.
- PSRAM save storage.
- Cartridge initialization.
- ROM launch behavior.

## Core Components

| Component | Description | Technical Role |
|---|---|---|
| Kernel Binary | Original cartridge operating firmware | System initialization |
| Kernel Disassembly | Annotated firmware reconstruction | Reverse engineering |
| Kernel Patches | IPS-based modifications | Firmware customization |
| Injection Tools | Code insertion utilities | Kernel modification |
| Build Scripts | Automated reconstruction tools | Firmware generation |
| Configuration | EZGB.CFG | Runtime settings |
| Bootloader Mod | Experimental startup modification | Cartridge boot management |
| SameBoy FPGA Stub | Development and testing support | Emulation environment |
| Hardware Documentation | Registers and memory maps | Hardware analysis |

## Key Features

### Kernel Interface Improvements

- Sorted file browser with directories displayed before files.
- Continuous scrolling beyond screen boundaries.
- Improved cursor positioning and page navigation.
- Faster input response through frame-based button sampling.
- Improved visual rendering and screen updates.

### Interface and Configuration

- Optional 12-pixel menu font.
- Multiple display themes.
- Custom background and foreground colors.
- Improved file identification through icons.
- Configurable ROM name cleanup.
- Filtering of unnecessary filesystem entries.

### ROM and Save Management

- Individual ROM management menu.
- Save backup and restoration.
- Save backup deletion.
- ROM favorites and launch counters.
- Sorting by launch frequency.
- Last-launched ROM recovery.
- Configurable automatic launch.

### Boot and Storage Management

- Configurable fast launch.
- Faster ROM loading on supported FW5 configurations.
- RTC backup and restoration through SD storage.
- Handling of invalid battery-backed records.
- Improved boot menu behavior.
- Experimental bootloader modifications.

## Kernel Compatibility

| Kernel Version | Firmware Family | Patch Support |
|---|---|---|
| 1.04e | FW4 | Supported |
| 1.05e-0731 | FW5 | Supported |
| 1.05e-0918 | FW5 | Supported |

The project uses separate patch packages for each supported kernel revision.

The 1.05e-0731 build is the primary development target, with features ported to other supported kernel versions.

The 1.04e kernel can also operate on FW5 cartridges.

Always match the patch to the appropriate original kernel binary.

## Firmware Installation and Configuration

### Prerequisites

- EZ-Flash Junior cartridge.
- Compatible microSD card.
- Original EZ-Flash Junior kernel file.
- Matching IPS patch.
- IPS patching utility.
- Access to the cartridge filesystem.

### Standard Kernel Modification

1. Obtain the original kernel file from the official EZ-Flash Junior firmware package.
2. Identify the kernel revision.
3. Select the corresponding IPS patch.
4. Apply the patch using a compatible IPS patching utility.
5. Copy the resulting `ezgb.dat` to the microSD card root.
6. Start the cartridge and verify the modified kernel version on the HELP screen.

The original kernel file should be retained so the standard configuration can be restored.

### Configuration

The configuration file is located at:

`/EZGB.CFG`

Available configuration areas include:

- Interface appearance.
- Font selection.
- File browser behavior.
- Fast launch.
- ROM selection.
- RTC backup.
- Boot ROM handling.
- Display themes.

### Firmware Verification

The HELP tab displays the kernel revision and modification version.

This information can be used to identify the active modified kernel.

### Experimental Bootloader Modification

The project also contains an experimental firmware modification introducing a new bootloader with fast launch, kernel selection, and SD error recovery on a supported FW5 configuration.

This modification is separate from the standard reversible kernel patch and requires particular care because an unsuccessful firmware modification can render the cartridge unusable.

## Technical Specifications

| Parameter | Details |
|---|---|
| Project | EZ Flash Junior Kernel Mod |
| Target Hardware | EZ-Flash Junior |
| Console Compatibility | Game Boy / Game Boy Color |
| Software Type | Cartridge Firmware Modification |
| Processor | SM83 |
| Original Firmware | EZ-Flash Junior Kernel |
| Supported Revisions | 1.04e / 1.05e |
| Patch Format | IPS |
| Configuration | EZGB.CFG |
| Kernel File | ezgb.dat |
| Development Languages | C / Python / Assembly |
| Build Tools | RGBDS and project utilities |
| License | AGPL-3.0 for project contributions |
| Official Repository | lukesau/ezgb |

## Development Environment

The repository provides a development environment for reverse engineering and modifying the cartridge kernel.

### Main Tools

- Python 3.
- RGBDS.
- MGBDIS.
- SameBoy.
- IPS patching utilities.
- Custom injection scripts.

### Repository Structure

| Directory | Purpose |
|---|---|
| `re/` | Kernel disassemblies |
| `decomp/` | Reconstructed kernel sources |
| `kernel/` | Feature implementations and injection tools |
| `docs/` | Technical documentation |
| `scripts/` | Build and patch automation |
| `patches/kernel/` | Kernel modification patches |
| `patches/sameboy/` | Emulator development patches |

Original proprietary firmware binaries are not redistributed by the project. Developers must provide their own firmware dump for reconstruction workflows.

## Frequently Asked Questions

### Is this a Custom Firmware for the Game Boy Color?

No. It modifies the firmware of the EZ-Flash Junior cartridge rather than the internal system software of the Game Boy Color console.

### Which consoles are compatible?

The EZ-Flash Junior is designed for the original Game Boy and Game Boy Color cartridge environments. The project also documents behavior on additional compatible hardware.

### Does the standard modification flash the console?

No. The modified kernel is loaded from the cartridge's microSD card as `ezgb.dat`.

### Which kernel versions are supported?

The project supports the 1.04e, 1.05e-0731, and 1.05e-0918 kernel revisions through separate patches.

### What is the experimental bootloader modification?

It is a separate cartridge firmware modification that adds an alternative startup process, kernel selection, and additional boot functionality. It is distinct from the standard kernel patch.

## SEO Keywords

EZ Flash Junior kernel mod, Game Boy Color cartridge firmware, EZ Flash Junior firmware, Game Boy cartridge kernel, EZGB firmware modification, Game Boy kernel reverse engineering, EZ Flash Junior IPS patch, SM83 firmware development, Game Boy cartridge development, EZ Flash Junior bootloader, Game Boy Color kernel patching, EZGB.CFG configuration, Game Boy cartridge firmware analysis, EZ Flash Junior kernel update, Game Boy SD cartridge software, Game Boy firmware disassembly, EZ Flash Junior ROM browser, Game Boy cartridge reverse engineering, EZ Flash Junior GitHub, Game Boy Color system software.

## Technical References

- [Original EZ Flash Junior Kernel Mod Repository](https://github.com/lukesau/ezgb)
- [Official Project Releases](https://github.com/lukesau/ezgb/releases)
- [EZ Flash Official Website](https://www.ezflash.cn/)
- [RGBDS Development Tools](https://github.com/gbdev/rgbds)
- [SameBoy Emulator](https://github.com/LIJI32/SameBoy)
- [Game Boy Development Resources](https://github.com/gbdev/awesome-gbdev)

<p align="center">
  <strong>EZ Flash Junior Kernel Mod</strong>
  <br>
  Nintendo Game Boy · Game Boy Color · Cartridge Firmware
  <br>
  Firmware Reverse Engineering and Development
</p>
