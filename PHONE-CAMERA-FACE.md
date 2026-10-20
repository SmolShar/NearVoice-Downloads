# Phone, camera and local face preview

Add this **single URL** in Dalamud `/xlsettings` > Experimental > Custom Plugin Repositories, enable and Save:

```text
https://raw.githubusercontent.com/SmolShar/NearVoice-Downloads/main/phone-camera-face.json
```

Refresh `/xlplugins` and use **All Plugins > All**. Install **Aethr App (local Discord)**, **Musical Guide (local camera R7)** and **NearFace Local Controls (prototype)** as needed. NearFace requires the matching **Customize+ (local NearFace fork)**. The existing Customize+ package still shares the upstream `CustomizePlus` identity: Dalamud can hide that entry when the official catalog contains the same identity. This camera update does not change or migrate that package. Retain an existing matching local Customize+ installation and its profiles. No system Python installation is needed.

Before enabling this local phone, disable the official Aetherphone, old PocketLink and LocalPhone. Back up existing plugin configurations; retain your Customize+ profiles. The local phone has its own configuration namespace and does not import the original Aethernet account.

## Phone — R3 1.3.2.3

This is a modified copy of the original Aetherphone shell and apps, not a PocketLink replacement. Open `/phone` or `/aetherphone` (or its plugin Open button), then Contacts/Messages and connect Discord explicitly. Authorize **your own** Discord account. Friends and avatars come from the official Social SDK. Recent text DM history is limited by the SDK; no fake message/read receipts are generated. Session tokens and messages stay in helper memory and are cleared on unlink/exit. Reauthorization may be needed after restart.

R3 uses distinct window identities for Discord notifications, message history and the message composer. The avatar status display counts ready, loading and failed avatars and provides a retry action. The new avatar status and retry text is included in all nine bundled locales, including Turkish.

The Aethernet social service is disabled in this edition. Ordinary personal Discord calls, general embedded browsing/video and the optional online Hunts feed are unavailable. This is not an official Aetherphone, Discord or Square Enix release.

## Camera — R7 1.8.0.9 near-plane fog correction

**Update Musical Guide (local camera R7) to 1.8.0.9, then fully exit and restart FFXIV.** The package still uses `MusicalGuideLocalCamera` and the same repository URL. Existing 1.8.0.8 camera settings, FOV, offsets and saved hand-clipping preference are retained. Keep other Musical Guide copies disabled; they share `/mguide` and camera hooks.

Open `/mguide`. The title must contain **near fog fix r7**. The title's assembly version remains 1.8.0.0; the installer and file version are 1.8.0.9. This is a newly compiled camera behavior correction.

R6 could make distant scenery white/foggy when **Reduce hand / object clipping** was enabled. R7 changes the native camera's near distance consistently with projection generation, and restores its captured baseline on supported cleanup routes. The projection hook forwards native arguments unchanged and still requires the original executable, ABI, local owner and matrix proof. Other camera callbacks cannot suspend the owned local near value. The status label now reflects the current enabled state.

Use **First Person Settings → First Person Adjustments / Hand clipping**. The saved **Automatically restore hand-clipping reduction** preference remains opt-in. For manual use, enter normal local first person and press **Test and enable hand-clipping reduction**; keep **Local near distance** at **0.010** for the original comparison. Compare the same scene with reduction off and on. Check that hand clipping improves without the white fog and that disabling restores the normal view. The code was built and its managed tests passed; this release has not been visually accepted inside FFXIV here.

The camera movement, reduced-motion yaw, local head coordination and mount options retain their existing behavior. R7 does not migrate settings from the original `MusicalGuide` identity. If you already transferred settings to `MusicalGuideLocalCamera`, no further transfer is needed. Do not reset plugin data.

## Face / webcam

Enable the matching Customize+ fork and open `/nearface`. **Start live session (webcam + receiver)** explicitly opens the bundled webcam and local receiver together. No separate Python setup or console launcher is needed. **Stop live session** or unloading NearFace stops its owned helper. A parent-stdin EOF also stops capture. Nothing opens the webcam merely by loading the plugin or opening its panel.

Components still start disabled: preview your actual face, then choose live eyelids/mouth/brows. Measured eyelid rotations remain opt-in for the correct sculpt. Tongue and native gaze retargeting are incomplete. Only local numeric coefficients are transmitted over loopback; webcam images are not recorded/uploaded.

If you explicitly launch START-WEBCAM.cmd manually, that independent console must be stopped there; the plugin only controls the helper it started itself. Missing helper/camera/device errors are shown in the panel.

## Source and validation limits

Current corresponding source: [phone R3 1.3.2.3](https://github.com/SmolShar/NearVoice-Downloads/releases/download/phone-camera-r3-r6-2026-10-19-preview/AethrAppLocalDiscord-1.3.2.3-source.zip), [camera R7 1.8.0.9](https://github.com/SmolShar/NearVoice-Downloads/releases/download/camera-r7-near-fog-fix-2026-10-20/MusicalGuideLocalCamera-1.8.0.9-source.zip), [NearFace controls 0.2.4.0](https://github.com/SmolShar/NearVoice-Downloads/releases/download/phone-webcam-hotfix-2026-10-19/NearFaceControls-0.2.4.0-source.zip), and [Customize+ 2.2.1.6 in the existing preview source bundle](https://github.com/SmolShar/NearVoice-Downloads/releases/download/phone-camera-face-2026-10-19-preview/Face-Camera-Corresponding-Source.zip). The NearFace and Customize+ source archives are unchanged by this release. Webcam runtime/model source and original notices remain inside the existing NearFace payload. Original AGPL/Apache/MIT/BSD notices are retained. Obtain official Discord SDK headers/import libraries separately for rebuilding the unchanged native helper; its integrated DLL and notices remain unmodified.

R7 was built with .NET SDK 10.0.402 and matching official Dalamud 15.0.3.8 references. All 35 projection/ownership tests and 67 existing camera math/pose tests passed. Reports distinguish managed/model checks from native game acceptance. R7 package checks also cover source-to-PDB hashes, archive contents, dependency metadata and repository version consistency. R3 package checks cover the supplied file hashes and metadata. Previous release builds, webcam smoke checks and standalone OAuth results are historical evidence, not newly rerun R3/R6 tests. Native game presentation, real DM send/receive, camera and mount behavior, and advanced expressions still require runtime acceptance. This update does not add advanced face channels or establish a complete avatar fix. No account configuration, OAuth token, credential, captured webcam image or user profile is included.

This separate index leaves the existing NearVoice `repo.json` and releases unchanged.

