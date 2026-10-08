# Orchestrator Test — Handoff Context for Claude Code

*Compiled from a Claude.ai chat thread. Paste this at the start of the Claude Code session so it has full context without needing to be re-explained.*

## 1. What we're actually testing

Wallisson's existing `mercans_pipeline_v2_9.sh` runs the Mercans Research Pipeline (11 stages, CCG through Skill Compiler) as sequential `claude -p` calls from Bash. A separate chat with Gemini proposed replacing this with a proper state-machine orchestrator ("harness pattern") — deterministic code handles workspace/state/tools, the AI only does the thinking.

**The goal right now is not to rebuild the whole pipeline.** It's to validate the harness pattern itself, on the smallest possible slice, before investing further. Test order: Stage 1 (CCG) → confirm it works → expand module by module → then move to Stage 2, etc., consecutively.

## 2. Decisions already made (don't re-litigate these)

- **Anthropic only — no OpenAI.** Gemini's original proposal mixed GPT-4o/GPT-4o-mini in for "strict JSON" and "stealth scraping." Both claims were checked and rejected: Claude's tool-use already gives strict structured output (proven by every tool call in this whole project), and the "Stage 0 scraping" step Gemini invented doesn't exist in the real 11-stage pipeline — source acquisition is already handled inside Stage 1 (try direct fetch, ask the human to download manually if blocked), and it already works in production (Belgium, Colombia, Chile) with Claude alone. Adding OpenAI would also mean a new vendor, new credentials, new IT approval — friction this project has hit every single time it left what Mercans already sanctioned (Drive, MCP, OAuth).
- **Model-per-stage mapping** (all Anthropic, current model names — Gemini's "Claude 3.5 Sonnet" was outdated):

  | Stage(s) | Nature of work | Model |
  |---|---|---|
  | 2 (Scope Lock-In), 4 (DD) | Structured validation, template fill | Haiku 4.5 |
  | 1 (CCG), 3 (Report Specs), 5 (WTC), 6 (SIR), 7 (Payslip) | Deep legal research, drafting | Sonnet 5 |
  | 8 (Alignment), 9 (Audit+Fixer), 10 (QA), 11 (Skill) | Cross-artifact reconciliation, judgment calls | Opus 5 |

- **Hermes, not Maestri.** Gemini lumped these together as interchangeable "orchestrators." They're not: Hermes is a general-purpose autonomous agent runtime (SKILL.md-compatible, can run unattended) — the right category for a backend pipeline. Maestri is a visual, human-supervised canvas for watching multiple coding-agent terminals side by side — genuinely useful for a different job (e.g. watching Claude Code and Codex review each other live), but not for unattended stage automation. (Note: Maestri did ship a real Windows build since — themaestri.app/en/windows — so the earlier "Mac-only" finding is now stale, but the fit assessment above is unchanged; platform availability isn't the reason it doesn't fit.)
- **Local-first, not cloud.** No AWS S3 / GCS in this first round. Testing architecture and vendor governance at the same time compounds risk for no reason — validate the pattern locally first, exactly like the existing Bash pipeline already runs.
- **One narrow tool per job, not a generic "save anything" function.** Gemini's proposed `salvar_documento(caminho, conteudo)` is too broad — it doesn't account for the DOCX tracked-changes surgery or XLSX style-copy rules the real pipeline already depends on. (Gemini also mis-generalized the "XML surgery" rule — that's a DOCX/tracked-changes rule; XLSX already works fine with careful `openpyxl`, no ZIP-level surgery needed.) Tools should stay scoped to exactly what one stage needs.

## 3. What's already built and validated

- **A minimal hand-rolled Node.js harness** (not using Hermes) — `mercans-orchestrator-poc.js` + `package.json`. Deterministic workspace setup (`fs.mkdirSync`), one narrow tool (`write_ccg_module`), bounded tool-call loop, real post-hoc file verification (never trusts the model's own "done" claim). Already syntax-checked, dependency-installed, and run locally: Country Gate correctly blocks with no args; with a country but no API key, the workspace is created for real and it fails cleanly exactly at the API call — proving the deterministic half works independently of AI availability.
- **A Hermes-compatible skill + config** (this is the one currently being set up — see §4): `mercans-ccg-builder/SKILL.md` (adapted from the real Stage 1 CCG prompt in `mercans_pipeline_v2_4.sh`) and `config.yaml` (forces `provider: anthropic` directly, no `fallback_providers` to OpenRouter/Nous Portal, minimal toolset — file_operations, terminal, web only).
- **The real 11-stage pipeline structure**, confirmed from a shared zip (`mercans-skills-e-estrutura.zip`) cross-checked against a live "Research Pipeline I" run on Colombia:

  `CCG → Scope Lock-In → Report Specs → DD → WTC → SIR → Payslip → Alignment Patch → Audit+Fixer → QA Cross-check → Skill`

  Stage 11 (Skill) is genuinely integrated as of pipeline v2.7+ (confirmed live in v2.9), not just a standalone script anymore.

## 4. Exactly where we are right now — pick up here

Setting up the Hermes workspace for the Stage-1 test, on a **clean, dedicated test machine** (`DESKTOP-TKRQLF7`, intentionally isolated from the real pipeline machines).

**Done:**
- `~/.hermes/config.yaml` — placed
- `~/.hermes/skills/mercans/mercans-ccg-builder/SKILL.md` — placed
- `~/.hermes/skills/mercans/mercans-ccg-builder/references/` — created, **still empty**

**Blocked on:** this machine never had `~/mercans-pipeline/shared/` (confirmed via `find` — genuinely not present, not just unfound). The skill needs 3 reference files from a machine that does have it (`DESKTOP-F5A4T8E` or `DESKTOP-QIVU360`):
- `CCG_TEMPLATE_QUESTIONS.md`
- `country_failure_log.md`
- `REFERENCE_CCG_Bulgaria.docx` (needs converting to `.md` — no `pandoc` on this machine either; use Word → Save As → Plain Text, rename to `.md`)

Plan: email these 3 files from the machine that has them, download on `DESKTOP-TKRQLF7`, then:
```bash
cp ~/Downloads/CCG_TEMPLATE_QUESTIONS.md \
   ~/.hermes/skills/mercans/mercans-ccg-builder/references/ccg_template_questions.md
cp ~/Downloads/country_failure_log.md \
   ~/.hermes/skills/mercans/mercans-ccg-builder/references/country_failure_log.md
# + the Bulgaria file, converted to reference_ccg_bulgaria.md the same way
```

## 5. Remaining steps after that (6 total, currently on step 1)

1. ~~Prepare the Hermes workspace~~ *(in progress — blocked on the 3 files above)*
2. Confirm `config.yaml` routes only through Anthropic — no fallback to OpenRouter/Nous Portal
3. Smoke test first — a trivial task that only exercises the file-write tool, before spending a full research run on it
4. Run just 1–2 real CCG modules (not all 13) against Chile — already complete/verified, so it's a ready-made comparison baseline
5. Compare the output against the real Chile CCG: real citations (not fabricated), correct H3-per-question format, content equivalent to what's already in Drive
6. Only if that passes: consider the full 13 modules, then Stage 2, in that order — not before
