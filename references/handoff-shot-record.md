# Handoff, from project files to a shot record

Do not ask for "make the prompt" in isolation. Give Claude the production record first, and have it return **one** structured record per shot.

## The three file types in the workflow
- **`.md`**, plain text (Markdown). Notes, instructions and skills.
- **Skill (`SKILL.md`)**, a folder of `.md` instructions with the rules for one topic. Claude opens it when the task fits and works to that standard. Not every `.md` is a skill, sometimes it is just a system prompt.
- **`.jsx`**, technically code, but we use it as a **shotlist**, a structured container of shot data (number, description, timing, prompts) that Claude reads fields from.

## What to give Claude (explicit authority)
| Input | Provides |
|---|---|
| Scene brief `.md` | Story beat and intent of the shot |
| Approved references plus exact `@` Element names | Character, location and prop identity |
| Relevant `SKILL.md` | Rules for this type of prompt |
| Current `.jsx` shotlist | Shot number, timing and continuity |

Memory helps recall the project, but it **does not pick the latest brief for you**. Tell Claude which files are authoritative.

## The request (replace what is in brackets)
```
Use the scene brief, approved reference images, relevant SKILL.md, and current
.jsx shotlist in this project.
Prepare shot [number] only. Preserve the story beat, continuity, and approved
Element names. If a missing decision would change the shot, ask before writing.
Do not invent an Element.
Return one record with exactly this structure and no preamble:
{
shot: "[number]",
description: "[one-sentence action and framing]",
duration: "[seconds]",
elements: ["[@name]", "[@name]"],
prompt: "[one complete, standalone Cinema Studio prompt]"
}
```

## After the record
Review the record in Claude and save it in the `.jsx` shotlist. Cinema Studio does **not** ingest that whole file. Open the right project and folder, paste the `prompt` value into the Prompt Box, and select each `elements` entry through the `@` picker. For video, carry `duration` too. Before generating, the visible `@` tags must match the record exactly.

---

# Prompt method (fallback if Leera is not available)

When the `leera` skill is available, **delegate to it** for location prompts (it runs the 4-D method with its decision log). This summary is the fallback.

## Six decisions, then one prompt
There is no universal sentence formula. There is one reliable pass of decisions. Separate **subject, action, setting, light, camera/motion, constraints**, and assemble the six answers into one paragraph. A raw thought hints at a slot without resolving it ("hot summer day" says nothing about light direction or shadow shape). The final paragraph is not better for being longer, every clause has a job. If Claude adds a prop, style, weather or motion you did not choose, ask what ambiguity it resolves, then approve it, replace it or remove it.

## Leera's 4-D method (summary)
1. **DECONSTRUCT**, quote the useful words from the brief and map them to the six slots (plus camera motion if the target is video). Mark each slot as explicit, implicit or missing.
2. **DIAGNOSE**, audit gaps and ambiguity. Check logic, a single sun, believable doors and windows, shadows falling away from the declared source. For each gap, ask or label the proposed default. Never silently add weather, props, style or motion.
3. **DEVELOP**, build from approved decisions. A clear subject and action, the setting around them, a **named anchor object** (sofa, threshold, banner) to place the character later, explicit light (soft sources in interiors, hard visible rays tend toward slop), a tonal palette with soft falloff and no crushed shadows, and a camera angle (default 3/4 for depth if you give none). Motion only for video. Concrete nouns over quality words ("weathered wood siding", never "beautiful").
4. **DELIVER**, the optimized prompt as one paragraph in English, then a decision log. For every added or rewritten detail, name the ambiguity or failure it resolves.

**Modes.** DETAIL (default for a new location) asks 2-3 questions before optimizing, then does a deep pass. BASIC (quick fix) asks nothing, uses clearly labeled minimal defaults, and delivers now.
**Iteration.** When you reply with changes ("move the house to the right third, sun out of frame, sunset"), rewrite the **full** prompt with the change applied, never a diff or a fragment.

## Rules that keep a location believable
- **3/4 plus reverse test.** A 3/4 exposes side geometry and separates fore, mid and background (it gives floor and distance cues for placing the character). The reverse is a separate generation and a continuity test. Keep anchor, openings, light side, materials and palette locked, and compare the two frames before calling them the same location. Shot head-on, the location flattens into a backdrop and hidden geometry is free to invent doors and walls.
- **Blocking anchor.** One clear object you tie the blocking to. Change "the character is on the left" to "the character is between the sofa arm on the hallway side and the window". The relationship is testable in a later frame, vague direction is not.
- **Five locks to preserve in the reverse.** Anchor, openings (doors and windows), light side, materials, palette. If a lock disappears from the decision log, restore it before generating.
