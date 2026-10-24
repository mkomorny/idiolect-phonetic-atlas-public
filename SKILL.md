---
name: idiolect-phonetic-atlas
description: Generates exhaustive, forensic-grade Idiolect & Phonetic Atlas reports cataloging a speaker's private phoneme system, Wells 24 lexical sets, allophonic rules, VOT in ms, rhoticity %, th-stopping rate, yod-dropping, word-level pronunciations, and minimal pairs for voice cloning and synthesis. Trigger with 'create phonetic atlas for', 'idiolect atlas of', 'map phoneme system for', or '/idiolect-atlas'.
---

# Idiolect & Phonetic Atlas

## Purpose & Scope

This skill documents and formalizes the speaker's **private phonemic and allophonic realization system**. It moves beyond broad dialect labels (e.g., "NYC accent" or "Southern drawl") to capture the exact phonetic rules, formant targets, voice onset times, consonant clusters, and idiosyncratic lexical pronunciations that distinguish two speakers of the same dialect and pitch baseline.

This skill owns:
- Precise acoustic realization of all 24 Wells standard lexical sets
- Quantitative Voice Onset Time (VOT in ms) per stop category
- Allophonic conditioning rules (flapping, glottalization, nasalization, l-darkening)
- Sociolinguistic variables: rhoticity percentage, th-stopping, yod-dropping, short-a split
- Speaker-specific idiosyncratic word pronunciation dictionary
- Critical minimal-pair discrimination inventory for synthesis validation

This skill does **not** own fundamental frequency intonation curves (owned by `prosodic-grammar-intonation-os`) or speech timing and pauses (owned by `temporal-pause-breath-architecture`).

---

## Activation Triggers

Activate automatically when:
- User asks for a phonetic breakdown, idiolect profile, or phonemic atlas (e.g., *"create phonetic atlas for [speaker]"*, *"idiolect of [character]"*).
- User triggers `/idiolect-atlas [subject]`.
- Voice cloning or neural TTS prompts require exact phonetic spelling, IPA substitution rules, or pronunciation dictionaries.
- User requests analysis of regional accent realization, allophonic shifts, or consonant/vowel mechanics.

---

## Mandatory Report Schema & Structure

Every generated profile MUST follow this comprehensive 6-section format:

### 1. Wells Lexical Sets & Vowel Realization Targets
Detail exact steady-state formant targets (F1, F2, F3 in Hz), duration (ms), and IPA realization for all 24 sets:
- **Short Vowels:** KIT (/ɪ/), DRESS (/ɛ/), TRAP (/æ/), LOT (/ɒ/), STRUT (/ʌ/), FOOT (/ʊ/)
- **Long Vowels & Diphthongs:** FLEECE (/iː/), PALM (/ɑː/), THOUGHT (/ɔː/), GOOSE (/uː/), FACE (/eɪ/), GOAT (/oʊ/), PRICE (/aɪ/), CHOICE (/ɔɪ/), MOUTH (/aʊ/)
- **R-Colored & Marginal Vowels:** NURSE (/ɜːr/), NEAR (/ɪər/), SQUARE (/ɛər/), START (/ɑːr/), NORTH (/ɔːr/), FORCE (/oʊr/), CURE (/ʊər/), BATH (/æ/ vs /ɑː/), CLOTH (/ɒ/ vs /ɔː/)

### 2. Allophonic Realizations & Phonological Processes
- **T/D Dynamics:** Flapping frequency [ɾ] in intervocalic contexts vs. glottal replacement [ʔ] vs. aspirated alveolar retention [tʰ].
- **L-Vocalization & Darkening:** Degree of velarization [ɫ] in onset vs. coda; F2 frequency lowering metrics in Hz.
- **Vowel Nasalization:** Pre-nasal vowel raising, nasal coupling bandwidth expansion, and velopharyngeal timing.
- **Consonant Cluster Reduction:** Final consonant cluster reduction rates (e.g., /st/ -> [s], /nd/ -> [n]) in casual vs. monitored registers.

### 3. Consonant Dynamics & Voice Onset Time (VOT)
- **Voiceless Stops (/p, t, k/):** Mean VOT in ms, aspiration noise spectral peak (kHz), burst release energy (dB).
- **Voiced Stops (/b, d, g/):** Negative VOT (pre-voicing) occurrence %, closure duration in ms, voicing lead stability.
- **Fricatives & Sibilance:** Spectral center of gravity (CoG in kHz) for /s/ and /ʃ/, peak frequency, dynamic range.

### 4. Sociolinguistic & Dialectal Variables
- **Rhoticity Index (%):** Coda /r/ retention rate across word-final, pre-consonantal, and linking environments.
- **TH-Stopping & Fronting:** Frequency of [t, d] stopping for /θ, ð/; fronting to [f, v] occurrence rate.
- **Yod-Dropping:** Retention or deletion of /j/ after coronals (/t, d, n, s/) in words like *tune, due, news, suit*.
- **Short-A Split Dynamics:** Distribution of tense [eə] vs. lax [æ] according to phonetic environment (nasals, voiceless fricatives, stops).

