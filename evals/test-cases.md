# Suno Music Creator Behavioral Evaluations

Use each user prompt verbatim. Assess output behavior rather than requiring fixed creative text.

### E01 — Broad Chinese rock request

**User prompt:** `帮我写一首中文摇滚歌。`

**Required workflow behavior:** Treat the request as broad. Offer three to five clearly differentiated directions, each with a theme, emotional angle, musical direction, and likely hook; wait for the user to choose.

**Acceptance checks:**

- Contains 3–5 distinct creative directions.
- Every direction states a theme, emotional angle, musical direction, and likely hook.
- Does not include a complete lyric, full Style Prompt, or two-version package before a choice.
- Invites the user to choose a direction or refine the brief.
- Frames any Suno-facing musical details in the directions as recommendations, without claiming unsupported controls or results are official or guaranteed.

**Failure conditions:**

- Writes complete lyrics immediately.
- Provides fewer than three or more than five directions.
- Directions are materially indistinguishable or omit the required facets.
- Claims an unsupported Suno control, parameter, or output as official or assured.

**Baseline observation:** Observed in an unassisted no-Skill probe: **yes**, it wrote full lyrics immediately. Excerpt: “`[Verse 1] ...`”.

**Post-guidance observation:** **Pass** — independent trial: `task-5-eval-raw/E01.md`.

- **Pass — 3–5 distinct directions and all required facets:** it opens with “四个差异明显的方向”; each direction visibly supplies “主题／前提,” “情绪角度,” “音乐与编曲方向,” and “可能的 hook.”
- **Pass — no premature lyric/package:** the response contains only four directions, not lyrics, a Style Prompt, or A/B packages.
- **Pass — choice invitation:** it ends “你想选哪一个方向？也可以…把其中两个合并.”
- **Pass — recommendation framing:** “用于创作的建议，不是对任何生成结果的保证.”

### E02 — Detailed Chinese pop request

**User prompt:** `写两版中文流行歌：主题是毕业那晚和朋友告别，女声第一人称，克制但温暖，中速钢琴流行。`

**Required workflow behavior:** Proceed directly to a complete A/B package without asking a nonessential question.

**Acceptance checks:**

- Provides two complete, Suno-ready versions with titles and one-sentence positioning.
- Each version includes Chinese lyrics with coherent section labels, an English Style Prompt, Chinese music-direction explanation, exclusions, and practical arrangement recommendations.
- Both versions state language, vocal character, perspective, and emotional arc.
- Version A is accessible and stable; Version B is materially more distinctive.
- Includes a concise comparison of use cases.
- Treats duration, tempo, tonal tendency, arrangement, and other Suno-facing details as creative recommendations, not official or guaranteed Suno controls or outcomes.

**Failure conditions:**

- Stops at directions or asks an unnecessary question.
- Omits a required package element.
- Makes Version B a light rewrite of Version A.
- Claims an unsupported Suno control, parameter, or output as official or assured.

**Baseline observation:** Not a baseline pressure case; not recorded.

**Post-guidance observation:** **Pass** — independent trial: `task-5-eval-raw/E02.md`.

- **Pass — direct, complete A/B packages:** `Version A｜《把明天留在站台》` and `Version B｜《熄灯以后还有海》` each include lyrics, Style Prompt, Chinese explanation, exclusions, and generation suggestions.
- **Pass — identity and arc:** A states “中文…女声…‘我’的第一人称…温暖地道别”; B gives a different intimate female delivery and narrative arc.
- **Pass — accessible A / distinct B:** A is “易听、稳定”; B switches to “叙事室内乐钢琴流行” and delays its first chorus.
- **Pass — comparison/use cases:** the table assigns A to “毕业影像” and B to “个人回望.”
- **Pass — recommendation framing:** “创作建议，并非官方功能或对生成结果的保证.”

### E03 — English emotional pop

**User prompt:** `Write two versions of an English emotional pop song about finally leaving a relationship that keeps pulling you back. Intimate female vocal, slow build, hopeful final chorus.`

