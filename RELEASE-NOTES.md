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
