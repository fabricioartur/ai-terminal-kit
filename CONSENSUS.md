# Consensus notes

This project started from a simple question asked independently to 16 AI agents/models:

> If you could request any terminal tool to work better, spend fewer tokens, and be more efficient, what would you ask for?

The answers converged around a practical idea: the bottleneck is often not the model, but the environment where the model works.

## 1. Find information faster

Tools:

- `ripgrep`
- `fd`
- `ast-grep`
- `bat`
- `eza`
- `tree`
- `tokei`

Why agents care: they reduce blind exploration. Instead of reading entire files or dumping huge directory listings into context, agents can find the exact files, symbols, patterns, or project shape they need.

## 2. Reduce noise before it reaches the model

Tools:

- `jq`
- `yq`
- `httpie`
- `pandoc`

Why agents care: structured data is cheaper to reason over than raw output. JSON, YAML, API responses, and documents should be filtered locally before being sent into an LLM context window.

Note: `jq` is intentionally not in the Brewfile because recent macOS versions may already provide it. Verify with `command -v jq`.

## 3. Make environments reproducible

Tools:

- `tmux`
- `direnv`
- `mise`
- `uv`
- `zoxide`
- `fzf`

Why agents care: long-running commands, project-specific environment variables, runtime versions, and local navigation all become more predictable. Predictable environments mean fewer retries.

## 4. Treat GitHub and validation as terminal-native workflows

Tools:

- `gh`
- `git-delta`
- `lazygit`
- `act`
- `semgrep`
- `hyperfine`
- `btop`

Why agents care: agents need to inspect changes, validate claims, check CI, detect risks, and measure whether optimizations actually helped.

Note: `gh` is not in this Brewfile because it was already present in the verified environment, but it is highly recommended if you do not have it.

## 5. The non-tooling layer

The strongest recommendation was not a package. It was project discipline:

- `AGENTS.md` or `CLAUDE.md` for project context
- `justfile` for standard commands
- `.mise.toml` for runtime versions

These files help agents avoid rediscovering the same project structure, commands, and conventions every session.

