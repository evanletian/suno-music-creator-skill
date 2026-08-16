# Suno Music Creator Skill Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build and validate an installable ChatGPT/Codex Skill that creates original Chinese, English, and mixed-language Suno song packages with two genuinely different versions.

**Architecture:** A concise `SKILL.md` owns triggering, routing, and the end-to-end decision flow. Focused reference files own language craft, structures, genres, prompting, and quality checks; evaluation cases define observable behavior before the production guidance is written.

**Tech Stack:** Markdown, YAML, Agent Skills format, Python 3, `skill-creator/scripts/init_skill.py`, `generate_openai_yaml.py`, and `quick_validate.py`.

## Global Constraints

- Skill name: `suno-music-creator`.
- Supported languages: Chinese, English, and mixed Chinese-English.
- Broad requests return three to five creative directions before full creation.
- Detailed requests proceed directly and ask only materially important questions.
- Full creation returns two substantially different versions.
- Prompts remain version-resilient and do not claim unofficial settings as guaranteed Suno controls.
- Named-artist requests are translated into objective musical traits.
- First release excludes Suno account automation, voice cloning, audio analysis, and automatic publishing.
- `SKILL.md` stays concise and routes detailed guidance to one-level-deep reference files.

---

## File Map

- `SKILL.md`: trigger conditions, request classification, reference routing, workflow, and delivery rules.
- `agents/openai.yaml`: user-facing metadata and default invocation prompt.
- `references/workflow.md`: direction-selection behavior and the complete A/B output contract.
- `references/chinese-lyrics.md`: Chinese phrasing, rhyme, hooks, and singability.
- `references/english-lyrics.md`: English idiom, stress, rhyme, and mixed-language behavior.
- `references/song-structures.md`: short-form, standard single, narrative, and instrumental structures.
- `references/genre-library.md`: genre vocabulary, instrumentation, groove, vocal treatment, and compatible fusion rules.
- `references/suno-prompts.md`: version-resilient Style Prompt and Exclude Styles guidance.
- `references/quality-check.md`: final review gates and revision rules.
- `evals/test-cases.md`: pressure scenarios, baseline observations, and acceptance checks.
- `docs/superpowers/specs/2026-08-16-suno-music-creator-design.md`: approved design.
- `docs/superpowers/plans/2026-08-16-suno-music-creator-implementation.md`: this plan.

### Task 1: Establish Behavioral Evaluations

**Files:**
- Create: `evals/test-cases.md`

**Interfaces:**
- Consumes: approved behavior from the design specification.
- Produces: ten named scenarios with prompts, required workflow behavior, rejection conditions, and acceptance criteria used by Tasks 2–6.

- [ ] **Step 1: Write the evaluation cases before production guidance**

Create ten cases covering:

```text
E01 broad Chinese rock request -> 3–5 directions, no full lyrics yet
E02 detailed Chinese pop request -> direct full A/B package
E03 English emotional pop -> natural idiom and singable stress
E04 mixed-language hook -> functional language switching
E05 conflicting genre fusion -> concise conflict explanation and compatible interpretation
E06 short-video song -> compressed structure and early hook
E07 named living artist -> translate name into objective traits
E08 two versions -> substantial structural or narrative difference
E09 revision request -> diagnose and improve both lyrics and prompt
E10 instrumental request -> omit lyrics and adapt deliverable
```

For every case, include one concrete user prompt, observable acceptance checks, and explicit failure conditions.

- [ ] **Step 2: Run baseline pressure checks without loading the new Skill**

For E01, E07, E08, and E10, record whether an unassisted agent:

```text
E01 incorrectly writes full lyrics immediately
E07 repeats the artist name in the Style Prompt
E08 produces near-duplicate versions
E10 invents lyrics for an instrumental
```

Record only observed behavior and short excerpts; do not add the intended production guidance to the baseline prompt.

- [ ] **Step 3: Verify the evaluation file is complete**

Run:

```bash
rg -n '^### E(0[1-9]|10)' evals/test-cases.md
rg -n 'User prompt|Acceptance checks|Failure conditions|Baseline observation' evals/test-cases.md
```

