# wiki-ai-detector

An interpretable heuristic tool for reviewing possible AI-writing signals in text — based on Wikipedia's empirically documented field guide on LLM writing patterns, extended with deeper structural tells from recent observation of newer models.

This is not a definitive AI detector and does not prove authorship. It is designed for editorial review, triage, and analysis using explainable signals.

Works with any text: articles, emails, reports, marketing copy, Wikipedia drafts, social media posts.

## What it does

Scans text for characteristic signals across 12 categories:

- **Vocabulary density** — overused words like *pivotal, delve, underscore, tapestry, meticulous*
- **Content patterns** — significance inflation, "challenges" formula, vague attribution, "quietly" narratives, overgeneralization from few sources
- **Sentence structure** — copula avoidance, Latinate-over-Saxon preference, negative parallelisms, rule-of-three, elegant variation
- **Formatting tells** — title case headings, excessive bold, em dash overuse, curly quotes, markdown in non-markdown contexts
- **Communication leakage** — phrases like "I hope this helps", placeholders, chat artifacts
- **Citation & markup artifacts** — ChatGPT/Perplexity/Grok technical residue
- **Image & caption tells** — keyword-matched illustrations, inflated captions
- **Argumentative & discussion tells** — rhetorical anaphora, hallucinated references, refusal-to-concede patterns
- **Newer model evasion (2025+)** — what persists when models suppress classic tells
- **Older model tells** — *"It's important to note that…"*, *"In conclusion,"* and similar
- **Context-sensitive phrase restrictions** — phrases like *"genuinely"* or *"didn't see it coming"* used in contexts that don't earn the emotional weight
- **Deeper structural tells (Romero, 2025)** — abstraction trap, sensing without sensing, treadmill effect, subtext vacuum

## Signal strength

Not all signals are equal. The tool works by evaluating clusters, not isolated occurrences.

**Strong signals**
- citation residue (e.g. `turn0search0`, `contentReference[...]`)
- chat leakage and assistant phrases
- placeholders and formatting artifacts
- on modern models: deeper structural tells (Section 12) — abstraction without imagery, sensory descriptions that don't track reality, paragraphs that don't advance the argument, explicit explanation of every implication

**Moderate signals**
- repetitive structure and transitions
- formulaic paragraph construction
- predictable rhetorical flow
- Latinate-over-Saxon vocabulary preference
- structural uniformity (every paragraph the same shape)

**Weak signals**
- isolated buzzwords
- generic polished phrasing
- common stylistic patterns

## Output

For each detected signal:
- quoted fragment
- signal category
- short explanation

Then:
**Final verdict:** Likely AI / Possibly AI / Likely Human
**Confidence:** Low / Medium / High

## How to use

Add `SKILL.md` as a skill in your Claude Cowork setup. Paste any text and ask:

> "Check this text for AI tells"

## Verdict logic

- One signal → coincidence
- Multiple signals in proximity → meaningful
- Dense clusters → strong indicator

The system weights patterns and repetition, not single words.

## Limitations

- Does not prove authorship
- False positives are possible
- Some signals depend on genre, tone, or platform
- Heavily edited AI text may not trigger obvious markers
- High-quality human writing can appear "AI-like"
- Different models produce different patterns
- Newer models (GPT-5.1+, Claude 4+) actively suppress known tells; rely on Section 12 (deeper structural tells) when classic markers are absent

## What this tool is for

- editorial review
- content triage
- explainable analysis
- understanding AI writing patterns

## Based on

- Wikipedia's community-maintained field guide on LLM writing patterns — refined through real editorial experience.
  Source: https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
- Alberto Romero, "10 Signs of AI Writing That 99% of People Miss" (Medium, December 2025) — basis for Section 12 (deeper structural tells)
