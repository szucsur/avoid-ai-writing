# Subtitle Translator Skill

A Claude Code skill for translating subtitle files using AI. Uses Claude Code as orchestrator and Codex CLI (`codex`, model `gpt-5.6-sol`) as the translation engine.

## Why Claude Code + Codex CLI?

Codex's `gpt-5.6-sol` is excellent at translation — natural, fluent, and context-aware. Claude is excellent at agentic workflows — orchestrating multi-step processes, managing files, and running verification checks. This skill combines the best of both: Claude manages the workflow while Codex does the actual translation.

## Why?

Streaming platform subtitle translations are often terrible. This skill produces natural, context-aware translations by building a glossary first, then translating with that context, and running consistency checks afterward.

Supports all subtitle formats (SRT, ASS, SSA, VTT, SUB, SBV) and all languages.

Output is always written in the target language's own characters — full diacritics
and native script, never an ASCII-folded approximation (`Türkçe`, not `Turkce`).

## How It Works

1. **Glossary Creation** — Codex reads all subtitle files and builds a translation glossary with character names, recurring terms, and tone guidelines
2. **Glossary Review** — You review and correct the glossary before translation begins
3. **Translation** — Each file is sent to Codex one by one with the glossary for context-aware translation
4. **Verification** — Block counts, timecodes, formatting tags, and native-character usage are checked
5. **Consistency Check** — All translations are reviewed together for cross-episode consistency
6. **Technical Check** (optional) — Line length, line count, and other platform-specific rules

## Prerequisites

1. Install [Claude Code](https://docs.anthropic.com/en/docs/claude-code) and [Codex CLI](https://developers.openai.com/codex/cli) (`codex` command)
2. Run each one once and complete the login/authentication process

## Installation

Give this repo's URL to Claude Code and tell it to install the skill:

```
Install this skill: https://github.com/saidsurucu/subtitle-translator-skill
```

## Usage

1. Put your subtitle files in a folder
2. Open Claude Code in that folder
3. Tell Claude Code to translate your subtitles — the skill activates automatically

Claude Code will ask you for:
- Target language
- Show/movie details (title, genre, characters, tone)
- Timecode mode (preserve or retimed)
- Song lyrics preference (translate or keep original)

## License

MIT