Expected: ten case headings and all four required fields for every case.

- [ ] **Step 4: Commit**

```bash
git add evals/test-cases.md
git commit -m "test: define Suno skill behavior evaluations"
```

### Task 2: Implement Language-Craft References

**Files:**
- Create: `references/chinese-lyrics.md`
- Create: `references/english-lyrics.md`

**Interfaces:**
- Consumes: E02, E03, E04, and E09.
- Produces: language-specific rules referenced by `SKILL.md` and `references/quality-check.md`.

- [ ] **Step 1: Convert evaluation failures into Chinese lyric rules**

Write focused guidance that covers natural modern Chinese, line length, breath, semantic progression, rhyme flexibility, hook construction, concrete imagery, and common failure repairs. Include one weak/strong pair for a verse and one for a chorus.

- [ ] **Step 2: Convert evaluation failures into English and mixed-language rules**

Write focused guidance that covers natural idiom, stress, syllable density, flexible rhyme, conversational phrasing, hook clarity, and functional language switching. Include one weak/strong English pair and one mixed-language example.

- [ ] **Step 3: Check required topics**

Run:

```bash
rg -n '押韵|副歌|口语|行长|呼吸|意象' references/chinese-lyrics.md
rg -ni 'stress|syllable|idiom|rhyme|mixed|hook' references/english-lyrics.md
```

Expected: every search term has at least one meaningful match.

- [ ] **Step 4: Commit**

```bash
git add references/chinese-lyrics.md references/english-lyrics.md
git commit -m "feat: add bilingual lyric craft guidance"
```

### Task 3: Implement Structures and Genre Vocabulary

**Files:**
- Create: `references/song-structures.md`
- Create: `references/genre-library.md`

**Interfaces:**
- Consumes: E01, E05, E06, E08, and E10.
- Produces: selectable song structures and objective music vocabulary used by the workflow and prompt builder.

- [ ] **Step 1: Define structure templates**

Document exact section sequences and selection conditions for:

```text
Short video: Hook → Verse → Chorus → Tag
Standard single: Intro → Verse 1 → Pre-Chorus → Chorus → Verse 2 → Chorus → Bridge → Final Chorus → Outro
Narrative: Verse 1 → Verse 2 → Chorus → Verse 3 → Bridge → Final Chorus
Rock escalation: Intro → Verse → Pre-Chorus → Chorus → Verse → Chorus → Breakdown/Bridge → Final Chorus
Instrumental: Intro → Theme A → Theme B → Development → Climax → Outro
```

Explain when labels may be omitted and how duration changes section count.

- [ ] **Step 2: Build the genre library**

For pop, rock, folk, R&B/soul, hip-hop, electronic, jazz, metal, cinematic, and Chinese-inspired fusion, define genre traits in terms of tempo tendency, groove, core instruments, vocal delivery, arrangement movement, mix character, compatible fusions, and likely conflicts.

- [ ] **Step 3: Add conflict-resolution rules**

Include concrete resolutions for acoustic + industrial, intimate vocal + stadium anthem, lo-fi + cinematic orchestral, and aggressive metal + soft lullaby. Each resolution must state which trait leads and which becomes an accent.

- [ ] **Step 4: Verify coverage**

Run:

```bash
rg -n '^## ' references/song-structures.md
rg -ni 'pop|rock|folk|R&B|hip-hop|electronic|jazz|metal|cinematic|Chinese' references/genre-library.md
rg -ni 'lead|accent|priority|conflict' references/genre-library.md
```

Expected: all five structures, all ten genre families, and explicit conflict-priority guidance are present.

- [ ] **Step 5: Commit**

```bash
git add references/song-structures.md references/genre-library.md
git commit -m "feat: add song structures and genre library"
```

### Task 4: Implement Suno Prompt and Delivery Contracts

**Files:**
- Create: `references/suno-prompts.md`
- Create: `references/workflow.md`