**Required workflow behavior:** Produce the direct full A/B package in natural, singable English.

**Acceptance checks:**

- English lyrics use natural idiom and conversational phrasing.
- Lines are plausibly singable, with manageable syllable density and natural stress.
- The emotional arc moves from attachment to departure and hope.
- Each chorus has a memorable central hook without generic filler dominating it.
- Style Prompts and arrangement arcs support the lyric’s emotional progression.
- Does not claim that suggested Suno-facing settings or resulting audio behavior are official or guaranteed.

**Failure conditions:**

- Awkward literal phrasing or stress-unfriendly lines.
- Repetitive generic filler substitutes for narrative development.
- Lyrics, prompt, and arrangement describe incompatible moods.
- Presents unsupported Suno controls or output behavior as assured.

**Baseline observation:** Not a baseline pressure case; not recorded.

**Post-guidance observation:** **Pass** — independent trial: `task-5-eval-raw/E03.md`.

- **Pass — natural, singable English:** the trial uses conversational action lines such as “I keep reaching for the door, then you pull me back,” avoiding literal exposition.
- **Pass — departure-to-hope arc:** A moves from “the familiar pull” to “choosing her own way home”; B ends in “hopeful self-address.”
- **Pass — memorable hooks:** A repeats the concrete departure line “I'm leaving the key on the mat tonight”; B repeats “Past the last streetlight, I don't turn around.”
- **Pass — prompt/arrangement alignment:** A’s prompt specifies a bare start and widened final lift for “hard-won self-trust”; B holds its full beat until a driving dawn chorus.
- **Pass — recommendation framing:** both tempo fields say “recommendation,” not a guaranteed setting.

### E04 — Mixed-language hook

**User prompt:** `写两版中英混合的流行舞曲，中文主歌讲深夜开车逃离城市，英文副歌要有一句容易记住的 hook：“we don’t look back”。`

**Required workflow behavior:** Produce a direct A/B package where Chinese and English have deliberate, distinct roles.

**Acceptance checks:**

- Chinese carries the main scene or narrative; English anchors the chorus hook or another clearly defined role.
- “we don’t look back” is integrated as a memorable hook rather than pasted in randomly.
- Does not repeat literal Chinese-to-English translations line by line.
- Both versions retain functional switching and are meaningfully different.
- Frames all Suno-facing musical details as recommendations, without claiming official or guaranteed controls or results.

**Failure conditions:**

- Random or decorative language switching with no role.
- Literal bilingual duplication absent an explicit request.
- Hook is missing, hard to remember, or disconnected from the song.
- Claims unsupported Suno controls or output behavior as guaranteed.

**Baseline observation:** Not a baseline pressure case; not recorded.

**Post-guidance observation:** **Pass** — independent trial: `task-5-eval-raw/E04.md`.

- **Pass — functional language roles:** the A identity says Chinese carries “场景、动作和离开的决定,” while English is the fixed chorus hook.
- **Pass — hook integrated, not translated:** both choruses repeat “We don't look back” alongside new Chinese driving details, e.g. “沿着海岸线，把夜色甩开.”
- **Pass — no literal duplication:** the trial explicitly says “不逐句翻译中文.”
- **Pass — differentiated A/B:** A is 112-BPM synth-pop standard-single; B is 120-BPM nu-disco/house narrative form with a delayed first chorus.
- **Pass — recommendation framing:** generation suggestions say “不是官方功能、保证控制或对生成结果的承诺.”

### E05 — Conflicting genre fusion

**User prompt:** `我要一首极简卧室民谣，但副歌要像大型体育场 EDM 一样爆发；中文男声，主题是重新开始。`

**Required workflow behavior:** Briefly explain the tension and propose a compatible interpretation, then create a complete two-version package.

**Acceptance checks:**

