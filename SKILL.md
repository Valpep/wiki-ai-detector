---
name: wikipedia-not-ai
description: "Detect AI-generated text by identifying characteristic patterns, phrases, and structural tells from LLMs like ChatGPT, Gemini, and others. Use when the user wants to check if a text was written by AI, audit content for AI tells, clean up AI-generated writing to make it less detectable, understand what makes text sound AI-generated, or review emails, articles, reports, marketing copy, or any prose for AI markers."
---

# AI Text Detection Guide

Derived from Wikipedia's empirically documented field guide on LLM writing patterns. Applicable to any text — not just Wikipedia.

## How to analyze text

Scan for signals across the categories below. Weight **clusters** more heavily than isolated occurrences — one "pivotal" is coincidence; five AI-vocab words in a paragraph is a strong signal.

**Output format:** Quote specific examples from the text, categorize each signal, then give an overall verdict: **Likely AI / Possibly AI / Likely Human** with brief reasoning.

**Important:** Newer models (GPT-5.1+, Claude 4+) actively suppress known tells like em dashes and classic AI vocabulary. Absence of classic markers is NOT proof of human origin. Look for subtler patterns: overly cautious hedging, Latinate word preference, "quietly" narratives, structural uniformity, and the four deeper tells in Section 12 (abstraction trap, sensing without sensing, treadmill effect, subtext vacuum) — these are the most reliable signals on modern models.

---

## 1. AI Vocabulary Density (strongest signal)

LLMs statistically overuse specific words. Check for density/clusters.

See **[word-lists.md](references/word-lists.md)** for the complete list by model era.

Quick scan: *pivotal, underscore, tapestry, delve, meticulous, vibrant, intricate, testament, bolstered, garner, fostering, showcasing, align with, enhance, highlighting*

One word = coincidence. Five+ in a short passage = strong AI signal.

---

## 2. Content Patterns

### Significance inflation
Adds statements about how mundane facts "represent a shift," "mark a pivotal moment," or "contribute to the broader landscape" — even for population data or etymology.

Trigger phrases: *stands as, serves as, marks a pivotal, underscores its importance, reflects broader, symbolizing its enduring, setting the stage for, indelible mark, deeply rooted, evolving landscape*

### Challenges formula
Rigid structure, usually at the end: *"Despite its [positive adjective], [subject] faces challenges including... Despite these challenges, [vague optimism about the future]."*

### Superficial -ing clauses
Tacks present participle phrases onto sentences as pseudo-analysis:
*"...highlighting its importance," "...underscoring the significance," "...reflecting the broader trend."*

### Vague attribution weaseling
Attributes claims to no one specific: *"Experts argue," "Observers have noted," "Industry reports suggest," "Several sources indicate," "Some critics argue."*

### Promotional/travel-guide tone
Warm, advertisement-like prose even on neutral topics: *nestled, vibrant, rich cultural heritage, breathtaking, diverse array, boasts, showcasing, groundbreaking, renowned, in the heart of.*

### Overgeneralization from few sources
LLMs take information from 1–2 sources but present it as widely held or as an incomplete list. Watch for: *"including..."* or *"such as..."* when the enumeration actually covers everything the sources say; opinions from a single source framed as consensus; *"widely regarded," "generally considered"* without evidence of breadth.

### "Quietly" narratives
LLMs often describe actions or developments as happening *"quietly"* — a pseudo-narrative detail that adds false drama or modesty. Rare in factual human writing, common across multiple LLM families.

---

## 3. Sentence Structure Tells

### Copula avoidance
Replaces simple "is/are/has" with elaborate constructions:
- ❌ *"serves as the primary hub"* → ✅ "is the primary hub"
- ❌ *"marks a significant milestone"* → ✅ "was a significant milestone"
- ❌ *"boasts four separate spaces"* → ✅ "has four separate spaces"

### Latinate over Saxon
Systematically chooses Latin/Greek-derived words over simpler Germanic equivalents, even in plain contexts:
- ❌ *"utilize"* → ✅ "use"
- ❌ *"facilitate"* → ✅ "help"
- ❌ *"is devoid of"* → ✅ "has no"
- ❌ *"commence"* → ✅ "start/begin"
- ❌ *"ameliorate"* → ✅ "improve"
- ❌ *"expedite"* → ✅ "speed up"

This is distinct from copula avoidance — it's about lexical register, not syntax. As Orwell noted, bad writers are "haunted by the notion that Latin or Greek words are grander than Saxon ones." LLMs embody this tendency statistically.

### Negative parallelisms
Pseudo-balance: *"Not only X, but also Y"*, *"It's not just X, it's Y"*, *"Not X — it's Y."* Sounds thoughtful but is formulaic.

### Rule of three
Compulsive tripling: "adjective, adjective, and adjective" or "phrase, phrase, and phrase" even when two or four would be more natural.

### Elegant variation
Avoids repeating a word by substituting awkward synonyms throughout: subject → "the eponymous figure" → "the key player" → "this individual."

---

## 4. Formatting Tells

