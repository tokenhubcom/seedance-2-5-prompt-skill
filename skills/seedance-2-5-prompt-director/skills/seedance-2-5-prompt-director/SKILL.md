---
name: seedance-2-5-prompt-director
description: Create, improve, and troubleshoot English production briefs and prompts for Seedance 2.5 video generation. Use when a user wants text-to-video, image-to-video, reference-to-video, video editing, camera direction, audio direction, consistent characters or products, a multi-beat 30-second scene, or a better Seedance 2.5 prompt.
---

# Seedance 2.5 Prompt Director

Turn a creative idea into an executable video brief. Write prompts in English and optimize for coherent subjects, controlled motion, explicit camera language, purposeful audio, and a clear ending.

## Model Profile

For direct Volcengine Ark use, target `doubao-seedance-2-5-260628`. The model supports text-, image-, video-, and audio-guided video generation, reference-to-video, video editing, video extension, and first/last-frame generation. Its published profile supports 4–30 second output, 24 fps, 480P or 720P, and up to 50 references in one request: 30 images, 10 videos, and 10 audio assets.

Treat those values as a current working profile, not a permanent contract. Confirm account entitlement, endpoint availability, and interface-specific labels before generating. This skill writes and improves prompts; it does not call a generation API unless the user separately asks for generation and provides an available tool or provider.

Read [references/model-capabilities.md](references/model-capabilities.md) when selecting a generation mode, checking input limits, or explaining model-specific constraints. Do not load it for ordinary prompt rewriting when the requested mode and settings are already clear.

## Intake

Extract or ask only for missing details that materially affect the result:

- **Goal:** ad, social clip, product demo, narrative, music video, editorial, or other.
- **Mode:** text-to-video, first-frame or first/last-frame image-to-video, reference-to-video, edit, or extension.
- **Format:** target duration, aspect ratio, platform, and whether sound matters.
- **Anchors:** people, product, environment, style, reference assets, prohibited changes.
- **Story:** opening state, one primary action arc, final frame.
- **Camera and sound:** framing, movement, lighting, ambience, dialogue, music cues.

If no target duration is supplied, write a modular three-beat prompt that can be scaled to the duration available in the user's interface.

## Choose the Right Prompt Strategy

| Situation | Prioritize |
|---|---|
| Text only | Define the subject, setting, action, camera, light, sound, and final image. |
| Image-to-video | Treat the source image as the visual anchor; describe motion, camera behavior, and changes rather than repeating the image. |
| Multiple references | Assign each asset one role: identity, product, environment, style, camera, or audio. Use only the references needed for control and consistency; 50 is a maximum, not a target. Resolve conflicts before writing. |
| Product or character consistency | Lock the identity in the opening beat; keep wardrobe, materials, proportions, and key details stable. |
| Edit or extension | State what must remain unchanged, name the exact region or continuation point, then specify the smallest intended change. |
| Dialogue or music | Keep spoken lines short and unambiguous. Separate spoken dialogue, diegetic sound, ambience, and music cues. |

Never invent, translate, or normalize reference labels. If the selected interface exposes a reference token, copy it exactly as displayed, even when the token is not English. If no token is visible, describe the uploaded asset by its role instead of creating a token.

## Build the Prompt

Write the prompt as a production brief, not as a keyword list. Use this ordering:

1. **Opening anchor** — subject, setting, identity locks, framing, baseline lighting.
2. **Timed action beats** — one main action arc divided into simple sequential beats.
3. **Camera plan** — framing plus one deliberate camera move per beat.
4. **Look and lighting** — spatial depth, light source, direction, color, texture, and visual style.
5. **Sound plan** — ambience, key sound effects, music behavior, and dialogue when requested.
6. **Closing anchor** — the final composition, action completion, and hold or exit.
7. **Constraints** — only constraints that matter: preserve identity, no readable text, no extra people, no logos, or no camera movement.

### Three-Beat Structure

Use a three-beat scene for longer clips:

- **Opening:** establish the subject, environment, and visual rules.
- **Development:** execute one readable action or reveal.
- **Closing:** direct the final composition instead of leaving the ending unspecified.

