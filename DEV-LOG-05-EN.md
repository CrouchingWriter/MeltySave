**Dev Log #05 — Appearance & scene-load fixes**

MeltySave **0.8.0** adds character colors and another round of scene-loading repairs for **MeltyNight VR Premium 0.6.7**.

**Appearance**
- Open Appearance beside Scene slots in the existing character-settings menu.
- Edit hair and eyes with a color field, brightness control or RGB input.
- Hair color also updates eyebrows.
- Edit mapped animal ears/tails separately, or enable **Follow hair color**.
- Enable **Absolute color** to replace the original hue while retaining texture detail and shading.
- Shared Colors, Recent, Copy/Paste, appearance presets, Favorites and Revert changes.
- Separate left/right eye colors where the model supports them.
- Colors and links are saved with each scene. Loading closes the old editor.

**Bug report / repair**
The previous HMD report also occurred with newly created saves. Investigation found that restoring a pose name and animation did not run the game's native interaction-start sequence. Loading now uses the native motion controller and rebuilds character/interaction bindings.

Copies of the reported saves pass automated Unity contact checks, including real prop collider contact, interaction SFX start/stop and reloading during contact. The native Appearance entry overlap has also been corrected.

**Physical HMD confirmation is still pending.** I am not calling every reported interaction/voice/penis issue conclusively fixed yet. The Hand collider limit remains unchanged. Settings now includes **Capture diagnostics** for follow-up reports.

Installation ZIP and English instructions:
https://github.com/CrouchingWriter/MeltySave/releases/tag/v0.8.0
