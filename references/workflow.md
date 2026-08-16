# Creation Workflow and A/B Delivery Contract

Use this workflow to turn a request into an original, usable Suno package. Pull lyric craft from `chinese-lyrics.md` or `english-lyrics.md`; pull form and music vocabulary from `song-structures.md` and `genre-library.md`; construct each English Style Prompt with `suno-prompts.md`.

## 1. Classify the request

Treat a request as **broad** when it supplies only a loose mood, genre, or use case and leaves the premise, language, perspective, or musical axis open. Treat it as **detailed** when it already specifies enough of those choices to write. Ask only questions whose answer would materially change the result; otherwise make a clearly stated creative recommendation.

If the request names an artist or a song, translate that reference into objective traits before drafting and remove the name from the final Style Prompt.

## 2. Broad-request directions

For a broad request, present **three to five** genuinely different directions. Every direction must contain:

- **Direction title**
- **Theme/premise**
- **Emotional angle**
- **Genre and arrangement direction**
- **Likely hook idea**

Vary a consequential axis across directions, such as narrative premise, language role, lead genre, groove, vocal distance, or arrangement arc. Do not supply full lyrics or the A/B package at this stage. Stop after the directions and **wait** for the user to select, combine, or revise a direction.

## 3. Detailed-request creation

For a detailed request, proceed directly to the A/B package. Make Version A and Version B substantially different: Version B must change a structure template or a lead genre/arrangement axis. A cosmetic instrument swap or wording change does not count. For an instrumental request, omit lyrics and provide a complete instrumental structure instead.

### Instrumental override

For an instrumental request, apply these overrides to both Version A and Version B so the shared package cannot introduce vocals:

- Set **Language** to `N/A`, **vocal** to `instrumental/no vocals`, and **perspective** to `N/A`; describe the emotional arc as musical rather than narrative.
- In the English Style Prompt, fill the vocal range/texture/delivery/layering field with exactly `instrumental/no vocals`.
- Provide the complete instrumental structure instead of lyrics, including the musical change in each section.
- Omit vocal recommendations from Generation suggestions; retain duration, tempo, tonal tendency, instrumentation, and arrangement recommendations.

## 4. Complete A/B deliverable

Deliver both versions using the following exact package. Use the requested language; the **English Style Prompt** remains English, and the explanation immediately below it remains concise Chinese.

### Version A

1. **Title** — a distinct working title.
2. **Positioning** — listener/use-case and the version's lead genre or arrangement axis.
3. **Language / vocal / perspective / emotional arc** — identify language, vocal character, narrative point of view, and movement from opening emotion to ending emotion.
4. **Full lyrics or instrumental structure** — provide complete, labeled lyrics with the selected song structure, or the complete instrumental section sequence and what changes in each section.
5. **English Style Prompt** — follow the ordered prompt pattern in `suno-prompts.md`.
6. **简要中文说明** — concisely explain the central production and vocal choices in Chinese.
7. **Exclude Styles** — a short list of audible conflicts.
8. **Generation suggestions** — duration recommendation, tempo recommendation, tonal tendency, vocal recommendation, instrumentation recommendation, and arrangement recommendation. Mark all as creative recommendations, not guaranteed controls.

### Version B

1. **Title** — a distinct working title.
2. **Positioning** — listener/use-case and the changed lead genre or arrangement axis.
3. **Language / vocal / perspective / emotional arc** — identify language, vocal character, narrative point of view, and a deliberately different emotional movement where appropriate.
4. **Full lyrics or instrumental structure** — provide complete, labeled lyrics with the selected song structure, or the complete instrumental section sequence and what changes in each section.
5. **English Style Prompt** — follow the ordered prompt pattern in `suno-prompts.md`; do not include a named artist or song title.
6. **简要中文说明** — concisely explain the central production and vocal choices in Chinese.
7. **Exclude Styles** — a short list of audible conflicts.
8. **Generation suggestions** — duration recommendation, tempo recommendation, tonal tendency, vocal recommendation, instrumentation recommendation, and arrangement recommendation. Mark all as creative recommendations, not guaranteed controls.

## 5. Final comparison

End with a **Version A vs. Version B comparison**. State the changed axis explicitly and compare at least the structure or lead genre, groove, vocal distance/delivery, arrangement movement, and intended listener effect. This comparison must make clear why the versions are alternatives rather than near-duplicates.

## 6. Revision workflow

When revising, first identify whether the issue is lyric craft, prompt specificity, structure, genre conflict, or insufficient A/B difference. Preserve the requested premise unless the user asks to change it; then revise the affected lyrics or instrumental structure, English Style Prompt, Exclude Styles, and recommendations together so the package remains internally consistent.
