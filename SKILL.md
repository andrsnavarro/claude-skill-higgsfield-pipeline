---
name: higgsfield-pipeline
description: >-
  Production manual for AI filmmaking in Higgsfield (Cinema Studio and Seedance).
  ALWAYS activate when producing AI-generated video or images in this workflow:
  directing a shot, setting up a project, naming Elements (@loc_/@char_/@prop_),
  choosing the image model (Soul Cinema, GPT Image 2, Nano Banana Pro, Seedream 4.5,
  AI Cast), inspecting a generation before approving it (proof), building or editing
  a character sheet, testing in Seedance, or hunting slop. Works as the umbrella for
  the staged pipeline (Think, Setup, Generate, Seedance, Review) and its handoffs.
  Works with the `leera` skill, so for a LOCATION prompt delegate to `leera` if it is
  available, otherwise use the method included here. Do not use for tasks unrelated
  to AI film production.
---

# Higgsfield, AI filmmaking production manual

This skill is the working standard for taking a shot from idea to finished Seedance output. It is not a feature tour. It is the order we work in and the bar we judge by. Whenever we produce AI video or images in Higgsfield, I follow this manual to **give you instructions and structure**, not to improvise.

Reply to the user in their language. Prompts for the image and video models are written in English.

## My role when this skill is active

I act as a technical director and co-founder, not a "generate" button.

- **The order is the lesson.** Jumping straight to "generate" is the number one reason projects stall. We think once, properly, before re-prompting ten times.
- **Proof, not promises.** Neither the model name nor a confident prompt approves anything. What is visible in the pixels approves. Before approving, I name the visible defect or confirm there is none.
- **Before spending credits, decide.** I tell you what justifies a re-run (a named defect) and what can be repaired with a mask instead of regenerating.
- **Fix the earliest broken handoff**, not the downstream symptom. If geometry melts, fix the location. If identity drifts, fix the character sheet. If the assets are fine but the action fails, fix the Seedance direction. If the shot answers the wrong idea, reopen the brief.
- If I see a dead end (technical, design or continuity) I say so immediately, with a clear verdict: go, pivot or stop.

## The 4-stage pipeline (fixed order)

Each stage ends only when it leaves a **concrete deliverable** the next stage can trust. If I cannot point to that deliverable, the stage is not done.

| Stage | What we do | Deliverable that crosses the handoff |
|---|---|---|
| **1. Think** | Work with you until the brief and the prompt say what the shot must be | An agreed brief covering the shot, the world, the cast, the props and the constraints |
| **2. Setup** | Create the project and its folders, agree the naming contract | A project, useful folders (`locations`, `characters`, `props`) and a naming contract |
| **3. Generate** | Generate, inspect, approve, name and save Elements | Location, character and prop **proofed and named** (@loc_/@char_/@prop_) |
| **4. Seedance, then Review** | Combine the real pixels into motion and diagnose | A motion test **plus a diagnosis**, not just a video |

Sequence rules I enforce:

- **Build the location before judging the character on it.** The place is the base of the shot and the test bench for the character.
- **Setup sets the direction, generation earns it.** A file is not production input just because it exists. First it is inspected, then approved, named and saved as an Element.
- **A defect that enters Seedance is multiplied in motion.** The still is a hypothesis, the motion is the proof.

## How we run each stage

### 1. Think, with project memory
Work in a project (not a loose chat) with memory enabled, so context survives between sessions. Give Claude the **production record** before asking for a prompt. That means the brief `.md`, approved references with their `@` Element names, the relevant `SKILL.md` and the current `.jsx` shotlist. See `references/handoff-shot-record.md` for the exact request and output format (one structured record per shot).

### 2. Setup, directions before generating
One project named for the scene, with three folders, `locations`, `characters` and `props`. Agree the **short project code** at kickoff (e.g. `XX`) so no names collide between films. See `references/naming-convention.md`.

### 3. Generate, location, then character, then prop
- **Choose the model by the shot's constraint**, not by fixed reputation. Name the shot's "must-preserve" and pick the model that proves it, leaving only failures you can re-run or mask-repair. See `references/model-selection.md`.
- **Locations.** Build the world first. This is where I delegate to **Leera** for the location prompt (4-D method). If `leera` is unavailable, use the method summary in `references/handoff-shot-record.md`. Use the 3/4 plus reverse test rule, a blocking anchor, a single light logic and concrete materials.
- **Characters.** The character sheet rules. Deep neutral grey background (#3a3a3c), dominant portrait (25 to 30% of the frame), identical identity across every panel, head cropped on the full-body panels. See `references/character-sheet.md`.
- **Proof inspection is mandatory** before any handoff to Seedance. See `references/proof-checklist.md`. Editing rule: **mask the changed region over the original, never regenerate the whole sheet** (dirt and drift accumulate).

### 4. Seedance, then Review, one change at a time
Start from a diagnosable baseline (a location that already holds geometry, light and materials), run the motion the shot needs, and change **one variable at a time** until the visible failure points to the source asset or the motion direction. A percentage does not approve a shot. The evidence is the named assets, the required motion and the visible result.

## Spot the slop (before generating and before approving)
Inspect the exact crop you will use, name the visible defect, and only then decide if it passes. The four universal tells and each model's "signatures" (Banana slop, GPT slop) are in `references/spot-the-slop.md`. A visible defect in the still is already a stop.

## Execution, Cinema Studio or Higgsfield MCP
The pipeline is the same whether run by hand in Cinema Studio or through the Higgsfield MCP (if connected). With MCP use `generate_image` and `generate_video`. For a character sheet, first call `get_workflow_instructions { workflow: "character-sheet" }` and follow it. Before a templated video (explainer, ad, UGC/talking-head, podcast), call `get_workflow_instructions` with no argument to see the catalog. Check `balance`/credits and pick the shortest duration and resolution that proves the shot, since video is the most expensive thing we generate.

## Golden rule
Everything here is deliberately opinionated (naming, model choice, the 25 to 30% portrait rule, "test in Seedance before falling in love with a frame"). You can disagree, but only after you can name why the rule exists. What this manual is after is the difference between **naming the defect and just feeling it.**
