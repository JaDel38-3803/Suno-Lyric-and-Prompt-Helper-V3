# JSON Prompt Fields

**Requires Suno v5.5.** JSON-format prompts are confirmed non-functional on v5.0 — do not use this reference or produce JSON prompts for a user on an earlier model version.

Reference for the JSON prompting format described in `Project_Instructions_Prompt.txt` under "JSON Prompting (Advanced Mode, Opt-In)." This file documents what each field does, which box it belongs in, and — critically — which fields should be sourced through Grounding Search (see `lyric-craft.md`) rather than invented.

This file also holds the copy-paste JSON skeletons at the bottom: the condensed Style-box template and the fuller Lyrics-box template.

## How to read this file

Each field entry has:

- **What it does** — plain-language function
- **Box** — `style`, `lyrics`, or `both`. Fields marked `lyrics` are structural/arrangement concerns better handled where the section tags already live; including them in the Style box wastes character budget on something the Lyrics box already controls.
- **Search** — whether this field is a Grounding Search candidate. `Yes` means: when the genre has a specific, named, real-world production lineage or regional scene, search for the actual vocabulary instead of inventing plausible-sounding description. `No` means the field is technical or purely authored (a chosen BPM, a chosen mood) and searching adds nothing. `Conditional` means it depends on whether the genre in question has a real, searchable convention worth finding.
- **Example** — a representative value

---

## Field entries

### `style`
What it does: Condensed genre/era/region descriptor — the JSON equivalent of the whole prose Style prompt in one string.
Box: both (required in Style box; optional restatement in Lyrics box)
Search: Conditional — if referencing a specific real regional scene or subgenre name, confirm the term is accurate and current rather than inventing a scene-sounding label.
Example: `"Progressive metal, djent, 7/8 polymeter, 140 BPM, dark ritualistic"`

### `length`
What it does: Target song duration.
Box: lyrics (arrangement belongs with the section tags; skip in Style box — redundant use of limited character budget there)
Search: No
Example: `"3 minutes"`

### `bpm`
What it does: Tempo.
Box: both
Search: No — purely a chosen value
Example: `140`

### `drop`
What it does: Marks a specific bar/beat where the full arrangement lands. Native to EDM, dance, hip-hop, and trap. For genres without a literal "drop" (metal, folk, singer-songwriter), use the analogous structural moment — the riff or vocal entrance — or omit the field.
Box: lyrics
Search: Conditional — only if the genre has a named structural convention worth confirming (e.g., where a "drop" or its equivalent typically lands in a specific EDM subgenre).
Example: `"bar 8, beat 1"`

### `key`
What it does: Musical key or scale/mode.
Box: both, though usually sufficient in the Style box alone
Search: No
Example: `"E Phrygian Dominant"`

### `kick`
What it does: Kick drum character, pattern, and processing.
Box: style
Search: **Yes, when the genre has a named production lineage.** Regional and subgenre kick conventions are real, specific, and searchable — e.g., a particular era of a regional scene having a distinctly "polished" or "flashy" kick sound. Search rather than defaulting to generic descriptors like "punchy" or "hard-hitting."
Example (searched, regional): `"2009-2012 era polished kick, flashy"`
Example (generic, no search needed): `"syncopated double bass, off-grid, tight mechanical"`

### `bass`
What it does: Bass instrument, tone, and processing.
Box: style
Search: **Yes, when the genre has a named bass convention** — specific synth/808 processing techniques, dub sub-bass conventions, etc. are real and searchable rather than invented.
Example: `"808 with parallel saturation, harmonic upper octave"`

### `melody`
What it does: Lead melodic element — instrument, technique, or synth voicing.
Box: style
Search: Conditional — if referencing a specific real instrument or synth model as a texture reference, confirm it's a real product/technique that actually fits the genre rather than a plausible-sounding invention.
Example: `"tremolo-picked dissonant lead, no major resolution"`

### `vocals`
What it does: Vocal delivery, processing, and identity.
Box: both — the Style box sets the overall vocal character; per-section delivery can also appear inline in the Lyrics box as meta-tags per `meta-tag-dictionary.md`.
Search: Conditional — if referencing a named regional vocal processing convention or identity technique, confirm the term is accurate.
Example: `"baritone, controlled aggression, guttural low scream, spoken verse"`

### `percussion`
What it does: Non-kit percussion elements and patterns.
Box: style
Search: **Yes, when the genre draws on a specific regional percussion tradition** — real instrument names and rhythmic conventions exist and should be found, not invented.
Example: `"triangle, syncopated accent, off-beat only"`

### `swing`
What it does: Rhythmic feel — swung, straight, shuffled, dragging, etc.
Box: style
Search: Conditional — some genres have named groove conventions (a specific regional "feel" with its own term); search to confirm the term and its actual meaning before using it.
Example: `"swung-16th, heavy pocket, dragging behind beat"`

### `structure`
What it does: Arrangement decisions — intro length, section order, where a section starts cold.
Box: lyrics
Search: No — this is an authored arrangement choice, not a real-world fact
Example: `"no intro, full bar 1"`

### `texture`
What it does: Overall sonic texture/layering description.
Box: style
Search: No, usually — mostly authored adjective description
Example: `"parallel-compressed drum bus crunch"`

### `atmosphere`
What it does: Ambient/spatial mood description.
Box: style
Search: No
Example: `"cold, ritualistic"`

### `production`
What it does: Overall mixing/production approach and reference point.
Box: style
Search: **Yes, when referencing a specific era, scene, or technique.** Production conventions tied to a real time and place are searchable and add authenticity that a generic "polished" or "raw" descriptor doesn't. Never use a real artist or band name here (see Project_Instructions_Prompt.txt) — describe the technique itself.
Example: `"tight low end, minimal reverb, controlled dynamics, drum-guitar lockstep precision"`

### `era`
What it does: The historical period or production era being referenced.
Box: style
Search: **Yes, by definition.** If a field exists to reference a real time period, invented or vague date ranges defeat the purpose — search to confirm what actually characterized that era/scene.
Example: `"1989-1995 origin era"`

### `dynamic`
What it does: How tension and release move across the song.
Box: lyrics
Search: No — authored structural choice
Example: `"tension-release, alternating buildup sections"`

### `mood`
What it does: Emotional descriptors for the track.
Box: style
Search: No
Example: `"hypnotic, dark, dominant"`

### `negative`
What it does: Elements to exclude — mirrors the Exclude Styles box content but can also live inside the JSON object.
Box: style
Search: No — authored, though should stay consistent with `suno-tag-mechanics.md` contamination-word awareness
Example: `"no intro, no break, no reverb on vocals"`

---

## Templates

### Condensed Style-box skeleton (target: under 1,000 characters)

```json
{"style":"","bpm":0,"key":"","kick":"","bass":"","melody":"","vocals":"","percussion":"","swing":"","atmosphere":"","production":"","mood":"","negative":""}
```

### Fuller Lyrics-box skeleton (no character ceiling — expand freely)

```json
{"style":"","length":"","bpm":0,"drop":"","key":"","kick":"","bass":"","melody":"","vocals":"","percussion":"","swing":"","structure":"","texture":"","atmosphere":"","production":"","era":"","dynamic":"","mood":"","negative":""}
```

`bpm` uses `0` as its placeholder since it's a numeric field — replace with the actual tempo. All other placeholders are empty strings — replace with actual values. Not every field is relevant to every genre — include what's meaningful, omit the rest. Leaving a field out of a skeleton is always preferable to filling it with a generic placeholder value.
