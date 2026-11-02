# Ten breaks, cheapest fix first

Match the symptom, give the fix, name the evidence label. Snapshot October 2026. Retry rule at the bottom.

1. **Product won't spin, the camera does.** Object rotation merged with camera language. Fix: two separate blocks (object, camera), "camera movement must never be interpreted as object rotation", name the failure. See R-01. [tested]
2. **Image-to-video barely moves.** The prompt re-describes the still. Fix: write only NEW motion ("fingertip slides along the ice, cold mist drifts"); on Seedance 2.5 with a start image set mode `omni_reference`. See R-02. [tested 28 Oct: motion-only wording moved a still that a re-describing prompt left near-frozen; n=1]
3. **422 with no reason.** Not a prompt problem. Seedance 2.5 with a start image needs mode `omni_reference`; a video reference shorter than about 2 s also fails, and `get_cost` does not warn. Fix: check the mode and the media, not the wording. [tested]
4. **The aspect is wrong.** Cinema Studio 3.0 and video_v2 silently default to 3:4; Kling image-to-video may follow the still's shape. Fix: always set `aspect_ratio`, and read the `adjustments` block of `get_cost` before paying. [tested]
5. **The shot froze after a "no camera movement" list.** A ban list reads as an order to stand still. Fix: one wanted camera move in the positive, nothing else. [tested]
6. **The face changes between shots.** No identity anchor, or appearance text competing with the reference image. Fix: one reference carries identity, delete appearance words, anchor every shot on the ORIGINAL reference, cap an extension chain at 2-3 links. [community]
7. **A product or face from an Element came out invented.** `cinematic_studio_3_0` does not inject Elements even with the tag in the prompt. Fix: route that shot to `kling3_0` (Elements work) or `seedance_2_5` with `image_references`. [tested 19 Sep]
8. **A cut inside one generation broke the character.** An internal hard cut discards the identity anchor. Fix: one beat, one generation, join in the editor. [tested]
9. **Lip-sync drifts off the words.** Handheld or low-shutter looks on speaking shots confuse the sync solver. Fix: steady camera, paste the exact line, for existing footage use a video-to-video lip-sync model (`sync_so`). [community/vendor]
10. **Upscale price was a surprise.** The video upscaler has no cost preview. Fix: judge at low resolution, upscale only the accepted take, run the first upscale on a short clip. [tested]

Retry rule: change one variable per try. Three paid failures on one shot: stop and decide (accept, resize, defer, placeholder); do not go for a fourth.
