# Model picker: choose by constraint, not by taste

Snapshot October 2026 (live catalog checked 27 Oct: 57 video ids). Confirm an id with `models_explore` before naming it. Prices are dated quotes: use `get_cost`.

| You need | Use | Not |
|---|---|---|
| Start frame + end frame | `kling3_0`, `seedance_2_0` / `seedance_2_5`, `veo3_1_lite`, `wan2_7`, `cinematic_studio_3_0` (newer, check live: `kling4_0`, `kling_o3_flf`) | `minimax_hailuo` at 512 (no end image) |
| A video reference (copy motion, style) | `seedance_2_0` / `seedance_2_5`, `gemini_omni`, `minimax_h3`, `wan2_6`, `flux_3_video`, Genjutsu | any `cinematic_studio_*` (no video references) |
| Aspect 4:3 | check each model's limits | Kling and Veo (no 4:3) |
| Longer than 15 s | `seedance_2_5` (up to 30 s, extension), `wan3_0` (up to 30 s), `flux_3_video` (up to 20 s) | `veo3_1` (8 s ceiling) |
| Native sound in one pass | Seedance 2.x, Kling 3.0, Wan 2.7 / 3.0, `flux_3_video`, `gemini_omni` | Veo for dialogue-heavy shots (vendor says voice is still in development) |
| A product or face that must not change | `kling3_0` with Elements; `seedance_2_5` with `image_references` | `cinematic_studio_3_0` (does not inject Elements) |
| Cheap iteration | `kling3_0` pro, 5 s, sound off: 7.5 cr at the 19 Sep quote (8.75 cr for 5 s image-to-video on 28 Oct) | `seedance_2_5` 1080p (48 cr for 4 s at the 19 Sep quote) |
| Text inside the picture | `gpt_image_2` / `gpt_image_2_5`, `openai_hazel`, `seedream_v5_pro` | a general model |
| The same face across many generations | Soul ID (`soul_2`, `soul_cinematic`), then Element into the video model | describing the face in words |

Model ids gone from the live video list on 27 Oct (do not recommend without re-checking): `veo3` (use `veo3_1` / `veo3_1_lite`), `sora_2`, `sora_2_pro`, `seedance_3_0`, `kling3_0_omni`, `kling_o1`, `wan2_5`.
Always set `aspect_ratio`, `mode`, `resolution`, `duration` and `generate_audio` yourself: several models default them silently. `seedance_2_5` `draft:true` returns a 480p draft that can be finalised for up to 7 days: the cheaper path to a final. [vendor, live 26 Oct]
The full Router adds every model's limits, traps and prompt order.
