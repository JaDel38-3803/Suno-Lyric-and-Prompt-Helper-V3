# Suno Lyric Helper

A prompting system for [Suno AI](https://suno.com) that turns a rough idea into a production-ready Style prompt, Exclude Styles prompt, and (on request) full Lyrics-box content — built for musicians who write and produce their own tracks with Suno rather than casual one-off generations.

It's not a prompt library. There's no list of pre-written prompts to browse. Instead, it's a set of reference files that teach an LLM the *reasoning* behind good Suno prompts — genre mechanics, lyric-writing craft, and the specific ways Suno's models respond to structure — so the assistant builds a prompt from scratch for whatever you're actually trying to make, and can defend or adjust any part of it on request.

## What's in this repo

| File | What it covers |
|---|---|
| `Project_Instructions_Prompt.txt` | The master instructions. Defines the assistant's role, mode detection (Simple / Advanced / Studio), output format, and when to pull from each of the files below. **This is the system prompt / custom instructions field** — everything else is a knowledge file it references. |
| `suno-tag-mechanics.md` | Primary reference. Suno's modes, the hybrid tag+prose prompt format, contamination words (words that silently break your prompt, like `live` or `acoustic`), bracket vs. parenthesis syntax, and Exclude Styles strategy. |
| `lyric-craft.md` | Lyric-writing craft: prosody, syllable/rhyme mechanics, section structure, content-quality filters, Grounding Search (using real-world research instead of generic detail), genre-specific technical standards, and a set of artist style profiles. |
| `json-prompt-fields.md` | Field-by-field reference for Suno's JSON-format prompting (v5.5+), including which fields benefit from research vs. which are purely authored values. |
| `meta-tag-dictionary.md` | Specialty bracket tags for the Lyrics box (`[crescendo]`, `[Guitar Solo]`, `[modulation]`, etc.) beyond the basic section tags. |
| `overused-words.md` | Single words that read as generic AI lyric writing (pattern-recognition list, not a hard ban). |
| `phrase-cliches.md` | Longer clichéd phrases and sentence-level patterns to avoid by default (heartbreak, pain, time, generic metaphor, grandeur, sentence openers). |
| `structural-tells.md` | Whole-song statistical AI tells — patterns only visible once a complete lyric is read end to end (parallel construction, escalation schedules, rhyme-driven word choice, self-referential tics). |

## How to use these files

The short version: **one file goes in the system/custom-instructions field, the rest go in the model's file/knowledge attachment.** Every platform below supports some version of this split. Exact menu names change often — if something's moved, search the platform's help docs for "custom instructions" or "knowledge files."

### Claude (claude.ai)

1. Create a **Project** (sidebar → Projects → New project).
2. Open **Project settings** → paste the full contents of `Project_Instructions_Prompt.txt` into the **Project instructions** field.
3. Upload the remaining seven `.md` files to the Project's **Knowledge** section.
4. Start any chat inside that Project — the assistant will ask which Suno mode you're in and go from there.

### ChatGPT

1. Go to **Explore GPTs → Create a GPT** (or use an existing Custom GPT).
2. In the **Configure** tab, paste `Project_Instructions_Prompt.txt` into the **Instructions** field.
3. Upload the remaining seven files under **Knowledge**.
4. Save and use the GPT normally.

If you'd rather not build a Custom GPT, ChatGPT **Projects** work too: set the project's custom instructions to the contents of `Project_Instructions_Prompt.txt` and upload the other files to the project's files.

### Gemini (Gemini Advanced / Gems)

1. Go to **Gems → New Gem**.
2. Paste `Project_Instructions_Prompt.txt` into the Gem's **Instructions** field.
3. Attach the remaining seven files as knowledge files for the Gem.
4. Save and start chatting with the Gem.

Gemini's file-count and size limits per Gem are smaller than Claude's or ChatGPT's — if you hit a limit, the four highest-priority files to keep are `suno-tag-mechanics.md`, `lyric-craft.md`, `overused-words.md`, and `phrase-cliches.md`; `meta-tag-dictionary.md`, `json-prompt-fields.md`, and `structural-tells.md` matter most for Advanced Mode and lyric-heavy work specifically.

### Grok

1. Go to **Projects** (or **Custom Instructions**, depending on your account tier).
2. Paste `Project_Instructions_Prompt.txt` into the custom instructions field.
3. Upload the remaining seven files to the project's attached files.
4. Start a new conversation inside that project.

### General notes for any platform

- All eight files are plain Markdown/text — no special import step needed, any file-upload field that accepts `.md` or `.txt` works.
- If a platform doesn't support both an instructions field *and* file uploads, paste `Project_Instructions_Prompt.txt` in first, then paste the contents of the reference files directly into the same field or the first message of the conversation — this system doesn't require a specific storage mechanism, only that the assistant has access to all eight files' content at once.
- These files assume Suno v5.5 or later for the JSON prompting section. If you're prompting for an older Suno model, the assistant will stick to hybrid-prose prompts and skip JSON entirely — no changes needed on your end.
- Keep all eight files as a set. The reference files cross-link each other (e.g., `lyric-craft.md` points to `structural-tells.md` for the whole-song revision pass), and the instructions file assumes all seven are present.
