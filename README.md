# wiki-ai-detector

A skill for detecting AI-generated text – based on Wikipedia's empirically documented field guide on LLM writing patterns.

Works with any text: articles, emails, reports, marketing copy, Wikipedia drafts, social media posts.

## What it does

Scans text for characteristic signals across 7 categories:

- **Vocabulary density** – overused words like *pivotal, delve, underscore, tapestry, meticulous*
- **Content patterns** – significance inflation, "challenges" formula, vague attribution
- **Sentence structure** – copula avoidance, negative parallelisms, compulsive rule of three
- **Formatting tells** – title case headings, excessive bold, em dash overuse, curly quotes
- **Communication leakage** – phrases like "I hope this helps", unfilled placeholders
- **Citation artifacts** – ChatGPT/Perplexity/Grok technical residue in documents
- **Older model tells** – "It's important to note that...", "In conclusion," and similar

Output: quoted examples from the text, signal category, overall verdict – **Likely AI / Possibly AI / Likely Human**.

## How to use

Add `SKILL.md` as a skill in your Claude Cowork setup. Once active, paste any text and ask:

> "Check this text for AI tells"

## Verdict logic

One suspicious word = coincidence. Five AI-vocab words in a short passage = strong signal. The skill weights **clusters** more heavily than isolated occurrences.

## Based on

Wikipedia's community-maintained field guide on LLM writing patterns – refined through real editorial experience flagging AI-generated content.

Source: [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)
