# RS3-Dev-Cheat-Config
Replace the 4th controller config on Rainbow Six 3 with various cheats and tools for tinkering.
# Rainbow Six 3 (Xbox / 360 BC) – Dev/Cheat Controller Profile (UMD config)

This repo documents a **ButtonConfig4 “Dev/Cheat” control profile** for Rainbow Six 3-era builds that support console-style commands via UMD input mappings.

It adds a practical set of in-mission toggles (e.g., Ghost/Walk, FullAmmo, GodTeam) while **preserving normal controls** in the default profiles.

> Goal: **high ROI**, no trainers, no offsets hunting, no fragile memory patches.

---

## What this does

- Keeps standard control profiles intact (Config 1–3)
- Uses **ButtonConfig4** as a dedicated dev/cheat profile
- Adds quick toggles for:
  - **Ghost / Walk** (noclip + restore interaction)
  - **FullAmmo**
  - **GodTeam**
  - **KillTerro**
  - **PlayerInvisible**
  - **CompleteMission**
  - **ThirdPerson view** (recoverable via `walk`)

---

## Why this is better than trainers (for this use-case)

- No TitleID-based trainer dependency
- No emulator/bc offset drift
- Works as a data/config change
- Easy to revert
- Easy for others to adopt without installing extra tooling

---

## Safety / Warnings

### Ghost breaks interaction (by design)
`ghost` often disables collision + use traces. You may be unable to interact with doors/objects while ghosted.

✅ Fix: use `walk` to restore normal physics + interaction.

### Third-person
Third-person can be fun for scouting/curiosity, but can also affect feel/aim.  
✅ Fix: `walk` reliably restores normal behavior.

### Don’t bind critical gameplay to commands
Keep **Action**, **PrimaryFire**, **PauseMenu** functional on any profile you actually play with.

---

## Installatio

Installation (UMD replacement)

This replaces the game’s UMD configuration file.

Where the UMD goes

The modified .umd file must be placed in the game’s system folder.

Typical layout:

<game root>/
 ├─ system/
 │   ├─ xboxdynamic.umd   ← replace this file
 │   ├─ xboxufiles.umd
 │   └─ other system files
 ├─ maps/
 ├─ sounds/
 └─ ...


⚠️ The exact filename may vary slightly by region/build.
Replace the existing UMD in the system directory.

OG Xbox

Copy the modified .umd into the game’s system folder

Overwrite the original

Reboot the console (recommended to clear cached data)

Xbox 360 (Backwards Compatibility)

Same folder layout inside the extracted game directory

If the game hangs after replacement:

launch a different title once

then relaunch RS3 (BC cache can be sticky)

### Requirements
- Ability to access/edit the relevant `.umd` file used by your setup
- A hex editor (HxD recommended)
- Keep file size unchanged (pad with spaces `0x20` as needed)

### Key rule
- Do **not** insert `00` bytes inside the text region.
- Use consistent CRLF (`0D 0A`) line endings.
- Avoid duplicate `Joy#=` entries within the same `[ButtonConfigX]` block.

---

## Usage

1. Apply the ButtonConfig4 mappings
2. Boot the game
3. Switch to **Controller Config 4** in the in-game options
4. Use your binds in-mission

---

## Example bind philosophy

- D-Pad Up/Down: **Ghost / Walk** (paired)
- D-Pad Left/Right: **GodTeam / KillTerror**
- X: **FullAmmo**
- Y: **CompleteMission**
- Back: **PlayerInvisible**
- B: **ThirdPerson** (reset via Walk)

Your exact Joy# → physical button mapping may vary slightly by build/controller profile,
but the command behavior is the same.

---

## Known Issues / Notes

- If you see only some configs loading or some mappings silently failing:
  - Check for embedded `00` bytes in the config text region (this will truncate parsing).
  - Check for duplicate `Joy#=` lines in the same config block.
  - Keep consistent CRLF endings.

- Some debug commands (e.g., `dbgthis`) may do nothing in retail builds.

---

## Contributing

If you find additional working commands (especially ones that print on-screen confirmation),
open an issue or PR with:

- command name
- what it does
- when it works (menu only / in-mission / SP only)
- any side effects

---

## Legal

This repo contains **no copyrighted game data**.  
It documents configuration behavior and user-applied changes only.

---

## Credits

Community research + old-school Unreal/RS3 modding vibes.  
Built with stubbornness, curiosity, and a healthy disrespect for “you can’t do that.”
