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
| `Cosplay-Full-Setup.exe` | Self-extracting installer, Cosplay logo as its icon (recommended) | ~600 KB |
| `Cosplay-Setup.cmd` | Self-extracting installer, same package (batch) | ~740 KB |

Both files carry the identical package: double-click either one to install everything —
portable Python / Node.js if the PC is missing them, the Claude Code CLI, the gateway,
the Admin UI, and a desktop shortcut.

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
- Thinking level is configured per **routing slot** (default / fast_tasks / heavy_analysis /
  research / fallback_1–3) and auto-saves when changed.

## Version history

- **v3.9 (2026-08-08)** — provider-agnostic setup (no vendor hardcoding); new
  `Cosplay-Full-Setup.exe` with the Cosplay logo as its icon; desktop shortcut with logo;
  install flow waits for you to set the API key before launching; uninstaller now restores
  `~/.claude/settings.json` and removes the desktop shortcut.

## License

MIT-based, **with two additional terms**:

- Anyone may **use, edit, and redistribute** the software (including commercially as part
  of your own services), provided the copyright notice stays intact.
- You may **not sell** the Software itself, or charge for the Software / a product whose
  main value is the Software.
- You may **not use the name "Cosplay"** (or a confusingly similar name) for your own
  derivative products — the name is reserved for the original project.

Claude Code is Anthropic's CLI — check its license and terms before distributing this
project alongside it.

```
Cosplay License (MIT-based, with restrictions)

Copyright (c) 2026 Cosplay Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, and distribute copies of the Software,
subject to the following conditions:

1. The above copyright notice and this permission notice shall be included in
   all copies or substantial portions of the Software.

2. You may not sell the Software, or charge money for the Software or for any
   product whose main value is the Software.

3. You may not use the name "Cosplay" (or any confusingly similar name) for
   any product, service, or derivative work based on the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
