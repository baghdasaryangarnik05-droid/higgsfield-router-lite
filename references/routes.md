# Routes (lite): five Higgsfield jobs

Labels: [tested] ran by us · [vendor] Higgsfield docs/catalog · [community] creator notes · [untested]. Snapshot October 2026.

## R-01 Product spin
**Job.** The product turns on its own axis while the camera stays calm. Failure: the engine orbits the camera around a product that does not turn; the camera wins.
**Route.** `generate_video`, image-to-video, start frame = one clean product photo. Model `seedance_2_5`, mode `omni_reference`. Cheaper check: `draft: true` (480p), finalise only the take that works. [vendor]
**Prompt skeleton.** [tested, Sept 2026]
```
THE [OBJECT] - READ THIS AS A SEPARATE INSTRUCTION FROM THE CAMERA.
Camera movement must never be interpreted as object rotation.
Rotation belongs exclusively to the [object]; its centre of mass does not translate and does not orbit.
An object holding one fixed orientation = failed take.
```
**Why.** No separate channel for "object turns" vs "camera circles"; ambiguous wording collapses into camera language. Two caps blocks separate them; naming the failure gives a stop condition.
**If it breaks.** 1) Rewrite with the two blocks (cheapest). 2) Retry as 480p drafts. 3) After three fails, use a 3D route: camera and product become separate objects; a 2D warp cannot show the product's side.

## R-02 Animate a still
**Job.** A finished still should move; result is almost frozen.
**Route.** `generate_video`, start_image = the still. Identity: `seedance_2_5` mode `omni_reference`. Cinematic motion: `kling3_0`. Realism: `veo3_1`. [vendor]
**Prompt.** Only NEW motion: "hair gently lifts", "dust drifts through the light", "steam rises from the cup". Do not re-describe the frame. [community]
**If it breaks.** 1) Add motion words, drop description. 2) Seedance 2.5 with a start image needs mode `omni_reference` or the call fails (422). [tested] 3) Identity fine but motion dull: switch model.

## R-03 Start and end frames
**Job.** Two stills (start state, end state); the clip should travel between them without inventing a scene.
**Route.** `generate_video` with `start_image` + `end_image`. Models listing both roles in September: `kling3_0`, `seedance_2_0`/`seedance_2_5`, `veo3_1_lite`, `wan2_7`, `cinematic_studio_3_0`. Newer, check live: `kling4_0`, `kling_o3_flf`. [vendor]
**Settings.** Do NOT add `video_references` together with both frames: the reference video brings its own world (3 of 8 s became its street). [tested] Always set `aspect_ratio` (Cinema Studio defaults to 3:4). [tested] Seedance 2.5: mode `omni_reference`. [tested] Hailuo at 512: no `end_image`. [vendor] Fix light in the stills first. [community]
**Prompt skeleton.**
```
Start frame: [what is in frame, light, subject state]. End frame: [same fields].
Bridge: [the physical action that connects them, one verb chain].
[Element X] is absent at the start; it appears only when [cause] and is fully visible in the end frame.
```
**If it breaks.** Invented element: name where and when it appears [community]. Flat or drifting colour: regrade the stills, not the clip [community]. Untested: whether "finish in the exact framing" tightens the landing.
**Price examples (19 Sep 2026).** Seedance 2.5 4 s: 28 credits 720p, 48 at 1080p. Kling 3.0 pro 5 s, no sound: 7.5.

## R-04 Transitions
**Job.** Two clips should feel like one edit (match cut, whip pan, a hard cut that does not jar).
**Route.** One beat = one generation; clip B starts from the last frame of clip A (`start_image`); cut in the editor on the shared gesture, not on the timecode. Model: `kling3_0` pro was the cheapest we priced; `seedance_2_5` needs mode `omni_reference` for a start image. [tested]
**Settings.** `multi_shots` off (a cut inside one generation loses the identity anchor; our 8 s multi-shot test was rejected). Set `aspect_ratio`. Stop chains at 2 to 3 links, rebuild from the original still. [tested/community]
**Prompt skeleton (clip B).**
```
Opens on the final frame of the previous clip. State: [pose, hand position, who holds the prop].
Camera: [continues the slow push-in | starts static]. Action: [one beat only].
The [gesture] that ended the previous clip starts this clip.
```
**If it breaks.** Accidental-looking join: share one gesture or framing across the cut [community]. Subject-to-subject cut: hold about 1 s of empty frame [community]. Morph transitions: no morph primitive documented; do two shots, before and after [untested].
**Alternative.** The Transitions app (6 credits listed, [vendor], untested by us).

## R-05 Motion transfer
**Job.** A driving video has the movement (dance, walk, gesture, camera path); your character should perform it.
**Route.** `generate_video`, model `hf_mult_motion_control` (Genjutsu): one driving video (up to 30 s) + reference photos of the character and/or setting. Cheaper tier: `hf_mult_motion_control_flash` (Wan 3.0, up to 15 s; new since September, untested by us). Not for this job: legacy `motion_control`, `ad_multiplier`. [vendor]
**Settings.** Driver: one continuous shot, no editing cuts, subject fully in frame. Photo: close-up, even light, neutral face, head and body uncropped. No camera words: the driver owns the camera and a camera you add is summed with it (pan and shake rose several-fold in our measurement). [tested]
**Prompt skeleton.**
```
The reference video supplies only the camera path, timing, framing and pacing.
Every person, object and building comes from the supplied images: [image 1] is the performer, [image 2] is the setting.
The performer repeats the driving video's movement: [one line].
```
**If it breaks.** Empty error: simplify to one clean driver and one character photo (two 1:1 reconstruction attempts failed this way) [tested]. Face drifts: the photo carries identity, delete appearance words [community]. Background detaches: Kling 3.0 Motion Control (`kling3_0_motion_control`) has a background-source switch [vendor].
**Price.** Not measured.