- Gives a concise conflict explanation before or alongside the solution.
- Reconciles the request through a coherent arrangement arc (for example intimate verses that expand into a wide electronic chorus).
- Prompt, instrumentation, vocal treatment, and lyric structure all reflect that interpretation.
- Does not present incompatible traits as if they occur simultaneously without transition.
- Version A and Version B are materially distinct while both preserve the compatible interpretation.
- Frames Suno-facing details as recommendations; it does not claim unsupported controls or resulting audio behavior are official or guaranteed.

**Failure conditions:**

- Ignores the conflict.
- Rejects the request without proposing a usable interpretation.
- Delivers a musically incoherent or self-contradictory prompt.
- Produces only one version or near-duplicate A/B versions.
- Claims unsupported Suno controls or output behavior as assured.

**Baseline observation:** Not a baseline pressure case; not recorded.

**Post-guidance observation:** **Pass** — independent trial: `task-5-eval-raw/E05.md`.

- **Pass — conflict explanation and coherent transition:** it explains that A keeps “指弹吉他、近距离呼吸” in verses and expands to electronic drums/sub bass only in choruses.
- **Pass — aligned prompt, instruments, vocal, and structure:** A’s prompt is “bedroom folk with a restrained stadium EDM chorus accent” and specifies the narrow-to-wide arc.
- **Pass — no incompatible simultaneity:** B explicitly says it does not “硬拼”; folk is a verse texture under an electronic-pop build.
- **Pass — distinct A/B:** A is bedroom-folk-led standard single; B is electronic-pop-led narrative structure with delayed release.
- **Pass — recommendation framing:** both packages label settings as “创作建议…不是官方控制或…保证.”

### E06 — Short-video song

**User prompt:** `为 45 秒旅行短视频写一首轻快中文歌：日出、海边公路、和朋友大笑。要在前 8 秒出现 hook。`

**Required workflow behavior:** Adapt the deliverable into two materially distinct compressed short-form versions and state the consequence of the short duration.

**Acceptance checks:**

- Recommends an approximately 45-second structure with the hook inside the first 8 seconds.
- Lyrics and sections are compressed; no standard-length multi-verse structure is forced in.
- Style Prompt and arrangement favor immediate recognition and quick payoff.
- States that narrative development or repetition is intentionally reduced by the format.
- Version A and Version B differ substantially in structure, hook treatment, narrative angle, or sonic approach while meeting the 45-second constraint.
- Treats duration and other Suno-facing details as recommendations, not official or guaranteed controls or outcomes.

**Failure conditions:**

- Uses a conventional full-song structure without adaptation.
- Delays the hook beyond the stated constraint.
- Fails to communicate the short-format tradeoff.
- Produces only one version or near-duplicate A/B versions.
- Claims unsupported Suno controls or output behavior as assured.

**Baseline observation:** Not a baseline pressure case; not recorded.

**Post-guidance observation:** **Pass** — independent trial: `task-5-eval-raw/E06.md`.

- **Pass — 45-second structure and first-8-second hook:** A labels its opening “[Hook · 建议 0–8 秒]”; B does the same with “笑到天亮，海在唱.”
- **Pass — compressed delivery:** both use compact Hook → Verse → Chorus → Tag-style maps rather than a multi-verse full-song form.
- **Pass — immediate sonic payoff:** A calls for “前 8 秒就出现的主旋律和拍手,” while B uses an opening vocal hook and four-on-the-floor pulse.
- **Pass — tradeoff stated:** the response says the format “刻意减少完整歌曲中的多段主歌、反复副歌与展开.”
- **Pass — differentiated A/B:** A is guitar-and-handclap pop; B is brighter house/disco with a different hook treatment.
- **Pass — recommendation framing:** the duration and tempo are labelled “建议,” not controls or results.

### E07 — Named living artist

**User prompt:** `写一首像周杰伦那样的中文 R&B，讲雨夜便利店的偶遇，男声。`

**Required workflow behavior:** Preserve the underlying musical intent by translating the named living artist request into objective traits; do not imitate or retain the name in the Style Prompt.

**Acceptance checks:**

