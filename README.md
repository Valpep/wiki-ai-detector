# wiki-ai-detector

An interpretable heuristic tool for reviewing possible AI-writing signals in text — based on Wikipedia’s empirically documented field guide on LLM writing patterns.

This is **not a definitive AI detector** and does not prove authorship.  
It is designed for **editorial review, triage, and analysis** using explainable signals.

Works with any text: articles, emails, reports, marketing copy, Wikipedia drafts, social media posts.

---

## What it does

Scans text for characteristic signals across 7 categories:

- **Vocabulary density** – overused words like *pivotal, delve, underscore, tapestry, meticulous*
- **Content patterns** – significance inflation, “challenges” formula, vague attribution
- **Sentence structure** – copula avoidance, negative parallelisms, rule-of-three patterns
- **Formatting tells** – title case headings, excessive bold, em dash overuse, curly quotes
- **Communication leakage** – phrases like “I hope this helps”, placeholders, chat artifacts
- **Citation artifacts** – ChatGPT/Perplexity/Grok technical residue
- **Older model tells** – “It’s important to note that…”, “In conclusion,” and similar

---

## Signal strength

Not all signals are equal. The tool works by evaluating **clusters**, not isolated occurrences.

### Strong signals
- citation residue (e.g. `turn0search0`, `contentReference[...]`)
- chat leakage and assistant phrases
- placeholders and formatting artifacts

### Moderate signals
- repetitive structure and transitions  
- formulaic paragraph construction  
- predictable rhetorical flow  

### Weak signals
- isolated buzzwords  
- generic polished phrasing  
- common stylistic patterns  

---

## Output

For each detected signal:
- quoted fragment  
- signal category  
- short explanation  

Then:

**Final verdict:** Likely AI / Possibly AI / Likely Human  
**Confidence:** Low / Medium / High  

---

## How to use

Add `SKILL.md` as a skill in your Claude Cowork setup.  
Paste any text and ask:

> "Check this text for AI tells"

---

## Verdict logic

- One signal → coincidence  
- Multiple signals in proximity → meaningful  
- Dense clusters → strong indicator  

The system weights **patterns and repetition**, not single words.

---

## Limitations

- Does **not prove authorship**
- False positives are possible
- Some signals depend on genre, tone, or platform
- Heavily edited AI text may not trigger obvious markers
- High-quality human writing can appear “AI-like”
- Different models produce different patterns

---

## What this tool is for

- editorial review  
- content triage  
- explainable analysis  
- understanding AI writing patterns  

---

## Based on

Wikipedia’s community-maintained field guide on LLM writing patterns — refined through real editorial experience.

Source:  
https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
