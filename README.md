# AI Terminal Kit

> Terminal tools that 16 independent AI agents agreed are essential — verified on a real machine, not just recommended.

## The experiment

I use several AI agents daily — Claude Code, OpenAI Codex, Gemini CLI, Grok, Cursor, Opencode, among others — all with access to my terminal, browser, and machine. Instead of deciding on my own what to install, I asked all 16 of them the same question, independently:

> "Given that I use tools like (list your agents), all of which can access the internet, browser, terminal, and my computer — if you could request any terminal tool to work better, spend fewer tokens, and be more efficient, what would you ask for?"

The answers converged strongly around a core set of tools, with some genuine disagreement on pace of adoption, multi-agent orchestration, and heavier infrastructure. I cross-checked every claim on the actual machine with `command -v` and `brew list` — and caught real errors along the way (a tool reported as "installed via Homebrew" that was actually native to macOS, package names confused with actual commands).

Full write-up: **[link to blog post]**

## What's inside

- `Brewfile` — the recommended core kit (23 tools), ready to install with Homebrew Bundle
- `PROMPT.md` — the exact prompt used to survey the 16 agents

## Install

```bash
git clone https://github.com/fabricioartur/ai-terminal-kit.git
cd ai-terminal-kit
brew bundle --file=Brewfile
```

## Why these tools

Each tool in the kit reduces one of four bottlenecks for an autonomous agent working in a terminal: finding information fast, reducing noise before it reaches the model, making commands and environments reproducible, and giving reliable visibility into what's happening. Details and reasoning for each tool are in the full article.

## License

MIT — see [LICENSE](LICENSE).
