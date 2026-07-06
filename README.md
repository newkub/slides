# slides

> 🚀 Slidev presentations monorepo with shared Vue components, layouts, and utilities

Turborepo + Bun workspaces monorepo for managing Slidev presentation slides. Each slide project lives in `apps/` and shares reusable Vue components from `packages/shared`.

![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)
![Turborepo](https://img.shields.io/badge/Turborepo-2.10.3-blue.svg)
![Bun](https://img.shields.io/badge/Bun-1.3.13-f9f1e1.svg)
![Slidev](https://img.shields.io/badge/Slidev-52.16.0-5d8390.svg)
![Vue](https://img.shields.io/badge/Vue-3.5.33-42b883.svg)

## Project

<details><summary>Goal</summary>

| Icon | Goal | Status | Description |
|------|------|--------|-------------|
| 🎯 | Centralized slide management | ✓ Goal | Single repo for all Slidev presentations |
| 🧩 | Shared components | ✓ Goal | Reusable Vue components across all slide projects |
| ⚡ | Turbo task orchestration | ✓ Goal | Build, dev, export tasks via Turborepo caching |
| 📦 | Per-project package.json | ✗ Not Goal | Root-level dependencies only for Slidev core |
| 🏗️ | Full web app | ✗ Not Goal | Presentation slides only, not a web application |

</details>

<details><summary>Scope</summary>

| Icon | Scope | Status | Description |
|------|-------|--------|-------------|
| 📊 | Slidev presentations | ✓ In Scope | Markdown-based slide decks with Vue components |
| 🎨 | Shared Vue components | ✓ In Scope | CodeBlock, TopicCard, ComparisonTable, layouts |
| 🔧 | Turbo build pipeline | ✓ In Scope | Cached builds, filtered dev servers, PDF export |
| 🌐 | Web hosting | ✗ Out of Scope | Slides are presented locally, not deployed |
| 📱 | Mobile slides | ✗ Out of Scope | Desktop-first presentation slides |

</details>

<details><summary>Key Concepts</summary>

| Icon | Concept | Description |
|------|---------|-------------|
| 📝 | Slidev | Vue-based presentation framework using Markdown |
| 🏗️ | Turborepo | Monorepo task runner with caching and filtering |
| 📦 | Bun Workspaces | Package manager with workspace protocol support |
| 🧩 | Shared Package | `@slides/shared` exports components, layouts, utils |
| 🎨 | Vue SFC | Single File Components for reusable slide elements |

</details>

<details><summary>Core Principles</summary>

| Icon | Principle | Description |
|------|-----------|-------------|
| 🧩 | DRY | Shared components avoid duplication across slide projects |
| ⚡ | Fast Dev | Turbo caching + Bun speed for instant dev servers |
| 📝 | Content First | Each project is just `slides.md` + optional components |
| 🔗 | Workspace Protocol | `workspace:*` for internal dependencies |

</details>

<details><summary>When To Use</summary>

| Icon | Use Case | Description |
|------|----------|-------------|
| 🎓 | Learning topics | Create slide decks for topics you're learning |
| 📊 | Team presentations | Share technical talks with your team |
| 🦀 | Language deep dives | Compare languages like Rust vs TypeScript |
| ⚛️ | Framework overviews | Present SolidJS, Vue, or other frameworks |

</details>

<details><summary>Best Practices</summary>

| Icon | Practice | Description |
|------|----------|-------------|
| 🧩 | Use shared components | Import from `@slides/shared` instead of duplicating |
| 📁 | One slide per concept | Keep each slide focused on a single topic |
| 🎨 | Use themes | Set `theme: seriph` or `theme: default` in frontmatter |
| 🔍 | Filter dev server | Use `--filter=@slides/{name}` to run one project |
| 📦 | Root dependencies | Keep Slidev CLI and themes at root level |

</details>

## Features

| Icon | Feature | Description | Benefit | Usage |
|------|---------|-------------|--------|-------|
| 🏗️ | Turborepo Monorepo | Task orchestration with caching | Fast builds, filtered dev servers | `bunx turbo run dev --filter=@slides/learn-rust` |
| 🧩 | Shared Components | Vue SFCs reusable across all slides | DRY, consistent UI | `import { TopicCard } from '@slides/shared'` |
| 📝 | Slidev Integration | Markdown-based slides with Vue | Rich presentations with code | `slidev slides.md --open` |
| 🎨 | Dual Themes | Seriph and default themes included | Visual variety | `theme: seriph` in frontmatter |
| 📤 | PDF Export | Export slides to PDF | Share offline | `bunx turbo run export --filter=@slides/{name}` |
| 🏗️ | Build Static | Build slides as static sites | Deploy anywhere | `bunx turbo run build --filter=@slides/{name}` |
| ⚡ | Bun Runtime | Fast package management and scripts | Quick installs, native ESM | `bun install` |
| 🔍 | Smart Filtering | Run tasks on specific workspaces | Save time during dev | `--filter=@slides/{name}` |
| 📦 | Workspace Protocol | Internal deps via `workspace:*` | Version consistency | `"@slides/shared": "workspace:*"` |
| 🎯 | Per-Project Slides | Each app has its own `slides.md` | Isolated content | `apps/{name}/slides.md` |
| 📐 | Shared Layouts | SectionDivider, CenterLayout | Consistent slide layouts | `import { SectionDivider } from '@slides/shared'` |
| 🔧 | Slide Utils | `formatSlideTitle`, `slugify` helpers | Code reuse | `import { slugify } from '@slides/shared'` |

## Quick Start

<table><tr><td width="50%" valign="top">

1. **Clone and Install** — `terminal`

Clone the repo and install dependencies.

```bash
git clone https://github.com/newkub/slides.git
cd slides
bun install
```

2. **Run a Presentation** — `terminal`

Start the Slidev dev server for a specific project.

```bash
bunx turbo run dev --filter=@slides/learn-rust
```

Opens at `http://localhost:3031`

3. **Build Static Site** — `terminal`

Build slides as a static site for deployment.

```bash
bunx turbo run build --filter=@slides/learn-rust
```

Output: `apps/learn-rust/dist/`

4. **Export to PDF** — `terminal`

Export slides to a PDF file for offline sharing.

```bash
bunx turbo run export --filter=@slides/learn-rust
```

5. **Create New Slide Project** — `terminal`

Create a new slide project with shared components.

```bash
mkdir apps/my-topic
```

```json
### apps/my-topic/package.json
{
  "name": "@slides/my-topic",
  "version": "1.0.0",
  "type": "module",
  "private": true,
  "scripts": {
    "dev": "slidev slides.md --open",
    "build": "slidev build slides.md --out dist",
    "export": "slidev export slides.md",
    "verify": "echo \"no verify needed\""
  },
  "dependencies": {
    "@slides/shared": "workspace:*"
  }
}
```

```bash
bun install
bunx turbo run dev --filter=@slides/my-topic
```

</td><td width="50%" valign="top">

<p align="center">

Quick start shows the result of running each step.<br>
Turbo + Slidev work together seamlessly.

</p>

```ansi
┌─────────────────────────────────────┐
│  ✓ Cloned                           │
│  ✓ Installed (1278 packages)        │
│                                     │
│  ● turbo 2.10.3                     │
│  ● @slidev/cli 52.16.0              │
│  ● @slidev/theme-seriph 0.25.0      │
│                                     │
│  ── Running dev server ──           │
│                                     │
│  ●■▲                                │
│  Slidev  v52.16.0                   │
│                                     │
│  theme       seriph                 │
│  css engine  unocss                 │
│  entry       slides.md              │
│                                     │
│  ● public slide show                │
│    http://localhost:3031/           │
│                                     │
│  ● presenter mode                   │
│    http://localhost:3031/presenter  │
│                                     │
│  ● slides overview                  │
│    http://localhost:3031/overview   │
│                                     │
│  ✓ Build → dist/                    │
│  ✓ Export → slides.pdf              │
└─────────────────────────────────────┘
```

</td></tr></table>

## Usage

<table><tr><td width="50%" valign="top">

### slides.md

```markdown
### apps/learn-rust/slides.md
---
theme: seriph
title: Rust for TypeScript Developers
---

# Rust for TypeScript Developers

import { TopicCard, ComparisonTable } from '@slides/shared'

<TopicCard title="Rust" description="Systems programming language" icon="🦀" />

---

## Ownership vs Garbage Collection

<ComparisonTable
  headers={["Feature", "Rust", "TypeScript"]}
  rows={[
    ["Memory", "Ownership", "GC"],
    ["Safety", "Compile-time", "Runtime"],
  ]}
/>
```

</td><td width="50%" valign="top">

<p align="center">

Use shared components in any slide project.<br>
Import from `@slides/shared` directly in Markdown.

</p>

```ansi
┌─────────────────────────────────┐
│  Slidev v52.16.0                │
│                                 │
│  theme       seriph             │
│  css engine  unocss             │
│  entry       slides.md          │
│                                 │
│  ● public slide show            │
│    http://localhost:3031/       │
│                                 │
│  ● presenter mode               │
│    http://localhost:3031/pre    │
│                                 │
│  ● slides overview              │
│    http://localhost:3031/over   │
└─────────────────────────────────┘
```

</td></tr></table>

## API References

<details><summary>Shared Components (@slides/shared)</summary>

| Icon | Component | Props | Description |
|------|-----------|-------|-------------|
| 📝 | `CodeBlock` | `title?`, `filename?`, `lang?` | Code block wrapper with optional filename header |
| 🎴 | `TopicCard` | `title`, `description?`, `icon?` | Card component for topic highlights |
| 📊 | `ComparisonTable` | `headers: string[]`, `rows: string[][]` | Table for side-by-side comparisons |
| 📐 | `SectionDivider` | `title?` | Full-height centered section divider layout |
| 🎯 | `CenterLayout` | `title?` | Centered content layout for slides |

</details>

<details><summary>Shared Utilities (@slides/shared)</summary>

| Icon | Function | Signature | Description |
|------|----------|-----------|-------------|
| 🏷️ | `formatSlideTitle` | `(title: string) => string` | Convert `kebab-case` to `Title Case` |
| 🔗 | `slugify` | `(text: string) => string` | Convert text to URL-safe slug |

</details>

<details><summary>Turbo Tasks</summary>

| Icon | Task | Command | Description |
|------|------|---------|-------------|
| 🚀 | `dev` | `turbo run dev` | Start Slidev dev servers (persistent) |
| 📦 | `build` | `turbo run build` | Build static sites with caching |
| 📤 | `export` | `turbo run export` | Export slides to PDF |
| ✅ | `verify` | `turbo run verify` | Run verification checks |

</details>

## Development

<details><summary>Tech Stack</summary>

| Layer | Technology | Version | Description |
|-------|-----------|---------|-------------|
| Runtime | Bun | 1.3.13 | JavaScript runtime and package manager |
| Monorepo | Turborepo | 2.10.3 | Task orchestration and caching |
| Slides | Slidev | 52.16.0 | Vue-based presentation framework |
| UI | Vue | 3.5.33 | Reactive UI framework for components |
| Theme | @slidev/theme-seriph | 0.25.0 | Serif typography theme |
| Theme | @slidev/theme-default | 0.25.0 | Default Slidev theme |
| Language | TypeScript | ESNext | Type-safe components and utilities |
| Module | ESM | ESNext | ES Modules throughout |

</details>

<details><summary>How It Work</summary>

```ansi
┌──────────────────────────────────────────────────┐
│                  Monorepo Flow                    │
│                                                   │
│  📦 Root package.json                             │
│  ├── @slidev/cli + themes + vue                   │
│  ├── turbo (devDependency)                        │
│  └── workspaces: apps/*, packages/*               │
│                                                   │
│  🔧 turbo.json                                    │
│  ├── dev (persistent, no cache)                   │
│  ├── build (cached, dependsOn ^build)             │
│  ├── export (dependsOn ^build)                    │
│  └── verify (dependsOn ^build)                    │
│                                                   │
│  🧩 packages/shared                               │
│  ├── Components: CodeBlock, TopicCard, Comparison │
│  ├── Layouts: SectionDivider, CenterLayout        │
│  └── Utils: formatSlideTitle, slugify             │
│                                                   │
│  📝 apps/learn-rust                               │
│  ├── slides.md (content)                          │
│  └── depends on @slides/shared                    │
│                                                   │
│  📝 apps/solidjs                                  │
│  ├── slides.md + components/ + pages/             │
│  └── depends on @slides/shared                    │
│                                                   │
│  ⚡ bun install → bunx turbo run dev              │
└──────────────────────────────────────────────────┘
```

</details>

<details><summary>Architecture</summary>

```
slides/
├── package.json                  # Root: turbo + bun workspaces + slidev deps
├── turbo.json                    # Turbo tasks: dev, build, export, verify
├── bun.lock                      # Lockfile
├── .gitignore                    # Ignores: node_modules, dist, .turbo, .slidev
├── packages/
│   └── shared/                   # @slides/shared workspace
│       ├── package.json          # Exports: ., ./components/*, ./layouts/*, ./utils/*
│       ├── tsconfig.json         # ESNext + strict + jsx: preserve
│       └── src/
│           ├── index.ts          # Barrel exports
│           ├── components/
│           │   ├── CodeBlock.vue       # Code block wrapper
│           │   ├── TopicCard.vue       # Topic highlight card
│           │   └── ComparisonTable.vue # Side-by-side comparison table
│           ├── layouts/
│           │   ├── SectionDivider.vue  # Full-height section divider
│           │   └── CenterLayout.vue     # Centered content layout
│           └── utils/
│               └── slide-utils.ts      # formatSlideTitle, slugify
└── apps/
    ├── learn-rust/               # @slides/learn-rust workspace
    │   ├── package.json          # depends on @slides/shared
    │   └── slides.md             # Rust for TypeScript Developers
    └── solidjs/                  # @slides/solidjs workspace
        ├── package.json          # depends on @slides/shared
        ├── slides.md             # SolidJS Presentation
        ├── components/
        │   └── Counter.vue       # Project-specific component
        ├── pages/
        │   └── imported-slides.md
        └── snippets/
            └── external.ts
```

</details>

<details><summary>Scripts</summary>

```json
{
  "dev": "turbo run dev",          // Start all dev servers
  "build": "turbo run build",      // Build all slide projects
  "export": "turbo run export",    // Export all slides to PDF
  "verify": "turbo run verify"     // Run verification checks
}
```

</details>

<details><summary>Workspaces</summary>

| Icon | Workspace | Package Name | Description |
|------|-----------|-------------|-------------|
| 📦 | `packages/shared` | `@slides/shared` | Shared Vue components, layouts, utils |
| 📝 | `apps/learn-rust` | `@slides/learn-rust` | Rust for TypeScript Developers |
| 📝 | `apps/solidjs` | `@slides/solidjs` | SolidJS Presentation |

</details>

## License

MIT License — see [LICENSE](LICENSE) for details.
