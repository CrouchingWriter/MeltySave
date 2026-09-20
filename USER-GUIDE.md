# Scene Slots / MeltySave 0.5.0

A removable BepInEx IL2CPP scene-save plugin for **MeltyNight VR Premium 0.6.7, Windows x64**. The plugin UI and documentation are in English. Original game executables, assets, and metadata are not edited.

## Use

1. Start the game and open its existing hand menu.
2. Select **Scene slots**. Use the game's controller laser and click input. **F8** also opens or closes the window.
3. Choose **+ Save scene** in an empty slot to capture the current scene and its thumbnail.
4. Choose **Load**, then **Confirm**, to restore a saved scene. The scene before loading is saved as a recovery snapshot.
5. Use **Manage** to overwrite, rename, copy, move, or delete a slot.

The interface uses a single window with screens for slots, settings, management, name entry, and confirmation. **Recenter** moves it in front of the current view. **Close** or **Escape** hides it. Controls are locked while a scene is loading.

**Reset player position**, in the window header, returns the player to the current environment's start and resets the tracking-origin offset and tilt. It also recenters the menu. Use it after getting stuck or leaving the environment. It does not reload characters or overwrite a slot.

Each page holds five slots. **Previous**, **Next**, and **Add page** navigate a library of up to 1,000 pages. Copy and move require an empty destination slot, including on other pages. **Undo delete** restores the last deleted slot if its original position is empty. **Restore previous scene** restores the snapshot from before the last load.

**Rename** uses an on-screen English keyboard, digits, space, hyphen, and underscore. Existing user-entered names are preserved; their display depends on installed font coverage. Renaming does not recapture the scene or its thumbnail. Overwriting captures both again.

## Saved state

- Selected environment, including Beach and Mixed Reality (passthrough).
- Spawned character list and the character currently selected for editing.
- Each character's world position (X/Y/Z) and rotation.
- Player body position (X/Y/Z), heading, and VR tracking-origin offset and heading.
- Message display checkbox, position parameter, and angle parameter.
- Outfit selection, active clothing parts, and blend-shape values.
- Animation state, speed, mirror, and other animator parameters.
- Music, ambience, effects, voice, mute-toggle values, and master audio volume.
- The game's native **Touch response** checkbox value.
- A 640 x 360 scene thumbnail, embedded in the slot file.

Character portraits reuse sprites from the game's own character selection menu. No character artwork is bundled with the mod.

**Touch response** is the existing `BodyTouch` checkbox: it enables/disables contact between the player's hands and character bodies. It is not an independent haptics-only switch. The plugin restores this checkbox and its contact behavior; physical controller vibration still depends on the base game and VR runtime.

Animations resume from the beginning of the saved state. This is not a complete process checkpoint: physics, transient effects, exact animation time, and live interactions are not preserved. The environment's built-in `Necomaid` NPC is not treated as a user-spawned character.

## Thumbnails

Saving hides active game canvases for the capture and restores them immediately afterward. The thumbnail uses the game camera's current view; it excludes mod and game menus. It is a normal game-camera render, not an HMD compositor screenshot: external passthrough video and some camera post-processing may differ from what the headset displays.

Thumbnails travel with the slot through copy, move, rename, overwrite history, deletion, and recovery. Old saves without thumbnails remain loadable and show an empty preview area. Overwrite an old slot to add a new capture. A capture failure leaves the existing slot untouched and reports an error.

## Audio and settings

**Settings** provides **-**, **+**, and **Toggle mute** for Music, Ambience, Effects, and Voice. **Show messages** hides or shows the game's message text. **Message position** and **Message angle** use the original game's slider parameters and limits. Position changes in steps of 0.01 and angle changes in steps of 5 degrees.

Settings changes apply immediately. Audio and native message-slider changes are automatically saved after a short pause. Mod message controls save immediately. **Save settings** saves audio and messages immediately; **Apply saved settings** reloads those global preferences. They are also loaded on the next game launch. Message settings are stored in each scene slot and restored independently of the audio option. A legacy slot without message data leaves the current message preferences unchanged.

