# ChatLog CLI

[![GitHub license](https://img.shields.io/github/license/BeaversLab/chatlog?style=flat-square)](https://github.com/BeaversLab/chatlog/blob/main/LICENSE)
![Rust](https://img.shields.io/badge/built_with-Rust-dca282.svg?style=flat-square)

**无缝同步、保留并本地化版本控制你的 AI 编程对话历史。**

ChatLog CLI 是一个轻量级的工具，自动捕捉并存档你的 AI 编程会话（Claude Code, Gemini CLI, OpenAI Codex CLI），将其导出为整洁、可搜索的本地 Markdown 文件。不要再因为会话过期而丢失上下文——ChatLog CLI 帮你实现 AI 历史的本地所有权。

本仓库 fork 自 [shayne-snap/waylog-cli](https://github.com/shayne-snap/waylog-cli)。

[English](README.md) | [中文文档](README_zh.md)

---

## ✨ 特性

- **🔄 自动同步**：实时同步聊天历史至 `.chatlog/history/`，边聊边记。
- **📦 全量历史恢复**：使用 `pull` 命令扫描全机，将过去或丢失的会话恢复到当前项目中。
- **📝 Markdown 原生**：所有历史记录均保存为带 Frontmatter 元数据的高质量 Markdown 文件。

## 🚀 安装

### 使用 Homebrew（推荐）

**Apple 芯片与 Intel 芯片** 的 Mac 均可安装（tap 提供通用二进制）：

```bash
brew install BeaversLab/tap/chatlog
```

### 使用 Cargo

从源码在当前机器上编译，二进制架构与 **当前 CPU** 一致：

```bash
cargo install chatlog
```

若出现 **`bad CPU type in executable`**，多数情况是 `PATH` 里优先命中了**另一份** `chatlog`（例如此前只含 arm64 的 Homebrew 包在 Intel Mac 上运行，或相反），而不是这次 `cargo install` 生成的文件。请执行 `which chatlog` 与 `file "$(which chatlog)"` 确认路径与架构，卸载或调整 `PATH` 顺序即可。

## 💡 使用方法

### 1. 实时记录 (`run`)

使用 `chatlog run` 代替直接调用 AI 工具。ChatLog 将启动代理并实时记录对话。



```bash
# 启动 Claude Code 并同步
chatlog run claude

# 启动 Gemini CLI
chatlog run gemini
```

![ChatLog Run Demo](demo/run.gif)

### 2. 全量同步 / 恢复历史 (`pull`)

扫描本地 AI 供应商的存储，并将所有相关的会话“拉取”到项目的 `.chatlog` 文件夹中。



```bash
# 拉取当前项目的所有历史记录
chatlog pull
```
![ChatLog Pull Demo](demo/pull.gif)

## 📂 支持的供应商

| 供应商 | 状态 | 描述 |
|----------|--------|-------------|
| **Claude Code** | 🚧 Beta | 支持 Anthropic 的 `claude` 命令行工具。 |
| **Gemini CLI** | 🚧 Beta | 支持 Google 的 Gemini 命令行工具。 |
| **Codex** | 🚧 Beta | 支持 OpenAI Codex CLI。 |


### 源码安装

```bash
git clone https://github.com/BeaversLab/chatlog.git
cd chatlog
./scripts/install.sh
```

## 🤝 贡献

欢迎贡献！请随时提交 Pull Request。

## 📄 许可证

基于 Apache License 2.0 许可证分发。详见 `LICENSE` 文件。