For a 4–10 second clip, keep one subject action and one camera action active at a time. For a 20–30 second narrative, use an explicit timeline with distinct shots or beats, clear cut points, and one primary action per beat. Do not leave transitions or the final composition implicit.

### Reference Plan

Before writing, state the role of each reference in one short list. Use human-readable asset roles here; do not place synthetic interface tokens in the plan:

```text
First uploaded image - protagonist identity and wardrobe
Product packshot - product shape and label placement
Camera reference video - camera rhythm only
Music reference - musical mood and beat timing
```

When writing the copy-ready prompt:

- use an interface token only when the user or the active interface provides the exact token;
- preserve that token character-for-character and never translate it;
- otherwise refer to the asset in plain English, such as `the uploaded product packshot`;
- never expose template placeholders such as `{{product_reference}}` in a finished prompt.

Use reference assets to anchor appearance and visual language. Use text to describe the new action, composition, and progression. Do not give two references contradictory roles.

### Camera Language

Name the shot and movement directly: `wide establishing shot`, `medium tracking shot`, `slow push-in`, `locked-off close-up`, `gentle handheld follow`, `rack focus`, or `slow lateral pan`. For a multi-shot prompt, number the shots and give each an exact time range.

Prefer controlled movement. Avoid combining multiple complex camera moves with fast subject motion in the same beat. If stability matters more than spectacle, keep the camera locked and add a small natural subject action.

### Sound and Dialogue

Describe audio as part of the scene:

- **Ambience:** room tone, rain, street noise, wind, crowd, machinery.
- **Sync event:** an impact, beat drop, door close, pour, or gesture.
- **Dialogue:** identify the speaker and give the exact short line in quotation marks. State the spoken language when it matters.
- **Music:** identify mood, energy, and timing; do not request a named copyrighted song.

If the selected interface does not support audio generation, preserve the sound plan as post-production guidance.

## Output Format

Unless the user requests a different format, return:

1. **Creative approach** — one sentence.
2. **Reference plan** — only when assets are provided.
3. **Copy-ready prompt** — English, plain text, ready for the chosen interface.
4. **Optional negative constraints** — short and relevant.
5. **Settings checklist** — aspect ratio, duration, mode, and audio; mark anything provider-dependent as “verify in interface”.

Use the template in [assets/prompt-brief.md](assets/prompt-brief.md) when the user asks for a reusable brief or wants to fill in the details themselves.

Use [assets/templates/prompt_templates.json](assets/templates/prompt_templates.json) when the user wants a scenario-specific starting point. Select the closest template, replace every placeholder, remove irrelevant fields, and adapt the timing to the requested duration. Never return an unfilled template as a finished prompt.

## Diagnose and Revise

Change the smallest relevant part after each result. Do not rewrite the whole prompt without a diagnosis.

| Failure | Likely cause | Revision |
|---|---|---|
| Character or product drifts | Identity anchor is weak or references conflict | Put the identity lock in the opening; give each reference one role; remove conflicting descriptions. |
| Camera becomes chaotic | Too many movements or unclear sequence | Keep one camera move and one action per beat. |
| Scene feels static | No clear action progression | Add a single visible action with a beginning and an end. |
| Ending collapses | No final-frame instruction | Specify the final composition and hold. |
| Lighting changes unpredictably | Multiple or contradictory light sources | Name one key light, its direction, and one supporting practical source at most. |
| Extra people or objects appear | Scene is underconstrained | State the exact subject count and exclude unwanted elements. |
| Text is unreadable | Generated typography is unreliable | Remove the text request and add titles or labels in post-production. |
| Motion looks unstable | Fast or layered movement is over-specified | Slow the action, shorten the movement chain, or split into timed shots. |
| Audio does not match the scene | Sound direction is absent or too dense | Describe one ambience layer and a small number of synchronized events. |

## Quality Gate

Before delivering, verify that the prompt:

- starts with a clear subject and setting;
- has one coherent action arc;
- assigns non-conflicting roles to all references;
- gives the camera an explicit, physically plausible plan;
- uses an explicit time plan for narratives longer than one simple shot;
- defines the final frame;
- separates visual, audio, and constraint instructions;
- contains no unsupported API claim, external link, credential, attribution, or copied source text.
