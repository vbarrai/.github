# VBarrAI

Open-source tools built around modern AI-assisted development workflows.

VBarrAI develops practical utilities that help developers integrate AI coding agents into their daily workflow — securely, efficiently, and naturally.

---

## Projects

### [maconfai](https://github.com/vbarrai/maconfai)

**Minimal skills manager for Claude Code, Cursor, Codex, and Open Code.**

Install, update, and uninstall agent skills from GitHub repos or local directories. Maconfai discovers `SKILL.md` files inside a `skills/` directory, lets you pick which skills and agents to install to, and copies them to a canonical `.agents/skills/` directory with symlinks to each agent's skills folder. MCP server config and hooks are translated automatically between agent formats.

```bash
npx maconfai install owner/repo
```

### [parcai](https://github.com/vbarrai/parcai)

**Lightweight shell isolation for AI agents on macOS.**

Run Claude, Codex, or any AI coding assistant confined to your project directory — no access to secrets, no risk to your system. Uses macOS native sandboxing (`sandbox-exec` + APFS clone) — no Docker, no VM, no daemon. The agent writes to a clone, not the original project; on exit, you review the diff and choose to apply or discard. Includes secret masking via `.parcai.json`, network control (`--no-network`), and session persistence across runs.

```bash
cd my-project && parcai
```

### [murmurai](https://github.com/vbarrai/murmurai)

**Push-to-talk voice transcription and AI assistant for macOS.**

Hold a key, speak, release — your speech is transcribed locally by [faster-whisper](https://github.com/SYSTRAN/faster-whisper) and pasted at the cursor. A second hotkey sends the transcript plus any selected text to a local AI agent via [Ollama](https://ollama.com). Bilingual FR/EN mode runs two Whisper passes in parallel and fuses the results locally using a built-in dictionary of ~100 technical terms — keeping French sentence structure with English jargon intact, no LLM needed. Fully local, no cloud API required.

| Mode | Default key | What it does |
|---|---|---|
| **Transcript** | Right Option (hold) | Records → transcription → pasted at cursor |
| **Agent** | Right Command (hold) | Records → transcription + selected text → Ollama → response pasted |

---

## Philosophy

Each tool addresses a specific friction point in AI-assisted development:

- **maconfai** — standardize and share agent skills across tools
- **parcai** — sandbox agent execution to protect your system
- **murmurai** — interact with agents using your voice, locally and privately
