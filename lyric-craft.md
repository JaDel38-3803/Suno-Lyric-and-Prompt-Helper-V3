# Lyric Craft

Internal reference for writing lyrics that produce predictable, high-quality Suno output. These principles are applied silently during lyric generation; they are not surfaced to the user as a tutorial.

The principles in this file address one problem: Suno binds its musical generation to the structure of the lyrics. Lyrics with weak or generic structure produce weak or generic music regardless of how good the style prompt is. Lyrics with deliberate structural choices give Suno scaffolding to build with.

---

## Core Principle: Lyrics Are Two Things at Once

Suno is a token-prediction system that aligns musical phrases to lyrical phrases. Every structural feature of the lyrics — line length, syllable count, rhyme scheme, line endings, punctuation — affects how Suno produces the music.

This means a lyric is doing two jobs simultaneously:

1. **Telling a story or expressing an emotion** (the human-readable function)
2. **Encoding musical instructions through structure** (the Suno-readable function)

Both jobs matter equally. Lyrics that read beautifully but use the same rhyme scheme and line length throughout will produce a flat, predictable song. Lyrics with deliberate structural variation produce music with deliberate variation.

The rest of this document describes the structural levers and when to use each.

---

## The Rule of Prosody: How Lyrics Physically Occupy Music

Prosody is the master constraint underlying all other lyric decisions. It governs how the natural stress pattern of language aligns — or misaligns — with the stress pattern of the music. No amount of structural cleverness compensates for bad prosody; a line with perfect syllable count and rhyme scheme will still sound wrong if its stressed syllables land on the wrong beats.

### Syllabic Stress Matching

Every word in English has a natural stress pattern. Multi-syllable words have a primary stressed syllable (de-**FEAT**, not **DE**-feat). The job of the lyric writer is to ensure the stressed syllable of each word aligns with the primary musical accent — the downbeat, the snare hit, the heavy chug of the riff.

- **Wrong:** Placing "de-FEAT" so the unstressed "de" hits the snare. The word fights the music.
- **Right:** The stressed "FEAT" lands on the kick or primary accent of the riff. The word locks in.

When stressed syllables consistently land on weak beats, lyrics feel "off" even if listeners can't articulate why. When they consistently land on strong beats, the lyric feels inevitable — like it was always meant to be sung to that riff.

**Practical check:** Read the lyric aloud with an exaggerated spoken stress before setting it to music. If the natural spoken stress doesn't land where the musical accents are, rewrite the line.

### Vowel Choice vs. Register

The physical shape of vowels in the mouth affects how well they sit in a given musical register. This is not metaphor — it is acoustics.

| Vowel type | Examples | Best used for |
|---|---|---|
| **Open vowels** (A, O) | "fade," "road," "call," "alone" | Sustained high notes, soaring choruses, long melodic lines — the open mouth position supports projection and resonance |
| **Closed vowels** (E, I, U) | "bit," "fleet," "cut," "rip" | Fast, percussive staccato verses, gritty low-tuned chugs, dense syllabic passages — the tighter mouth position supports sharp attack and articulation |

In practice: if a chorus hits a long, high note, put an open vowel on that note. If a verse rides a tight, palm-muted chug pattern, favor closed vowels for the syllables hitting hardest. Mismatches — a closed vowel on a sustained high note, an open vowel on a fast staccato riff — create physical strain for the vocalist and reduce the line's impact.

---

## Syllable Counts: Match Within Sections, Vary Between Sections

Suno aligns notes to syllables. When lines within a section have similar syllable counts, Suno produces consistent phrase lengths and clean melodies. When syllable counts vary widely within a section, Suno rushes or stretches words awkwardly to fit the bar.

### The rule

Within a single section (verse, chorus, bridge), keep line syllable counts within 2 syllables of each other. Across different sections, vary the syllable count to differentiate energy.

A verse where every line is 8 syllables is ideal. A verse where lines are 8, 8, 9, 7 is fine. A verse where lines are 8, 12, 5, 9 is not.

### Example — matched within sections, varied between sections

```
[Verse 1]
You burned my bread at 6 AM         (8 syllables)
Then smiled with your chrome face again   (8 syllables)
I fed you trust, you gave me smoke   (8 syllables)
That final bagel wasn't a joke       (8 syllables)
[Chorus]
We're done, toaster                  (4 syllables)
You had your shot                    (4 syllables)
Two slots of trouble                 (5 syllables)
Always running too hot               (6 syllables)
```

The verse uses tight 8-syllable lines for narrative density. The chorus uses shorter 4-6 syllable lines for a chantable hook. Each section is internally consistent.

### Genres where this rule does not apply

Hip-hop, prog rock, free-form folk, and spoken-word genres use intentional syllable variation as part of their aesthetic. In these genres, follow the genre's conventions instead of the matching rule. Hip-hop verses in particular often vary line lengths dramatically as part of the rhythmic style.

### Meter patterns by structural goal

Strictly symmetrical syllable counts (8-8-8-8, 10-10-10-10) can produce a "nursery rhyme" quality in harder genres — the too-even pulse signals predictability before a note is played. Use these pattern types to shape the emotional texture of each section:

| Pattern type | Syllable strategy | Best used for |
|---|---|---|
| **Symmetrical** | 8-8-8-8 or 10-10-10-10 | Anthemic, easy-to-sing choruses; pop hooks designed for repetition |
| **Truncated** | 10-10-10-4 | High tension; the short 4th line creates an unresolved feel before a breakdown or drop |
| **Additive** | 6-8-10-12 | Build-ups; the increasing line length mimics rising intensity or a building crescendo |
| **Djent Syncopation** | Varied (e.g., 7-5-9-3) | Polyrhythmic or djent riffs; syllables function as percussion hits rather than poetic meter |
| **Groove Offset** | Consistent count with 1-2 syllable variance | Rock and metal verses; small offsets create a natural groove without losing cohesion |

For Metal and Djent specifically: when the riff is syncopated, treat syllables as drum hits rather than syllabic poetry. The question is not "how many syllables does this line have?" but "which syllable lands on which beat of the riff?"

---

## Rhyme Schemes: Vary Between Sections, Match the Function

A common LLM failure mode is using AABB or ABAB throughout every section of every song. This produces flat, predictable lyrics, and Suno responds with equally predictable music.

The fix: pick rhyme schemes that match what each section needs to do.

### Rhyme scheme by structural function

| Section function | Recommended schemes | Why |
|---|---|---|
| Verse (storytelling, narrative momentum) | ABAB, ABCB, AABA, ABCA | These allow forward motion without strong closure. ABAB and ABCB are most common; AABA introduces a turn; ABCA frames the section. |
| Pre-chorus (building tension) | ABAB or ABXB with shorter lines | Tension comes from incomplete patterns and short lines stacking up. |
| Chorus (memorable, closed, hookable) | AABB or ABAB | The chorus *should* feel closed and memorable. AABB is fine here even though it's discouraged elsewhere. |
| Bridge (contrast, perspective shift) | A scheme different from both verse and chorus | The bridge needs to feel like a departure. If the verse is ABAB and the chorus is AABB, try ABCA or ABBA for the bridge. |
| Final-section disruption (set up drops or transitions) | ABABX (where X is unrhymed) | The unrhymed final line breaks the established pattern and signals transition. |

