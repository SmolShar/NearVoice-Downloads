# Unified local plugin installation — phone, camera and face

Use the unified canonical URL in Dalamud `/xlsettings` → Experimental → Custom Plugin Repositories:

```text
https://raw.githubusercontent.com/SmolShar/NearVoice-Downloads/main/repo.json
```

The index now contains **NearVoice 0.2.1.0**, **AethrAppLocalDiscord 1.3.2.3**,
**MusicalGuideLocalCamera 1.8.0.10**, **CustomizePlus 2.2.1.6** and
**NearFaceDiagnostics 0.2.5.0**. Plugin binaries and saved settings are unchanged
by this index consolidation.

**Existing installations:** keep the old `phone-camera-face.json` repository
enabled until source migration is complete. It is an identical compatibility
mirror because Dalamud associates installed third-party updates with their
original repository URL. New installations need only `repo.json`. See
[the main installation instructions](README.md).

Refresh `/xlplugins`. Update **Musical Guide (local camera R8) to 1.8.0.10** and
**NearFace Local Controls (prototype) to 0.2.5.0**, then **fully exit and restart
FFXIV**. The installer identities and saved settings remain in place. Do not
reset plugin data or repeat the earlier Musical Guide settings migration.

The matching **Customize+ (local NearFace fork) 2.2.1.6** remains the facial
animation dependency. Head input can run without enabling facial components.
The C+ package shares the upstream `CustomizePlus` identity and may be hidden
by the official catalog; retain the existing matching local installation and
profiles. No separate system Python installation is needed.

Keep other Musical Guide copies disabled because they share hooks and `/mguide`.
Before enabling the local phone, disable official Aetherphone, old PocketLink
and LocalPhone. The local phone has its own configuration namespace and does
not import the original Aethernet account.

## Phone — R3 1.3.2.3

This is a modified copy of the original Aetherphone shell and apps, not a PocketLink replacement. Open `/phone` or `/aetherphone` (or its plugin Open button), then Contacts/Messages and connect Discord explicitly. Authorize **your own** Discord account. Friends and avatars come from the official Social SDK. Recent text DM history is limited by the SDK; no fake message/read receipts are generated. Session tokens and messages stay in helper memory and are cleared on unlink/exit. Reauthorization may be needed after restart.

R3 uses distinct window identities for Discord notifications, message history and the message composer. The avatar status display counts ready, loading and failed avatars and provides a retry action. The new avatar status and retry text is included in all nine bundled locales, including Turkish.

The Aethernet social service is disabled in this edition. Ordinary personal Discord calls, general embedded browsing/video and the optional online Hunts feed are unavailable. This is not an official Aetherphone, Discord or Square Enix release.


## Camera R8 and NearFace 0.2.5

This local preview adds a stable first-person view, per-mount seat offsets, and
physical head input. It is a modified Musical Guide fork, not an official
upstream or Square Enix release. The existing installer identity and camera
configuration are retained.

## Quick setup

1. Update **Musical Guide (local camera R8) 1.8.0.10** and **NearFace Local
   Controls 0.2.5.0** through the unified `repo.json` repository (the previous URL remains a compatibility mirror).
   Fully exit and restart FFXIV after updating the camera hooks.
2. Open `/mguide`. The title must contain **mount + head tracking r8**. The
   internal assembly version stays 1.8.0.0 for configuration compatibility;
   the installer/file version is 1.8.0.10.
3. Under First Person Settings, the R8 sections appear before the older camera
   controls. **Steady view is enabled by default.** It anchors the eye to the
   gameplay character frame and ignores animated head/root displacement and
   animated yaw. It preserves configured FoV and eye offsets. Real character
   movement, teleports and gameplay-facing changes remain real movement.
4. **Mount camera starts disabled.** Mount up, enter first person, enable
   **Binege ozel kamera konumunu kullan**, then set forward/up/side offsets.
   Each mount ID has its own saved profile. This calibrates the game's native
   first-person seat; it does not contain hand-authored presets for every mount.
   **Koltuk hizasini yeniden al** or `/mguide mount-center` recalibrates it.
