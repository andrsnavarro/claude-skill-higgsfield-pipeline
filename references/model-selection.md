# Choosing the image model

There is no permanent "best" model. Treat these as today's candidates and choose by the shot's **non-negotiable**. If the roster changes, repeat the evidence test on the shot instead of carrying today's ranking forward.

## The decision rule
Before each location or character pass, **name one must-preserve requirement**. Inspect the output at its real crop.
- Location, atmosphere, material texture, anchor objects.
- Character, identity, skin, pose, gradients.

Choose the model that **proves** the must-preserve and leaves only failures you can re-run or mask-repair.

## Candidates

**Soul Cinema**, the *from-scratch* candidate when cinematic texture and atmosphere matter more than exact object control.
- For it: raking side light that keeps materials tactile, haze that creates depth, creative angles, color and light for location exploration, realistic skin and clothing for character sheets from scratch, and it handles short and long prompts.
- Can rule it out: creative variation means an exact composition may take several runs, props, monsters and creatures are a weaker fit, and it can rework an image but **cannot** attach multiple references or edit a finished image.
- Also the first choice for **generating characters**.

**GPT Image 2**, the *control* candidate for legible text, prop geometry, fine detail, reverse angles and reference-guided edits.
- For it: keeps body and object geometry consistent across views (passes the reverse-angle test), stickers and labels are legible and well placed, complex mechanical detail with consistent scale and proportion, and convincing material wear.
- Can rule it out: **oversharpens human skin into slop** (it is the *creatures* model, not the humans model), hard halos on edges, everything in focus with no plane separation, warm or yellow white balance, plastic materials.
- Use it for a **precise addition** on an existing character (small patch), text, or exact geometry.

**Nano Banana Pro**, the *edit* candidate when a finished image needs a bold change of wardrobe, face or object and landing the change matters most.
- For it: a broad re-dress lands coherently across views, it also works for monsters and creatures, and it can attach a finished image to edit.
- Can rule it out: edits can tint the whole image and damage gradients (**mask only the changed region** over the original), uncovered faces come out symmetric and lifeless, and from-scratch locations come out centered and stock. **Never use it to start a location or a hero character from scratch.**

**Seedream 4.5**, the *character sheet edit* candidate when preserving skin and clothing texture matters more than exact pose or landing every requested detail.
- For it: keeps fine armor and clothing detail across views, freckles, pores and eye detail survive, and it avoids the "banana" or oversharpened look.
- Can rule it out: it can shift pose or angle (needs a longer mask-and-composite), and it can preserve texture but **lose part of the requested change**. Compare it with Nano Banana Pro when landing every change is the biggest risk.
- Runs in parallel batches, take the cleanest result.

**AI Cast (Cinema Studio)**, a strong casting tool, worth exploring for characters.

## Editing, run models in parallel
For edits (locations or characters) you do not pick one. You run GPT Image 2, Nano Banana Pro and Seedream 4.5 in parallel and take the best result per change. Every edit is **composited over the original with a Photoshop mask**, only the region that changed, with the rest untouched. Each edit re-renders the whole image, so regenerating the entire sheet accumulates drift and dirt.
