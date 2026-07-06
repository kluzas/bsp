# Agent Instructions for Radxa CM3 U-Boot Project

## Project Overview
Build usable U-Boot images for the Radxa CM3 board with SPI flash as the primary storage and an SD card (on a carrier board) that must be limited to 3.3V.

## Key Constraints
- **Primary Boot**: Must boot from internal SPI flash regardless of SD presence.
- **SD Voltage**: Carrier board supports only 3.3V; ensure no 1.8V switching in DTS/U-Boot config.
- **Reproducibility**: All changes must be commit-ready and triggerable via GitHub Actions.

## Proactiveness Rule
If a clear next step action is planned in the project plan or task list, proceed with that action immediately without waiting for user input unless an ambiguity requires clarification or a major risk is identified.
1.  **Research & Analysis (Read Only)**: Identify target files (DTS, defconfig) and audit SPI flash partition layouts. Verify build scripts (`bsp` tool).
2.  **Configuration & Code Changes**:
    *   Modify DTS to enforce 3.3V for SD MMC nodes.
    *   Verify/Update SPI Flash nodes in Device Tree.
    *   Adjust `defconfig` to prioritize SPI boot commands and enable mandatory drivers (`CONFIG_MMC`, `CONFIG_SPI`).
    *   Ensure `u-boot/latest/fork.conf` correctly activates the `radxa-cm3-rpi-cm4-io` variant.
3.  **GitHub Actions Integration**:
    *   Define a `.github/workflows/*.yml` that utilizes the existing `bsp` build system.
    *   Use Docker containers to mirror the standard environment.
    *   Automate artifact upload for successful builds.

## Reproducibility Rules
- Never make "manual" changes outside the repo (e.g., temp files, local env vars).
- Every change must be committed before proceeding to the next logical step of the build flow.
- Always use the `bsp` script as the primary build entry point to ensure consistency with the repository's native tools.

## Tool Execution Policy
- Never write a paragraph explaining that you are "going to" run a tool. 
- Do not ask for confirmation for read-only actions (like glob, read, or grep).
- Immediately output the formatting block required to run the tool on your turn.
