# vale-ai-guard

A [Vale](https://vale.sh) package that catches AI-generated prose patterns and enforces clear, direct writing. It flags the hedging, filler, passive voice, and corporate jargon that AI assistants lean on, so your docs read like a human wrote them.

If you use AI to help write documentation, blog posts, or technical content, the output often *looks* fine but carries telltale patterns. Vague quantities instead of specifics. Nominalizations where verbs belong. Escape clauses that dodge commitment. ai-guard catches these automatically during your writing workflow.

Pairs well with [`vale-ai-tells`](https://github.com/tbhb/vale-ai-tells), which catches vocabulary fingerprints and rhetorical formulas. ai-guard focuses on structural and stylistic problems (readability, sentence length, passive voice, weasel words) that ai-tells does not cover.

## Installation

Add the package to your `.vale.ini`:

```ini
StylesPath = styles
MinAlertLevel = suggestion

Packages = https://github.com/pfaciana/vale-ai-guard/releases/latest/download/ai-guard.zip

[*.md]
BasedOnStyles = ai-guard
```

Then run:

```bash
vale sync
```

## What it catches

ai-guard ships 32 rules across a few categories:

**AI prose habits.** The patterns that make AI-assisted writing feel generic. Em-dash overuse, hedging (`it's worth noting`), filler phrases that add no information, escape clauses that avoid committing to an answer, and formulaic conclusions.

**Clarity and readability.** Passive voice, nominalizations (using `utilization` when you mean `use`), copula constructions, sentence length, and readability scores (Gunning-Fog and Flesch-Kincaid). These keep prose direct and accessible.

**Precision.** Vague quantities (`many users`, `significant improvement`) that need actual numbers, weasel words, and jargon that obscures meaning.

**Mechanical quality.** Oxford commas, heading punctuation, spacing, hyphenation, quote types, and heading density. No 500-word walls of text under a single heading.

## Customization

Disable rules that do not fit your style:

```ini
[*.md]
BasedOnStyles = ai-guard
ai-guard.Contractions = NO
ai-guard.OxfordComma = NO
```

Change severity levels:

```ini
[*.md]
BasedOnStyles = ai-guard
ai-guard.PassiveVoice = suggestion
```