5. **Head tracking starts disabled.** Turn off **MouseLock**, choose **NearFace
   (tek webcam)**, and press **Webcam ve kafa takibini baslat**. Look straight
   at the screen and hold still briefly. One webcam feeds the face and camera
   paths independently. Facial components can remain disabled while head
   tracking runs. No webcam opens merely because a plugin loads or a panel opens.
6. Use **Bakisi ortala**, `/mguide center`, or **Ctrl+Alt+C** to establish a new
   neutral view. Advanced controls set sensitivity, dead zone, smoothing,
   maximum angles and axis inversion. If the device's direction is reversed,
   change the corresponding inversion. **Webcam ve takibi durdur** stops both
   tracking and the helper started by NearFace.

## Behavior and limits

- Stable on-foot view stops following animation-driven head motion. This is
  separate from suppressing the game's actual actor movement or auto-facing;
  those are not suppressed. The first valid eye calibration waits for an active
  ability to finish rather than storing a displaced buff pose as the baseline.
- Head input is additive to mouse look, with bounded angles, wrap-aware filtering,
  outlier rejection, a dead zone and time-based smoothing. There is no camera
  roll or physical translation in this release. Steady view is required while
  tracking is enabled. Absolute vertical look is capped at 85 degrees in that
  mode to avoid pole inversion; saved legacy limits remain stored.
- Neutral calibration requires at least eight unique valid frames spanning
  400 ms. Repeated IPC polls do not count as new frames. Source/session changes,
  ownership changes and longer tracking loss require a new stable center.
  Lost or stale input returns toward neutral instead of freezing indefinitely.
- The built-in NearFace path reports fit quality and explicit loss. A numeric
  score is not biometric identity confidence. Large geometry changes, low
  confidence, cropped faces and detected multiple faces can pause input. The
  detector has a two-face budget, not a guarantee of detecting every background
  face. Facial expressions and head pose use different filters.
- Right mouse steering, **MouseLock**, flying and diving suspend physical head
  input. Look is recalibrated when supported control resumes. Seat offsets can
  still work while flying or diving. Pillion riders and unsupported camera
  ownership/control transitions keep native positioning.
- While tracking is enabled, the game's first-person camera auto-adjustment is
  temporarily set to Never. The captured previous option is restored when
  disabled only if the user or another controller has not replaced it. A later
  external change pauses tracking rather than being repeatedly overwritten.
- GPose, cutscenes, zoning, event cameras and detected Brio/Ktisis camera owners
  do not receive the new gameplay tracking. Existing GPose behavior remains
  outside the new tracking path. Mount position smoothing affects local seat
  offsets only; actual world motion and teleports are not delayed.
- `/mguide tracking off` turns camera input off. Use `/nearface stop` as well
  to close the webcam, or use the combined stop button. A separately launched
  manual webcam console remains under its own owner's control.

## Optional OpenTrack input

NearFace is the integrated default. As an alternative, select OpenTrack and set
its output to **UDP over network**, destination **127.0.0.1:4242** (or the same
configured port). The receiver accepts the 48-byte six-double little-endian
protocol. Translation is validated but ignored; yaw and pitch drive this view.
Only one source runs at once. Do not run two independent captures against a
webcam that cannot be shared.

