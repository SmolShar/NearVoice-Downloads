# Third-party notices

NearVoice is an experimental modification of [Ricimon/FFXIV-ProximityVoiceChat](https://github.com/Ricimon/FFXIV-ProximityVoiceChat). The original MIT license and copyright are retained in `LICENSE`. This is not an official Square Enix or upstream ProximityVoiceChat release.

The original third-party license texts are retained without translation under `licenses/`. `licenses/package-license-index.json` lists the exact runtime NuGet package versions, authors, copyright, license declarations and project links obtained from their package metadata. Package-provided license texts and metadata are copied under `licenses/packages/`. Supplementary upstream license copies are under `licenses/upstream/`; their source URLs and Git blob hashes are recorded in `licenses/license-provenance.json`.

| Component | Version / source | License / notice location |
|---|---|---|
| ProximityVoiceChat source | Original Ricimon code with NearVoice modifications | `LICENSE` — MIT, copyright 2024 Ricimon |
| MixedReality-WebRTC managed wrapper and native library | Vendored wrapper and original `mrwebrtc.dll`, with the documented specialized correction | `licenses/upstream/MixedReality-WebRTC/LICENSE`, full `NOTICE` including embedded third-party components |
| Native WebRTC | Material incorporated by the native library / VAD | `licenses/upstream/WebRTC-Native/LICENSE` and MixedReality-WebRTC `NOTICE` |
| Concentus | 2.2.2, managed Opus | `licenses/packages/Concentus-2.2.2/LICENSE` — BSD-style Opus license and attribution; no Concentus.Native package included |
| NAudio and NAudio.Asio/Core/Midi/Wasapi/WinForms/WinMM | 2.2.1 | `licenses/packages/NAudio-2.2.1/license.txt` — MIT; related package metadata retained |
| Ninject and Ninject.Extensions.Factory | 3.3.6 / 3.3.3 | `licenses/upstream/Ninject/LICENSE.txt`, `Ninject-Extensions-Factory/LICENSE.txt` — dual Apache-2.0 / Ms-PL text |
| Castle.Core | 4.2.0 | Apache-2.0 text supplied by package under `licenses/packages/Castle.Core-4.2.0/`; copyright in package metadata |
| NLog | 6.0.7 | `licenses/upstream/NLog/LICENSE.txt` — BSD-3-Clause |
| AsyncAwaitBestPractices | 10.0.0 | `licenses/upstream/AsyncAwaitBestPractices/LICENSE.md` — MIT |
| ReactiveProperty and ReactiveProperty.Core | 9.8.0 | `licenses/upstream/ReactiveProperty/LICENSE.txt` — MIT |
| SocketIOClient, SocketIO.Core and serializer packages | 3.1.2 | `licenses/upstream/SocketIOClient/LICENSE` — MIT |
| System.Reactive | 6.1.0 | `licenses/upstream/System-Reactive/LICENSE` — MIT |
| Microsoft.Extensions.Logging.Abstractions / DependencyInjection.Abstractions | 10.0.0 | `licenses/upstream/DotNet-Runtime/LICENSE.TXT`, `THIRD-PARTY-NOTICES.TXT` — MIT and retained notices |
| WebRtcVadSharp | 1.3.2 | `licenses/upstream/WebRtcVadSharp/LICENSE` — MIT; native WebRTC notices also retained |
| WindowsInput | 6.4.1 | `licenses/packages/WindowsInput-6.4.1/LICENSE.txt` and `licenses/upstream/WindowsInput/LICENSE.txt` |
| YamlDotNet | 16.3.0 | `licenses/upstream/YamlDotNet/LICENSE.txt` — MIT |
| YellowDogMan.RRNoise.NET | 0.1.9 | `licenses/upstream/RNNoise-Net/LICENSE` — MIT |
| RNNoise native libraries | Native binaries provided by YellowDogMan.RRNoise.NET 0.1.9 | `licenses/upstream/RNNoise-Native/COPYING` — BSD-style RNNoise license; upstream notices retained |
| Microsoft.Windows.SDK.NET / WinRT.Runtime projection | Runtime pack Microsoft.Windows.SDK.NET.Ref 10.0.17763.57 | `licenses/upstream/Windows-SDK/Windows-SDK-license.html`, `source.json`, package metadata; Microsoft Windows SDK terms apply |

The bundled native `mrwebrtc.dll` is specialized to NearVoice's single `ordered=false, reliable=false` channel request. Its original SHA-256 is `67726CF278D6D15DD48839F9180F478624B6AF0473065CFDDE47D30D28D528F9`; the corrected copy is `EC76EC9533154DAD47AFEFCB3D8DA3B1E2612C9AF19EF78800693602EC3DFA00`. Exactly 12 bytes change; file length is 7,945,216 bytes. Source/guarded patch script, provenance, bounded disassembly and native local proof accompany the source archive. Changes do not remove the original license obligations and this correction is not a general-purpose native flags implementation.

The Windows/.NET SDK, Dalamud and original service credentials are not distributed in this package. The source archive may retain the original signaling-server reference source; it is not run or installed by the NearVoice runtime package. No claim is made that supplementary current upstream license copies describe the exact complete build composition of an otherwise precompiled vendored native library; its supplied full MixedReality-WebRTC `NOTICE` is retained for that purpose.

NearVoice's Turkish panel reads the existing Windows Segoe UI font through a plugin-owned managed font handle. The Segoe UI font file is not redistributed in either archive. The optional talking animation uses API types supplied by the user's Dalamud/FFXIVClientStructs SDK; those SDK binaries are not included.

## Separate phone and camera preview — phone R3 / camera R7

The optional packages in `phone-camera-face.json` have their own upstream sources and notices:

- **Aethr App (local Discord) R3 1.3.2.3** derives from [XeldarAlz/FFXIV-Aetherphone](https://github.com/XeldarAlz/FFXIV-Aetherphone). `AethrAppLocalDiscord-1.3.2.3.zip` retains the original AGPL-3.0-or-later `LICENSE.md`, `NOTICE`, `THIRD-PARTY-NOTICES.md`, trademark policy and component notices. Its modifications are identified in `LOCAL-EDITION.txt`. [Corresponding R3 source](https://github.com/SmolShar/NearVoice-Downloads/releases/download/phone-camera-r3-r6-2026-10-19-preview/AethrAppLocalDiscord-1.3.2.3-source.zip) is provided separately.
- **Musical Guide (local camera R7) 1.8.0.9** derives from [Sidiousious/musical-guide](https://github.com/Sidiousious/musical-guide). `MusicalGuideLocalCamera-1.8.0.9-preview.zip` retains `LICENSE.md`, `LICENSE-Brio-GPL3` and `LICENSE-FFXIVClientStructs.txt`. [Corresponding R7 source](https://github.com/SmolShar/NearVoice-Downloads/releases/download/camera-r7-near-fog-fix-2026-10-20/MusicalGuideLocalCamera-1.8.0.9-source.zip) includes the rebuilt application, tests, packaging instructions and modification notes. R7 corrects the projection-only near override using the live camera field and guarded baseline restoration. The separate installer identity and original PE assembly identity are retained. Original license bytes remain unchanged.

The phone archive's `DiscordBridge` directory retains `Discord-SDK-License-Notices.txt` alongside the unchanged native helper and Discord SDK library. Official Discord SDK headers and import libraries are obtained separately to rebuild that helper. The existing NearFace and Customize+ packages retain their previously published source and notices, linked in [the phone/camera/face instructions](PHONE-CAMERA-FACE.md).