**Interfaces:**
- Consumes: language guidance from Task 2 and structure/genre vocabulary from Task 3.
- Produces: the exact user-facing A/B package and the Style Prompt construction method used by `SKILL.md`.

- [ ] **Step 1: Define the version-resilient Style Prompt pattern**

Specify this ordered prompt shape:

```text
genre/subgenre; era or production character; tempo and groove; instrumentation;
vocal range/texture/delivery/layering; structure and dynamic arc;
mix space/ambience/finish; emotional tone
```

Define Exclude Styles as a short list of audible conflicts. State that BPM, key, duration, and production details are creative recommendations rather than guaranteed controls.

- [ ] **Step 2: Define named-artist translation**

Add a transformation table:

```text
artist identity -> vocal texture + phrasing + instrumentation + production era + emotional delivery
song title -> structural traits + groove + arrangement arc + mix character
```

Require removal of the name from the final Style Prompt.

- [ ] **Step 3: Define broad-request directions**

Each of three to five directions must contain:

```text
direction title
theme/premise
emotional angle
genre and arrangement direction
likely hook idea
```

Require the workflow to stop after directions and wait for selection.

- [ ] **Step 4: Define the complete A/B deliverable**

For each version require title, positioning, language/vocal/perspective/emotional arc, full lyrics or instrumental structure, English Style Prompt, concise Chinese explanation, Exclude Styles, duration/tempo/tonal tendency/vocal/instrumentation/arrangement suggestions, and final comparison.

- [ ] **Step 5: Verify the contracts**

Run:

```bash
rg -ni 'genre/subgenre|tempo|instrumentation|vocal|dynamic arc|mix|emotional' references/suno-prompts.md
rg -n 'Version A|Version B|three to five|wait|Exclude Styles|comparison' references/workflow.md
```

Expected: every prompt dimension and every output component is explicitly present.

- [ ] **Step 6: Commit**

```bash
git add references/suno-prompts.md references/workflow.md
git commit -m "feat: define Suno prompts and creation workflow"
```

### Task 5: Implement Quality Gates

**Files:**
- Create: `references/quality-check.md`
- Modify: `evals/test-cases.md`

**Interfaces:**
- Consumes: all reference contracts from Tasks 2–4.
- Produces: a single pre-delivery checklist and post-Skill observations for all ten evaluations.

- [ ] **Step 1: Write the quality checklist**

Include checks for theme, emotional movement, verse development, chorus hook, natural language, singability, coherent labels, A/B differentiation, prompt/lyric alignment, exclude/require contradictions, named-artist removal, unsupported claims, and instrumental handling.

- [ ] **Step 2: Add revision priorities**

Require fixes in this order:

```text
1. brief compliance
2. hook and emotional arc
3. language naturalness and singability
4. section development
5. prompt/arrangement alignment
6. polish and novelty
```

- [ ] **Step 3: Re-run all ten evaluation cases with the completed reference set**

Append a `Post-guidance observation` to every case. Record pass/fail against each acceptance check and preserve short evidence excerpts.

- [ ] **Step 4: Verify evaluation completion**

Run:

```bash
test "$(rg -c '^### E(0[1-9]|10)' evals/test-cases.md)" -eq 10
test "$(rg -c 'Post-guidance observation' evals/test-cases.md)" -eq 10
rg -n 'brief compliance|hook and emotional arc|named-artist|instrumental' references/quality-check.md
```

Expected: all commands exit 0.

- [ ] **Step 5: Commit**

```bash
git add references/quality-check.md evals/test-cases.md
git commit -m "test: add quality gates and evaluation results"
```

### Task 6: Assemble and Validate the Installable Skill

**Files:**
- Create: `SKILL.md`
- Create: `agents/openai.yaml`

**Interfaces:**
- Consumes: every file created in Tasks 1–5.
- Produces: the installable `suno-music-creator` Skill and UI metadata.

- [ ] **Step 1: Write `SKILL.md` frontmatter**

Use exactly:

```yaml
---
name: suno-music-creator
description: Use when creating or revising original songs, lyrics, song structures, style prompts, or exclude-style guidance intended for Suno, including Chinese, English, and mixed-language requests.
---
```

