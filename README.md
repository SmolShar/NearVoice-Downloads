# NearVoice, phone, camera and face — one installer index

This single canonical Dalamud repository URL lists all six local plugins:

```text
https://raw.githubusercontent.com/SmolShar/NearVoice-Downloads/main/repo.json
```

| Plugin | Installer identity | Current version |
|---|---|---|
| NearVoice proximity voice | `NearVoice` | 0.2.1.0 |
| Aethr App — local Discord phone | `AethrAppLocalDiscord` | 1.3.2.3 |
| Musical Guide — local camera R8 | `MusicalGuideLocalCamera` | 1.8.0.10 |
| Customize+ — local NearFace fork | `CustomizePlus` | 2.2.1.6 |
| NearFace — local webcam/face/head input | `NearFaceDiagnostics` | 0.2.5.0 |
| It's Up Combo — Samurai and Sage HUD | `ItsUpCombo` | 0.1.0.0 |

## Install and update

In `/xlsettings` → **Experimental** → **Custom Plugin Repositories**, add the URL
above, press **+**, keep it enabled and **Save**. Refresh `/xlplugins`. Select the
plugins you need. Updating the camera hooks requires a full FFXIV restart.
This consolidation changes the index, not the plugin binaries or saved settings.

For an existing installation, keep its previous `phone-camera-face.json` entry
enabled until the installed plugins' source has been migrated to `repo.json`.
Dalamud 15.0.3.8 matches third-party updates to the installed source URL as well
as the plugin identity. The legacy URL mirrors the canonical index; future changes must keep the same
manifest entries, versions and download links at both addresses.
New installations need only `repo.json`. Do not reset configurations or remove
unrelated custom repositories to consolidate these five plugins.

Customize+ retains its existing `CustomizePlus` identity. An official catalog
entry can hide the local entry; adding it to one JSON does not resolve that
identity collision. Retain the installed matching local fork and its profiles.
NearVoice still needs the original ProximityVoiceChat local service settings;
keep that installation/configuration and disable its running plugin when using
NearVoice. NearFace facial animation needs the matching C+ fork, while camera
head input can run without enabling facial components.

Detailed camera, webcam and phone controls, source downloads and validation:
[PHONE-CAMERA-FACE.md](PHONE-CAMERA-FACE.md).

Current camera/webcam release:
[R8 1.8.0.10 + NearFace 0.2.5.0](https://github.com/SmolShar/NearVoice-Downloads/releases/tag/camera-face-r8-tracking-2026-10-20).

The source-URL update rule is documented by the version-pinned
[Dalamud PluginManager](https://github.com/goatcorp/Dalamud/blob/15.0.3.8/Dalamud/Plugin/Internal/PluginManager.cs).

## It's Up Combo — Samurai and Sage

Install **It's Up Combo 0.1.2.0** from the same `/xlplugins` repository. `/itsupcombo`
opens settings; `/itsupcombo move` arranges three independently movable/resizable
panels: core actions, resource/proc availability, and cooldown reminders.
`/itsupcombo lock` finishes editing. Key hints sit below their icons.

During play there are no background cards or section headings; only action icons,
below-icon key hints and optional action names remain. Thin positioning guides
appear only while editing. Interrupted combo animations continue from the current
visible position and opacity; repeated/press-only state does not restart a delayed fade.

Only actions placed on the current input mode's hotbars are shown: keyboard uses
normal bars, controller uses crossbars. Unused controller defaults cannot enter
the keyboard HUD. Hidden and unbound mounted slots remain supported. Learned
actions already ready at login or outside combat can be
shown immediately. Samurai's Kenki/Sen/Meditation and native proc actions, plus
Sage's Addersgall/Addersting actions, appear only when their resource requirements
and own cooldowns pass. Shared GCDs do not make the resource panel flicker.
Sage core spells use native trait/Eukrasia replacements. The overlay stays visible
when the game HUD is hidden and never invokes actions or changes hotbars.

[Download 0.1.2.0 and corresponding source](https://github.com/SmolShar/NearVoice-Downloads/releases/tag/its-up-combo-0.1.2-2026-10-24).
Final release evidence records 114 production-linked model/resource/cooldown
scenarios and 31 native ImGui harness scenarios. Live FFXIV rendering,
combat timing and physical game input remain unverified.

## NearVoice details — experimental 0.2.1

NearVoice is a modified version of [Ricimon's ProximityVoiceChat](https://github.com/Ricimon/FFXIV-ProximityVoiceChat). Original copyright (c) 2024 Ricimon and the MIT license are retained. It is not an official upstream or Square Enix release. This repository contains only the public installer index, release binary and notices; the fork's development source is maintained separately.

### Existing service dependency

NearVoice 0.2.0 reads the local service configuration from an existing ProximityVoiceChat installation. Keep the original installed, but disable it while using NearVoice so both voice plugins do not run together. No account settings, service key, TURN password, or GitHub credential is included in this download.

The current client depends on the original service and its availability. This distribution does not provide a separate voice backend and does not claim upstream endorsement or an unlimited service entitlement. The code license and permission to use an independently operated service are separate matters.

Both peers need NearVoice 0.2.1 and the same world/map/instance. `/yakin` or `/nearvoice` opens the panel. Automatic proximity connects when the character and map are ready. The first migration starts the microphone muted; select the correct devices and enable it when ready. Optional voice-driven talking animation is experimental and disabled by default.

## Validation and licenses

63 focused checks and native two-way local transport/reconnection tests passed. Real two-computer Internet speech, physical microphone behavior, TURN fallback and in-game installation remain separate acceptance checks; public availability does not claim those tests passed.

The release ZIP is flat: NearVoice.dll and NearVoice.json are at its root (Dalamud API 15, assembly 0.2.1.0). SHA256 of latest.zip:

```text
373FE9F1581A60D49AE2A1C225D6DB4D9A6C02517D31D9FA42E9579A3BE68F0E
```

The original [LICENSE](LICENSE), [third-party notices](THIRD-PARTY-NOTICES.md), and full dependency licenses inside latest.zip are retained. The native WebRTC correction is documented in those notices.

## 0.2.1 hotfix

Fixes native WebRTC/VAD loading when Dalamud loads the managed plugin from memory (Assembly.Location is empty). The old path failure could remove a discovered peer and leave only yourself in the list. PluginInterface.AssemblyLocation supplies the real plugin directory. Seven focused regression checks pass with the exact initializer, real native calls, missing-file checks, immutable paths and original-native preload isolation. The earlier 63 checks are prior evidence; two-computer in-game voice needs a fresh test after updating.

