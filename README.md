# NearVoice downloads - experimental 0.2.0

NearVoice is a modified version of [Ricimon's ProximityVoiceChat](https://github.com/Ricimon/FFXIV-ProximityVoiceChat). Original copyright (c) 2024 Ricimon and the MIT license are retained. It is not an official upstream or Square Enix release. This repository contains only the public installer index, release binary and notices; the fork's development source is maintained separately.

## Install through Dalamud

In `/xlsettings` → **Experimental** → **Custom Plugin Repositories**, add this URL, press **+**, keep it enabled, and press **Save**:

```text
https://raw.githubusercontent.com/SmolShar/NearVoice-Downloads/main/repo.json
```

Open `/xlplugins`, refresh the list, search **NearVoice**, and select **Install**. This hosted URL needs no local JSON helper or GitHub login. Disable any older NearVoice development-plugin copy before enabling the installer copy. These JSON instructions are the current distribution method; the runtime ZIP's older bundled README describes the manual installation alternative.

## Existing service dependency

NearVoice 0.2.0 reads the local service configuration from an existing ProximityVoiceChat installation. Keep the original installed, but disable it while using NearVoice so both voice plugins do not run together. No account settings, service key, TURN password, or GitHub credential is included in this download.

The current client depends on the original service and its availability. This distribution does not provide a separate voice backend and does not claim upstream endorsement or an unlimited service entitlement. The code license and permission to use an independently operated service are separate matters.

Both peers need NearVoice 0.2.0 and the same world/map/instance. `/yakin` or `/nearvoice` opens the panel. Automatic proximity connects when the character and map are ready. The first migration starts the microphone muted; select the correct devices and enable it when ready. Optional voice-driven talking animation is experimental and disabled by default.

## Validation and licenses

63 focused checks and native two-way local transport/reconnection tests passed. Real two-computer Internet speech, physical microphone behavior, TURN fallback and in-game installation remain separate acceptance checks; public availability does not claim those tests passed.

The release ZIP is flat: NearVoice.dll and NearVoice.json are at its root (Dalamud API 15, assembly 0.2.0.0). SHA256 of latest.zip:

```text
AD3C2DBF5B710DCE3E63E9FE695210B51D3B6F29FD5E34829D924D480A2B1902
```

The original [LICENSE](LICENSE), [third-party notices](THIRD-PARTY-NOTICES.md), and full dependency licenses inside latest.zip are retained. The native WebRTC correction is documented in those notices.