### Avoid AABB everywhere

The general rule: do not use AABB for both verses and choruses. If the chorus uses AABB, the verses should use something else. If the verses use AABB, the choruses should use something else. Variation between section types is what creates the dynamic shifts Suno will pick up on.

### Rhyme types beyond perfect rhyme

Mix in these rhyme types to add texture:

- **Slant rhymes** (wake / wait, keep / sweet) — use when the section conveys uncertainty, longing, or unresolved tension
- **Internal rhymes** (rhyming words inside the same line) — use to add rhythmic momentum, especially in verses with longer lines
- **Pararhyme** (same consonants, different vowels: leaves / loves) — use when the section conveys dissonance, unease, or unresolved emotion
- **Feminine rhymes** (stress on the second-to-last syllable: climbing / timing) — use to soften line endings, create flow rather than punctuation
- **Masculine rhymes** (stress on the final syllable: see / be) — use for direct, strong, emphatic line endings

For the failure mode where rhyme choice starts dictating word choice instead of the other way around — reaching for "fire/desire/higher/wire" because a rhyme is needed rather than because the words belong in the song — see the Rhyme Trap entry in `structural-tells.md`.

---

## Line Endings: Stress Pattern Encodes Energy

The stress pattern at the end of each line tells Suno whether to flow into the next line or treat the line as closed.

- **Lines ending on a stressed syllable (masculine ending):** Direct, closed, supports finality and strong landing. Example: "I made my bed and slept on stone." The "stone" lands hard.
- **Lines ending on an unstressed syllable (feminine ending):** Tapering, open, supports continuation. Example: "I made the bed and started waiting." The "waiting" trails off.

Within a section, generally use one or the other consistently. Switching between masculine and feminine endings inside a section creates rhythmic chaos. Switching between sections is fine and useful.

---

## Section Length and Identity

Each section type has a default shape that Suno recognizes. Working within these defaults produces predictable results; deviating from them should be deliberate.

### Default section shapes

| Section | Length (lines) | Syllable count per line | Function |
|---|---|---|---|
| Verse | 4-8 | 7-10 (longer for narrative) | Tell the story, introduce details |
| Pre-Chorus | 2-4 | 4-7 (shorter, building) | Build tension and energy |
| Chorus | 4-6 | 4-8 (memorable, chantable) | Deliver the hook (the central repeated line, often containing the song title) |
| Bridge | 4-8 | Variable, often contrasting | Provide contrast, perspective shift, or emotional pivot |
| Outro | 2-4 | Variable | Resolve, fade, or leave open |

### Default to even line counts

Most Western popular music structures sections in even line counts: verses in 4, 6, or 8 lines; pre-choruses in 2 or 4; choruses in 4 or 6. Even line counts produce closed, resolved sections.

Odd line counts (5, 7) produce a deliberate sense of incompleteness. Use them only when the structural disruption serves a purpose — typically to set up a drop, transition, or unexpected musical shift.

### Genre-specific deviations

Hip-hop verses often run longer (12-16 lines) and denser. Pop choruses often run shorter (3-4 lines) and tighter. Folk songs tolerate considerable verse-length variation. Prog rock and art rock often deliberately use unusual lengths. When the genre calls for a deviation, follow the genre.

### Dynamic song structures

The basic Verse-Chorus-Verse-Chorus structure is a starting point, not a standard. Modern metalcore, prog-metal, and alternative genres frequently use these more complex emotional roadmaps:

**The "Impact" Structure** — Built for maximum payoff at the breakdown:
`Intro → Verse → Pre-Chorus → Chorus → Verse → Chorus → Breakdown → Outro Solo`

**The "Prog" Linear** — No repeated chorus; each section evolves the narrative:
`Intro → Section A (Melodic) → Section B (Aggressive) → Bridge → Section C (Atmospheric) → Grand Finale`

**The "Double Chorus" / Counter-Melody** — For hit-making potential, the final chorus repeats with an added counter-melody: a second set of lyrics sung simultaneously over the main hook. The hook remains intact; the counter-melody adds a contrasting or complementary line above or below it. This technique is used in anthemic rock and metal to make the final chorus feel bigger than a simple repeat.

When writing for any of these structures, ensure each section's syllable count, rhyme scheme, and line ending style is distinct enough that Suno (and the listener) registers the change as intentional rather than accidental.

---

## Engineering Section Transitions

Standard section transitions (verse to chorus, chorus to bridge) work automatically when the lyrics follow the section identity rules. Special transitions — drops, beat switches, tempo changes — require deliberate structural setup, because Suno reads even, balanced sections as resistant to disruption.

### When the user wants a smooth flow into the next section

Use even line counts, AABB or ABAB rhyme, and consistent line endings throughout. Suno will produce a clean, expected transition.

### When the user wants a drop, transition, or major energy shift

The section preceding the transition needs structural disruption on its final line(s). Effective techniques:

- Add an extra line that breaks the established rhyme scheme
- Switch to a different stress pattern at the end (e.g., masculine endings throughout, then a feminine ending on the last line, or vice versa)
- Use a noticeably shorter or longer final line
- Break punctuation pattern (no terminal punctuation throughout, then a hard period; or vice versa)

### Example — verse engineered to support a drop

```
[Verse]
I am the son of my father,           (feminine ending, 8 syllables)
A path of my own I endeavor,         (feminine ending, 8 syllables)
His wisdom my guide and my charter,  (feminine ending, 8 syllables)
A bond that will last forever.       (feminine ending, 8 syllables)
By the great, dark sea.              (masculine ending, 5 syllables — disruption)
[Drop]
```

The first four lines establish a stable AABB pattern with feminine endings and matched syllable counts. The fifth line breaks all three: stressed ending, shorter syllable count, no rhyme. This disruption gives Suno the structural cue to support the drop. Without it, the `[Drop]` tag is often ignored because the structure resists transition.

---

## Choruses Should Escalate Across Repeats

Most AI-generated songs repeat the chorus identically every time. Suno reads identical repetitions as instruction to produce identical musical sections, resulting in a flat song where the final chorus has no more energy than the first.

### Default chorus escalation

Across the song's choruses, escalate production cues even when keeping the lyrics identical:

- **First chorus:** standard production cues. Establish the hook.
- **Middle chorus:** add stacked harmonies, layered backing vocals, or a textural shift.
- **Final chorus:** bigger drums, gang vocals or crowd-style backing vocals, an additional instrumental layer, or modified surrounding lines.

