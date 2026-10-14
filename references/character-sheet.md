# Character sheets, building one Seedance will not break

A character lives or dies by its character sheet, the reference image Seedance reads to know who it is. **Seedance reads it literally**, so every flaw in the sheet becomes a flaw in every shot.

## The character pipeline (always in this order)
1. **Prompt** in the Prompt Box, a description Claude writes (moodboard and description first, then a single production prompt that packs all angles into one generation).
2. **Generate** one sheet with a full front, a full back, and a dominant close-up portrait.
3. **Inspect** before anything downstream touches it (a stray rim light, a face that does not match, or plastic skin here bleeds into every shot).
4. **Masked edit over the original.** Fix flaws with Photoshop masks composited onto the original sheet. **Never regenerate the whole sheet**, or drift and dirt accumulate.
5. **Test in Seedance** on a good location. The test is the goal, not the generation.

## Which model
- **Soul Cinema**, first choice for generating characters.
- **Seedream 4.5**, also works, run it in parallel.
- **AI Cast (Cinema Studio)**, a strong casting tool.
- **Nano Banana Pro**, only to **edit** a finished sheet, never to generate.
- **GPT Image 2**, creatures and precise add-ons. On human skin it oversharpens and turns to slop, so keep it to a small patch.

## The rules that make a sheet Seedance-proof
- **Deep neutral grey background** (#3a3a3c). White bleeds and washes out the location, black eats detail. Grey is the golden midpoint.
- **Dominant portrait (25 to 30% of the frame).** Without an authoritative face panel, Seedance lacks facial evidence and invents a different one every shot.
- **Angle the portrait.** Slightly off-frontal reads head volume instantly, or add a separate smaller 3/4 portrait.
- **Eyes never black.** The iris color must read. Crushed-black eyes give no light information, so tones drift between generations.
- **Catchlight or dead eyes.** Always a glint in the eye, as in a real shoot.
- **Break the symmetry.** Real faces are symmetric but never perfect. A perfect mirror reads as AI.
- **No 3D-game-render look.** Seedance recognizes the mood of a game model and animates the character like game footage.
- **Crop the head on full-body panels.** In full body the face always distorts and drifts from the portrait. Crop it and Seedance is forced to take the face from the portrait panel, where the pixels and the precision are.
- **Identical identity in every panel.** Same face, same light, same grading. Two identities on the sheet means drift in the video.

## Production template (works on any model)
Two things never change, the deep neutral grey background and the column split with one dominant portrait (add columns if the character needs them). The CHARACTER block is rewritten with Claude for your character. The prompt is in English.

```
Character reference sheet of a single consistent [female] character, presented
on a pure clean deep neutral grey (#3a3a3c) seamless studio background, clean
editorial layout arranged in three vertical sections, horizontal landscape
composition read left to right, identical character identity, lighting and color
grading across every panel for perfect consistency:
, COLUMN 1 (largest, leftmost): chest-up portrait, front view, head and upper
chest in frame, sharp focus on the eyes, soft catchlights in both eyes.
, COLUMN 2: full-body front view, standing relaxed neutral A-pose, arms slightly
away from the body, weight evenly distributed, full figure head-to-toe inside
the frame with even margins.
, COLUMN 3 (rightmost): full-body back view, same standing pose mirrored,
showing hair fall, back posture, garment fit and shoe heels.
CHARACTER (must remain identical in all panels): [woman, mid-20s, height ~175cm,
elegant proportions, oval face, sharp high cheekbones, defined but soft jawline,
straight nose, full natural lips, light scattered freckles across the nose and
cheeks, clear fair skin with realistic natural texture and subtle imperfections,
grey-green eyes with detailed iris, well-groomed natural brows, straight auburn
hair with a center part falling just past the shoulders with a soft natural
sheen, neutral calm relaxed expression].
LIGHTING & RENDER: clean soft even studio lighting, large diffused key light
with gentle fill, soft natural shadows, no harsh highlights, true-to-life skin
tones, neutral white balance, minimal high-fashion editorial presentation,
polished modern professional model sheet aesthetic, shot on full-frame camera
with an 85mm lens look, shallow yet controlled depth of field, crisp tack-sharp
detail, high dynamic range, 8k.
```
> Note: on the full-body panels, crop the head after generating (Photoshop) to force Seedance to read the face from the portrait.

## What a SLOP sheet looks like (reject)
- **Dirty sheet.** Mottled, dirty plate (from regenerating the whole sheet over and over) plus a full-body face that does not match the portrait, so two identities.
- **Game render.** Plastic game-model textures, baked-in orange rim light, and a portrait that is too small (far from 25 to 30%).
- **Nano Banana slop.** Mirror-symmetric face, soapy or waxy skin, and six nearly identical tiles with no dominant portrait.

In all cases, **mask repairs over the original and audit again.**

## Editing characters is surgery
Every Seedream, GPT Image 2 or Nano Banana Pro change goes onto the original sheet with a mask. Change only the region that changed and leave the original intact everywhere else. The clean file stays as the master, and nothing regenerates on top of it.