The OpenTrack UDP protocol carries no tracking-validity or fit-quality field.
It cannot distinguish a stream repeatedly transmitting a frozen pose from a
person holding still. It is therefore not given fabricated face-loss confidence.
Source reference: [OpenTrack UDP implementation at
99815e8](https://github.com/opentrack/opentrack/blob/99815e8ae7aaaa84a2e956b12365a6441db34688/proto-udp/ftnoir_protocol_ftn.cpp).

## Existing settings and hand-clipping reduction

No configuration reset or original-to-local migration is performed. Existing
`MusicalGuideLocalCamera` FoV, offsets, head coordination and hand-clipping
preferences remain. R7's guarded native near-distance correction is retained;
the new mount camera does not enable that correction for mounts. Keep other
Musical Guide copies disabled because they share hooks and commands.

The matching Customize+ 2.2.1.6 package and its saved profiles remain unchanged.
Its local facial channels still require sculpt-specific visual calibration and
explicit component enablement. This update is not complete tongue/gaze or
52-blendshape retargeting and does not synchronize expressions to other players.

## Verification

Both plugins were built using .NET SDK 10.0.402 and official Dalamud 15.0.3.8
references. The following linked-source checks passed:

| Area | Result | Scope |
|---|---:|---|
| Camera integration math | 953 assertions | Gameplay eye anchor, angle composition, overlay cleanup |
| Existing camera math/pose | 67 tests | Regression checks, head mask and yaw policies |
| Projection/near ownership | 35 tests | R7 fog/depth correction and cleanup policy |
| Mount seat | 45 tests | Math/state and matching-SDK allocated native-layout fixtures |
| Head input | 46 tests | State/filter math and real local UDP transport |
| Presentation ownership | 20 tests | FoV/pitch/roll restoration and foreign replacements |
| NearFace Python | 29 tests | Numeric pose/filters and owned helper quit/EOF |
| NearFace controller | 49 checks | Production-linked protocol/IPC, real UDP and owned fixture process |

The camera build reported one NU1900 warning because the NuGet vulnerability
service was unavailable; this is not a completed vulnerability audit. Both
compilations had zero errors. NearFace's controller build had zero warnings.
The original portable Windows inference runtime and model are retained from the
verified 0.2.4 package; old inference smoke tests are historical evidence.

**Physical webcam signs/neutral pose, lighting/glasses, live FFXIV input/render
ordering, actual mount placement and facial appearance still need user-side
acceptance.** No live game or physical webcam was available in this build
environment. A 250 ms freshness timeout measures input arrival age, not total
capture-to-screen latency. If a rare receiver socket error occurs, the status
requests a NearFace Stop/Start.

First check while standing still: head right/up, center, face out of frame,
face back in frame, mouse takeover, one rotating/buff ability, then mount and
dismount. Use small offsets first. The in-panel status explains when tracking
is waiting or paused.

## Corresponding source and packages

- [Camera R8 complete source](https://github.com/SmolShar/NearVoice-Downloads/releases/download/camera-face-r8-tracking-2026-10-20/MusicalGuideLocalCamera-1.8.0.10-source.zip) — application, tests,
  manifest, packaging script, build instructions and original notices.
- [NearFace 0.2.5 complete controls/helper source](https://github.com/SmolShar/NearVoice-Downloads/releases/download/camera-face-r8-tracking-2026-10-20/NearFaceControls-0.2.5.0-source.zip) —
  controller, both Python modules, tests, build notes and verification.
- [NearFace 0.2.5 Windows runtime](https://github.com/SmolShar/NearVoice-Downloads/releases/download/camera-face-r8-tracking-2026-10-20/NearFaceDiagnostics-0.2.5.0.zip) retains the original
  portable runtime, model, OpenSeeFace vendor source and component licenses.
- [Unchanged phone R3 source](https://github.com/SmolShar/NearVoice-Downloads/releases/download/phone-camera-r3-r6-2026-10-19-preview/AethrAppLocalDiscord-1.3.2.3-source.zip).
- [Unchanged Customize+ source bundle](https://github.com/SmolShar/NearVoice-Downloads/releases/download/phone-camera-face-2026-10-19-preview/Face-Camera-Corresponding-Source.zip).

Original AGPL/Apache/MIT/BSD notices remain in their packages. No account
configuration, OAuth credential, live capture or user profile is included.
The unified `repo.json` contains all five plugins. NearVoice 0.2.1.0 and the other plugin binaries remain unchanged; `phone-camera-face.json` mirrors the same entries for existing installs.
