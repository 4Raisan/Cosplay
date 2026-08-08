# Cosplay — v3.9

**Self-contained, fully-local AI proxy + Admin UI + Claude Code launcher for Windows.**

Install on any (even clean) Windows PC, add one provider API key (any OpenAI-compatible
endpoint — NVIDIA NIM, Groq, a local vLLM server, ...), and `cclaude` gives you a working
Claude Code CLI routed through a local FastAPI gateway — no Anthropic account needed.

## Download (v3.9 — 2026-08-08)

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

## What's inside

- FastAPI gateway on `127.0.0.1:8082` — OpenAI-compatible `/v1/*` endpoints Claude Code talks to
- Admin web UI: providers, model routing, thinking levels, voice, diagnostics
- One-command launcher `cclaude` (starts the server if needed, opens the UI, runs Claude Code)
- Clean uninstaller (keeps/removes Cosplay, Claude Code, Python, Node.js independently)

## Version history

- **v3.9 (2026-08-08)** — provider-agnostic setup (no vendor hardcoding); new
  `Cosplay-Full-Setup.exe` with the Cosplay logo as its icon; desktop shortcut with logo;
  install flow waits for you to set the API key before launching; uninstaller now restores
  `~/.claude/settings.json` and removes the desktop shortcut.

## License

MIT.

Claude Code is Anthropic's CLI — check its license and terms before distributing this
project alongside it.

```
MIT License

Copyright (c) 2026 Cosplay Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
