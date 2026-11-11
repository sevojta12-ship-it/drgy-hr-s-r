# Truly Dark x Complementary Reimagined compat (Forge 1.20.1, client-side)

Truly Dark darkens Minecraft's vanilla light texture. Complementary Reimagined ignores that texture and does
its own lighting, so Truly Dark normally does nothing while shaders are on.
This mod bridges the gap: it reads Truly Dark's live settings and writes the matching Complementary options.

## What it does (when a pack named like "Complementary...Reimagined" is active in Oculus)
| Truly Dark setting | Complementary Reimagined option |
|---|---|
| Dark Overworld on | enables the compat (otherwise the shader is left alone) |
| starlight + moonlight (8 phases) | Moon Phased Night Lighting + Atmosphere ON; Full / Partial / Dark moon intensity |
| dark caves | Cave Lighting Multiplier = 0 (config `cave_lighting`) |

Night level per phase = starlight + moonlight(phase), scaled so Truly Dark's default full moon = shader default 1.00.
Full moon -> phase 0, Dark moon -> phase 4, Partial -> average of the other six phases.
Truly Dark preset "Truly Dark" (all zero) => lowest value the shader allows (0.01 = near pitch black).
When you change Truly Dark settings in-game the shaders reload automatically within ~2 s.
If Truly Dark gets turned off, your original shader values are restored (saved in config/tdcrcompat-backup.properties).

## Install
Forge 1.20.1 + Oculus 1.8.0 + Embeddium + Truly Dark (2.0.0) + this jar, Complementary Reimagined in `shaderpacks`.
Config: `config/tdcrcompat.properties` (night_scale, cave_lighting, apply_night, apply_caves, pack_match, poll_seconds).

## Known limits
* Complementary's options are global, not per dimension: Cave Lighting 0 also applies in the Nether.
* Complementary has only 3 moon-phase buckets, Truly Dark has 8 phases, so in-between phases are interpolated.
* "Affect block light only" in Truly Dark is not mapped.
* Verified against Complementary Reimagined r5.9.3 option names and Oculus 1.8.0 / Truly Dark 2.0.0 class layout. Not run in-game yet.

## Build
Upload to GitHub; the Actions tab builds the jar (artifact `tdcrcompat-jar`).
