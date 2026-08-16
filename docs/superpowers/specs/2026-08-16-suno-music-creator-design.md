# Suno Music Creator Skill — Design Specification

Date: 2026-08-16  
Repository: `evanletian/suno-music-creator-skill`  
Skill name: `suno-music-creator`

## 1. Purpose

Create an installable ChatGPT/Codex Skill for producing original Suno-ready songs. The Skill supports Chinese, English, and mixed Chinese-English creation. It generates complete lyrics and structured music prompts without depending on a fixed Suno version.

## 2. Primary behavior

### 2.1 Broad requests

When the user gives only a broad request such as “write a rock song,” the Skill first presents three to five clearly differentiated creative directions. Each direction includes a concise theme, emotional angle, musical direction, and likely hook. It waits for the user to choose before producing the full song package.

### 2.2 Detailed requests

When the user already provides a usable theme, genre, emotion, language, or narrative premise, the Skill proceeds directly. It asks only questions whose answers would materially change the result.

### 2.3 Two-version default

The full workflow produces two genuinely different versions around the same core brief:

- Version A: accessible, melodic, stable, and broadly usable.
- Version B: more distinctive in narrative, genre fusion, imagery, or section design.

Version B must not be a lightly reworded copy of Version A.

## 3. Default deliverable

Each version contains:

1. Song title and one-sentence positioning
2. Language, vocal character, perspective, and emotional arc
3. Complete lyrics with Suno-readable section labels such as `[Verse]`, `[Pre-Chorus]`, `[Chorus]`, `[Bridge]`, and `[Outro]`
4. English Suno Style Prompt
5. Concise Chinese explanation of the musical direction
6. Exclude Styles / elements to avoid
7. Suggested duration, tempo range, tonal tendency, vocal approach, instrumentation, and arrangement development
8. A short comparison explaining which version fits which use case

These are creative recommendations, not claims of official or guaranteed Suno controls.

## 4. Language requirements

### 4.1 Chinese lyrics

- Prefer clear, natural, singable modern Chinese.
- Avoid forced inversions, empty slogan-like lines, and piles of obscure imagery.
- Control line length and phrasing so important stresses land naturally.
- Give the chorus a concise, repeatable central hook.
- Use rhyme as a musical aid, not as a reason to damage meaning.

### 4.2 English lyrics

- Use natural idiom and conversational phrasing.
- Consider stress, syllable density, breath, and singability.
- Keep rhyme flexible and avoid repetitive generic filler.
- Preserve a clear emotional or narrative progression.

### 4.3 Mixed-language lyrics

- Give each language a functional role rather than switching randomly.
- Keep the central hook easy to remember.
- Avoid literal translation repeated line by line unless explicitly requested.

## 5. Suno prompt design

The prompt system is version-resilient and describes audible musical characteristics instead of relying on a fixed Suno release.

A Style Prompt may specify:

- genre and subgenre
- era or production character
- tempo and groove
- instrumentation
- vocal range, texture, delivery, and layering
- song structure and dynamic arc
- mix space, ambience, and production finish
- emotional tone

The Skill must not depend on living artist names or direct imitation. If a user requests a named artist, it translates that request into objective musical traits while preserving the user's underlying intent.

## 6. Proposed repository structure

```text
suno-music-creator-skill/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── workflow.md
│   ├── chinese-lyrics.md
│   ├── english-lyrics.md
│   ├── song-structures.md
│   ├── genre-library.md
│   ├── suno-prompts.md
│   └── quality-check.md
├── evals/
│   └── test-cases.md
└── docs/
    └── superpowers/
        └── specs/
            └── 2026-08-16-suno-music-creator-design.md
```

## 7. Module responsibilities

- `SKILL.md`: trigger conditions, routing logic, core workflow, and references to supporting files. It stays concise.
- `agents/openai.yaml`: display name, short description, and default prompt.
- `references/workflow.md`: full output format, broad-request direction flow, and A/B version rules.
- `references/chinese-lyrics.md`: Chinese lyric craft, phrasing, rhyme, hooks, and failure patterns.
- `references/english-lyrics.md`: English lyric craft, stress, rhyme, idiom, and singability.
- `references/song-structures.md`: short-form, standard single, narrative, and other useful structures.
- `references/genre-library.md`: genre vocabulary, instrumentation, groove, vocal treatment, and compatible fusions.
- `references/suno-prompts.md`: structured, version-resilient Style Prompt guidance.
- `references/quality-check.md`: pre-delivery quality checklist.
- `evals/test-cases.md`: representative prompts and observable acceptance criteria.

## 8. Error and ambiguity handling

- If the brief is broad, offer directions instead of inventing a full premise silently.
- If requirements conflict, explain the conflict briefly and propose a compatible interpretation.
- If a requested format is unusually long or short, adapt the structure and state the consequence.
- If a named-artist imitation is requested, replace the name with musical traits.
- Never present unverified parameters as official Suno controls.
- If essential information remains missing after one focused question, use clearly stated reasonable defaults.

## 9. Quality gates

Before delivery, verify:

- the lyric has a clear theme and emotional movement
- verses develop rather than repeat the chorus message
- the chorus contains a memorable central hook
- language is natural and singable
- section labels are structurally coherent
- A and B are meaningfully different
- Style Prompt matches the lyric and arrangement arc
- excluded elements do not contradict required elements
- no direct cloning of a living artist or existing song is encouraged
- no unsupported claim is made about Suno behavior

## 10. Evaluation set

The initial evaluation file covers at least:

1. Broad Chinese rock request that must return creative directions first
2. Detailed Chinese pop request that should proceed directly
3. English emotional pop song
4. Chinese-English mixed hook
5. Genre fusion request with conflicting attributes
6. Short-form song intended for a video
7. Named-artist request requiring trait translation
8. Request for two versions that must be substantially different
9. Weak first draft requiring lyric and prompt revision
10. Instrumental request where lyric generation should be skipped

Each case records expected workflow behavior and quality criteria rather than a single fixed answer.

## 11. Out of scope for the first release

- Suno account automation or song generation through a browser/API
- voice cloning or training
- deterministic rhyme-analysis scripts
- audio analysis
- automatic publishing
- claims of guaranteed Suno output

## 12. Acceptance criteria

The first release is complete when:

- the Skill can be discovered from requests for Suno songs, lyrics, or music prompts
- broad requests produce three to five directions before full creation
- detailed requests produce the complete two-version package
- Chinese, English, and mixed-language outputs follow their respective guidance
- prompts are structured and do not lock the Skill to one Suno version
- all required files validate as an installable Skill
- the evaluation cases cover the core paths and pass manual review
