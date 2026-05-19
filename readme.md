# claude-skills

A collection of Claude skills for legal academia and practice — opinion editing, modernization, case briefing, exam authoring, and prose-style tooling — authored by Seth J. Chandler.

Each `.skill` file is a self-contained zip with its own `SKILL.md`, references, scripts, and per-skill README/CHANGELOG/LICENSE. Download the one you want and unzip it into your Claude skills directory.

## Available skills

| Skill | What it does |
|--|--|
| **belcher-proof** | Scrubs AI-generated prose of the ten flaws identified by Wendy Laura Belcher (Princeton, 2025): banality, bloated emptiness, synonym variation, abstraction chains, causal miswiring, erased interpreters, adjective inflation, moralizing framing, unattributed arguments, factual errors. |
| **case-briefer** | Detailed 1L case briefs with comprehensive analysis, hypotheticals, critique, and conversion to LaTeX (article or Beamer). |
| **eardraft** | Transforms reading-oriented prose into listening-optimized text suitable for being read aloud with flat/neutral TTS delivery. |
| **law-professor** | Emulates a top-flight law professor preparing materials for teaching or scholarship — class prep, hypotheticals, paper seeds, doctrinal analysis. |
| **opinion-editor** | Edits judicial opinions for teaching and scholarship. Preservation-first, voice-preserving, with a verifiable canonical-passages contract and Tufte-style PDF output modeled on *Carson v. Makin*. Ships with three worked Preservation Lists (Brown, Golan, Lawrence) and a scripted fidelity check. |
| **opinion-modernizer** | Transforms passages from older Supreme Court opinions into plain modern language while preserving legal subtleties. Companion to `opinion-editor`'s Modernize mode. |
| **real-world-law-exam** | Generates law school essay exam questions grounded in real case law, with model answers in Bluebook citation form. |
| **rewrite-anatomy** | Produces a pedagogical LaTeX document that walks a writer through what changed between an original draft and a heavily revised version — section by section, naming each move. |
| **statute-briefer** | <!-- TODO: add one-line description --> |

## Installing a skill

Each `.skill` is a plain zip archive. Download the one you want and unzip:

```bash
unzip -o <skill-name>.skill -d <your-skills-dir>/
```

On Claude Desktop / Cowork on macOS the skills directory is typically:

```
~/Library/Application Support/Claude/.../skills/
```

Restart your Claude session so the skill loader picks up the new install. Each `.skill` includes its own README inside the bundle with skill-specific notes on dependencies, system requirements, and usage.

## Soft dependencies between skills

Some skills enhance each other but none hard-depend on another:

- `opinion-editor` ↔ `opinion-modernizer`. The editor prefers the modernizer's full technique library for pre-1900 opinions, but ships a compressed self-contained fallback so it never crashes if the modernizer is absent.
- `case-briefer` ↔ `law-professor`. Both produce legal-academic content; can be composed but neither requires the other.
- `belcher-proof` and `rewrite-anatomy` are downstream tools — they read prose someone else (or you) produced and analyze or annotate it. They don't require any other skill.

Each skill's own README lists its full dependency picture.

## System requirements

Vary by skill. Common to several:

- **pdflatex** with `tufte-handout`, `tgpagella`, `microtype` for the LaTeX-output skills (`opinion-editor`, `opinion-modernizer`, `case-briefer` in some modes, `rewrite-anatomy`).
- **Python 3.7+** with `PyYAML` for the verification script in `opinion-editor`.

Check each skill's README for specifics.

## Versioning

Each skill is versioned independently with semantic versioning. See each `.skill`'s `CHANGELOG.md` inside the bundle.

## License

Each skill carries its own `LICENSE` inside its bundle. Default is MIT unless a particular skill states otherwise.

## Contact and contributions

Issues and pull requests welcome. For substantive contributions to a specific skill — new Preservation Lists, new technique entries, bug reports on a verification script — please reference the skill name in the title.