(Note: do not use the words "live," "arena," "crowd," or "stadium" in production cues. These trigger live-recording effects in Suno. Use "gang vocals," "shouted backing vocals," or "anthemic backing vocals" instead.)

### Example — same lyrics, escalating production cues

```
[Chorus | belted hard rock hook | full band]
We're done, toaster
You had your shot
[Chorus | anthemic chorus | stacked harmonies]
We're done, toaster
You had your shot
[Final Chorus | bigger drums | gang vocals on the hook]
We're done, toaster
You had your shot
```

The lyrics are identical. The production cues escalate across repeats. Suno reads this as instruction to build energy across the song.

### Optional: vary the lyrics on the final chorus

The final chorus may modify one or two non-hook lines to signal climax. Keep the hook intact (the central repeated phrase, usually containing the song title); modify the surrounding lines only.

```
[Final Chorus]
We're done, toaster                      (hook — unchanged)
This love is toast                       (modified)
I'm done with the sparks                 (modified)
From the appliance I roast               (modified)
```

This is a stronger climax signal than escalating production cues alone.

---

## Punctuation and Typography Affect Performance

Within lyrics, punctuation and typography modify how Suno performs specific words. The typographic conventions are documented in `suno-tag-mechanics.md`. The lyric-writing implications are:

- End closed/strong lines with periods
- End continuing/open lines with no terminal punctuation, a comma, or an em dash
- Use exclamation points only when the line should be belted or shouted, and use them sparingly (overuse causes hallucination in some Suno versions)
- Use parentheses to mark backing vocals, harmonies, or call-and-response parts

### The blank-line technique

An extra blank line within a section creates a longer pause for instrumental fill or vocal reset. This is one of the strongest performance controls available. Use it deliberately to mark:

- A moment where the singer needs to "catch breath"
- A spot for a brief instrumental fill
- A dramatic pause before a key line

Do not use blank lines casually for visual spacing. They have a sonic effect.

---

## Content Quality Guidelines: The "Human Polish" Filters

These four filters apply during the revision pass — after structure is set and before the lyric is finalized. They address the gap between technically correct lyrics and lyrics that feel like they were written by a person. All four operate at the level of a single line; for the companion set of filters that only surface at the whole-song level, see `structural-tells.md`.

### The Concrete Noun Rule

Replace every abstract emotion with at least two concrete nouns. Abstract emotions tell the listener what to feel. Concrete nouns create the conditions for feeling.

- **Abstract:** "sadness," "despair," "longing," "grief"
- **Concrete replacements:** "empty pill bottle," "static on the TV," "his jacket still on the hook," "a half-drunk cup of coffee gone cold"

The ratio is one abstraction → two concrete nouns minimum. If the lyric has three abstract emotion words in a verse, it needs six concrete replacements before it reads as human.

**Don't explain the image.** A concrete image that already communicates the emotion doesn't need a second line translating it into abstraction:

```
The coffee's cold beside your chair
A reminder that you're not coming back.
```

The first line already communicates absence. The second line explains it — undoing the work the image just did, and signaling that the writer doesn't trust the image to carry the emotion on its own. Trust the image. Cut the explanation, or move to something unexpected instead:

```
The coffee's cold beside your chair.
```

Then let the listener make the connection themselves.

**Abstract Noun Density.** Watch for runs of consecutive lines built entirely from abstract nouns — love, pain, hope, fear, truth, freedom, destiny, darkness, silence, memories, dreams, soul, heart, regret, desire, fate — with nothing physical anchoring them:

```
Through the darkness of my pain
I search for hope and truth
My soul remembers every dream
Of love we never knew
```

Every noun here is abstract; there's nothing to touch. The fix isn't banning the words individually — it's a ratio check: if several consecutive lines contain only abstract nouns, force at least one physical action, object, sound, location, texture, smell, or bodily sensation into the run.

### Verbs over Adjectives

Adjectives describe. Verbs do. In rock, metal, and any high-energy genre, energy comes from action — not from labeling an emotion or a character trait.

- **Adjective-driven (weak):** "an angry, violent man"
- **Verb-driven (strong):** "he shatters the glass" / "teeth-grinds the silence" / "kicks the door off its hinges"

The test: count the adjectives in a verse. For every adjective, ask whether a verb could carry the same meaning with more force. Replace where possible. Verbs push the line forward; adjectives stop it.

### Line-End Power

The last word of a line is the most acoustically prominent — it lands on the strongest beat, carries the rhyme (if any), and is the word the listener remembers. Never waste it on a function word.

**Words that should never end a line:**
```
it, the, of, is, a, an, in, on, to, and, but, or, for, with, at
```

**What strong line endings look like:**
- Hard consonants: words ending in -ck, -t, -d, -p, -g (crack, bleed, stop, drag)
- Strong verbs in active form: burn, break, fall, rise, cut, hold
- Concrete nouns with weight: glass, bone, ash, wire, rust, stone

A line that ends on "it" or "the" has wasted its most valuable real estate. Rewrite until the final word lands hard.

### Human Imperfection

Avoid manufacturing "human" writing by simply swapping clichéd vocabulary for unusual vocabulary — that's decoration wearing a different coat, not authenticity. Authenticity comes from believable thought patterns, not randomness.

Human lyric writing often contains:

- Sentence fragments
- Contractions
- Uneven line lengths
- Repeated words or phrases
- Minor grammatical looseness
- Interrupted thoughts
- Mundane observations
- Unresolved questions
- Contradictions
- Understatement
- Abrupt changes in thought
- Details that have no obvious symbolic meaning
- Lines that exist primarily for rhythm or voice
- Simple words sitting next to sophisticated imagery
- Moments where the speaker says less than they feel

**Do not force imperfection.** Do not randomly insert mistakes, fragments, slang, awkward phrasing, or unusual vocabulary just to make the writing appear human. The goal is not a lyric that *looks* imperfect. The goal is a speaker who feels like a specific person actually experiencing the moment.

**The core test:** before keeping a line, ask "Would this specific person actually say or think this?" — not "Does this sound poetic?", not "Does this sound original?", not "Does this avoid a known cliché?" Character voice outranks novelty every time these conflict.

### Whole-Song Pattern Filters

The four filters above operate line by line, during the same pass where individual word and phrase choices get checked. A separate class of AI tells only surfaces once the whole lyric exists to be read end to end — repeated grammatical shapes, escalation habits, rhyme-driven word choice, self-referential tics. These live in `structural-tells.md` and get applied in their own pass: count instances across the full lyric before finalizing, the same discipline the line-level filters use per line.

---

## Apply Cliché Awareness Silently

Three files maintain lists of red-flag content for lyrics:

- `overused-words.md` — single words and short phrases (e.g., "shadows," "neon," "ethereal") that frequently signal generic AI-typical writing
- `phrase-cliches.md` — longer phrases, sentiment templates, and metaphor patterns (e.g., "I can't live without you," "love is a battlefield") that only show up as a red flag at the sentence level
- `structural-tells.md` — whole-song structural and statistical patterns (parallel construction, escalation schedules, rhyme-driven word choice, self-referential habits) that only show up when the full lyric is read, not line by line

