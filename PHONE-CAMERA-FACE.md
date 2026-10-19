# Phone, camera and local face preview

Add this **single URL** in Dalamud `/xlsettings` > Experimental > Custom Plugin Repositories, enable and Save:

```text
https://raw.githubusercontent.com/SmolShar/NearVoice-Downloads/main/phone-camera-face.json
```

Refresh `/xlplugins`. Install **Aethr App (local Discord)**, **Musical Guide (local camera R5)**, **Customize+ (local NearFace fork)** and **NearFace Local Controls (prototype)**. The last two work together. No system Python installation is needed.

Before enabling this local phone, disable the official Aetherphone, old PocketLink and LocalPhone. Back up existing plugin configurations; retain your Customize+ profiles. The local phone has its own configuration namespace and does not import the original Aethernet account.

## Phone

This is a modified copy of the original Aetherphone shell and apps, not a PocketLink replacement. Open `/phone` or `/aetherphone` (or its plugin Open button), then Contacts/Messages and connect Discord explicitly. Authorize **your own** Discord account. Friends and avatars come from the official Social SDK. Recent text DM history is limited by the SDK; no fake message/read receipts are generated. Session tokens and messages stay in helper memory and are cleared on unlink/exit. Reauthorization may be needed after restart.

The Aethernet social service is disabled in this edition. Ordinary personal Discord calls, general embedded browsing/video and the optional online Hunts feed are unavailable. This is not an official Aetherphone, Discord or Square Enix release.

## Camera

Open `/mguide`. Select Reduce motion, Follow animated yaw in reduced motion, and Reduce motion in combat. R5 gates animated yaw to real ability timelines, reducing idle horizontal sway. FOV and offsets are yours to set. Local mounts have a scoped drawing option.

The verified local near override is session-only, under Camera diagnostics. The original user visually accepted 0.010 for the clipping issue; test it on your own character. R5 mount/idle behavior still needs game acceptance.

## Face / webcam

Enable the matching Customize+ fork and open `/nearface`. **Start live session (webcam + receiver)** explicitly opens the bundled webcam and local receiver together. No separate Python setup or console launcher is needed. **Stop live session** or unloading NearFace stops its owned helper. A parent-stdin EOF also stops capture. Nothing opens the webcam merely by loading the plugin or opening its panel.

Components still start disabled: preview your actual face, then choose live eyelids/mouth/brows. Measured eyelid rotations remain opt-in for the correct sculpt. Tongue and native gaze retargeting are incomplete. Only local numeric coefficients are transmitted over loopback; webcam images are not recorded/uploaded.

If you explicitly launch START-WEBCAM.cmd manually, that independent console must be stopped there; the plugin only controls the helper it started itself. Missing helper/camera/device errors are shown in the panel.

## Source and validation limits

Current corresponding source: [phone 1.3.2.2](https://github.com/SmolShar/NearVoice-Downloads/releases/download/phone-webcam-hotfix-2026-10-19/AethrAppLocalDiscord-1.3.2.2-source.zip), [NearFace controls 0.2.4.0](https://github.com/SmolShar/NearVoice-Downloads/releases/download/phone-webcam-hotfix-2026-10-19/NearFaceControls-0.2.4.0-source.zip). [Camera and Customize+ source](https://github.com/SmolShar/NearVoice-Downloads/releases/download/phone-camera-face-2026-10-19-preview/Face-Camera-Corresponding-Source.zip) is unchanged. Webcam runtime/model source and original notices are inside its payload. Original AGPL/Apache/MIT/BSD notices are retained. Obtain official Discord SDK headers/import libraries separately for rebuilding the unchanged native helper; its integrated DLL and notices remain unmodified.

Offline tests/builds, portable blank inference, wire smoke, archive hashes and anonymous downloads were checked. A prior standalone human OAuth test returned 89 real friends. This does **not** establish native game presentation, real DM send/receive, advanced expressions or mounts. Those still require runtime acceptance. No account configuration, OAuth token, credential, captured webcam image or user profile is included.

This separate index leaves the existing NearVoice `repo.json` and releases unchanged.
