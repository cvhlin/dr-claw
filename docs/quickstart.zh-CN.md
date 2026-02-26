[English](./quickstart.md) | [中文](./quickstart.zh-CN.md)

# 快速入门

在 10 分钟内让 VibeLab 在你的机器上运行起来。

## 前置要求

| 要求 | 详情 |
|------|------|
| **Node.js** | v20 或更高版本（推荐 v22 — 见 `.nvmrc`）。使用 `node -v` 检查。 |
| **Git** | 任意较新版本。使用 `git --version` 检查。 |
| **CLI 工具** | 至少安装以下之一：[Claude Code](https://docs.anthropic.com/en/docs/claude-code)、[Cursor CLI](https://docs.cursor.com/en/cli/overview) 或 [Codex](https://developers.openai.com/codex)。 |
| **构建工具** | 用于编译原生模块（`node-pty`、`better-sqlite3`）— 见下文。 |

### 平台构建工具

原生 Node.js 模块需要 C/C++ 编译器：

- **macOS** — 安装 Xcode 命令行工具：
  ```bash
  xcode-select --install
  ```
- **Ubuntu / Debian** —
  ```bash
  sudo apt-get install -y build-essential python3
  ```
- **Windows** — 安装 [Visual Studio Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) 和 Python 3，或运行：
  ```bash
  npm install -g windows-build-tools
  ```

## 安装步骤

### 1. 克隆仓库

```bash
git clone https://github.com/bbsngg/VibeLab.git
cd VibeLab
```

### 2. 安装依赖

```bash
npm install
```

> 如果 `npm install` 失败并出现原生模块报错（`gyp ERR!`、`better-sqlite3` 等），请先参阅上方的[前置要求](#平台构建工具)以及 [FAQ](./faq.zh-CN.md)。

### 3.（可选）从源码重新编译 node-pty

如果集成 Shell 标签页显示错误，请重新编译 `node-pty`：

```bash
npm rebuild node-pty --build-from-source
```

### 4. 配置环境

```bash
cp .env.example .env
```

默认值适用于本地开发。如需生产环境或网络暴露的部署，请编辑 `.env` — 所有可用变量请参阅[配置参考](./configuration.zh-CN.md)。

### 5. 启动应用

```bash
npm run dev
```

### 6. 打开浏览器

访问 **http://localhost:3001**（或你在 `.env` 中设置的端口）。

## 你应该看到什么

### 终端输出

当两个服务器成功启动后，你会看到类似以下的输出：

```
[INFO] App Installation: /path/to/VibeLab
[INFO] Database: server/database/auth.db
Database initialized successfully
Server running on port 3001
```

以及 Vite 开发服务器：

```
VITE v5.x.x  ready in XXX ms
➜  Local:   http://localhost:5173/
```

### 浏览器

1. **登录 / 注册界面** — 创建你的第一个账户。
2. **项目侧边栏** — 列出从 Claude Code / Cursor / Codex 会话目录中自动发现的项目。

> **提示：** 如果项目列表为空，请在 VibeLab 外的终端中先在某个项目目录下运行 `claude`（或 `cursor`、`codex`）。VibeLab 从 CLI 会话历史中发现项目。

---

## 快速故障排除

| 症状 | 可能原因 | 快速修复 |
|------|---------|---------|
| `npm install` 时出现 `gyp ERR!` | 缺少 C/C++ 构建工具 | [安装构建工具](#平台构建工具) |
| Shell 标签页报错 | `node-pty` 二进制不匹配 | `npm rebuild node-pty --build-from-source` |
| "未找到 Claude 项目" | 从未在任何项目中运行过 CLI | 先在项目目录中运行 `claude` |

更多解决方案请参阅 [FAQ](./faq.zh-CN.md)。