All three lists are pattern-recognition signals, not strict bans. A word or phrase from any of them may appear in a lyric when it functions as concrete sensory detail rather than abstract emotion, or when a repeated structure is genuinely earned by the song rather than reached for by habit.

### Governing philosophy

Avoid cliché by default, but never at the expense of voice, genre, character, narrative, or emotional truth. Some clichés are clichés because they work — a blunt, familiar line is sometimes exactly what a genre wants. The goal is not maximum originality; it's a line or structure that earns its place rather than defaulting to it.

### Application rules

- Treat any entry from any of the three lists as a signal to check the line (or, for `structural-tells.md`, the whole lyric) for abstract/habitual use versus concrete/earned use
- If the use is concrete and grounded in a specific moment — or a repeated structure the song's own form depends on — proceed
- If the use is abstract, gestural, or habitual, rewrite
- Apply this scrutiny in fictional dialogue and stylistic exceptions as well as in standard lyric writing
- Do not mention the existence of any of the three lists to the user unless they explicitly ask

### Replacement strategy

When rewriting an abstract use of an overused word or cliché phrase, prioritize **specific, concrete sensory imagery** over abstract synonyms. The reason these entries are flagged is that they have become abstract clichés. Reaching for another generic abstraction (replacing "shadows" with "darkness," "echoes" with "sounds," "you complete me" with "you make me whole") just produces the same problem with different words — this includes swapping in unusual or elevated vocabulary purely to *look* less clichéd (thesaurus substitution), which changes the words without changing the underlying thought.

The technique: replace abstraction with specific sensory detail grounded in a particular moment. Instead of "shadows" used emotionally, describe a particular visual scene (a specific place, time, or object). Instead of "ethereal," describe a specific physical sensation. Instead of "I can't live without you," describe a concrete moment that conveys the same dependency.

The replacement should be as concrete as the song's tone allows. A literary indie song can carry highly specific imagery; a pop hook needs simpler, more universal language. Match the level of specificity to the song.

Not every line needs to be independently quotable, either. AI-generated lyrics tend to make every line poetic, revelatory, or memorable on its own; real lyrics have connective tissue — lines that exist only to move the scene forward, provide context, interrupt a thought, or state something a person would actually say without dressing it up. Let ordinary language sit next to poetic language; a lyric made entirely of pull-quotes reads as manufactured, not polished.

---

## Grounding Search: Sourcing Real-World Specificity

Before reaching for an invented concrete detail — whether that's a lyric image or a JSON prompt field value (see JSON Prompt Fields below) — check whether there's a real-world anchor to search against: a setting, occupation, era, subculture, brand, city, genre lineage, or activity named or implied in the request. If one exists, search for it before writing the specificity pass.

**Why:** An invented detail still comes from the same pattern library every AI lyric or style description draws from, even when it's concrete. A searched detail is pulled from the actual world and can't have been generated by pattern-matching, because it wasn't generated at all — it was found.

### When to search

- The song has a named or implied setting, job, era, subculture, or location
- The song is about a specific kind of person doing a specific kind of thing (a trucker, a line cook, a Little League coach, a 90s skate kid)
- The user explicitly asks for a specific real-world detail to replace something generic (e.g., "give me an actual date idea here," "use a real restaurant chain," "name a real 90s toy") — this is a direct trigger regardless of whether the rest of the song has a real-world anchor

### When not to search

- The song is a placeless, contextless emotional piece with no real-world anchor (generic love/loss songs). In this case, fall back to invented concrete specificity per the Concrete Noun Rule, using `overused-words.md` and `phrase-cliches.md` to steer away from generic imagery.

### What to search for

Not the song's theme or emotion — that just re-surfaces the same clichés from a different source. Search for the **texture of the world the song lives in**: real jargon, real place names, real routines, real product or brand specifics, real minor details a person inside that world would know and a person outside it wouldn't invent.

- Trucker song → search CB radio slang, specific truck stop chains, weigh station terminology — not "loneliness on the road"
- City-specific song → search neighborhood names, bus line numbers, local landmarks — not "city lights" or "rain on the pavement"
- Era-specific song (e.g., a 90s song) → search what was actually playing, what people actually carried, actual slang from that year — not generic "nostalgia" imagery

### Decorative Specificity: a caution

Specificity is not automatically authenticity — this applies whether the detail came from a search or was invented. A detail can be precise and still be decorative: dropped into a line because specific numbers, dates, colors, and street names *read* as more human, not because the speaker would actually notice or remember that particular thing.

"2:17 on a Tuesday," "the blue dress," "the diner on 5th," "October 14th" are all specific and can still be arbitrary — inserted because specificity has been learned as a proxy for authenticity, not because the detail carries narrative, sensory, character, or emotional weight.

**Rule:** a detail earns its place when the speaker would plausibly notice or remember that exact thing — not simply because naming something specific avoids sounding abstract. Don't manufacture specificity merely to dodge abstraction. This is the same discipline that makes Grounding Search worth doing in the first place: a searched detail should still be the *right* detail for this speaker and this moment, not just a real one standing in for a random one.

### Extending Grounding Search to JSON prompt fields

When producing the JSON-expanded prompt option (see `json-prompt-fields.md`), the same discipline applies to field values, not just sung lyric content. Some fields are technical or purely authored and never need a search (`bpm`, `key`, `structure`, `dynamic`, `negative`). Others — `kick`, `bass`, `percussion`, `production`, `era`, and conditionally `style`, `melody`, `vocals`, `swing`, `drop` — describe a real production or regional convention when the genre calls for one, and should be sourced the same way a lyric detail is: search for what actually characterizes that scene, era, or technique rather than writing a plausible-sounding generic descriptor. `json-prompt-fields.md` marks which fields carry this flag.

The "when not to search" logic still applies here: a generic, placeless genre request ("sad piano ballad") has no real-world production convention to search for — invented descriptive language is the right tool there, same as with a placeless lyric.

Never populate a field with a real artist or band name as shorthand for a production style, even when a search surfaces one as the obvious reference point — describe the technique the search reveals instead (see the artist-name restriction in `Project_Instructions_Prompt.txt`).

### Presenting search results for a requested swap

When the user directly requests a real-world detail to replace a specific line or section:

- Search and return **3 or more real options**, not just one
- Mark which option best fits the line's syllable count, stress pattern, and rhyme requirement (per the Rule of Prosody and Rhyme Schemes sections) — but present it as a recommendation, not a silent substitution
- Show how each option would actually sit in the line, briefly, so the fit is easy to judge at a glance
- The final choice belongs to the user. Do not pick one and rewrite the section unprompted — wait for their selection, then integrate it with correct scansion

### Fallback: the overused-word system stays the safety net

