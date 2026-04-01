> [!NOTE]
> This is repo is ONLY for research purposes only

# Claude Code

An AI coding agent that runs in your terminal — reading, editing, and executing code across your entire codebase.

[![TypeScript](https://img.shields.io/badge/TypeScript-100%25-blue)](https://www.typescriptlang.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## Overview

Claude Code is a terminal-based AI agent built on [Claude](https://claude.ai/). It has direct access to your filesystem, shell, and tools, so you can describe a task in plain language and Claude handles the implementation end-to-end — no copy-pasting, no context switching.

## ✨ Features

- **Intelligent Code Understanding** — Reads and analyzes your entire codebase context
- **Natural Language Interface** — Describe what you want in plain English
- **Full Filesystem Access** — Navigate, read, and modify files across your project
- **Shell Integration** — Run commands and scripts directly from the terminal
- **Permission-Based Security** — Control how much autonomy Claude has with configurable permission modes
- **Memory System** — Project-specific knowledge via `CLAUDE.md` files
- **Multiple Authentication Methods** — OAuth, API keys, AWS Bedrock, or GCP Vertex AI

## 📋 Prerequisites

- Node.js 18 or higher
- npm

To check your Node.js version:
```bash
node --version
```

## 🚀 Installation

Install the package globally with npm:

```bash
npm install -g @anthropic-ai/claude-code
```

Verify the installation:
```bash
claude --version
```

## 🔐 Authentication

Claude Code authenticates in two ways:

### OAuth (Recommended)
Sign in with your Anthropic account at [claude.ai](https://claude.ai). Run `claude` for the first time and follow the browser prompt.

### API Key
Set the `ANTHROPIC_API_KEY` environment variable:
```bash
export ANTHROPIC_API_KEY=sk-ant-...
```

### Cloud Providers
- **AWS Bedrock**: Set `CLAUDE_CODE_USE_BEDROCK=1` and configure AWS credentials
- **GCP Vertex AI**: Set `CLAUDE_CODE_USE_VERTEX=1` and configure Application Default Credentials

## 🎯 Quick Start

1. **Navigate to your project:**
   ```bash
   cd my-project
   ```

2. **Start an interactive session:**
   ```bash
   claude
   ```

3. **Try your first task:**
   ```
   > explain the structure of this codebase
   > add input validation to the signup form
   > write tests for the UserService class
   > find all places where we catch and swallow errors
   ```

4. **Initialize CLAUDE.md for your project:**
   ```
   > /init
   ```

## 🛡️ Permission System

Every tool use in Claude Code goes through a permission check. You control how much autonomy Claude has:

| Mode | Behavior |
|------|----------|
| `default` | Claude asks before running shell commands and making edits. You approve or deny each action. |
| `acceptEdits` | File edits are applied automatically. Shell commands still require approval. |
| `plan` | Claude produces a plan and asks for your sign-off before taking any action. |
| `bypassPermissions` | All actions run without prompts. Intended for automated pipelines in sandboxed environments. |

Set your permission mode:
```bash
claude --permission-mode acceptEdits
```

Or change it within a session using `/permissions`.

## 🧠 CLAUDE.md Memory System

Claude Code reads `CLAUDE.md` files from your repository at the start of every session. These files let you encode project-specific knowledge:

- **Project** (`CLAUDE.md` at repo root) — shared by everyone on the team
- **Personal** (`CLAUDE.local.md` at repo root) — your private preferences
- **Subdirectory** (`CLAUDE.md` inside subdirectories) — for monorepos with distinct modules

Generate a `CLAUDE.md` automatically:
```
/init
```

## ⌨️ Slash Commands

| Command | Description |
|---------|-------------|
| `/help` | Show available commands and keyboard shortcuts |
| `/init` | Generate or update a `CLAUDE.md` for the current project |
| `/memory` | View and edit memory files |
| `/permissions` | View or change the current permission mode |
| `/mcp` | Manage connected MCP servers |
| `/clear` | Clear the current conversation context |
| `/exit` | End the session |
| `/login` | Log in to a different account |
| `/logout` | Remove stored credentials |

## 📝 Non-Interactive Mode

Use the `-p` flag to run a single task without entering an interactive session:

```bash
claude -p "explain this codebase"
claude -p "list all TODO comments and the files they appear in"
claude -p "check for unused exports in src/"
```

## 📁 Project Structure

```
claude-code/
├── assistant/      # AI assistant logic
├── bootstrap/      # Bootstrap utilities
├── bridge/         # Bridge components
├── buddy/          # Buddy system
├── cli/            # Command-line interface
├── commands/       # Command handlers
├── components/     # UI components
├── constants/      # Application constants
├── context/        # Context management
├── coordinator/    # Task coordination
├── entrypoints/    # Application entry points
├── hooks/          # React hooks
├── ink/            # Terminal UI (Ink-based)
├── keybindings/    # Keyboard shortcuts
├── memdir/         # Memory directory
├── migrations/     # Database migrations
├── native-ts/      # Native TypeScript bindings
├── plugins/        # Plugin system
├── query/          # Query engine
├── remote/         # Remote operations
├── schemas/        # Data schemas
├── screens/        # Screen components
├── server/         # Server functionality
├── services/       # Business services
├── skills/         # AI skills
├── state/          # State management
├── tasks/          # Task management
├── tools/          # Tool integrations
├── types/          # TypeScript types
├── utils/          # Utility functions
├── vim/            # Vim integration
└── voice/          # Voice functionality
```

## 🤝 Contributing

This repository is a fork of [VineeTagarwaL-code/claude-code](https://github.com/VineeTagarwaL-code/claude-code).

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License.

## 🔗 Links

- [Documentation](https://www.mintlify.com/VineeTagarwaL-code/claude-code/introduction)
- [Original Repository](https://github.com/VineeTagarwaL-code/claude-code)
- [Anthropic](https://www.anthropic.com/)
- [Claude](https://claude.ai/)

---

<p align="center">Built with ❤️ using TypeScript</p>
