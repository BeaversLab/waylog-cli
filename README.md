# ChatLog CLI

[![GitHub license](https://img.shields.io/github/license/BeaversLab/chatlog?style=flat-square)](https://github.com/BeaversLab/chatlog/blob/main/LICENSE)
![Rust](https://img.shields.io/badge/built_with-Rust-dca282.svg?style=flat-square)

**Seamlessly sync, preserve, and version-control your AI coding conversations locally.**

ChatLog CLI is a lightweight tool written in Rust that automatically saves your AI coding sessions (Claude Code, Gemini CLI, OpenAI Codex CLI) into clean, searchable local Markdown files. Stop losing your context to session timeouts—ChatLog CLI helps you own your AI history locally.

This repository is forked from [shayne-snap/waylog-cli](https://github.com/shayne-snap/waylog-cli).

[中文文档](README_zh.md) | [English](README.md)

---

## ✨ Features

- **🔄 Auto-Sync**: Real-time synchronization of chat history to `.chatlog/history/` as you type.
- **📦 Full History Recovery**: The `pull` command scans your entire machine to recover past sessions into the current project.
- **📝 Markdown Native**: All history is saved as high-quality Markdown files with frontmatter metadata.


## 🚀 Installation

### Using Homebrew

Works on **Apple Silicon and Intel** Macs (universal binary from the tap):

```bash
brew install BeaversLab/tap/chatlog
```

### Using Scoop (Windows)

```powershell
scoop bucket add chatlog https://github.com/BeaversLab/scoop-bucket
scoop install chatlog
```

### Using Cargo

Builds from source for **your current CPU** (no cross-architecture surprises if this binary is the one you run):

```bash
cargo install chatlog
```

If zsh reports **`bad CPU type in executable`**, you are usually not running the `cargo`-built binary: another `chatlog` (for example from Homebrew) may be earlier in `PATH`, or was built for the other macOS architecture. Check with `which chatlog` and `file "$(which chatlog)"`, then remove or reorder installs so the architecture matches your Mac.

## 💡 Usage

### 1. Real-time Logging (`run`)

Use `chatlog run` instead of calling your AI tool directly. ChatLog will launch the agent and record the conversation in real-time.



```bash
# Run Claude Code with auto-sync
chatlog run claude

# Run Gemini CLI
chatlog run gemini

# Run Codex CLI
chatlog run codex
```

![ChatLog Run Demo](demo/run.gif)


### 2. Full Sync / Recover History (`pull`)

Scans your local AI provider storage and "pulls" all relevant sessions into your project's `.chatlog` folder.



```bash
# Pull all history for the current project
chatlog pull
```
![ChatLog Pull Demo](demo/pull.gif)

## 📂 Supported Providers

| Provider | Status | Description |
|----------|--------|-------------|
| **Claude Code** | 🚧 Beta | Supports `claude` CLI tool from Anthropic. |
| **Gemini CLI** | 🚧 Beta | Supports Google's Gemini CLI tools. |
| **Codex** | 🚧 Beta | Supports OpenAI Codex CLI. |

### Dev build

```bash
git clone https://github.com/BeaversLab/chatlog.git
cd chatlog
./scripts/install.sh
```


## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

Distributed under the Apache License 2.0. See `LICENSE` for more information.