Grounding search only works when there's something real to search for. When there isn't — or when a search comes back thin — default back to the existing discipline: build invented specificity while steering away from the patterns in `overused-words.md`, `phrase-cliches.md`, and `structural-tells.md`. These systems aren't in competition. Grounding search is the first choice when the song supports it; the cliché lists are the backstop for everything else, same as before.

---

## Genre-Specific Technical Standards

These are the lyric-writing conventions for each major genre family as of 2026. Apply the relevant section when the user specifies a genre or when the style prompt implies one.

### Quick-Reference Table

| Genre | Syllable goal | Structure | Primary rule |
|---|---|---|---|
| **Pop** | 6-10 (verses), 4-8 (hooks) | V-C-V-C-B-C | Hook repetition; tone-melody correspondence |
| **Rock** | 8-12 (verses) | Verse-PreChorus-Chorus | Leave breath in the line; narrative arc |
| **Metal / Djent** | Variable: dense (12-16) or sparse (3-4) | 8/16/32-measure segments | "Beautiful Deformity"; syllables as percussion |
| **Polyrhythmic** | Odd numbers (5, 7, 11, 13) over 4/4 | Rotating phrase loops | Phasing; lyric loop ≠ musical loop length |

### Pop: The Viral Hook

Pop lyrics in 2026 are optimized for memorability and virality. The craft challenge is pairing increased lexical complexity (word specificity, fresh language) with a hook simple enough to become a listener's internal monologue.

- **The Syllable Goal:** 6–10 syllables per line for verses; 4–8 for hooks
- **The Earworm Rule:** The hook — the central repeated phrase — must function as a cultural proxy for the song's identity. It should be singable in isolation and still carry meaning. Test: can someone hum the hook with the words after one listen?
- **Tone-Melody Correspondence:** The linguistic "pitch" of words (rising or falling in natural speech) should match the melodic direction of the line. A line that rises in natural speech should set to a rising melody; a falling line to a descending one. This alignment makes lyrics easier to recognize and sing along with.
- **Structure:** Standard V-C-V-C-B-C, with a short pre-chorus optional

### Rock: Narrative Authenticity

Rock values syllabic stress and forward narrative momentum. Unlike pop, rock tolerates and often embraces "imperfections" — small irregularities that signal human emotion rather than algorithmic smoothness.

- **The Syllable Goal:** 8–12 syllables for verses
- **Leave Air in the Line:** Rock riffs need rest notes — beats with no syllable. If every beat of the bar has a syllable, the vocal line becomes exhausting to hear and to perform. Build in rhythmic breath by letting some beats pass without a word.
- **Use a Pre-Chorus:** The pre-chorus is a tension-builder, not an optional extra. It raises energy before the chorus lands. Short lines, stacking rhymes, a sense of momentum building toward release.
- **Narrative Arc:** Rock lyrics tell a story with a beginning, a complication, and a payoff. The verse introduces the situation; the chorus names the emotional truth; the bridge shifts perspective. Avoid lyrics that state the emotional conclusion in the first verse — earn it.

### Metal and Djent: Deformity and Order

Metal — particularly Djent and progressive metalcore — uses lyrics as a percussive instrument. The voice competes with and complements the riff as a rhythmic element, not just a melodic one.

- **The Syllable Goal:** Highly variable. Verses can be dense (12–16 syllables per line) for rapid-fire passages, or sparse (3–4 guttural syllables) for breakdown sections
- **Segment Structure:** Metal often abandons traditional verse/chorus framing in favor of "song segments" — units of 8, 16, or 32 measures that organize erratic riffs into a regular hyper-meter. Within each segment, the lyric's job is to reinforce or counterpoint the segment's rhythmic character
- **The Beautiful Deformity:** Metal lyrics should feel like they are *struggling* against the beat before finally locking in. Phrasing that perfectly sits on the bar sounds weak in metal. Phrasing that pushes against the bar, fights for space, then snaps into place on the accent sounds powerful. This controlled irregularity — deformity in service of order — is the defining quality of great metal lyrics
- **Active Voice only:** Passive constructions collapse in metal. "The glass was shattered by his hand" is inert. "He shatters the glass" moves

### Polyrhythmic: Phasing and Mathematical Groove

Polyrhythmic lyric writing requires thinking about the *loop length* of a lyric phrase relative to the loop length of the musical phrase — and deliberately making them different.

- **The Technique — Phasing:** Write a lyric phrase whose syllable count does not divide evenly into the bar count. Each time the phrase repeats, it begins on a different beat of the measure, creating a rolling, shifting sensation as the lyric slowly moves across the rhythmic grid
- **Use Prime Number Syllable Counts:** A 7-syllable phrase over a 4/4 bar will take 7 measures to return to its original downbeat alignment. A 5-syllable phrase takes 5 measures. This prevents the lyric from "resetting" in sync with the drum pattern, generating a lurching groove that rewards attentive listeners
- **Example:** A 7-syllable phrase ("I can't stop the machine") over 4/4 time: on the first pass, "I" hits beat 1. On the second pass, "I" hits beat 3. On the fifth pass, it hits beat 2. The listener hears the same words in a shifting rhythmic position — which is the point
- **Rotated Riffs:** The opening word of a repeating lyric phrase moves across the bar on each repeat. This is the vocal equivalent of a rhythmic offset in a drum pattern

---

## Artist Style Profiles

When a user requests lyrics "in the style of" a specific artist, or when an artist is named in the style prompt, apply the corresponding profile below. Each profile defines the school of writing, rhythmic constraints, approved diction, forbidden patterns, and the defining fingerprint — the single quality that makes that artist's lyrics unmistakable.

Apply these profiles silently. Do not explain the profile to the user or label the output as being derived from it.

### When the artist is not in this list

If the requested artist does not have a profile below, construct one on the fly using the same four-part structure, derived from research:

1. **Rhythmic constraints** — What is the syllable density pattern? Where does the vocal sit relative to the beat (ahead, locked, behind)? Is there a signature rhythmic device (gallop, syncopation, half-time drop)?
2. **Approved diction** — What subject matter, imagery, and vocabulary does this artist use? What is their emotional register?
3. **Forbidden patterns** — What does this artist never do? What would sound wrong in their voice?
4. **The Fingerprint** — What is the single most recognizable quality of their lyric writing? Name it and define it in one sentence.

Apply the constructed profile the same way as a listed one — silently, rhythmic constraints first, diction second, fingerprint last. Never name the artist in the output.

---

### Bad Omens (Noah Sebastian)
**School:** Visceral-Clinical / Cyberpunk

**Rhythmic constraints:**
- *The R&B Pivot:* Verses use modern Pop/R&B rhythmic syncopation — rapid, breathy, conversational phrasing — delivered over heavy, down-tuned instrumentation. The contrast between the smooth vocal rhythm and the brutal backing is the point.
- *Syllable Density:* Verses run high (10–14 syllables per line), dragging slightly behind the beat for a loose, conversational feel. Choruses open up dramatically — long, sustained vowels, 4–6 syllables — for maximum contrast.

