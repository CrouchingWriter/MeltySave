# MeltySave

Scene slots, music playback and character colors for **MeltyNight VR Premium 0.6.7, Windows x64**.

**[Download v0.8.1](https://github.com/CrouchingWriter/MeltySave/releases/tag/v0.8.1)** · **[Installation](INSTALL.txt)** · **[User guide](USER-GUIDE.md)** · **[Report a bug](https://github.com/CrouchingWriter/MeltySave/issues)**

Download `MeltySave-v0.8.1.zip` from the release assets. GitHub's automatically generated **Source code** archives do not contain the installable plugin.

> 0.8.1 fixes a reproduced collision-layer initialization error after scene load. Fully restart the game after updating; existing saves remain usable. The previous 0.8.0 HMD retest failed, and physical confirmation of this hotfix is still pending.

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

Close the game, install/initialize BepInEx, then extract `MeltySave-v0.8.1.zip` into the folder containing `MeltyNight VR.exe`. The plugin should be at `BepInEx/plugins/MeltySave.dll`, beside `NVorbis.dll` and `NLayer.dll`. Back up existing plugin files and `MeltySave/saves` before updating.

Open the existing hand menu and select **Scene slots**, or press **F8**. Select a character in Character Settings, then choose **Appearance** to the left of Scene slots for colors. For music, use **Settings > BGM**. Put your tracks and category folders under **BGM**, then choose **Refresh files**.

## Release status

**0.8.1 is a prerelease.** 117 managed checks and the full game/graphics regression suite passed. The reported saves also pass native motion initialization, real Unity contact and interaction SFX start/stop tests outside HMD. Physical controller touch/kiss, audible voice/SFX recovery and the SteamVR 32-collider warning remain pending; this is not certification that every reported interaction bug is fixed. Choose **Settings > Capture diagnostics** to record a failed state and subsequent save/load locally. Other game versions are unverified.

Hair/eye profile bindings cover the game's 34 selectable character prefabs; optional ears/tails appear only where mapped. Original shader/detail/alpha are retained, so lighting still affects rendered colors. Bluerose uses Both eyes only. Native BreastSizeChange may warn for some outfit paths; saved mesh weights are reapplied. See [release notes](RELEASE-NOTES.md) and [Dev Log #05](DEV-LOG-05-EN.md) ([한국어](DEV-LOG-05-KO.md)).

Animations restart at the saved state. Exact animation time, transient physics and live interactions are not preserved. The native Touch response checkbox is saved; this is not a separate haptics-only toggle. Live character replacement, duplicate characters and higher character limits are not included.

This repository hosts release downloads and documentation. Packages include the plugin and audio decoder libraries, with their third-party licenses. Game files, music tracks, personal saves and game artwork are not distributed here.

## Music credits

The [music credits and source catalogue](MUSIC-CREDITS.md) identifies all 35 tracks from the maintainer's local collection and links to their creators. The same document is included in the installation ZIP. Obtain audio from the creators under their own terms; this release does not redistribute a music pack.