**Load slot audio: ON/OFF** controls whether a scene load also restores its stored audio. New libraries default to ON. Existing libraries retain their previous choice. Touch response is stored per scene and restored regardless of the audio option; it is not automatically saved as a global preference. Old saves without touch data leave the current checkbox unchanged.

## BGM selection and custom music

Open **Settings > BGM**. Select **Open** beside a folder to browse the user's own categories, or **Built-in music** for map tracks and the original three BGM choices. Choose **Play** beside a song. **Back** returns to the parent folder. The selection keeps playing across environment changes. **Map default** returns to the original music for the current map and follows later map changes. The game's original BGM selector also remains usable.

For custom music, place files or categorized folders in **BGM** beside `MeltyNight VR.exe`. Use **Refresh files**, then open a category or use **Next** for additional pages. Subfolders are scanned recursively; linked folders/files are skipped. Folder names and song filenames are shown unchanged, with only the file extension hidden. Korean/Japanese filenames use installed font fallbacks; interface controls remain English. Supported formats are **MP3**, **OGG Vorbis** and **WAV** (PCM 8/16/24/32-bit or float32), mono or stereo. Ogg Opus, encrypted `.bgm` files and WAV extensible/compressed variants are not supported in this build.

Tracks loop from the end of the file to the beginning. Seamless playback requires audio prepared for that boundary; embedded loop-point tags are not used. Decoding runs off the game thread, and the previous track continues until the new clip is ready. Missing, corrupt or unsupported files report an error and retain the previous selection. File size is limited to 128 MB and decoded PCM to 256 MB (8-192 kHz).

The selected track is saved with global audio settings and with scene slots. **Load slot audio** controls whether loading a scene also restores its music. Old saves without a track ID leave the selection unchanged. Custom audio is referenced by its path relative to BGM, so equal filenames in different folders remain distinct. It is not embedded in the scene file. Preserve the folder structure when moving saves to another installation. Renaming or moving a saved song requires selecting its new location and saving again.

Custom clips use the original BGM AudioSource and mixer, so Music volume/mute still applies and ambience/voices remain separate. Decoders: [NVorbis 0.10.5](https://github.com/NVorbis/NVorbis) for OGG and [NLayer 3.0.0](https://github.com/naudio/NLayer) for MP3. Both use MIT licenses under `licenses/`; installation copies the dependencies and licenses beside the plugin.

## Player position and environment changes

New slots restore the collision body and VR tracking origin together after environment loading. The tracked HMD pose is not serialized or forced; physical head movement continues to come from the VR runtime. Only upright player and origin headings are restored, not pitch or roll.

Old slots without player data use the selected environment's starting position. Overwrite an old slot to add the current player position. Original game environment changes also reset the player and origin together, instead of carrying a previous environment's origin offset into the new one. Saved positions are coordinates, not a navigation-mesh guarantee: a scene deliberately saved outside the map can still require **Reset player position**.

## Files

Paths relative to the game folder:

```text
BepInEx/plugins/MeltySave.dll   Plugin
BepInEx/plugins/NVorbis.dll     OGG decoder dependency
BepInEx/plugins/NLayer.dll      MP3 decoder dependency
BGM/                           User-supplied music and category folders
MeltySave/saves/library.json    Pages and load-audio preference
MeltySave/saves/slot-00001.json  Scene, player, messages, audio, touch, thumbnail
MeltySave/saves/audio.json      Global audio settings
MeltySave/saves/messages.json   Global message visibility/position/angle
MeltySave/saves/recovery.json   Scene before the last load
MeltySave/saves/history/        Previous file versions
MeltySave/saves/trash/          Deleted slots
BepInEx/LogOutput.log           Plugin log
```

Back up the entire `MeltySave/saves` directory with the game closed. History and trash are not automatically pruned. Unreadable slots are shown as **Unreadable slot** and preserved until explicitly deleted. Failed scene loading is not fully transactional; use **Restore previous scene** if needed.

Older scene saves remain readable. Compatibility is currently limited to game version 0.6.7. The public 0.5.0 package is a prerelease; other game versions and hands-on VR operation remain unverified. See MeltySave-INSTALL.txt in the installation ZIP for setup instructions.