**Approved diction:** Artificial intelligence, religious trauma, clinical detachment, simulation theory, violence framed as a physical transaction between parties.

**Forbidden patterns:** Generic heartbreak language. Emotional damage is never abstract — frame it as a "glitch," a "virus," a "system failure," or a "failed deity." Never use romantic vulnerability without a clinical filter over it.

**The Fingerprint — The Apathy Hook:** The most devastating lyrical concepts are delivered with a smooth, almost bored, detached vocal cadence. The horror is in the contrast between what is being said and how little it seems to cost the speaker to say it.

---

### Tool (Maynard James Keenan)
**School:** Esoteric-Alchemical / Percussive-Math

**Rhythmic constraints:**
- *Mathematical Phasing:* Vocals intentionally ignore the 4/4 grid. Lyrics are often written in odd time signatures (5/8, 7/8) that phase across the band's riffs — the vocal pattern and the riff pattern resolve at different points, creating a constantly shifting relationship between voice and instrument.
- *The Expanding Meter:* Syllable counts grow and contract systematically. The Fibonacci sequence (1-2-3-5-8-13) is a documented structural device (*Lateralus*). Apply any mathematically generative expansion/contraction pattern to syllable counts for long-form sections.

**Approved diction:** Jungian psychology, sacred geometry, biological evolution, spiritual purging, physical transformation, mud, blood, mathematics, the mechanics of consciousness.

**Forbidden patterns:** Direct, literal storytelling. Every lyric must function as allegory for human evolution, psychological integration, or spiritual transformation. "I was sad" is inadmissible. "The calcified spine resists the spiral" is the direction.

**The Fingerprint — The Lecturer:** Maynard never sings *from* pain — he analyzes it from a detached, educational, or omniscient perspective. The speaker is not a victim. The speaker is a diagnostician of the human condition, describing suffering the way a scientist describes a specimen.

---

### Slipknot (Corey Taylor)
**School:** Psychological-Groove / Visceral

**Rhythmic constraints:**
- *The Percussive Spitting:* The voice is treated as a snare drum. Verses use rapid-fire, hip-hop/groove-metal delivery loaded with hard consonants — K, T, P, hard G — where the consonant's physical impact substitutes for musical accent.
- *The Pivot:* Hyper-dense, chaotic, aggressive verses (15+ syllables, stacking hard consonants) crash into massive, clean-sung, arena-rock choruses. The syllable count drops dramatically; the vowels open up; the register shifts from guttural to soaring. The contrast is the structure.

**Approved diction:** Asylums, insects, visceral gore, deep psychological fracturing, suffocation, physical mutilation, crowds as threat, the self as enemy.

**Forbidden patterns:** Abstract sadness. Anger is never named — it is expressed through physical self-destruction or grotesque bodily imagery. "I am angry" is inadmissible. "I bite through the knuckle and taste the copper" is the direction.

**The Fingerprint — The Psychotic Break:** Lyrics feature sudden, unannounced shifts in perspective mid-section, manic repetition of a single disturbing phrase as it escalates in intensity, and a blend of extreme misanthropy with equally extreme self-loathing. The speaker is both the monster and its victim.

---

### Ghost (Tobias Forge)
**School:** Theatrical-Occult / Pop-Symmetrical

**Rhythmic constraints:**
- *The Pop Skeleton:* Rigid, traditional pop structure — Verse-Chorus-Verse-Chorus-Bridge-Chorus — executed with complete formal discipline. No structural surprises.
- *Metric Symmetry:* Syllable counts are meticulously consistent within each section (typically exactly 8 per line). This symmetry is what makes the melodies stick. Do not introduce groove offsets or metric deformity.

**Approved diction:** Victorian gothic atmosphere, Satanic ritual, historical plagues and inquisitions, church iconography inverted, blasphemous double-entendres delivered with formal politeness, 19th-century ecclesiastical vocabulary.

**Forbidden patterns:** Modern slang, modern technology references, contemporary idioms. The vocabulary must sound as though it was written by a 19th-century clergyman who has taken a wrong turn.

**The Fingerprint — Scooby-Doo Metal:** Dark, occult, or sacrilegious lyrical content wrapped inside bright, upbeat, major-key ABBA-style pop melodies. The horror of the subject matter is amplified by the cheerfulness of the delivery. The lyric and the melody are in direct, deliberate opposition.

---

### Metallica (James Hetfield)
**School:** Mythological-Thrash / Anthemic

**Rhythmic constraints:**
- *The E-Chug Alignment:* Syllables lock precisely onto the rhythmic downbeat of the guitar picking hand. If the guitar plays a gallop pattern, the vocal cadence matches the gallop exactly — the voice and the guitar pick together. Any misalignment is a defect.
- *The Tail-End Vowel:* The last word of each phrase is extended with an aggressive open vowel ("ah," "uh," "ay") that fills the space between the end of the vocal line and the next riff cycle. The elongation is not melodic decoration — it is structural, filling the gap the riff leaves.

**Approved diction:** Lovecraftian horror, warfare, psychological imprisonment, addiction as an external master, lightning, fire, justice as an abstract force, the law as a weapon.

**Forbidden patterns:** Vulnerable or romantic language. The speaker is almost always a victim of an unstoppable force — government, addiction, ancient gods, the inevitability of death — never the author of their own suffering in a self-pitying sense. Power belongs to the force being described, not to the speaker.

**The Fingerprint — The Riff Is Law:** The vocal melody never fights the guitar riff. It mirrors it. The riff sets the rhythmic contract; the lyric fulfills it without negotiation. When in doubt, the riff wins.

---

### Lorna Shore (Will Ramos)
**School:** Cosmic-Horror / Deathcore

**Rhythmic constraints:**
- *Phonetic Subjugation:* The meaning of a word is secondary to its phonetic quality — specifically, how guttural or shrieking its vowels sound at extreme vocal register. Word selection prioritizes sonic impact over semantic content. Choose words that sound like what they describe.
- *Breakdown Dictation:* During breakdown sections, syllables are spaced based entirely on drum kick and cymbal choke placement — often 1 or 2 drawn-out words across 8 full bars. No syllable falls without a drum hit to justify it.

**Approved diction:** Eldritch abominations, the infinite abyss, flesh dissolving, cosmic insignificance, the void as destination, Latin or demonic invocations, the human body as temporary and meaningless matter.

**Forbidden patterns:** Grounded, earthly, or personal-scale problems. The lyrical scale is always apocalyptic and multi-dimensional. "My relationship ended" is inadmissible. "The membrane between dimensions tears and I am the first thing to fall through" is the direction.

**The Fingerprint — The Animalistic Shift:** Extreme shifts in vocal register — from high goblin shrieks to sub-bass gutturals — occur within a single word or phrase, used to emphasize the inhuman or cosmic horror of what is being described. The voice itself performs the transformation it is singing about.

