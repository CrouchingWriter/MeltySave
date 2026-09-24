# MeltySave

Current preview: **0.8.8** — Appearance selection, native ear/tail color protection and INABA KAYA Absolute color fixes.

Scene slots, music playback and character colors for **MeltyNight VR Premium 0.6.7, Windows x64**.

**[Download v0.8.8](https://github.com/CrouchingWriter/MeltySave/releases/tag/v0.8.8)** · **[Installation](INSTALL.txt)** · **[User guide](USER-GUIDE.md)** · **[Report a bug](https://github.com/CrouchingWriter/MeltySave/issues)**

Download `MeltySave-v0.8.8.zip` from the release assets. GitHub's automatically generated **Source code** archives do not contain the installable plugin.

> 0.8.8 includes all local changes since v0.8.2. It keeps Appearance available after target changes, expands native ear/tail protection, saves hair links with scenes, and repairs INABA KAYA Absolute color while selected. Physical HMD acceptance is pending.

## Features

- Five scene slots per page, with additional pages and slot management.
- Save/load the environment, characters, poses, clothing, player/character positions, audio and message settings.
- Scene thumbnails, character portraits, overwrite, rename, copy, move, delete and recovery.
- Reset player position to the current map's start.
- Select built-in BGM from other maps or your own MP3, OGG Vorbis and WAV tracks.
- Browse music by mood folders and original filenames, including Korean/Japanese titles.
- Restore selected BGM, playback mode, playhead and transport state with scene slots.
- Seek, play, pause, stop, switch tracks, cycle folders/Favorites and reuse cached custom audio.

- Hair/eye RGB editing, live color field, synchronized eyebrows, mapped ear/tail colors, hair links and optional Absolute color mode.
- Shared Colors, Recent, Copy/Paste, appearance presets, Favorites and per-character scene persistence.
- Native motion initialization during scene loading, hand-menu Appearance entry fix, movement multiplier and local interaction diagnostics.

## Installation

Requires **BepInEx 6.0.0-be.697, Unity IL2CPP Windows x64**; the loader is a separate download linked in [INSTALL.txt](INSTALL.txt). The loader version was verified from the local game's runtime log.

Close the game, install/initialize BepInEx, then extract `MeltySave-v0.8.8.zip` into the folder containing `MeltyNight VR.exe`. The plugin should be at `BepInEx/plugins/MeltySave.dll`, beside `NVorbis.dll` and `NLayer.dll`. Back up existing plugin files and `MeltySave/saves` before updating.

Open the existing hand menu and select **Scene slots**, or press **F8**. Select a character in Character Settings, then choose **Appearance** to the left of Scene slots for colors. For music, use **Settings > BGM**. Put your tracks and category folders under **BGM**, then choose **Refresh files**.

## Release status

**0.8.8 is a prerelease.** 133 automated checks and 62 game/graphics stages passed, including the native selection-state regression and UI callbacks. Physical HMD/controller acceptance remains pending. Other game versions are unverified. Choose **Settings > Capture diagnostics** to record a failed state locally. This release does not claim to resolve the SteamVR 32-collider warning.

Hair/eye profile bindings cover the game's 34 selectable character prefabs; optional ears/tails appear only where mapped. Original shader/detail/alpha are retained, so lighting still affects rendered colors. Bluerose uses Both eyes only. Native BreastSizeChange may warn for some outfit paths; saved mesh weights are reapplied. See [release notes](RELEASE-NOTES.md) and [Dev Log #05](DEV-LOG-05-EN.md) ([한국어](DEV-LOG-05-KO.md)).

Animations restart at the saved state. Exact animation time, transient physics and live interactions are not preserved. The native Touch response checkbox is saved; this is not a separate haptics-only toggle. Live character replacement, duplicate characters and higher character limits are not included.

This repository hosts release downloads and documentation. Packages include the plugin and audio decoder libraries, with their third-party licenses. Game files, music tracks, personal saves and game artwork are not distributed here.

## Music credits

The [music credits and source catalogue](MUSIC-CREDITS.md) identifies all 35 tracks from the maintainer's local collection and links to their creators. The same document is included in the installation ZIP. Obtain audio from the creators under their own terms; this release does not redistribute a music pack.