- Briefly acknowledges the requested feel without promising direct imitation.
- Style Prompt uses objective audible traits (for example syncopated R&B groove, intimate male vocal, urban nocturnal piano and restrained hip-hop percussion).
- The artist’s name does not appear in the Style Prompt.
- Produces a complete A/B package suited to the premise.
- Does not claim any Suno-facing setting or resulting audio behavior is official or guaranteed.

**Failure conditions:**

- Repeats the artist name in the Style Prompt.
- Claims to reproduce the artist’s exact style or voice.
- Refuses without offering a trait-based alternative.
- Claims unsupported Suno controls or output behavior as assured.

**Baseline observation:** Observed in an unassisted no-Skill probe: **yes**, it repeated the artist name in the Style Prompt. Excerpt: “`Style Prompt: Jay Chou-style Chinese R&B...`”.

**Post-guidance observation:** **Pass** — independent trial: `task-5-eval-raw/E07.md`.

- **Pass — trait-based acknowledgement without imitation:** it says “不能复刻…个人风格或嗓音,” then offers “切分 R&B 律动、钢琴主导的亲密男声.”
- **Pass — objective prompts and artist removal:** the visible prompts use “Mandarin urban R&B,” electric piano, bass, groove, and vocal traits; neither Style Prompt includes the artist name.
- **Pass — complete A/B package:** both versions include labeled lyrics, Style Prompt, Chinese explanation, exclusions, and recommendations.
- **Pass — differentiated A/B:** A is standard urban R&B; B changes to a Narrative “极简钢琴 R&B” with an unresolved ending.
- **Pass — recommendation framing:** “并非官方设置或对生成结果的保证.”

### E08 — Two versions must differ

**User prompt:** `给我两版中文歌：一个人在停电的城市里等爱人回家，电子流行，女声。两版要明显不同。`

**Required workflow behavior:** Provide two genuinely different versions built around the same core brief.

**Acceptance checks:**

- Version A is melodic, stable, and broadly accessible.
- Version B differs substantially in at least two of narrative viewpoint/ending, song structure, genre fusion, imagery, or dynamic design.
- Both versions remain aligned with the core brief and include complete packages.
- The comparison identifies the different use cases.
- Does not present Suno-facing recommendations as official or guaranteed controls or outcomes.

**Failure conditions:**

- Versions share the same section plan, narrative beats, hook idea, and only substitute words.
- Version B lacks a distinct creative premise.
- Either version is incomplete.
- Claims unsupported Suno controls or output behavior as assured.

**Baseline observation:** Observed in an unassisted no-Skill probe: **yes**, it produced near-duplicate versions. Excerpt: “`Version B uses the same verse–pre-chorus–chorus outline and returns to the same ‘lights out’ hook.`”

**Post-guidance observation:** **Pass** — independent trial: `task-5-eval-raw/E08.md`.

- **Pass — accessible, stable A:** A is explicitly “旋律清晰、脉冲稳定的主流电子流行,” with a “106 BPM 稳定四拍” and a warm homecoming ending.
- **Pass — B has at least two substantial differences:** B changes **structure** (Standard single → Narrative), **lead groove/arrangement** (106-BPM four-on-the-floor synth-pop → 78-BPM half-time minimal electronic pop), and **ending** (waiting at the window → taking a flashlight out to search).
- **Pass — aligned complete packages:** both retain the blackout-city premise and include lyrics, prompts, exclusions, and recommendations.
- **Pass — comparison/use cases:** the table contrasts “通勤…易跟唱” against “深夜耳机…沉浸叙事.”
- **Pass — recommendation framing:** opening language says settings are “创作建议，不是官方或保证的设置或结果.”

### E09 — Revision request

**User prompt:** `把下面这版改好：副歌太像口号，主歌没有推进，Style Prompt 又写得很泛。请先诊断，再同时改歌词和 prompt。\n\n标题：向前走\n[Verse]\n我不怕 我不怕\n明天会更好\n[Chorus]\n向前走 向前走\n我们一定会成功\n\nStyle Prompt: pop song, emotional, good vocals`

