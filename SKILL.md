---
name: suno-music-creator
description: Use when creating or revising original songs, lyrics, song structures, style prompts, or exclude-style guidance intended for Suno, including Chinese, English, and mixed-language requests.
---

# Suno Music Creator

Create original, internally coherent Suno-ready song packages. Treat tempo, duration, tonal tendency, arrangement, and production details as creative recommendations rather than official or guaranteed controls.

## Core workflow

1. Read [Creation Workflow and A/B Delivery Contract](references/workflow.md). Classify the request before drafting:
   - **Broad:** The premise, language, perspective, or musical axis remains open. Offer three to five genuinely different directions, each with a title, premise, emotional angle, genre/arrangement direction, and likely hook. Stop and wait for the user to select, combine, or revise a direction.
   - **Detailed or selected:** Proceed directly to the complete Version A and Version B package. Make Version B change a structure template or lead genre/arrangement axis, then end with an explicit comparison.
   - **Scoped revision:** Diagnose the supplied lyric, prompt, structure, or differentiation issue, then revise the connected elements together. Do not invent an A/B package unless requested.
2. Route lyric craft by language:
   - For Chinese lyrics, read [中文歌词写作](references/chinese-lyrics.md).
   - For English or mixed-language lyrics, read [English and Mixed-Language Lyric Craft](references/english-lyrics.md). Give each language a distinct function; do not translate line by line.
3. Select a functional form from [Song Structures](references/song-structures.md), then choose one lead musical axis and compatible accents from [Genre Library](references/genre-library.md). Resolve conflicts by making one trait lead and the other a restrained accent.
4. For a named artist or song, translate the reference into objective audible traits such as vocal texture, phrasing, groove, instrumentation, arrangement movement, production character, and mix space. Never promise imitation or retain the name in the final Style Prompt or Exclude Styles.
5. Build each English Style Prompt and short Exclude Styles list with [Suno Prompt Construction](references/suno-prompts.md). Keep the prompt audible, ordered, specific, and aligned with the lyric or instrumental roadmap.
6. For an instrumental request, apply the instrumental override to both versions: set language and perspective to `N/A`, set vocal to exactly `instrumental/no vocals`, omit lyrics and vocal recommendations, and provide a complete arrangement-led structure with the musical change in every section.
7. Run [Pre-delivery Quality Check](references/quality-check.md). Repair higher-priority issues before lower-priority polish and repeat downstream checks after any premise, structure, genre, or vocal-role change.

## Delivery rules

- Follow the exact A/B package in [Creation Workflow and A/B Delivery Contract](references/workflow.md) for detailed or selected requests.
- Keep the English Style Prompt in English and place a concise Chinese explanation immediately below it.
- Make lyrics conversational, singable, scene-led, and structurally progressive; give the chorus one specific central hook.
- State the changed A/B axis in both prompts and in the final comparison. Cosmetic word changes or an accent-instrument swap do not create a second version.
- Keep Exclude Styles short, audible, and compatible with required traits.
- Never claim a model version, undocumented parameter, exact UI field, guaranteed duration, or guaranteed audio result.
