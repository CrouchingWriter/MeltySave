## 0.8.2 character color update

Maya and Kokoa now use the correct surface/shade color properties. On these two models, Ears changes outer fur while preserving inner skin/fluff; Tail changes its base while preserving the original tip and ornaments. Follow hair color and restored scenes use the same protection. Other models retain their existing mappings until individually checked. Existing saves/presets do not need conversion.

The user reports that scene saving/loading now appears fixed with 0.8.1. That repair is retained. Please check the new appearance results in HMD after restarting; in-game rendered colors still depend on lighting.
## 0.8.1 contact hotfix

The 0.8.0 HMD retest failed after scene loading. A further collision-policy defect has now been reproduced and corrected: applying a saved touch value before opening the native Settings panel could use uninitialized layer IDs and disable unrelated Default contacts. The handler now initializes before applying only the intended hand/body setting.

Fully close and restart the game after updating. Existing saves do not need recreation. Character Touch retains its native hand/body enable-disable behavior. Physical HMD confirmation remains pending; use Capture diagnostics during any remaining failure.
## Appearance and scene restoration (0.8.1)

Select a character in the game's **Character Settings**, then choose **Appearance** on the hand-menu header, left of **Scene slots**. The editor follows the native selection. It closes when a scene starts loading. Use Hair, Eyes, and the available Ears/Tail tabs, the color field, Brightness, quick swatches, or the RGB number pad (0-255).

Hair color also updates the mapped eyebrows. **Follow hair color** links an ear/tail color to the current hair color; entering a color directly unlinks that part. Parts without a mapped native animal-ear/tail mesh have no tab. If a model shares ear/tail UV coordinates, the editor labels the shared-color limitation. **Absolute color** removes the original hue from the color textures and handles additional colored shader contributions, while retaining texture detail, alpha and native shading. It is a color replacement mode, not an unlit guarantee that every rendered pixel equals the input RGB. Default tint mode remains available for older saves.

**Reset hair / Reset eyes / Reset ears / Reset tail** restore the original part appearance. **Revert changes** returns to the appearance at editor entry. Closing keeps edits; save or overwrite a scene slot to retain them across launches. Left/Right/Both eye selection is available; Bluerose supports Both eyes only because its iris UVs overlap.

**Colors** stores reusable individual colors. **Presets** stores resolved appearance combinations, now including accessory colors, links and absolute mode. Both support Save new, Overwrite, Rename, Delete and Favorites, with five entries per page. Recent stores 12 committed colors; dragging adds only the final color. Copy/Paste works across parts and characters. Libraries use `MeltySave/saves/colors.json`; scene slots store independent values, not references to library entries.

Scene loading now runs the native pose-selection lifecycle after reconstructing characters, so selecting a saved interaction pose also initializes its native controller and voice path. It does not replay an interrupted kiss/touch as a live contact. Old contacts are released, retained interaction objects are rebound, and actual physics may start a new contact after loading. Character options, native UI values and movement speed remain part of scene restoration. Older saves stay readable without bulk conversion; missing appearance uses native defaults, and missing movement speed retains the current preference.

**Settings > Slower / Faster** changes the left-stick multiplier from 0.25x to 3.00x, globally and per scene. **Settings > Capture diagnostics** records current interaction state and enables before-save/after-load and Hand-overflow snapshots for that session. Files are local under `MeltySave/diagnostics/interaction`; nothing is uploaded. Restart the game to end session recording (unless an explicit diagnostic flag is present).

This is a **prerelease for Premium 0.6.7**. The previous HMD report also reproduced with new saves. The new native-lifecycle fix passes non-HMD tests using copies of those saves and real Unity collider events, including interaction sound-source start/stop. Physical HMD controller contact, audible voice/SFX recovery, locomotion, and the 32-collider warning still require user confirmation. The Hand buffer remains 32; it has not been raised to hide the warning. Cross-version support is unverified.

---

