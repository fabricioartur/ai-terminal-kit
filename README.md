# AI Terminal Kit

> Terminal tools that 16 independent AI agents agreed are essential — verified on a real machine, not just recommended.

AI Terminal Kit is a reproducible Homebrew setup for people who use AI agents beyond chat: local terminals, real repositories, build/test loops, scripts, APIs, and developer workflows.

## The experiment

I use several AI agents daily — Claude Code, OpenAI Codex, Gemini CLI, Grok, Cursor, Opencode, among others — all with access to my terminal, browser, and machine. Instead of deciding on my own what to install, I asked all 16 of them the same question, independently:

> "Given that I use tools like (list your agents), all of which can access the internet, browser, terminal, and my computer — if you could request any terminal tool to work better, spend fewer tokens, and be more efficient, what would you ask for?"

The answers converged strongly around a core set of tools, with some genuine disagreement on pace of adoption, multi-agent orchestration, and heavier infrastructure. I cross-checked every claim on the actual machine with `command -v` and `brew list` — and caught real errors along the way (a tool reported as "installed via Homebrew" that was actually native to macOS, package names confused with actual commands).

Full write-up: [O que 16 agentes de IA concordam ser essencial no seu terminal e onde discordam](https://app.notion.com/p/fartur/O-que-16-agentes-de-IA-concordam-ser-essencial-no-seu-terminal-e-onde-discordam-392e769590bb802aa674d2cd07eb000c)

## What's inside

- `Brewfile` — the recommended core kit, ready to install with Homebrew Bundle
- `PROMPT.md` — the exact prompt used to survey the 16 agents
- `CONSENSUS.md` — why these categories appeared repeatedly across agent responses

## Install

Requires [Homebrew](https://brew.sh/).

```bash
git clone https://github.com/fabricioartur/ai-terminal-kit.git
cd ai-terminal-kit
brew bundle --file=Brewfile
```

## Why these tools

Each tool in the kit reduces one of four bottlenecks for an autonomous agent working in a terminal: finding information fast, reducing noise before it reaches the model, making commands and environments reproducible, and giving reliable visibility into what's happening. Details and reasoning for each tool are in the full article.

## Method note

This is not a scientific benchmark. It is a practical experiment with the agents I use in my real workflow. The value is in the convergence between independent answers and the later verification on a real machine.

Convergence between agents is a signal. `command -v` is proof.

## License

MIT — see [LICENSE](LICENSE).
