# Suno Prompt Construction

Build prompts from audible, objective choices rather than from a named performer or a promise about a specific control. Use the language craft references for lyric and vocal wording, and use the structure and genre references for the musical vocabulary.

## Style Prompt pattern

Write the English Style Prompt in this order, separating each dimension with a semicolon:

```text
genre/subgenre; era or production character; tempo and groove; instrumentation;
vocal range/texture/delivery/layering; structure and dynamic arc;
mix space/ambience/finish; emotional tone
```

Keep each field concrete and audible. Lead with one genre; if a fusion conflicts, name the lead trait and make the other a restrained accent. Do not turn the prompt into a list of unrelated genre labels.

Example:

```text
Mandarin alternative pop with restrained electronic accents; early-2000s analog warmth;
mid-tempo half-time pulse with a syncopated kick; muted electric guitar, warm synth bass,
dry drum machine, and sparse piano; low-to-mid intimate female vocal with close-mic
conversational phrasing, doubled only in the chorus; verse-pre-chorus-chorus form with
a quiet first verse and a widening final chorus; close verses, wide chorus reverb, soft
tape finish; late-night resolve after a difficult goodbye
```

### Recommendations, not guaranteed controls

Treat BPM, key, duration, and production details as creative recommendations. They communicate intended feel and arrangement, but are not guaranteed controls or promises of a particular generated result. Use a tonal tendency (for example, “minor-leaning” or “bright major lift”) when it is more useful than asserting an exact key.

## Exclude Styles

Include **Exclude Styles** as a short list of audible conflicts that would undermine the intended result. Prefer two to five concise exclusions, such as `maximal EDM drops; jazz improvisation; harsh screamed vocals`. Do not use it as a second style prompt or as a list of vague dislikes; name conflicting groove, vocal, arrangement, or mix behaviors.

## Named-artist and song-title translation

When a request names an artist or song, translate the reference into objective, audible traits before drafting. The reference can guide analysis, but its name must be removed from the final English Style Prompt and Exclude Styles.

| Request reference | Translate into |
| --- | --- |
| artist identity | vocal texture + phrasing + instrumentation + production era + emotional delivery |
| song title | structural traits + groove + arrangement arc + mix character |

For example, identify whether the requested vocal is breathy or projected, whether phrasing is clipped or legato, which instruments carry the hook, how polished or raw the production character is, and whether the delivery is restrained, playful, wounded, or triumphant. For a song reference, identify its section pacing, rhythmic pocket, build/release shape, and spatial finish. Then write those traits without the artist or song name.

## Prompt assembly check

Before delivery, check that the Style Prompt is English and contains every dimension in the stated order: genre/subgenre, era or production character, tempo and groove, instrumentation, vocal range/texture/delivery/layering, structure and dynamic arc, mix space/ambience/finish, and emotional tone. Confirm that Exclude Styles is short, audible, and compatible with the intended lead genre.
