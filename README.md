<p align="center">
  <img src="https://i.postimg.cc/59Qx7kv5/banner.png" alt="Baldur's Gate 3 PAK Sorter — Load Order Manager, modsettings.lsx Fixer & Save Vault" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-BG3%20PAK%20%26%20LSX%20Manager-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-bg3--pak--sorter--v1.3-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

# Baldur's Gate 3 PAK Sorter — Load Order Manager, modsettings.lsx Fixer & Save Vault

**Baldur's Gate 3 resetting your mod load order on launch, throwing 'Corrupted modsettings.lsx' errors, or blocking co-op joins due to mismatched .pak versions? Sort your Mods folder, generate valid modsettings.lsx XML, and back up your campaign saves in 1 click.**

Baldur's Gate 3 PAK Sorter reads `meta.lsx` metadata directly inside every `.pak` archive in `%LOCALAPPDATA%\Larian Studios\Baldur's Gate 3\Mods`: **letting you drag-and-drop load order, detect missing dependencies, write valid `modsettings.lsx`, and export shareable co-op mod lists**.

This project is aimed at **Baldur's Gate 3 on Windows 10/11 PC (Steam & GOG)** for managing `.pak` load orders, `modsettings.lsx` backups, and `Story` save snapshots.

## Quick Use-Case & Troubleshooting Reference

| Scenario / Issue | Cause | Solution |
| --- | --- | --- |
| BG3 resets active mods to empty on launch | Malformed XML or invalid UUID inside `modsettings.lsx` | Regenerate clean, schema-valid `modsettings.lsx` from installed `.pak` headers |
| Co-op friend gets 'Different Mod Versions' error when joining | Load order or `.pak` MD5 versions differ between host and guest | Export a **Co-op Mod Manifest** to verify identical `.pak` order and versions |
| Game crashes after installing a UI or subclass mod | Dependency mod (e.g. `ImpUI`) placed below dependent `.pak` files | Auto-sort foundational libraries (`ImpUI`, frameworks) to the top of load order |
| Protecting 100-hour Honor Mode or modded campaign saves | Single Honor Mode save slot overwritten on party wipe or mod bug | Create a dated `.zip` snapshot of `PlayerProfiles\Public\Savegames\Story` |

## Download for Windows

[**Download BG3PakSorter.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/BG3PakSorter.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why use `BG3PakSorter.exe`? (Key features)

- Reads internal `meta.lsx` UUIDs, version numbers, and dependencies directly from every `.pak` file in `Mods\`.
- Drag-and-drop load-order editor writes clean, crash-free `modsettings.lsx` with automatic `.bak` backup.
- Auto-pins library mods (`ImpUI`, community frameworks) to the top of the load order.
- One-click **Back Up Campaign & Honor Mode Saves** + **Export Vanilla `modsettings.lsx`** toggle.

### Sample Output

```text
[BG3PakSorter] Loaded 26 .pak archives from AppData\Local\Larian Studios\Baldur's Gate 3\Mods
[OK]   Dependencies     : ImpUI.pak pinned to Position #1 (All 26 UUIDs valid)
[OK]   modsettings.lsx  : Backed up & written cleanly (26 active mods)
[OK]   Save Snapshot    : Backed up 12 Story campaigns to Documents\BG3-SaveVault\2026-11-23\
```

The release ZIP is named `BG3PakSorter.zip`; the Windows executable inside is named `BG3PakSorter.exe`.

1. Close BG3 PAK Sorter before updating or replacing executable files.
2. Click **Download BG3PakSorter.zip** above.
3. Right-click the downloaded archive and choose **Extract All**.
4. Open the extracted folder and run `BG3PakSorter.exe`.
5. Review the options and output paths before processing files.

**Requirements:** Windows 10 or 11 (64-bit) with Baldur's Gate 3 installed.

### Verification & Windows SmartScreen Note

- **Offline & standard user permissions:** `BG3PakSorter.exe` runs locally without uploading your personal files and does not require disabling Windows Defender.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Problems this project solves

### Preventing `modsettings.lsx` corruption and silent load-order wipes

Reads exact `UUID`, `Folder`, `Name`, and `Version64` fields from each `.pak` so BG3 never rejects the XML.

### Ensuring identical mod lists for 4-player co-op

Compares `.pak` filenames and versions so co-op lobbies connect on the first try.

### One-click switch to Vanilla `modsettings.lsx`

Exports a clean vanilla `modsettings.lsx` when joining unmodded multiplayer campaigns.

### Protecting multi-act campaign saves

Archives `Savegames\Story` before adding or removing heavy gameplay mods.

## Default folders and configuration paths

Baldur's Gate 3 stores `.pak` mods, `modsettings.lsx`, and saves in `%LOCALAPPDATA%\Larian Studios`:

```text
%LOCALAPPDATA%\Larian Studios\Baldur's Gate 3\
```

Typical directory layout:

```text
%LOCALAPPDATA%\Larian Studios\Baldur's Gate 3\
├── Mods\
│   └── *.pak
└── PlayerProfiles\Public\
    ├── modsettings.lsx
    ├── modsettings.lsx.bak
    └── Savegames\Story\
```

Always close Baldur's Gate 3 and the Larian Launcher before exporting `modsettings.lsx`.

## Quick start guide

Follow these steps to get started:

1. **Close Baldur's Gate 3 and Larian Launcher.** Extract `BG3PakSorter.zip` and run `BG3PakSorter.exe`.
2. **Drag new `.pak` mods into the list and arrange load order (libraries at top).** Click **Save & Export modsettings.lsx**.
3. **Click **Back Up Saves** to archive `Savegames\Story`.** Launch Baldur's Gate 3 and verify active mods.

### Data safety note

BG3 PAK Sorter creates `modsettings.lsx.bak` automatically before writing any changes.

## What the status summary shows

BG3 PAK Sorter displays **installed `.pak` count, extracted UUIDs, dependency order status, and save backup path**.

## FAQ

**Why does Baldur's Gate 3 reset my modsettings.lsx file when I launch the game?**

If `modsettings.lsx` has a missing UUID, invalid XML tag, or references a deleted `.pak` file, BG3 overwrites it with an empty vanilla file on startup.

**Does this work with Patch 7 / Patch 8 in-game Mod Manager `.pak` files?**

Yes—it reads all `.pak` archives inside `AppData\Local\Larian Studios\Baldur's Gate 3\Mods`.

**Can I export a clean vanilla load order for unmodded co-op?**

Yes—click 'Export Vanilla modsettings.lsx' (your modded order stays saved as a preset).

## Useful reading

- [Larian Studios Support — Baldur's Gate 3 Modding](https://larian.com/support/baldur-s-gate-3)

## More Windows Gaming Utilities

- [SteamUpdate-ModBlockerLock](../SteamUpdate-ModBlockerLock) — Lock Steam appmanifest_*.acf to prevent mod-breaking updates
- [ModDrop-UniversalPakInstaller](../ModDrop-UniversalPakInstaller) — Drag-and-drop ZIP/PAK mod installer with conflict check
- [Cyberpunk2077-ModCleanerPresets](../Cyberpunk2077-ModCleanerPresets) — Cyberpunk 2077 leftover mod cleaner & red4ext cache reset
- [QuickSave-HotkeySnapshotVault](../QuickSave-HotkeySnapshotVault) — F5/F9 hotkey save snapshot & restore vault for any PC game

*Independent community project. Not affiliated with Larian Studios, Wizards of the Coast, Valve, or Steam.*