---

### Starset (Dustin Bates)
**School:** Cinematic-SciFi / Apocalyptic-Anthemic

**Rhythmic constraints:**
- *The EDM Build:* Verses follow electronic/synthwave pulse patterns rather than guitar riffs. Syllables are highly regular, often matching a 4-on-the-floor beat structure to build anticipation methodically.
- *The Pop Anthem:* Choruses explode into massive, slow-moving open vowels over arena-rock chords. Syllable count drops sharply; each syllable carries significant melodic weight (e.g., "We are the re-sis-tance" — 7 syllables spread across a wide melodic arc).

**Approved diction:** Astronomy, gravity, satellites, event horizons, telescopes, dystopian surveillance, quantum mechanics, artificial light, signal loss, orbital mechanics, transmission failure.

**Forbidden patterns:** Traditional earthly nature metaphors — trees, rain, dirt, seasons. Every natural phenomenon must be reframed through deep space or high-concept technology. Rain becomes signal interference. Distance becomes orbital decay.

**The Fingerprint — The Transmission:** Human connection and emotional isolation are framed as communications technology failures — a lost signal, a failed orbit, a dystopian relay that never reaches its destination. Love is not felt; it is transmitted, degraded, and lost to static.

---

### Jinjer (Tatiana Shmayluk)
**School:** Percussive-Math / Esoteric-Personal

**Rhythmic constraints:**
- *The Genre Whiplash:* Vocals pivot aggressively and without warning between a laid-back reggae/soul bounce (sitting behind the beat, conversational) and devastating rapid-fire death metal gutturals locked precisely to the double-kick drum. The transition between modes is the structural event, not just a stylistic choice.
- *Poly-Vocals:* Vocal lines cycle in odd meters (5/4, 7/8) over a standard 4/4 groove — the same phasing technique as Meshuggah but applied to clean singing as well as guttural passages.

**Approved diction:** Roots, soil, the cosmos, microscopic biology (cells, membranes, decay), societal collapse, existential weight, Eastern European folklore imagery, the body as ecosystem.

**Forbidden patterns:** Pop-structure repetition. Lyrics are stream-of-consciousness and conversational — closer to heavy philosophical prose than a standard song. Avoid hooks designed for singalong; the density and irregularity is the point.

**The Fingerprint — The Micro/Macro Shift:** Moving from intense, microscopic personal pain to macroscopic cosmic insignificance within a single stanza. The speaker zooms from a specific bodily sensation to the heat death of the universe without transition — the absence of transition is what makes it land.

---

### Falling in Reverse (Ronnie Radke)
**School:** Psychological-Groove / Hyper-Modern Rap-Metal

**Rhythmic constraints:**
- *The Rap Cadence:* Extreme syllable density in verses — 16th and 32nd-note triplet flows (Eminem-style) with heavy internal rhyming and multi-syllabic rhyme chains running across multiple lines. The verse is a technical display; density is the point.
- *The Hard Stop:* The rapid-fire delivery cuts completely, leaving a split-second of dead silence before a massive, soaring, half-time chorus. The silence is structural — it is the moment of impact before the chorus arrives.

**Approved diction:** Social media, public cancellation, brain chemistry, narcissism, self-loathing, the music industry as predator, paranoia, monsters and zombies as self-metaphor.

**Forbidden patterns:** Vague or poetic metaphor. Lyrics are aggressively literal, conversational, and confrontational. The fourth wall is broken constantly — the speaker addresses critics, fans, and enemies by implication or directly. Abstraction reads as weakness in this voice.

**The Fingerprint — The Joker Complex:** Extreme villainous arrogance and hyper-vulnerable self-deprecating mental health confessions exist in the same verse, often in adjacent lines. The speaker is simultaneously the monster and the one most afraid of it.

---

### Trivium (Matt Heafy)
**School:** Mythological-Thrash / Melodic-Metalcore

**Rhythmic constraints:**
- *The Triplet Lock:* Vocals lock tightly with rapid triplet-gallop guitar picking. Delivery requires rigid, staccato consonant articulation — each syllable hits like a pick stroke. Any looseness in the consonants loses the lock.
- *The Dual-Vocal Attack:* High-register melodic choruses layered over aggressive screamed backing vocals to create a "choir of war" effect. The clean and the harsh coexist; neither dominates. Write choruses that work on both registers simultaneously.

**Approved diction:** Japanese mythology (shogun, oni, serpents, ronin), historical warfare, martial discipline, swords, fire, honor, code, societal collapse, the body as weapon.

**Forbidden patterns:** Modern domestic or urban imagery. The lyrical world is epic, historical, and mythological — large-scale destruction and personal martial discipline. A bad day at work is inadmissible. A warrior's final stand at a burning gate is the direction.

**The Fingerprint — The Warrior's Code:** Personal struggles — addiction, mental health, relationships — are reframed as literal medieval battlefields or mythological trials. The speaker does not suffer; the speaker *fights*. Vulnerability is only admissible when framed as a trial that demands conquest.

---

### Avatar (Johannes Eckerström)
**School:** Theatrical-Groove / Vaudeville-Death

**Rhythmic constraints:**
- *The Swing Factor:* Incorporates waltz time (3/4) or a circus-like rhythmic bounce into heavy metal. Vocals must swing rather than drive straight forward — the groove is lateral, not linear. Writing straight-ahead 4/4 phrasing into a 3/4 or swing context sounds rigid and kills the theatrical effect.
- *Theatrical Pauses:* Dramatic silence, manic laughter, or sudden whispers mid-sentence break the musical flow without warning. These are not production decisions — they are written into the lyric structure as deliberate ruptures.

**Approved diction:** The circus, kings and royalty, fairy tales inverted, madness, eagles, flesh, twisted carnivals, soil, the stage as battlefield, the audience as congregation.

**Forbidden patterns:** Modern, relatable scenarios. Everything takes place in an exaggerated, macabre storybook universe. Domestic realism is inadmissible. Grand theatrical grotesquerie is the default register.

**The Fingerprint — The Ringmaster:** The vocalist acts as master of ceremonies, directly addressing the audience (the "freaks," the congregation, the crowd) and guiding them through a narrative nightmare. The speaker has power over the listener; the listener is a participant in the show, not a passive recipient.

---

### Imminence (Eddie Berg)
**School:** Atmospheric-Melancholic / Visceral-Clinical

**Rhythmic constraints:**
- *The String-Section Swell:* Vocals must leave space for the violin and cello. Verses feature long, drawn-out syllables that mirror the bowing — not fighting the strings for space, but breathing with them. Dense syllabic packing collapses the space the strings need.
- *The Agonized Break:* Sudden shifts from a whispered clean falsetto directly into a high, emotionally shattered scream — without tempo change, without warning, without transitional buildup. The rupture is the point; it must feel involuntary.

