# Seedance 2.5 Model Capabilities

Use this reference when a task depends on model-specific inputs, limits, or generation modes. Treat it as a dated capability snapshot and verify the selected provider's current interface before an actual generation request.

## Current Model Profile

- Model family: Doubao-Seedance-2.5
- Model ID for direct Volcengine Ark use: `doubao-seedance-2-5-260628`
- Input types: text, image, video, and audio
- Output type: video
- Published duration range: 4–30 seconds
- Published resolutions: 480P and 720P
- Published frame rate: 24 fps
- Maximum reference inputs: 50 total
  - Up to 30 images
  - Up to 10 videos
  - Up to 10 audio assets

The maximum reference count is a capacity limit, not a recommended target. Use only the assets that provide a distinct and necessary form of control.

## Supported Workflows

### Text-to-Video

Generate a video from a text production brief. Define the subject, setting, action progression, camera plan, lighting, sound, and final frame.

### First-Frame Image-to-Video

Use an image as the opening visual anchor. Preserve its subject identity, composition, materials, and lighting unless the user requests a deliberate change. Focus the prompt on motion and camera behavior.

### First-and-Last-Frame Image-to-Video

Use two images to constrain the opening and closing states. Describe a physically plausible transition between them and avoid introducing unrelated intermediate events.

### Multimodal Reference-to-Video

Use images, videos, and audio assets together. Assign every reference one explicit role, such as identity, product geometry, environment, visual style, camera behavior, or sound timing.

### Video Editing

Identify the exact region, object, character, or property to change. State what must remain unchanged. Prefer the smallest possible edit instruction to preserve the original motion and composition.

### Video Extension

Continue from the final state and motion direction of the source clip. Preserve subject identity, spatial layout, lighting logic, camera momentum, and sound continuity. Define the new ending explicitly.

## Reference Token Rules

- Copy reference tokens exactly as displayed by the user's interface.
- Do not translate or normalize a token.
- Keep the original token even when the surrounding prompt is written in English.
- Do not invent a token for an asset that has not been uploaded or selected.
- If the interface exposes no token, identify the asset by a clear plain-English role such as `the uploaded product packshot`.
- Do not expose internal template placeholders in a finished prompt.
- Resolve conflicting reference roles before writing the final prompt.

## Prompting Implications

- Use explicit time ranges for a long or multi-shot narrative.
- Keep one primary subject action per beat.
- Name each shot size, camera movement, transition, and final composition.
- Separate dialogue, ambience, synchronized sound effects, and music direction.
- State the spoken language and exact dialogue when lip synchronization matters.
- Prefer post-production for complex typography or exact logo rendering.
- Reduce reference count, action complexity, or camera complexity when results drift.

## Version-Safety Rule

Do not treat this file as a permanent API contract. If the user's interface shows different durations, resolutions, limits, model IDs, or supported modes, follow the selected interface and disclose the difference.