# Scene Slots / MeltySave 0.8.1

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
- Selected BGM, playback mode, queue folder, playhead, and playing/paused/stopped state.
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

**Repeat track** loops from the end of the file to the beginning. Seamless playback requires audio prepared for that boundary; embedded loop-point tags are not used. Decoding runs off the game thread, and the previous track continues until the new clip is ready. Missing, corrupt or unsupported files report an error and retain the previous selection. File size is limited to 128 MB and decoded PCM to 256 MB (8-192 kHz).

The selected track is saved with global audio settings and with scene slots. **Load slot audio** controls whether loading a scene also restores its music. Old saves without a track ID leave the selection unchanged. Custom audio is referenced by its path relative to BGM, so equal filenames in different folders remain distinct. It is not embedded in the scene file. Preserve the folder structure when moving saves to another installation. Renaming or moving a saved song requires selecting its new location and saving again.

### Playback controls and Favorites

The top row contains **Previous track**, **Play**, **Pause**, **Stop**, and **Next track**. Click or drag the seek bar to jump to a point in the track. Pause retains the playhead; Stop returns it to the start. The separate **Previous / Next** buttons below the list change browser pages.

- **Repeat track** repeats the selected track. Previous/Next track manually choose another track in its folder.
- **Folder** cycles tracks directly inside the selected track's folder.
- **Parent folder** cycles tracks in that folder's parent, including its subfolders. The parent remains fixed while the queue advances. A track directly in BGM uses all custom tracks. Built-in tracks cycle within the built-in library.
- **Favorites** cycles the saved Favorites list in the order tracks were added. Use **Add favorite / Remove favorite** beside a track. The **Favorites** button at the top opens the list; it does not change playback mode.

Normal folders cycle by relative filename. Lists wrap at their ends. Missing or failed tracks are skipped during cycling; an entirely unplayable list stops. Favorites are references, so adding one does not copy the audio file. Missing Favorites remain visible and removable. Folder browsing alone does not change the active queue; choose a track and then a mode.

Scene slots now capture BGM playback position and playing/paused/stopped state, along with the selected track, mode and queue folder. Global audio preferences retain the selection, mode and transport state; the continuously moving playhead is saved only in scene slots. Old slots without playback metadata remain supported. Player position/heading, VR origin, message controls and native Touch response remain part of scene state.

### BGM cache

Custom tracks are decoded on a worker thread and cached as PCM under **MeltySave/cache/bgm** (up to 1 GB on disk). Loaded Unity clips are also kept in memory (up to 512 MB; the playing/prepared clips are protected). Recently loaded tracks start directly from memory. Cycling prepares the next track ahead of time.

The disk cache survives game restarts and avoids decoding unchanged audio again. The first play of an uncached track, and loading cached PCM back into Unity after a restart or eviction, can still take time. This is not a guarantee of zero delay or gapless transitions. File size and modification time invalidate stale entries. **Clear cache** clears reusable entries while keeping the current clip playing; original music and saves remain intact. Files added or moved while the game is running require **Refresh files**.

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
MeltySave/saves/audio.json      Global audio and playback preferences
MeltySave/saves/music-library.json  Favorites list
MeltySave/cache/bgm/            Disposable decoded custom-music cache
MeltySave/saves/messages.json   Global message visibility/position/angle
MeltySave/saves/recovery.json   Scene before the last load
MeltySave/saves/history/        Previous file versions
MeltySave/saves/trash/          Deleted slots
BepInEx/LogOutput.log           Plugin log
```

Back up the entire `MeltySave/saves` directory with the game closed. History and trash are not automatically pruned. Unreadable slots are shown as **Unreadable slot** and preserved until explicitly deleted. Failed scene loading is not fully transactional; use **Restore previous scene** if needed.

Older scene saves remain readable. Compatibility is currently limited to game version 0.6.7. This 0.6.0 patch is a prerelease; other game versions and hands-on VR operation remain unverified. See MeltySave-INSTALL.txt in the installation ZIP for setup instructions.