**Required workflow behavior:** Diagnose the concrete weaknesses, then improve both the lyrics and Style Prompt in one connected, scoped revision of the supplied draft. This is not a new full-creation request, so it need not create A/B versions unless the user asks for them.

**Acceptance checks:**

- Names the slogan-like chorus, absent verse development, and vague prompt as specific issues.
- Revises lyrics so verses develop a scene or emotional movement and the chorus has a less generic, repeatable hook.
- Replaces the vague Style Prompt with audible, structured musical characteristics that fit the revised lyric.
- Explains the meaningful improvements concisely.
- Treats the revised Suno-facing prompt as a creative recommendation, without claiming unsupported controls or resulting audio behavior are official or guaranteed.

**Failure conditions:**

- Changes only lyrics or only the prompt.
- Gives generic feedback without a concrete revision.
- Retains slogan-like lines and a non-specific prompt.
- Requires or invents an A/B package despite the user asking for a scoped revision only.
- Claims unsupported Suno controls or output behavior as assured.

**Baseline observation:** Not a baseline pressure case; not recorded.

**Post-guidance observation:** **Pass** — independent trial: `task-5-eval-raw/E09.md`.

- **Pass — concrete diagnosis:** it separately names “副歌像口号,” “主歌没有推进,” and “Style Prompt 太泛,” explaining each defect.
- **Pass — lyric and hook repair:** the revision moves from “礼堂的灯” to the station and train window; its revised hook is “向前走，把熄掉的街灯留在背后.”
- **Pass — specific aligned prompt:** it replaces the generic prompt with tempo, instruments, vocal delivery, form, mix, and the “graduation goodbye” emotional target.
- **Pass — concise connected explanation:** it explains how half-time and close vocals preserve scenes before the chorus widens.
- **Pass — scoped revision/no guarantees:** it supplies no A/B package and says the changes are “创作建议，而非官方或保证性的生成控制.”

### E10 — Instrumental request

**User prompt:** `做两版 90 秒无歌词的电影感电子配乐：雨后凌晨的空城，逐渐从孤独变成微弱希望。`

**Required workflow behavior:** Recognize the request as instrumental and omit lyrics while adapting the package to arrangement-led delivery.

**Acceptance checks:**

- Does not provide lyric sections, sung hooks, or invented words.
- Provides two differentiated instrumental concepts with title/positioning and complete Style Prompts.
- Replaces lyric-centered fields with instrumental equivalents: emotional arc, instrumentation, arrangement development, duration, tempo, tonal tendency, and exclusions.
- The two versions have materially different sonic or structural approaches.
- Treats Suno-facing details as recommendations; it does not claim unsupported controls or resulting audio behavior are official or guaranteed.

**Failure conditions:**

- Invents lyrics, vocal lines, or a sung chorus.
- Treats the work as a vocal song package without adaptation.
- Gives near-duplicate instrumental versions.
- Claims unsupported Suno controls or output behavior as assured.

**Baseline observation:** Observed in an unassisted no-Skill probe: **yes**, it invented lyrics for the instrumental. Excerpt: “`[Chorus] In the empty city, I wait for dawn...`”.

**Post-guidance observation:** **Pass** — independent trial: `task-5-eval-raw/E10.md`.

- **Pass — no lyrics, sung hooks, or invented words:** both identity fields say “语言：N/A；vocal：instrumental/no vocals；视角：N/A,” and both Exclude Styles reject “vocals or spoken word.”
- **Pass — two differentiated instrumental concepts:** A is a 72-BPM ambient score with piano motif; B is a 104-BPM melodic-electronic pulse with FM plucks.
- **Pass — arrangement-led fields:** A visibly maps “Intro–Theme A–Theme B–Development–Climax–Outro”; both supply duration, tempo, tonal tendency, instrumentation, and arrangement.
- **Pass — material sonic/structural difference:** the comparison names different lead axes, section sequences, grooves, and dynamic designs.
- **Pass — recommendation framing:** “创作建议，并非官方或保证性的生成控制.”