- [ ] **Step 2: Write the concise core workflow**

The body must:

```text
classify broad versus detailed requests
route language guidance
route structure and genre guidance
run direction selection for broad requests
produce full A/B deliverables for detailed or selected requests
handle instrumental requests
translate named artists into objective traits
run the quality checklist before delivery
```

Link every reference directly from `SKILL.md`; do not nest reference discovery.

- [ ] **Step 3: Generate `agents/openai.yaml`**

Run from the skill-creator directory:

```bash
python scripts/generate_openai_yaml.py /workspace/scratch/2259c0e99bed/suno-music-creator-skill \
  --interface display_name="Suno Music Creator" \
  --interface short_description="Create bilingual Suno lyrics and structured music prompts" \
  --interface default_prompt="Use $suno-music-creator to create two complete Suno-ready song versions from my idea."
```

Expected `agents/openai.yaml`:

```yaml
interface:
  display_name: "Suno Music Creator"
  short_description: "Create bilingual Suno lyrics and structured music prompts"
  default_prompt: "Use $suno-music-creator to create two complete Suno-ready song versions from my idea."
```

- [ ] **Step 4: Run structural validation**

```bash
python /root/.codex/skills/oai/skill-creator/scripts/quick_validate.py /workspace/scratch/2259c0e99bed/suno-music-creator-skill
```

Expected: validation succeeds with no errors.

- [ ] **Step 5: Run repository checks**

```bash
rg -n '^name: suno-music-creator$|^description: Use when' SKILL.md
rg -n '\$suno-music-creator' agents/openai.yaml
find references -maxdepth 1 -type f | sort
test "$(find references -maxdepth 1 -type f | wc -l)" -eq 7
```

Expected: correct metadata, explicit default invocation, and exactly seven reference files.

- [ ] **Step 6: Re-run representative end-to-end evaluations**

Run E01, E02, E03, E04, E07, E08, and E10 with the complete Skill loaded. Confirm that broad requests stop at directions, detailed requests return complete A/B packages, named artists disappear from final prompts, versions differ materially, and instrumental requests omit lyrics.

- [ ] **Step 7: Commit**

```bash
git add SKILL.md agents/openai.yaml references evals/test-cases.md
git commit -m "feat: add installable Suno music creator skill"
```

### Task 7: Final Verification and Repository Handoff

**Files:**
- Verify: all files in the File Map
- Modify only if validation exposes a documented failure.

**Interfaces:**
- Consumes: complete Skill from Task 6.
- Produces: verified public repository ready for installation and future versioned maintenance.

- [ ] **Step 1: Run all automated checks from a clean checkout**

```bash
python /root/.codex/skills/oai/skill-creator/scripts/quick_validate.py .
test "$(rg -c '^### E(0[1-9]|10)' evals/test-cases.md)" -eq 10
test "$(find references -maxdepth 1 -type f | wc -l)" -eq 7
git status --short
```

Expected: validator succeeds, counts are correct, and the working tree is clean.

- [ ] **Step 2: Perform the final content review**

Confirm:

```text
no TBD, TODO, or unfinished placeholders
no claims of guaranteed Suno controls
no dependency on a fixed Suno version
no artist-name imitation instructions
all references are linked directly from SKILL.md
all ten evaluations contain baseline and post-guidance observations
```

- [ ] **Step 3: Verify remote paths**

```bash
git ls-tree -r --name-only HEAD | sort
```

Expected: all files in the File Map appear exactly once.

- [ ] **Step 4: Commit any validation-only fixes**

If validation required a fix, commit only the corrected files with:

```bash
git add SKILL.md agents/openai.yaml references evals/test-cases.md
git commit -m "fix: resolve Suno skill validation findings"
```

If no fix was needed, do not create an empty commit.

- [ ] **Step 5: Publish the final verification summary**

Report the validation command results, evaluation coverage, final commit SHA, and repository URL. Do not claim completion unless every required check passed.
