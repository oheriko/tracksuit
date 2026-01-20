# tracksuit 🏃‍♂️

> An intelligent CLI scaffolding tool that uses LLMs to generate full-stack applications

[![Built with Rust](https://img.shields.io/badge/built%20with-Rust-orange)](https://www.rust-lang.org/)
[![Powered by Ratatui](https://img.shields.io/badge/UI-Ratatui-blue)](https://ratatui.rs/)
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-green.svg)](https://opensource.org/licenses/Apache-2.0)

**tracksuit** is a smart project generator that leverages LLMs to scaffold complete, production-ready applications. Built with Rust and Ratatui, it provides a beautiful TUI experience for creating full-stack projects with your choice of frontend, backend, database, and infrastructure.

---

## ✨ Features

- 🎨 **Beautiful Interactive TUI** - Navigate your stack choices with an elegant terminal interface
- 🤖 **LLM-Powered Intelligence** - Conversational project generation that understands intent
- 🚀 **Multi-Stack Support** - Mix and match from dozens of frameworks and tools
- ⚡ **Fast & Lightweight** - Single Rust binary, no runtime dependencies
- 🔄 **Real-Time Streaming** - Watch the LLM generate your project live
- 🎯 **Smart Defaults** - Opinionated but flexible configurations
- 📦 **Complete Setup** - Dependency installation, git init, and more

---

## 🎯 Quick Start

### Installation

```bash
# From crates.io (coming soon)
cargo install tracksuit

# From source
git clone https://github.com/oheriko/tracksuit
cd tracksuit
cargo install --path .
```

### Usage

**Interactive Wizard Mode:**
```bash
tracksuit new my-app
```

**Conversational Mode:**
```bash
tracksuit "build me an app with Next.js, Supabase, and Tailwind"
```

**CLI Flags Mode:**
```bash
tracksuit new my-app \
  --frontend nextjs \
  --backend hono \
  --db postgres \
  --infra docker
```

**TOML Config Mode:**
```bash
tracksuit new my-app --config tracksuit.toml
```

With a `tracksuit.toml` file:
```toml
[project]
name = "my-app"
frontend = "nextjs"
backend = "hono"
database = "postgres"
infrastructure = "docker"

[llm]
backend = "anthropic"
model = "claude-3-5-sonnet"
```

---

## 🏗️ Supported Stacks

### Frontend Frameworks
- **React** - Create React App, Vite
- **Next.js** - App Router, Pages Router
- **SvelteKit** - Full-stack Svelte framework
- **Solid.js** - Reactive UI library
- **Vue** - Vite, Nuxt
- **Astro** - Content-focused sites
- **htmx** - Hypermedia-driven applications

### Backend Frameworks
- **Rust** - Axum, Actix-web, Rocket
- **Go** - Fiber, Gin, Echo
- **TypeScript/Bun** - Hono, Elysia
- **Node.js** - Express, Fastify, NestJS
- **Python** - FastAPI, Django, Flask

### Databases
- **PostgreSQL** - Relational database
- **SQLite** - Embedded database
- **MongoDB** - Document database
- **Supabase** - Postgres + Auth + Storage
- **Turso** - Edge SQLite
- **Redis** - In-memory cache/store

### Infrastructure
- **Docker** - Containerization
- **Nix** - Reproducible builds
- **Railway** - Deployment platform
- **Fly.io** - Edge deployment
- **Vercel** - Frontend hosting
- **Hetzner** - VPS hosting

---

## 🎨 TUI Interface

```
╔════════════════════════════════════════════════════════════╗
║                    TRACKSUIT v0.1.0                        ║
║              Smart Stack Generator                         ║
╠════════════════════════════════════════════════════════════╣
║                                                            ║
║  Project Configuration                                     ║
║  ────────────────────                                      ║
║                                                            ║
║  Project Name:     my-new-app                          ║
║  Frontend:         Next.js (App Router)                    ║
║  Backend:          Rust (Axum)                             ║
║  Database:         PostgreSQL                              ║
║  Infrastructure:   Docker + Nix                            ║
║                                                            ║
║  ────────────────────────────────────────────────          ║
║                                                            ║
║  [Generate Project]  [Reset]  [Quit]                       ║
║                                                            ║
╠════════════════════════════════════════════════════════════╣
║  ↑↓: Navigate  Enter: Select  q: Quit  Ctrl+C: Exit        ║
╚════════════════════════════════════════════════════════════╝
```

---

## 🧠 LLM Integration

tracksuit uses LLMs to intelligently generate project structures based on your choices:

### Supported LLM Backends

- **Anthropic Claude 4.5** (via API)
- **Google Gemini 3** (via API)
- **OpenAI GPT-5** (via API)
- **Local Models** (via llama.cpp, Ollama)

### Configuration

```bash
# Set your API key
export ANTHROPIC_API_KEY="sk-ant-..."

# Or use local models
tracksuit config set llm.backend local
tracksuit config set llm.model ministral3
```

### How It Works

1. **Analyze** - LLM understands your stack requirements
2. **Plan** - Generates optimal file structure and dependencies
3. **Generate** - Creates files with proper configurations
4. **Validate** - Checks generated code for common issues
5. **Initialize** - Sets up git, installs deps, provides next steps

---

## 🛠️ Architecture

```
tracksuit/
├── src/
│   ├── main.rs           # Entry point, CLI setup
│   ├── app.rs            # Application state management
│   ├── ui.rs             # Ratatui UI components
│   ├── llm/              # LLM integration
│   │   ├── mod.rs
│   │   ├── client.rs     # API clients
│   │   ├── prompts.rs    # System prompts
│   │   └── stream.rs     # Streaming responses
│   ├── scaffold/         # Project generation
│   │   ├── mod.rs
│   │   ├── generator.rs  # File/folder creation
│   │   ├── templates.rs  # Template system
│   │   └── validator.rs  # Code validation
│   └── config/           # Configuration management
│       ├── mod.rs
│       └── stacks.rs     # Stack definitions
└── templates/            # Base templates per stack
    ├── nextjs/
    ├── rust-axum/
    ├── go-fiber/
    └── ...
```

### Key Design Principles

- **Modular** - Each stack component is independent
- **Extensible** - Easy to add new frameworks/tools
- **Type-Safe** - Rust's safety guarantees throughout
- **Performance** - Fast TUI rendering, efficient generation
- **Offline-Capable** - Works with local LLMs

---

## 📋 Roadmap

### v0.1.0 (Current)
- [x] Basic Ratatui TUI setup
- [ ] Interactive wizard interface
- [ ] LLM integration (Anthropic API)
- [ ] Support for 5 frontend frameworks
- [ ] Support for 5 backend frameworks
- [ ] Basic project generation

### v0.2.0
- [ ] Streaming LLM responses in TUI
- [ ] Local LLM support (Ministral 3)
- [ ] Extended stack support (20+ combinations)
- [ ] Template customization
- [ ] Configuration file support

### v0.3.0
- [ ] MCP (Model Context Protocol) integration
- [ ] Plugin system for custom stacks
- [ ] Project migration tools
- [ ] Team presets/sharing
- [ ] Neovim plugin
- [ ] VS Code extension

### v1.0.0
- [ ] Production-ready stability
- [ ] Comprehensive documentation
- [ ] Enterprise features

---

### Development Setup

```bash
# Clone the repo
git clone https://github.com/oheriko/tracksuit
cd tracksuit

# Install dependencies
cargo build

# Run in development
cargo run

# Run tests
cargo test

# Run with logging
RUST_LOG=debug cargo run
```

<!-- ## 🤝 Contributing -->
<!---->
<!-- Contributions are welcome! This is an early-stage project and we'd love your help. -->

<!-- ### Guidelines -->
<!---->
<!-- - Follow Rust conventions and `rustfmt` -->
<!-- - Add tests for new features -->
<!-- - Update documentation -->
<!-- - Keep dependencies minimal -->
<!-- - Maintain TUI responsiveness -->

---

## 🎓 Learning Resources

New to the tech stack?

- [The Rust Programming Language](https://doc.rust-lang.org/book/) - Rust fundamentals
- [Clap Documentation](https://docs.rs/clap/) - CLI argument parsing
- [Ratatui Book](https://ratatui.rs/) - Learn TUI development
- [Anthropic API Docs](https://docs.anthropic.com/) - LLM integration

---

## 📝 Examples

### Example 1: Fashion Marketplace

```bash
tracksuit "build a fashion marketplace with:
- Next.js frontend with Tailwind
- Rust backend with Axum
- PostgreSQL database
- Image processing with AI
- Docker deployment"
```

Generates a complete project with:
- ✅ Next.js 16 with App Router
- ✅ Tailwind CSS configuration
- ✅ Rust Axum API server
- ✅ PostgreSQL with migrations
- ✅ Docker Compose setup
- ✅ AI image processing pipeline
- ✅ Authentication scaffolding

### Example 2: Simple CRUD App

```bash
tracksuit new todo-app \
  --frontend react \
  --backend go \
  --db sqlite
```

### Example 3: Real-Time Dashboard

```bash
tracksuit "create a real-time analytics dashboard using:
- SvelteKit for the frontend
- Go with Fiber for WebSocket server
- Redis for pub/sub
- Deploy to Fly.io"
```

---

## 🔐 Environment Variables

```bash
# LLM API Keys
ANTHROPIC_API_KEY=sk-ant-...
OPENAI_API_KEY=sk-...

# Local LLM Settings
TRACKSUIT_LLM_BACKEND=local  # or 'anthropic', 'openai'
TRACKSUIT_LLM_MODEL=ministral3    # model name

# Generation Settings
TRACKSUIT_TEMPLATES_PATH=~/.tracksuit/templates
TRACKSUIT_OUTPUT_PATH=~/projects
```

---

## 📜 License

Apache License 2.0 - see [LICENSE](LICENSE) for details.

---

Built with ❤️ by [oheriko](https://github.com/oheriko)
