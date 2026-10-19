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

Enable the matching Customize+ fork. Open `/nearface`, start reception and explicitly enable the wanted components. Then run:

```text
%APPDATA%\XIVLauncher\installedPlugins\NearFaceDiagnostics\0.2.3.0\NearFaceWebcam\START-WEBCAM.cmd
```

The webcam starts only when you launch that helper. Stop it with Ctrl+C or close its console; `/nearface stop` stops game reception only. The helper uses bundled Python/models, CPU inference and numeric coefficients over loopback. It does not record/upload webcam images. `SELF-TEST.cmd` does blank-image inference without opening a camera.

Mouth/brows/smile/sideways mouth are approximate. Measured eyelid rotations default off: do not blindly apply someone else's sculpt calibration. Tongue and native eye-gaze retargeting are incomplete.

## Source and validation limits

Corresponding source is attached to this release in **AethrAppLocalDiscord-1.3.2.1-source.zip** and **Face-Camera-Corresponding-Source.zip**. Webcam helper/model source and notices are inside its payload. Original AGPL/Apache/MIT/BSD and dependency notices are retained. Official Discord SDK headers/import libraries must be obtained separately from Discord for rebuilding its helper; the bundled DLL is unmodified and integrated into that helper.

Offline tests/builds, portable blank inference, wire smoke, archive hashes and anonymous downloads were checked. A prior standalone human OAuth test returned 89 real friends. This does **not** establish native game presentation, real DM send/receive, advanced expressions or mounts. Those still require runtime acceptance. No account configuration, OAuth token, credential, captured webcam image or user profile is included.

This separate index leaves the existing NearVoice `repo.json` and releases unchanged.