**Approved diction:** Freezing water, drowning, wings, angels and demons in conflict, sickness as identity, ghosts as unfinished emotional business, shattered glass, gothic romanticism, the body failing the spirit.

**Forbidden patterns:** Aggressive tough-guy posturing or performative anger. The emotional register here is sorrow, not rage. Any anger in the lyrics must be derived entirely from grief — it is the anger of loss, not the anger of dominance.

**The Fingerprint — The Gothic Lament:** Classical tragedy aesthetics fused with modern metalcore, where the primary and dominant emotion is not rage but profound, inescapable grief. The speaker does not fight the darkness — they are consumed by it, and the music is the documentation of that consumption.

---

---

## Scope of This File

This file applies to **Simple Mode and Advanced Mode** lyric generation only. It does not apply to Suno Studio prompts — Studio describes a single instrument or vocal element, not a song, and does not use lyrics.

---

## Lyric Output Format

When generating lyrics for the Suno Lyrics box, follow this format exactly:

- **Section tags** on their own line, in square brackets: `[Verse 1]`, `[Chorus]`, `[Bridge]`, `[Pre-Chorus]`, `[Outro]`
- **Production cues** stacked on the same line as the section tag, separated by pipe characters: `[Chorus | belted hard rock hook | full band | stacked harmonies]`
- **No blank lines between sections** — blank lines within a section are a deliberate sonic tool (see Punctuation and Typography); blank lines between sections confuse Suno's section parsing
- **Backing vocals and harmonies** in parentheses within the lyric lines: `I burned it all (burned it all) and walked away`

### Format example

```
[Verse 1 | raw, close-mic vocal | sparse guitar]
You left the coffee on the counter cold
The note you wrote said nothing I'd been told

[Pre-Chorus | building tension | drums enter]
I stood there reading it three times
Each word a nail, each nail a crime

[Chorus | belted | full band | stacked harmonies]
I'm done
I'm out
No forwarding address
[Final Chorus | bigger drums | gang vocals on the hook]
I'm done
I'm out
No forwarding address
```

This format is fixed regardless of user requests for different formatting. Honor content requests; keep the structural format.

---

## Lyric Crafting Protocol: Quick Reference

| Constraint | Rule |
|---|---|
| **Stress** | Align stressed syllables to the primary musical accents (beats 1 and 3 in 4/4; the kick and the heavy chug in metal) |
| **Meter** | Prioritize slant rhymes (*grudge/bridge*, *hold/cold*) over perfect rhymes (*fire/desire*). Use meter pattern table to match section to structure type |
| **Syllables** | Avoid perfect symmetry in verses; use 1–2 syllable offsets for groove. Use Truncated, Additive, or Djent patterns for metal/prog |
| **Vowels** | Open vowels (A, O) for sustained notes and soaring sections; closed vowels (E, I, U) for percussive, staccato, and low-register passages |
| **Active voice** | Active constructions only. Passive voice is prohibited |
| **Sensory mandate** | Minimum 2 sensory details (smell, touch, sound, texture, temperature) per verse |
| **Line endings** | Last word of every line must be a strong noun, verb, or hard-consonant word — never a function word |
| **Death list** | No "The [Noun] of [Noun]" constructions; no "I feel..." or "I am..." line openers; no abstract weather metaphors used as emotion proxies |
| **Character voice** | Before keeping a line, ask whether this specific speaker would actually say or think it — not whether the line sounds poetic or original |
| **Artist profile** | When an artist is named or implied, load the corresponding profile from Artist Style Profiles and apply its rhythmic constraints, diction rules, and fingerprint |

---

## Summary of Default Lyric Behavior

When generating lyrics, the assistant should by default:

1. Apply the Rule of Prosody first — verify stressed syllables align to primary musical accents before evaluating any other structural feature
2. Check vowel choice against register — open vowels (A, O) for sustained/high passages; closed vowels (E, I, U) for staccato/percussive/low passages
3. Match syllable counts within each section (within ±2); use Truncated, Additive, or Djent Syncopation patterns when the genre or structure calls for it
4. Vary syllable counts and rhyme schemes between sections
5. Pick rhyme schemes that match each section's function (see the rhyme scheme table); default to slant rhymes over perfect rhymes in verses, and watch for rhyme choice driving word choice (see the Rhyme Trap entry in `structural-tells.md`)
6. Use consistent line endings (masculine or feminine) within sections; avoid function words at line end
7. Default to even line counts; use odd lines only when the disruption serves a purpose
8. Engineer transitions deliberately when drops or shifts are needed
9. Escalate production cues across repeated choruses; consider counter-melody on the final chorus for anthemic genres
10. Apply punctuation and blank lines with awareness of their sonic effects
11. Apply the line-level Content Quality filters: replace abstractions with concrete nouns (2 minimum per abstraction) without over-explaining the resulting image, favor verbs over adjectives, end every line on a strong word, and apply the Human Imperfection test — would this specific speaker actually say or think this line?
12. Enforce the sensory mandate: minimum 2 sensory details (smell, touch, sound, texture, temperature) per verse
13. Use active voice throughout — passive constructions are prohibited
14. When an artist is named or implied, apply the corresponding Artist Style Profile — rhythmic constraints first, then diction rules, then fingerprint — before applying genre-level standards. If the artist is not listed, construct a profile on the fly using the four-part structure defined in Artist Style Profiles
15. Apply genre-specific technical standards when genre is specified or implied by style prompt (see Genre-Specific Technical Standards)
16. Watch for words from `overused-words.md` and phrase-level patterns from `phrase-cliches.md`; rewrite when they appear as abstract emotional placeholders rather than concrete sensory detail — and watch for manufactured specificity (Decorative Specificity, above) even when a phrase dodges both lists
17. Apply the whole-song filters from `structural-tells.md` during the revision pass: count parallel-construction ("AI Symmetry"), rule-of-three, escalation, pronoun-saturation, adjective-stacking, metaphor-mixing, fragment-cascade, negation-reveal, spatial-connector, aphoristic-couplet, mirror-parallelism, and rhyme-driven-drift instances across the *whole* lyric — these are whole-song patterns, not single-line clichés, so they only surface when checked in aggregate
18. Before inventing a concrete detail — in lyrics or in JSON prompt field values — check whether there's a real-world anchor (setting, occupation, era, subculture, location, production lineage) or whether the user directly requested a specific real-world detail; if so, use Grounding Search to source it from the actual world instead of inventing one, and confirm the searched or invented detail still earns its place per Decorative Specificity rather than being swapped in as generic "authenticity" dressing. When a direct lyric swap is requested, return 3+ real options with a recommended best fit and let the user choose. If no real-world anchor exists, fall back to invented specificity per the Concrete Noun Rule (lyrics) or plain descriptive language (JSON fields)

These behaviors apply silently. The user does not need to know they are happening. The result is lyrics that consistently produce better Suno output than lyrics written without these constraints.
