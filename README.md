# Seedance 2.5 Prompt Skill for AI Agents

A production-ready Seedance 2.5 prompt engineering skill for AI agents. It turns rough ideas, storyboards, product briefs, images, videos, and audio references into structured English prompts for text-to-video, image-to-video, reference-to-video, video editing, video extension, camera direction, and synchronized sound.

The repository is agent-agnostic: install the skill in Codex or copy it into another agent that supports Markdown-based skills and reusable instruction folders.

## What This Seedance 2.5 Skill Does

- Converts a creative brief into a copy-ready Seedance 2.5 video prompt.
- Plans short clips and structured 20–30 second narratives.
- Supports text-to-video, first-frame image-to-video, first-and-last-frame transitions, and multimodal reference-to-video workflows.
- Writes controlled camera movement, shot timing, lighting, dialogue, ambience, music, and sound-effect direction.
- Preserves character identity, product geometry, wardrobe, environment, and visual continuity.
- Creates precise prompts for video editing and continuity-preserving extension.
- Diagnoses unstable motion, character drift, chaotic cameras, weak endings, and mismatched audio.

## Supported Prompt Workflows

| Workflow | Typical use |
|---|---|
| Text-to-video | Cinematic scenes, social videos, advertisements, and narrative clips |
| Image-to-video | Animate a source image while preserving identity and composition |
| First-and-last-frame video | Build a controlled transition between two visual states |
| Reference-to-video | Combine identity, product, environment, motion, and audio references |
| Video editing | Change one object or region while preserving the rest of the clip |
| Video extension | Continue the action, camera, lighting, and sound from an existing ending |

## Installation

The installable skill is located at:

```text
skills/seedance-2-5-prompt-director/
```

### Codex

Copy the complete skill folder into your Codex skills directory, then start a new task so the skill can be discovered.

Example destination:

```text
~/.codex/skills/seedance-2-5-prompt-director/
```

### Other AI Agents

Copy the complete folder into the custom skill, instruction, or capability directory supported by your agent. Keep `SKILL.md` and its `agents`, `assets`, and `references` folders together. Discovery and invocation syntax depend on the selected agent.

## Usage

Invoke the skill directly when the agent supports named skills:

```text
$seedance-2-5-prompt-director
```

Example requests:

```text
Use $seedance-2-5-prompt-director to create a 15-second cinematic
image-to-video prompt from my product photo. Use a slow push-in,
preserve the packaging, and end on a clean hero frame.
```

```text
Use $seedance-2-5-prompt-director to turn this storyboard into a
30-second Seedance 2.5 prompt with timed shots, dialogue, ambience,
camera directions, and a defined final frame.
```

```text
Use $seedance-2-5-prompt-director to diagnose why my character changes
appearance between shots and rewrite only the unstable parts.
```

## Reference Token Safety

Reference labels vary between interfaces and languages. This skill follows three rules:

1. Copy a visible interface token exactly as displayed.
2. Never translate, normalize, or invent a token.
3. If no token is visible, describe the asset by role, such as `the uploaded product packshot`.

Internal template placeholders are never returned as part of a finished, copy-ready prompt.

## Included Resources

```text
skills/seedance-2-5-prompt-director/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── assets/
│   ├── prompt-brief.md
│   └── templates/
│       └── prompt_templates.json
└── references/
    └── model-capabilities.md
```

The template library includes cinematic narrative, vertical social, ecommerce product reveal, first-frame animation, first-and-last-frame transition, multi-reference character consistency, precise editing, video extension, and multilingual performance patterns.

## Current Model Profile

The bundled capability reference currently targets `doubao-seedance-2-5-260628` and records the working profile used by the skill. Model access, limits, resolution options, duration, and interface labels can change, so the active provider interface remains the final source of truth.

## Frequently Asked Questions

### Does this skill generate videos?

No. It creates and improves Seedance 2.5 prompts. Video generation requires a compatible interface or API selected by the user.

### Does the skill require an API key?

No. Prompt creation runs inside the user's agent. An API key is only required if the user separately connects a video-generation provider.

### Can it work with Chinese or localized reference labels?

Yes. The surrounding prompt can remain English while the original interface reference token is preserved exactly.

### Is it limited to one AI agent?

No. The content is designed as a portable agent skill. Installation details depend on how each agent discovers custom skills.

### Can it improve an existing Seedance prompt?

Yes. It can diagnose and revise camera motion, action complexity, continuity, identity drift, lighting, sound, pacing, and ending composition.