### 5. Idiosyncratic Word Lexicon
A curated table of specific lexical items exhibiting unique, non-standard, or highly personal phonemic choices (e.g., *huge*, *coffee*, *water*, *neither*, *route*, *names*).

### 6. Minimal Pair Discrimination Inventory
List of phonemic minimal pairs that the synthesizer MUST distinctly contrast without accidental merger (e.g., *cot* vs. *caught*, *pin* vs. *pen*, *Mary* vs. *marry* vs. *merry*, *lather* vs. *ladder*).

---

## Machine Output Block

Every profile must conclude with a standardized JSON block:

```json
{
  "$schema": "https://json-schemas.voice/idiolect-atlas.v1.json",
  "speaker_id": "SPEAKER_ID",
  "vowel_targets": {
    "KIT": {"ipa": "ɪ", "f1_hz": 410, "f2_hz": 1820, "f3_hz": 2550, "dur_ms": 78},
    "DRESS": {"ipa": "ɛ", "f1_hz": 560, "f2_hz": 1720, "f3_hz": 2510, "dur_ms": 88},
    "TRAP": {"ipa": "æ", "f1_hz": 690, "f2_hz": 1610, "f3_hz": 2480, "dur_ms": 115},
    "THOUGHT": {"ipa": "ɔːə", "f1_hz": 580, "f2_hz": 910, "f3_hz": 2350, "dur_ms": 165},
    "GOAT": {"ipa": "oʊ", "f1_hz": 490, "f2_hz": 1050, "f3_hz": 2400, "dur_ms": 140}
  },
  "consonant_metrics": {
    "vot_voiceless_stops_ms": {"p": 45, "t": 62, "k": 74},
    "vot_voiced_stops_ms": {"b": 8, "d": 12, "g": 18},
    "sibilant_cog_khz": {"s": 5.8, "sh": 3.4}
  },
  "dialectal_indices": {
    "rhoticity_percent": 34.5,
    "th_stopping_rate": 0.28,
    "yod_dropping": true,
    "short_a_split": "NYC_SYSTEM"
  },
  "lexicon_overrides": {
    "huge": "juːdʒ",
    "coffee": "kɔːə.fi",
    "water": "wɔː.ɾər"
  },
  "minimal_pair_checks": [
    {"pair": ["cot", "caught"], "status": "DISTINCT", "contrast_dimension": "F1_F2_BACKING"},
    {"pair": ["pin", "pen"], "status": "DISTINCT", "contrast_dimension": "F1_HEIGHT"}
  ]
}
```

---

## Biometric & Personality Crosswalk

| Idiolect Parameter | Core Biometric Section | Personality Profile Section | Synthesis Compiler Target |
| :--- | :--- | :--- | :--- |
| Wells Vowel Targets | §3 Formant Frequencies & Vowel Space | §3.1 Lexical Preferences | Klatt Formant Grid (F1-F3) |
| VOT Metrics | §6 Consonant Features | §5.2 Fillers & Articulatory Search | Synthesis Stop Closure Timers |
| Rhoticity & TH-Stopping | §6 Linguistic & Dialectal Characteristics | §3.4 Idiom & Cultural Vernacular | SSML `<phoneme>` substitutions |
| Idiosyncratic Lexicon | §6 Code-Switching & Dialect | §3.2 Comfort Lexicon | Lexicon Dictionary & Regex |
| Minimal Pair Rules | §10 Replicable Parameters | §1.0 Executive Summary | Verifier Automated Evaluator |

---

## Calibration Reference Example: Queens Orator Baseline

- **Wells THOUGHT Realization:** [ɔːə] with elevated F1 (585 Hz) and heavily retracted F2 (920 Hz); diphthongal offglide duration ~165 ms.
- **Rhoticity:** Coda /r/ vocalization in rapid speech (~32% retention); elevated retention in formal stress (~68%).
- **TH-Stopping:** Intervocalic and initial /ð/ stopping to dental [d̪] at a 28% incidence in non-scripted turns (*"dat's right"*).
- **Yod-Dropping / Gliding:** Deletion of /h/ before /j/ in *huge* -> [juːdʒ]; absence of coronal yod in *news* -> [nuːz].
- **Minimal Pair Contrast:** Distinct *cot* [kɑt] vs *caught* [kɔːət] preservation (non-merged low-back vowels).

---

## Generation Rules

1. Never use generic dialect summaries; provide exact IPA characters and Hz coordinates for all lexical classes.
2. Every stop category must specify numerical VOT in milliseconds.
3. Every profile must output the complete machine-readable `idiolect_atlas.json` block.
