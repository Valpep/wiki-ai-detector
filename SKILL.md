---
name: wikipedia-not-ai
description: "Detect AI-generated text by identifying characteristic patterns, phrases, and structural tells from LLMs like ChatGPT, Gemini, and others. Use when the user wants to check if a text was written by AI, audit content for AI tells, clean up AI-generated writing to make it less detectable, understand what makes text sound AI-generated, or review emails, articles, reports, marketing copy, or any prose for AI markers."
---

# AI Text Detection Guide

Derived from Wikipedia's empirically documented field guide on LLM writing patterns. Applicable to any text — not just Wikipedia.

## How to analyze text

Scan for signals across the categories below. Weight **clusters** more heavily than isolated occurrences — one "pivotal" is coincidence; five AI-vocab words in a paragraph is a strong signal.

**Output format:** Quote specific examples from the text, categorize each signal, then give an overall verdict: **Likely AI / Possibly AI / Likely Human** with brief reasoning.

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

---

## 3. Sentence Structure Tells

### Copula avoidance
Replaces simple "is/are/has" with elaborate constructions:
- ❌ *"serves as the primary hub"* → ✅ "is the primary hub"
- ❌ *"marks a significant milestone"* → ✅ "was a significant milestone"
- ❌ *"boasts four separate spaces"* → ✅ "has four separate spaces"

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

## 7. Older Model Tells (2022–2024)

Less common in newer models, useful for auditing older content:
- *"It's important to note that..."*, *"It's crucial to remember..."*
- *"In summary," "In conclusion," "Overall,"* ending sections
- *"As an AI language model, I..."* partial refusals
- Text cut off abruptly mid-sentence

---

## False Positives — Do NOT flag these alone

- Perfect grammar
- Formal or academic prose style in general
- Transition words (*Additionally, Furthermore*) in isolation
- Unsourced claims
- Long, detailed, thorough writing
- Letter-like formatting with salutations

---

## Reference

- **[word-lists.md](references/word-lists.md)** — Complete AI vocabulary lists by model era for systematic scanning