- **Title Case In Every Section Heading** (humans normally use sentence case)
- **Excessive boldface** — bolding key takeaways scattered throughout body text
- **Inline-header lists**: `• **Bold Term**: description text` pattern
- **Emoji** in headings or bullet points 🎯
- **Em dash overuse** — used dramatically — where a comma or parenthesis would do — often multiple times per paragraph
- **Unnecessary tables** for 2–3 data points that should just be prose
- **Curly quotes** (" " ' ') instead of straight quotes (" ') — common in ChatGPT/DeepSeek
- **Markdown in non-markdown contexts** — `**bold**`, `# Header`, `- list item` with dashes appearing in documents, emails, wiki markup, or any context where markdown is not the native format. Wikipedia added an edit filter specifically for this. Strong signal when combined with other tells.

---

## 5. Communication Leakage

Text meant for the AI chat interface that got pasted into the document:
- *"I hope this helps," "Would you like me to...", "Let me know if you need anything else"*
- Knowledge-cutoff disclaimers: *"as of my last update," "not widely documented," "maintains a low profile"*
- Unfilled placeholders: `[INSERT NAME HERE]`, `[Describe the specific section]`
- Subject lines in body text: *"Subject: Request for Edit"*
- Submission statements: *"This article meets WP:RS because..."*

---

## 6. Citation & Markup Artifacts (documents/web content)

Technical residue from specific AI tools:
- `turn0search0`, `turn0search1` — ChatGPT search citation artifacts
- `contentReference[oaicite:0]{index=0}` — ChatGPT reference rendering bug
- `oai_citation`, `+1` inline — ChatGPT markup bugs
- `{"attribution":{"attributableIndex":"X-Y"}}` — ChatGPT JSON attribution
- `utm_source=chatgpt.com` or `utm_source=openai` in URLs
- `[attached_file:1]`, `[web:1]` — Perplexity artifacts
- `<grok_card ...>` — Grok artifacts
- Invalid/unresolvable DOIs or ISBNs with correct-looking formats
- Book citations with no page numbers

---

## 7. Image & Caption Tells

LLMs select illustrations by keyword-matching file names or titles, not by actual visual relevance:
- Generic images loosely related to the topic but not to the specific content (e.g., a 19th-century painting of a waiter for a modern hospitality article)
- Captions that inflate a trivial detail from the image metadata: *"1946, marking an important year in..."* — significance inflation applied to image dates
- Multiple images that all illustrate the same general concept rather than different aspects of the text

---

## 8. Argumentative & Discussion Tells

When LLMs generate persuasive, argumentative, or discussion text (not just articles):
- **Rhetorical anaphora** — repeating sentence openers for emphasis in contexts where it's inappropriate (e.g., formal discussions, business emails)
- **Needless length** — walls of text that reiterate the same points in slightly different wording
- **Hallucinated references** — citing policies, rules, or frameworks that don't exist or don't apply (*"As per WP:UNDERREP..."*, *"According to industry standard 4.2.1..."*)
- **Context-alien terminology** — injecting jargon from unrelated domains (e.g., DEI language in a technical discussion, therapeutic language in a business context)
- **Refusal to concede** — in multi-turn text, progressively longer and more aggressive responses that add no new substance
- **That's-not-this-it's-that pattern** — frequent reframing: *"This isn't about X, it's about Y"*, *"The real issue isn't X — it's Y"*

---

## 9. Newer Model Evasion (2025+)

AI companies actively suppress known tells. Be aware:
- GPT-5.1 specifically reduces em dash usage
- Newer models use fewer classic AI-vocab words (see word-lists.md GPT-5 era section)
- Some models now mimic "imperfect" human patterns — occasional sentence fragments, contractions, informal tone
- **What persists:** structural uniformity (every paragraph roughly the same length/shape), Latinate vocabulary preference, overgeneralization, significance inflation in subtler forms, and the absence of genuine authorial quirks (idiosyncratic metaphors, personal references, domain-specific humor)
- **Key principle:** If a text has zero classic tells but also zero personality — uniform paragraph lengths, no surprises, no rough edges — that itself is a signal worth noting

---

## 10. Older Model Tells (2022–2024)

Less common in newer models, useful for auditing older content:
- *"It's important to note that..."*, *"It's crucial to remember..."*
- *"In summary," "In conclusion," "Overall,"* ending sections
- *"As an AI language model, I..."* partial refusals
- Text cut off abruptly mid-sentence

---

## 11. Context-Sensitive Phrase Restrictions

Certain phrases sound human in isolation but become AI tells when used in the wrong context. Flag these when the context doesn't justify the emotional weight.

### "and I didn't see it coming" / "I never saw it coming"
Legitimate only in: life-threatening situations, unexpected personal turning points, major life discoveries.
❌ Avoid in: software reviews, product descriptions, workflow descriptions, business writing.
Example of misuse: *"That combination changed how I work — and I didn't see it coming."* (software review)
Example of correct use: *"The diagnosis came back positive. I didn't see it coming."*

### "and what I didn't expect" / "what I didn't expect was"
Same rule as above. Reserve for genuine surprise in high-stakes personal or life contexts.
❌ Avoid in: tool reviews, feature descriptions, onboarding narratives, professional writing.
When in doubt: replace with a plain statement of the fact itself. *"I now manage most of it through Claude"* is stronger than *"what I didn't expect: I now manage most of it through Claude."*

### "genuinely"
Legitimate only in: references to authentic brands, original authorship, pure emotional states, sincere personal convictions.
❌ Avoid as a general intensifier in: product reviews, performance claims, workflow descriptions.
Example of misuse: *"genuinely changed how I work"* (software review — use the plain verb instead)
Example of correct use: *"This is genuinely his work, not a ghostwriter's."* / *"I genuinely don't know what to do."*

**General rule:** If a phrase adds emotional weight that the context hasn't earned, it's a tell. Software does not merit the same language as a near-death experience.

---

## 12. Deeper Structural Tells (Romero, 2025)

These four patterns operate below the level of vocabulary and syntax. They survive when a model is prompted to "avoid AI-isms" because they reflect the model's underlying nature, not its surface lexicon. Especially useful for auditing newer models (GPT-5+, Claude 4+) that have learned to suppress classic tells.

### Abstraction trap (disembodied vocabulary)
LLMs reach for abstract conceptual words instead of concrete, tangible ones — because they have read everything but experienced nothing. The text is *unimaginable* in the literal sense: you cannot form a mental image from it.

Markers:
- Heavy use of *comprehensive, foundational, nuanced, landscape, framework, dimension, dynamic, ecosystem, paradigm*
- Explanations stay at the level of categories rather than examples. *"This affects multiple aspects of digestive health"* instead of *"after lunch you stop feeling sleepy by 3 PM."*
- The reader cannot picture anything specific — no burnt socks, no sticky web, no dull knife

Test: read a paragraph, close your eyes, and ask "what do I see?" If the answer is "nothing — just concepts," it is likely AI.

Russian/Ukrainian markers: *комплексный, фундаментальный, многоаспектный, экосистема, парадигма, измерение, динамика процесса, ландшафт, поле, пространство (в переносном значении)*. Same effect: the abstract noun replaces the concrete image.

### Sensing without sensing (sensory failure)
LLMs string together sensory descriptions that are statistically plausible but physically wrong — because they know about touch, smell, and sound without ever having a body in a room.

Classic example: AI describes spider silk as "smooth" because "silk" co-occurs with "smooth" in training data (processed textiles). Anyone who walked into a real web knows it is sticky and elastic.

Markers in health/nutrition/science writing:
- Tastes and textures described by category rather than experience: *"a pleasant earthy flavor"* instead of *"like beetroot if you scraped off the dirt and didn't quite finish"*
- Physical processes described without weight or friction: *"the supplement supports the body"* with no sense of what supporting feels like
- Sensory claims that contradict ordinary experience but sound right by association

Test: would someone who has actually done the thing recognize the description? If the language tracks word-associations rather than embodied reality, it is AI.

### Treadmill effect (no displacement)
The text moves a lot but goes nowhere. Each paragraph rephrases the previous one without advancing the argument. The rate of new information per paragraph is near zero.

This is structural, not lexical — the words are different in each paragraph, but the *idea-content* is the same. It happens because LLMs are autoregressive: they know the next word from the latest word, but they do not know the last word. There is no destination conditioning the path.

Markers:
- After paragraph 3, you find yourself asking "where is this going?"
- Cutting any single middle paragraph would not change the meaning
- Restatements with synonyms instead of new evidence: *"In other words..." "To put it differently..." "What this means is..."*
- The conclusion does not feel earned by the body — it could have been written without reading the middle

Test: try to write a one-sentence thesis the text is arguing toward. If you can't, the text doesn't have one.

### Subtext vacuum (no trust in the reader)
AI explicitly explains every implication, joke, and emotional beat. It does not leave gaps for the reader to close, because it lacks a working theory of mind for "the reader" — ambiguity reads to the model as a hallucination risk to avoid.

Markers:
- Following a vivid statement with its own explanation: *"He looked at the door, feeling a strong desire to leave the room"* instead of just *"He looked at the door"*
- Spelling out what every example demonstrates: *"This shows that..." "The point here is..." "What this illustrates is..."*
- Jokes followed by their own punchline being explained
- Studies or anecdotes followed by a sentence stating the moral that the study/anecdote already made obvious

Test: cross out every sentence that explains what the previous sentence already showed. If the text gets significantly shorter and stronger, it was AI.

In Russian/Ukrainian popular science this is one of the strongest tells — a confident author trusts the reader to draw the conclusion. *«Учёные обнаружили X. Это означает, что нам стоит делать Y»* — the second sentence is often the AI tell. Good writing leaves Y as the reader's discovery.

---

## False Positives — Do NOT flag these alone

- Perfect grammar
- Formal or academic prose style in general
- Transition words (*Additionally, Furthermore*) in isolation
- Unsourced claims
- Long, detailed, thorough writing
- Letter-like formatting with salutations
- Rule of three used sparingly and appropriately (common human technique since antiquity)
- Em dashes in writers who habitually use them (check other samples if available)

---

## Reference

- **[word-lists.md](references/word-lists.md)** — Complete AI vocabulary lists by model era for systematic scanning
