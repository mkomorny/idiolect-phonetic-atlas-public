# Idiolect & Phonetic Atlas

> **Tri-Platform Agent Skill** for Claude Desktop / Code, Grok CLI, and Google Antigravity / Gemini.  
> Wells 24 Lexical Sets, VOT in ms, Rhoticity Percentage — Generates exhaustive, forensic-grade Idiolect & Phonetic Atlas reports cataloging a speaker's private phoneme system, Wells 24 lexical sets, allophonic rules, VOT, rhoticity %, and minimal pairs.

---

## Overview

`idiolect-phonetic-atlas` provides standardized capabilities across conversational AI platforms:
- Comprehensive Wells 24 lexical set phonetic realization mapping.
- Voice Onset Time (VOT) specifications in milliseconds for voiced and voiceless stops.
- Quantitative rhoticity percentage, th-stopping rate, yod-dropping, and l-vocalization.
- Allophonic conditioning rules and idiosyncratic lexical pronunciations.
- Standardized idiolect_phonetic_atlas.json schema for voice cloning.
- Tri-platform NTFS junctions connecting Claude, Grok, and Antigravity.
- Standard documentation suite: SKILL.md, HOW_TO_USE.txt, IMPLEMENTATION_PLAN.md, and README.md.

---

## Tri-Platform Architecture

Zero duplicate code across platforms. Canonical source resides in `.agents`:
- **Canonical Source**: `C:\Users\<you>\.agents\skills\idiolect-phonetic-atlas`
- **Claude**: `C:\Users\<you>\.claude\skills\idiolect-phonetic-atlas` (NTFS Junction)
- **Grok**: `C:\Users\<you>\.grok\skills\idiolect-phonetic-atlas` (NTFS Junction)
- **Antigravity**: `C:\Users\<you>\.gemini\config\skills\idiolect-phonetic-atlas` (NTFS Junction)

---

## Documentation Suite

- [`HOW_TO_USE.txt`](HOW_TO_USE.txt): Standardized user guide and prompt templates.
- [`IMPLEMENTATION_PLAN.md`](IMPLEMENTATION_PLAN.md): Feature checklist and roadmap.
- [`App Changes Tracker.html`](App%20Changes%20Tracker.html): Interactive visual version log.
- [`SKILL.md`](SKILL.md): Agent system instructions and triggers.
