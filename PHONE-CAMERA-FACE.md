# Phone, camera and local face preview

Add this **single URL** in Dalamud `/xlsettings` > Experimental > Custom Plugin Repositories, enable and Save:

```text
https://raw.githubusercontent.com/SmolShar/NearVoice-Downloads/main/phone-camera-face.json
```

Refresh `/xlplugins` and use **All Plugins > All**. Install **Aethr App (local Discord)**, **Musical Guide (local camera R6)** and **NearFace Local Controls (prototype)** as needed. NearFace requires the matching **Customize+ (local NearFace fork)**. The existing Customize+ package still shares the upstream `CustomizePlus` identity: Dalamud can hide that entry when the official catalog contains the same identity. This camera-only installer correction does not change or migrate that package. Retain an existing matching local Customize+ installation and its profiles. No system Python installation is needed.

Before enabling this local phone, disable the official Aetherphone, old PocketLink and LocalPhone. Back up existing plugin configurations; retain your Customize+ profiles. The local phone has its own configuration namespace and does not import the original Aethernet account.

## Phone — R3 1.3.2.3

This is a modified copy of the original Aetherphone shell and apps, not a PocketLink replacement. Open `/phone` or `/aetherphone` (or its plugin Open button), then Contacts/Messages and connect Discord explicitly. Authorize **your own** Discord account. Friends and avatars come from the official Social SDK. Recent text DM history is limited by the SDK; no fake message/read receipts are generated. Session tokens and messages stay in helper memory and are cleared on unlink/exit. Reauthorization may be needed after restart.

R3 uses distinct window identities for Discord notifications, message history and the message composer. The avatar status display counts ready, loading and failed avatars and provides a retry action. The new avatar status and retry text is included in all nine bundled locales, including Turkish.

The Aethernet social service is disabled in this edition. Ordinary personal Discord calls, general embedded browsing/video and the optional online Hunts feed are unavailable. This is not an official Aetherphone, Discord or Square Enix release.

## Camera — R6 1.8.0.8 installer fix

**Install Musical Guide (local camera R6) 1.8.0.8 as a separate plugin.** Its package identity is `MusicalGuideLocalCamera`; the preceding identity collided with the official catalog and was hidden by Dalamud. Disable the original Musical Guide and any development copy before installing/enabling R6. Both copies use `/mguide` and camera hooks. The existing `phone-camera-face.json` URL is unchanged.

The new identity starts with its own defaults; previous `MusicalGuide.json` settings are not imported or deleted. Reapply your preferred camera FOV/offsets. For a manual settings transfer, close the game and back up both configuration files first; copy `pluginConfigs/MusicalGuide.json` to `pluginConfigs/MusicalGuideLocalCamera.json` only before the new identity has created its own configuration. Do not reset plugin data.

Open `/mguide`. The title must contain **automatic near r6**; **stable idle r5** identifies the old build. The title still shows PE assembly version 1.8.0.0; the installer manifest is 1.8.0.8. This is an installer correction using the unchanged R6 DLL, not a new camera behavior revision.

Select Reduce motion, Follow animated yaw in reduced motion, and Reduce motion in combat. Animated yaw remains gated to real ability timelines, reducing idle horizontal sway. FOV and offsets are yours to set. Local mounts have a scoped drawing option.

R6 adds a saved, opt-in hand-clipping reduction preference. Open **First Person Settings → First Person Adjustments / Hand clipping**, enable **Automatically restore hand-clipping reduction**, and set **Local near distance** to **0.010**. The preference is saved and reapplied when a valid local first-person projection is observed. It starts disabled if an existing configuration has never enabled it. Test the distance on your own character; native game acceptance, including mount and idle behavior, remains pending.

## Face / webcam

Enable the matching Customize+ fork and open `/nearface`. **Start live session (webcam + receiver)** explicitly opens the bundled webcam and local receiver together. No separate Python setup or console launcher is needed. **Stop live session** or unloading NearFace stops its owned helper. A parent-stdin EOF also stops capture. Nothing opens the webcam merely by loading the plugin or opening its panel.

Components still start disabled: preview your actual face, then choose live eyelids/mouth/brows. Measured eyelid rotations remain opt-in for the correct sculpt. Tongue and native gaze retargeting are incomplete. Only local numeric coefficients are transmitted over loopback; webcam images are not recorded/uploaded.

If you explicitly launch START-WEBCAM.cmd manually, that independent console must be stopped there; the plugin only controls the helper it started itself. Missing helper/camera/device errors are shown in the panel.

## Source and validation limits

Current corresponding source: [phone R3 1.3.2.3](https://github.com/SmolShar/NearVoice-Downloads/releases/download/phone-camera-r3-r6-2026-10-19-preview/AethrAppLocalDiscord-1.3.2.3-source.zip), [camera R6 installer fix 1.8.0.8](https://github.com/SmolShar/NearVoice-Downloads/releases/download/camera-r6-installer-fix-2026-10-20/MusicalGuideLocalCamera-1.8.0.8-source.zip), [NearFace controls 0.2.4.0](https://github.com/SmolShar/NearVoice-Downloads/releases/download/phone-webcam-hotfix-2026-10-19/NearFaceControls-0.2.4.0-source.zip), and [Customize+ 2.2.1.6 in the existing preview source bundle](https://github.com/SmolShar/NearVoice-Downloads/releases/download/phone-camera-face-2026-10-19-preview/Face-Camera-Corresponding-Source.zip). The NearFace and Customize+ source archives are unchanged by this release. Webcam runtime/model source and original notices remain inside the existing NearFace payload. Original AGPL/Apache/MIT/BSD notices are retained. Obtain official Discord SDK headers/import libraries separately for rebuilding the unchanged native helper; its integrated DLL and notices remain unmodified.

R3/R6 package checks cover the supplied file hashes, release archive contents, dependency manifests and repository version consistency. Previous release builds, webcam smoke checks and standalone OAuth results are historical evidence, not newly rerun R3/R6 tests. Native game presentation, real DM send/receive, camera and mount behavior, and advanced expressions still require runtime acceptance. This update does not add advanced face channels or establish a complete avatar fix. No account configuration, OAuth token, credential, captured webcam image or user profile is included.

This separate index leaves the existing NearVoice `repo.json` and releases unchanged.

