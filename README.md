# Cosplay — v3.9

**Self-contained, fully-local AI proxy + Admin UI + Claude Code launcher for Windows.**

Install on any (even clean) Windows PC, add one provider API key, and `cclaude` gives you
a working Claude Code CLI routed through a local FastAPI gateway — no Anthropic account
required.

## Download

Latest release: **v3.9 (2026-08-08)** — grab the installers from the
[Releases page](https://github.com/4Raisan/Cosplay/releases) or from this repository:

| File | What | Size |
| --- | --- | --- |
| `Cosplay-Full-Setup.exe` | Self-extracting installer (recommended) | ~600 KB |
| `Cosplay-Setup.cmd` | Self-extracting installer, same package (batch) | ~740 KB |

Both files carry the identical **self-contained** package: **one run checks and installs
every dependency** (portable Python / Node.js if missing, the Claude Code CLI, the gateway
deps), configures everything, starts the server, and opens the Admin UI — nothing else to
download or set up manually.

## Quick start

1. Download `Cosplay-Full-Setup.exe` and double-click it.
2. Setup installs and starts the local server, then opens the Admin Dashboard at
   `http://127.0.0.1:8082`.
3. Add your provider API key (Providers > Add Provider).
4. Back in the terminal, wait for the prompt, press a key — Claude Code launches.

Run anytime with `cclaude`.

## Supported provider types

Cosplay is **provider-agnostic** — the Admin UI lets you add any of these four API types:

| Type | Description |
| --- | --- |
| **OpenAI Compatible** | Uses the common OpenAI-style API format (`/v1/chat/completions` or similar). Many providers support this, including various third-party / model-hosting APIs (NVIDIA NIM, Groq, Together, OpenRouter, ...). |
| **Anthropic** | Uses Anthropic's native API format, such as Claude's Messages API. |
| **Gemini** | Uses Google's Gemini API format. |
| **Local Provider** | Connects to an AI model running locally on your own computer/server (e.g. vLLM, Ollama, LM Studio), rather than a cloud API. |

## What it does

- **Web-first Admin UI** — the main control surface is the dashboard at
  `http://127.0.0.1:8082`: manage providers, discover models, route model slots, configure
  thinking, voice, and diagnostics.
- **Claude Code integration** — a priority companion: the `cclaude` launcher starts the
  server if needed, opens the UI, and runs the Claude Code CLI pointed at the gateway
  (`ANTHROPIC_BASE_URL` → the local server). OpenAI-compatible `/v1/*` endpoints keep the
  hand-off clean.

### Model working checks

- Every discovered model can be **validated against its provider** (connection check +
  real request). The UI marks models **✓ Working / ✗ Failed**.
- Verdicts are **persisted** and survive page refreshes and restarts — a model's status
  only changes when you re-run the check.

### Thinking settings

- Per-model **thinking levels** (Auto / Off / Light / Balanced / Deep / XHigh / Max) with a
  verified capability cap: levels at or below the cap show **✓ Working**, levels above are
  greyed out with **✗ Not Working**.
- **Priority flow** — the Admin UI controls the thinking level (default: **Auto**). The
  model you select in Claude Code is served through the gateway using that Admin-configured
  level for its routing slot; Claude Code itself does not need to set it.
- Thinking level is configured per **routing slot** (default / fast_tasks / heavy_analysis /
  research / fallback_1–3) and auto-saves when changed.

## Version history

- **v3.9 (2026-08-08)** — provider-agnostic setup (no vendor hardcoding); new
  `Cosplay-Full-Setup.exe` with the Cosplay logo as its icon; desktop shortcut with logo;
  install flow waits for you to set the API key before launching; uninstaller now restores
  `~/.claude/settings.json` and removes the desktop shortcut.

## License

```
MIT License — No-Sell Clause

Copyright (c) 2026 Cosplay Contributors


Free to use, copy, modify, and distribute, but you may not sell Cosplay or products whose main value is Cosplay.


Software is provided “as is” without warranty or liability.
```
