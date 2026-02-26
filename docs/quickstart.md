[English](./quickstart.md) | [中文](./quickstart.zh-CN.md)

# Quickstart

Get VibeLab running on your machine in under 10 minutes.

## Prerequisites

| Requirement | Details |
|-------------|---------|
| **Node.js** | v20 or higher (v22 recommended — see `.nvmrc`). Check with `node -v`. |
| **Git** | Any recent version. Check with `git --version`. |
| **CLI tool** | At least one of: [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Cursor CLI](https://docs.cursor.com/en/cli/overview), or [Codex](https://developers.openai.com/codex). |
| **Build tools** | Required for native modules (`node-pty`, `better-sqlite3`) — see below. |

### Platform Build Tools

Native Node.js modules need a C/C++ compiler:

- **macOS** — Install Xcode Command Line Tools:
  ```bash
  xcode-select --install
  ```
- **Ubuntu / Debian** —
  ```bash
  sudo apt-get install -y build-essential python3
  ```
- **Windows** — Install [Visual Studio Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) and Python 3, or run:
  ```bash
  npm install -g windows-build-tools
  ```

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/bbsngg/VibeLab.git
cd VibeLab
```

### 2. Install dependencies

```bash
npm install
```

> If `npm install` fails with native module errors (`gyp ERR!`, `better-sqlite3`, etc.), see [Prerequisites](#platform-build-tools) above and the [FAQ](./faq.md).

### 3. (Optional) Rebuild node-pty from source

If the integrated shell tab shows errors, rebuild `node-pty`:

```bash
npm rebuild node-pty --build-from-source
```

### 4. Configure environment

```bash
cp .env.example .env
```

The defaults work for local development. For production or network-exposed setups, edit `.env` — see the [Configuration Reference](./configuration.md) for every available variable.

### 5. Start the application

```bash
npm run dev
```

### 6. Open your browser

Navigate to **http://localhost:3001** (or the port you set in `.env`).

## What You Should See

### Terminal output

When both servers start successfully you will see output like:

```
[INFO] App Installation: /path/to/VibeLab
[INFO] Database: server/database/auth.db
Database initialized successfully
Server running on port 3001
```

And the Vite dev server:

```
VITE v5.x.x  ready in XXX ms
➜  Local:   http://localhost:5173/
```

### Browser

1. **Login / Register screen** — Create your first account.
2. **Projects sidebar** — Lists projects auto-discovered from Claude Code / Cursor / Codex session directories.

> **Tip:** If the project list is empty, open a terminal outside VibeLab and run `claude` (or `cursor`, or `codex`) inside a project directory first. VibeLab discovers projects from CLI session history.

---

## Troubleshooting Shortcuts

| Symptom | Likely cause | Quick fix |
|---------|-------------|-----------|
| `gyp ERR!` during `npm install` | Missing C/C++ build tools | [Install build tools](#platform-build-tools) |
| Shell tab errors | `node-pty` binary mismatch | `npm rebuild node-pty --build-from-source` |
| "No Claude projects found" | CLI never run in any project | Run `claude` in a project directory first |

For more solutions, see the [FAQ](./faq.md).
