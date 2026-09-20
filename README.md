# MeltySave

Scene slots and music selection for **MeltyNight VR Premium 0.6.7, Windows x64**.

**[Download v0.5.0](https://github.com/CrouchingWriter/MeltySave/releases/tag/v0.5.0)** · **[Installation](INSTALL.txt)** · **[User guide](USER-GUIDE.md)** · **[Report a bug](https://github.com/CrouchingWriter/MeltySave/issues)**

Download `MeltySave-v0.5.0.zip` from the release assets. GitHub's automatically generated **Source code** archives do not contain the installable plugin.

## Features

- Five scene slots per page, with additional pages and slot management.
- Save/load the environment, characters, poses, clothing, player/character positions, audio and message settings.
- Scene thumbnails, character portraits, overwrite, rename, copy, move, delete and recovery.
- Reset player position to the current map's start.
- Select built-in BGM from other maps or your own MP3, OGG Vorbis and WAV tracks.
- Browse music by mood folders and original filenames, including Korean/Japanese titles.
- Restore the selected BGM with settings and scene slots.

## Installation

Requires **BepInEx 6.0.0-be.697, Unity IL2CPP Windows x64**; the loader is a separate download linked in [INSTALL.txt](INSTALL.txt). The loader version was verified from the local game's runtime log.

Close the game, install/initialize BepInEx, then extract `MeltySave-v0.5.0.zip` into the folder containing `MeltyNight VR.exe`. The plugin should be at `BepInEx/plugins/MeltySave.dll`, beside `NVorbis.dll` and `NLayer.dll`. Back up existing plugin files and `MeltySave/saves` before updating.

Open the existing hand menu and select **Scene slots**, or press **F8**. For music, use **Settings > BGM**. Put your tracks and category folders under **BGM**, then choose **Refresh files**.

## Release status

**0.5.0 is a prerelease.** Automated checks and local game integration passed on game version 0.6.7. Actual headset/controller operation and audible loop transitions still need hands-on testing. Other game versions are unverified.

Animations restart at the saved state. Exact animation time, transient physics and live interactions are not preserved. The native Touch response checkbox is saved; this is not a separate haptics-only toggle. Live character replacement, duplicate characters and higher character limits are not included.

This repository hosts release downloads and documentation. Packages include the plugin and audio decoder libraries, with their third-party licenses. Game files, music tracks, personal saves and game artwork are not distributed here.

## Music credits

The [music credits and source catalogue](MUSIC-CREDITS.md) identifies all 35 tracks from the maintainer's local collection and links to their creators. The same document is included in the installation ZIP. Obtain audio from the creators under their own terms; this release does not redistribute a music pack.
