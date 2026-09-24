# MeltySave 0.8.2 — Maya/Kokoa colors and fur protection

- Correct UTS surface tint and shade-pass handling, addressing Maya/Kokoa hair that previously changed mostly at the outline. Regional eye/brow/accessory textures now reach shared UTS shade maps in tint mode too.
- Retain native shaders, texture detail and transparency. Absolute mode also handles the relevant UTS highlight, rim, MatCap and Angel Ring colors.
- On **Maya and Kokoa**, preserve inner-ear skin/fluff and original tail-tip colors. Ears changes the outer fur; Tail changes its base. Tail ornaments remain native. Follow hair color uses the same protection, including scene/preset restoration.
- Fur protection is currently curated for those two models only. Other characters need individual mapping checks; this release does not claim universal inner-ear/tail-tip separation.
- Keep the 0.8.1 contact collision fix, save format, slot UI and BGM behavior. Existing saves and color presets remain usable.

Fully close the game before updating. HMD/controller appearance acceptance remains a user check; non-HMD rendering and pixel checks are documented in the release description.

---

# MeltySave 0.8.1 — Contact collision hotfix

Fix scene loading before the native Settings panel has ever been opened. The touch checkbox listener had uninitialized layer IDs (0/0), so restoring a disabled touch setting could turn off Default/Default collision. This also broke unrelated contacts and could persist for the rest of that game session.

The loader now initializes the actual native listener before any checkbox callback and applies only PlayerHand/CharacterBody policy (8/20 in 0.6.7). It does not reset the global collision matrix or increase the Hand collider buffer. The native Character Touch checkbox still enables/disables hand/body contact as designed.

**Fully close and restart the game after installing.** Existing saves work without recreation. All 0.8.0 Appearance, BGM and scene features are retained. A primitive Unity-trigger regression reproduces failure on the old code and passes the fix across touch off/on transitions with the native Settings panel closed. Physical HMD acceptance still requires a retest; the user's previous 0.8.0 HMD test failed despite its earlier automated checks.

---

# MeltySave 0.8.0 — Appearance and scene restoration

Prerelease for MeltyNight VR Premium 0.6.7 (Windows x64).

- Move Appearance beside Scene slots on the native hand-menu header. The old entry overlapped Scene slots and could not be reached.
- Restore saved poses through the game's motion FSM. Restoring string fields and an animation alone left the native interaction controller stopped.
- Preserve character options, interaction-object configuration, player position, messages, movement speed and existing BGM work.
- Hair/eyebrow synchronization, mapped ear/tail editing, Follow hair color and an optional Absolute color mode.
- Close Appearance at the start of a scene load and clear its old character target.
- Shared Colors, Recent, Copy/Paste, independent eye colors where supported, appearance presets, Favorites and Revert changes.
- Save resolved appearance values, accessory links and absolute mode with scenes and presets. Older files remain readable without automatic rewriting.
- Add Settings > Capture diagnostics for physical VR follow-up. Snapshots stay on the local computer.

## Validation boundary

The loader passes non-HMD reproduction with copies of the reported saves: native motion initialization, actual Unity kiss trigger entry/exit, real prop collider contact with SFX source start/stop, and save/reload during contact. Storage and regression checks include existing slots/BGM/player/UI behavior and the new color data. See the release description for final build evidence.

**Physical HMD acceptance remains pending.** This release does not certify that every reported touch/penis/voice problem is resolved on the user's controllers. Test an idle save, an interaction-time save, enabled/disabled props, repeated map changes, native option values, left-stick movement and Appearance. If a failure remains, choose Capture diagnostics while it is happening, then reproduce save/load. The Hand collider capacity is unchanged at 32; physical overflow remains unclassified.

Native BreastSizeChange can throw during its outfit pass on some prefabs. Saved body/outfit weights are replayed afterward; tested values and UI match, but every native outfit callback is not certified. Colors preserve shading, so rendered brightness depends on lighting. Special facial-expression overlays may retain native colors. Bluerose has Both eyes only. No clothing recoloring, gradients, additional characters, duplicate-character support or live character swapping is included.

## Installation and rollback

Close the game, back up the current plugin, then extract the ZIP beside MeltyNight VR.exe. Keep MeltySave/saves and BGM. Required DLLs and decoder licenses are bundled; the game, BepInEx loader and music are not. Restore backed-up DLLs to roll back. See MeltySave-INSTALL.txt and USER-GUIDE.md.

Earlier local checkpoint notes follow; 0.7.0 and 0.7.1 were not published on GitHub.

---

## MeltySave 0.7.1 — Appearance, scene restoration and hand-menu fix (Preview)

For MeltyNight VR Premium 0.6.7 / Windows x64. Download **MeltySave-v0.7.1.zip** from the release assets; the automatic Source code archives are not installation packages. BepInEx is required separately; see INSTALL.txt in the ZIP.

- Fix the Appearance entry being hidden behind Scene slots in the native hand menu. Select a character in Character Settings, then use **Appearance** to the left of **Scene slots**.
- Keep the editor closed when the base game refreshes character controls. Continue using the native character selection as the editing target.
- Hair and iris color editing, live color field/brightness, RGB keypad, reset, per-character scene persistence, shared Colors, Recent, copy/paste, separate eyes where supported, presets, Favorites and Revert.
- Scene lifecycle repairs: release old contacts, rebind retained interaction objects to recreated characters, restore durable character options and synchronize native UI.
- Movement speed saved globally and per scene; BGM playback modes, Favorites, transport controls, seek and caching from the local 0.6 update are included.
- Existing saves remain readable; no bulk migration or automatic rewriting.

