# AI Terminal Kit

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Homebrew](https://img.shields.io/badge/Homebrew-Bundle-FBB040?logo=homebrew&logoColor=white)](https://brew.sh/)
[![Verified](https://img.shields.io/badge/Verified%20by-16%20AI%20agents-blue)](https://fabricioartur.com/blog/16-ai-agents-terminal-tools-consensus)

> Terminal tools that 16 independent AI agents agreed are essential — verified on a real machine, not just recommended.

AI Terminal Kit is a reproducible Homebrew setup for people who use AI agents beyond chat: local terminals, real repositories, build/test loops, scripts, APIs, and developer workflows. 24 tools, one command, verified with `command -v` — not just copy-pasted from a model's answer.

![Demo: inspecting the Brewfile, searching with ripgrep, and verifying jq](demo.gif)

## The experiment

I use several AI agents daily — Claude Code, OpenAI Codex, Gemini CLI, Grok, Cursor, Opencode, among others — all with access to my terminal, browser, and machine. Instead of deciding on my own what to install, I asked all 16 of them the same question, independently:

> "Given that I use tools like (list your agents), all of which can access the internet, browser, terminal, and my computer — if you could request any terminal tool to work better, spend fewer tokens, and be more efficient, what would you ask for?"

The answers converged strongly around a core set of tools, with some genuine disagreement on pace of adoption, multi-agent orchestration, and heavier infrastructure. I cross-checked every claim on the actual machine with `command -v` and `brew list` — and caught real errors along the way (a tool reported as "installed via Homebrew" that was actually native to macOS, package names confused with actual commands).

Full write-up: **[fabricioartur.com/blog/16-ai-agents-terminal-tools-consensus](https://fabricioartur.com/blog/16-ai-agents-terminal-tools-consensus)**

## The kit, at a glance

| Category | Tools | Why it matters to an agent |
|---|---|---|
| Find information faster | `ripgrep`, `fd`, `ast-grep`, `bat`, `eza`, `tree`, `tokei` | Removes blind exploration — exact files, symbols, and patterns instead of reading everything |
| Reduce noise before it reaches the model | `yq`, `httpie` — plus native/optional helpers like `jq` and `pandoc` | Structured data is cheaper to reason over than raw text (`jq` is usually native on modern macOS, `pandoc` is optional — see [CONSENSUS.md](CONSENSUS.md)) |
| Make environments reproducible | `tmux`, `direnv`, `mise`, `uv`, `zoxide`, `fzf` | Predictable environments mean fewer retries and no "works on my machine" |
| Treat Git/GitHub and validation as terminal-native | `git-delta`, `lazygit`, `act`, `semgrep`, `hyperfine`, `btop` — plus `gh` (recommended, not bundled) | Agents inspect changes, validate claims, and measure whether an "optimization" actually helped |
| Docs and project commands | `tldr`, `glow`, `just` | Standardized, guessable commands instead of rediscovering how to test/build every session |

`gh` is intentionally not in the `Brewfile` — it's highly recommended, but most people already have it. See [CONSENSUS.md](CONSENSUS.md) for the full reasoning per category, including every tool deliberately left out and why.

## What's inside

- [`Brewfile`](Brewfile) — the recommended core kit (24 tools), ready to install with Homebrew Bundle
- [`PROMPT.md`](PROMPT.md) — the exact prompt used to survey the 16 agents
- [`CONSENSUS.md`](CONSENSUS.md) — why these categories appeared repeatedly across agent responses
- [`LICENSE`](LICENSE) — MIT

## Install

Requires [Homebrew](https://brew.sh/).

```bash
git clone https://github.com/fabricioartur/ai-terminal-kit.git
cd ai-terminal-kit
brew bundle --file=Brewfile
```

### More demos

| `brew bundle check` — confirms all 24 tools are actually satisfied | `git show` rendered through `git-delta` |
|---|---|
| ![Verifying the Brewfile is satisfied](verify.gif) | ![A commit diff rendered readable by git-delta](delta.gif) |

All three GIFs in this README were recorded with [`vhs`](https://github.com/charmbracelet/vhs) from the `.tape` scripts in this repo (`demo.tape`, `verify.tape`, `delta.tape`) — reproducible, not hand-edited.

## Why these tools

Each tool in the kit reduces one of four bottlenecks for an autonomous agent working in a terminal: finding information fast, reducing noise before it reaches the model, making commands and environments reproducible, and giving reliable visibility into what's happening. Details and reasoning for each tool are in the full article and in [CONSENSUS.md](CONSENSUS.md).

## Method note

This is not a scientific benchmark. It is a practical experiment with the agents I use in my real workflow. The value is in the convergence between independent answers and the later verification on a real machine.

Convergence between agents is a signal. `command -v` is proof.

## Replicate it yourself

Ask your own agents the prompt in [`PROMPT.md`](PROMPT.md), verify every answer on your own machine before installing anything, and open an issue or PR with what you found — especially if your results diverge from this kit. Different stacks (Linux, WSL, different agent lineups) will surface different consensus, and that's useful data too.

## License

MIT — see [LICENSE](LICENSE).
