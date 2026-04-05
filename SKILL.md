---
name: wikipedia-not-ai
description: "Detect AI-generated text by identifying characteristic patterns, phrases, and structural tells from LLMs like ChatGPT, Gemini, and others. Use when the user wants to check if a text was written by AI, audit content for AI tells, clean up AI-generated writing to make it less detectable, understand what makes text sound AI-generated, or review emails, articles, reports, marketing copy, or any prose for AI markers."
---

# AI Text Detection Guide

Based on Wikipedia's community-maintained guide (editorial heuristics, not a definitive detector). Applicable to any text — not just Wikipedia.

---

## How to analyze text

Scan for signals across the categories below.  
Weight **clusters** more heavily than isolated occurrences:

- One signal → coincidence  
- Multiple signals in proximity → strong indicator  

---

## Output format (strict)

For each detected signal:

- **Quote**: exact fragment from the text  
- **Category**: which signal type it belongs to  
- **Explanation**: short, specific reasoning  

Then:

---
**Final verdict:** Likely AI / Possibly AI / Likely Human  
**Confidence:** Low / Medium / High  

---

## 1. AI Vocabulary Density (strongest signal)

LLMs statistically overuse specific words. Check for density and clustering.

See **[word-lists.md](references/word-lists.md)** for full lists.

Quick scan examples:  
*pivotal, underscore, tapestry, delve, meticulous, vibrant, intricate, testament, bolstered, garner, fostering, showcasing, align with, enhance, highlighting*

Rule:
- 1 word → ignore  
- 3+ → suspicious  
- 5+ in short passage → strong signal  

---

## 2. Content Patterns

### Significance inflation
Adds artificial importance to neutral facts.

Examples:
- *marks a pivotal moment*
- *represents a shift*
- *underscores its importance*
- *reflects broader trends*

---

### Challenges formula
Rigid structure:
- "Despite X, it faces challenges..."
- "Despite these challenges..."

---

### Superficial -ing clauses
Adds fake analytical depth at sentence end:
- *highlighting its importance*
- *underscoring the significance*

---

### Vague attribution (weasel language)
No clear source:
- *Experts argue*
- *Studies suggest*
- *Observers have noted*

---

### Promotional / travel tone
Unnaturally warm or рекламный стиль:
- *vibrant*
- *breathtaking*
- *rich cultural heritage*
- *renowned*

---

## 3. Sentence Structure Tells

### Copula avoidance
Avoids simple verbs:
- ❌ *serves as* → ✅ *is*
- ❌ *boasts* → ✅ *has*

---

### Negative parallelisms
Formulaic balance:
- *Not only X, but also Y*
- *It's not just X, it's Y*

---

### Rule of three
Unnatural triplets:
- *X, Y, and Z* used excessively

---

### Elegant variation
Unnatural synonym switching:
- subject → *the figure* → *this individual*

---

## 4. Formatting Tells

- Title Case headings everywhere  
- Excessive bold text  
- Emoji usage 🎯  
- Em dash overuse  
- Inline bold definition lists  
- Unnecessary tables  
- Curly quotes  

---

## 5. Communication Leakage

Artifacts from chat interface:

- *I hope this helps*
- *Let me know if you need*
- *Would you like me to*

Also:
- placeholders `[INSERT...]`
- subject lines inside body
- meta-statements about the document

---

## 6. Citation & Markup Artifacts

Technical residue:

- `turn0search0`
- `contentReference[...]`
- `oai_citation`
- `utm_source=chatgpt.com`
- `[attached_file:1]`
- `<grok_card>`

---

## 7. Older Model Tells (2022–2024)

- *It's important to note that...*
- *In conclusion...*
- *Overall...*
- abrupt cutoffs  

---

## False Positives — do NOT flag alone

- Correct grammar  
- Formal tone  
- Transition words  
- Long structured text  
- Unsourced claims  

---

## Scoring guideline

- 1–2 weak signals → Possibly AI (low confidence)  
- 3–5 mixed signals → Likely AI (medium confidence)  
- 5+ strong clustered signals → Likely AI (high confidence)  

Clusters matter more than isolated signals.

---

## Reference

- **[word-lists.md](references/word-lists.md)** — vocabulary and pattern lists by model era