Validation: 112 managed checks and full non-HMD graphics/game integration, including entry and editor raycasts in the original hand-menu hierarchy. The previous standalone-canvas test missed the entry overlap; the native-parent test now covers it.

**Physical VR acceptance remains pending.** This is a preview, not a claim that every reported touch/kiss/audio failure is fixed. The Hand 32-collider warning was not reproduced without HMD; capacity is unchanged. A native breast-size outfit callback can still warn; saved mesh weights and model/UI roundtrips pass. Bluerose supports Both eyes only; dark native hair textures and special expression overlays can limit the rendered result. Details are in USER-GUIDE.md.

Close the game and back up the old plugin and MeltySave/saves before updating. Packages include English instructions, decoder licenses and music attribution; no original game assets, music tracks or user saves are included.

---

## MeltySave 0.7.0 — Appearance and scene lifecycle

Local prerelease for MeltyNight VR Premium 0.6.7 / Windows x64.

- Add Appearance to native per-character settings: hair/iris colors, live color field, brightness, numeric RGB and original-material reset.
- Save independent appearance values with every character in a scene. Old scenes use native colors.
- Add shared Colors, 12 Recent colors, copy/paste, appearance presets, Favorites, rename/overwrite/delete and editing-session Revert.
- Support individual eye colors on independent UV regions; Bluerose remains Both eyes only.
- Rebind retained interaction objects to newly loaded characters; stop copying transient facial/contact animation state.
- Restore native character options and synchronize character-specific controls from the model.
- Save movement speed globally and per scene; adjust only scoped left-stick input.
- Preserve existing scene slots, thumbnails, portraits, player/body origin, message controls and all 0.6 BGM features.

Physical headset contact/audio recovery is still unverified. The reported 32-collider warning was not reproduced without VR; capacity remains unchanged. A native breast-size callback can throw during its outfit pass; optional failures are logged and captured mesh weights are restored afterward. Scene roundtrip checks passed despite that warning. Appearance mapping bindings cover 34 local character prefabs; detailed pixel/runtime checks focus on ICHIGO and Ciely. This package is for further physical VR acceptance testing, not a claim that every reported interaction failure is conclusively fixed.

No original game assets, music files or personal saves are bundled. Back up the previous DLL and MeltySave/saves before upgrading. Details and controls are in USER-GUIDE.md.

---

## MeltySave 0.6.0 — BGM playback, Favorites and caching

Local prerelease patch for **MeltyNight VR Premium 0.6.7 / Windows x64**.

- Save BGM mode, queue folder, playhead and playing/paused/stopped state with each scene.
- Preserve player body position/heading, VR origin, message settings and Touch response in scene slots.
- Repeat the current track, cycle a folder, cycle its parent and subfolders, or cycle Favorites.
- Add/remove Favorites without copying music files; keep the list across game restarts.
- Seek bar, Play, Pause, Stop, Previous track and Next track in Settings > BGM.
- Reuse loaded clips immediately, keep a bounded decoded cache across restarts, and prepare the next track during cycling.
- Detect changed source files; rebuild corrupted cache entries; clear the cache without deleting original audio.

English controls and original user filenames are retained. Hair/eye RGB work is paused and not included. Music audio, game files and personal saves are not bundled. A cold load can still take time; gapless playback and hands-on VR controller use need manual validation. Other game versions remain unverified.

Close the game before replacing the plugin and keep a backup of MeltySave/saves. Existing scene slots are supported. Enable Load slot audio to restore the saved BGM state.

---

## MeltySave 0.5.0 — Scene slots and expanded BGM selection

Initial public prerelease for **MeltyNight VR Premium 0.6.7 / Windows x64**.

### Download and install

Download **MeltySave-v0.5.0.zip** below. It includes English installation, update, uninstall and usage instructions, plus all mod-specific audio decoder dependencies. No source compilation is needed.

**BepInEx is required separately.** Follow [the installation guide](https://github.com/CrouchingWriter/MeltySave/blob/main/INSTALL.txt) for the verified Unity IL2CPP Windows x64 build and extraction steps. GitHub's **Source code** archives are not installation packages.

### Included features

- Scene save/load with five slots per page and expandable pages.
- Character/environment/pose/clothing/position settings, scene thumbnails and slot management.
- Player position recovery and message display/position controls.
- Built-in BGM selection across maps.
- Custom MP3, OGG Vorbis and WAV playback from the game-root BGM folder.
- Mood folders, original filenames, Korean/Japanese title display and Refresh files.
- Selected BGM saved with global settings and scene slots.

### Validation and limitations

64 automated checks passed, along with local game integration and decoding of a 35-track collection. Actual VR controller/headset operation and audible loop transitions remain unverified. Only game version 0.6.7 has been checked. Tracks repeat end-to-start; embedded loop-point tags are not used.

Back up `MeltySave/saves` and the existing plugin/dependencies before updating. Music files and game assets are not included. The attached SHA256SUMS.txt identifies the installation ZIP; an internal manifest lists every packaged file.

### Music attribution

The ZIP includes a [35-track credits and source catalogue](https://github.com/CrouchingWriter/MeltySave/blob/main/MUSIC-CREDITS.md), matched to the local collection's attribution notes. Audio is not bundled; obtain it from the linked creators under their respective terms.

[Full user guide](https://github.com/CrouchingWriter/MeltySave/blob/main/USER-GUIDE.md) · [Bug reports](https://github.com/CrouchingWriter/MeltySave/issues)
