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
| ![target](https://api.iconify.design/mdi:target.svg) | Centralized slide management | ✓ Goal | Single repo for all Slidev presentations |
| ![puzzle](https://api.iconify.design/mdi:puzzle.svg) | Shared components | ✓ Goal | Reusable Vue components across all slide projects |
| ![bolt](https://api.iconify.design/mdi:flash.svg) | Turbo task orchestration | ✓ Goal | Build, dev, export tasks via Turborepo caching |
| ![package](https://api.iconify.design/mdi:package-variant.svg) | Per-project package.json | ✗ Not Goal | Root-level dependencies only for Slidev core |
| ![building](https://api.iconify.design/mdi:domain-off.svg) | Full web app | ✗ Not Goal | Presentation slides only, not a web application |

</details>

<details><summary>Scope</summary>

| Icon | Scope | Status | Description |
|------|-------|--------|-------------|
| ![chart](https://api.iconify.design/mdi:presentation.svg) | Slidev presentations | ✓ In Scope | Markdown-based slide decks with Vue components |
| ![palette](https://api.iconify.design/mdi:palette.svg) | Shared Vue components | ✓ In Scope | CodeBlock, TopicCard, ComparisonTable, layouts |
| ![wrench](https://api.iconify.design/mdi:wrench.svg) | Turbo build pipeline | ✓ In Scope | Cached builds, filtered dev servers, PDF export |
| ![web](https://api.iconify.design/mdi:web-off.svg) | Web hosting | ✗ Out of Scope | Slides are presented locally, not deployed |
| ![mobile](https://api.iconify.design/mdi:cellphone-off.svg) | Mobile slides | ✗ Out of Scope | Desktop-first presentation slides |

</details>

<details><summary>Key Concepts</summary>

| Icon | Concept | Description |
|------|---------|-------------|
| ![doc](https://api.iconify.design/mdi:file-presentation-box.svg) | Slidev | Vue-based presentation framework using Markdown |
| ![building](https://api.iconify.design/mdi:domain.svg) | Turborepo | Monorepo task runner with caching and filtering |
| ![package](https://api.iconify.design/mdi:package-variant.svg) | Bun Workspaces | Package manager with workspace protocol support |
| ![puzzle](https://api.iconify.design/mdi:puzzle.svg) | Shared Package | `@slides/shared` exports components, layouts, utils |
| ![palette](https://api.iconify.design/mdi:palette.svg) | Vue SFC | Single File Components for reusable slide elements |

</details>

<details><summary>Core Principles</summary>

| Icon | Principle | Description |
|------|-----------|-------------|
| ![puzzle](https://api.iconify.design/mdi:puzzle.svg) | DRY | Shared components avoid duplication across slide projects |
| ![bolt](https://api.iconify.design/mdi:flash.svg) | Fast Dev | Turbo caching + Bun speed for instant dev servers |
| ![doc](https://api.iconify.design/mdi:file-document-edit.svg) | Content First | Each project is just `slides.md` + optional components |
| ![link](https://api.iconify.design/mdi:link-variant.svg) | Workspace Protocol | `workspace:*` for internal dependencies |

</details>

<details><summary>When To Use</summary>

| Icon | Use Case | Description |
|------|----------|-------------|
| ![school](https://api.iconify.design/mdi:school.svg) | Learning topics | Create slide decks for topics you're learning |
| ![presentation](https://api.iconify.design/mdi:presentation.svg) | Team presentations | Share technical talks with your team |
| ![language](https://api.iconify.design/mdi:language.svg) | Language deep dives | Compare languages like Rust vs TypeScript |
| ![framework](https://api.iconify.design/mdi:cube.svg) | Framework overviews | Present SolidJS, Vue, or other frameworks |

</details>

<details><summary>Best Practices</summary>

| Icon | Practice | Description |
|------|----------|-------------|
| ![puzzle](https://api.iconify.design/mdi:puzzle.svg) | Use shared components | Import from `@slides/shared` instead of duplicating |
| ![folder](https://api.iconify.design/mdi:folder.svg) | One slide per concept | Keep each slide focused on a single topic |
| ![palette](https://api.iconify.design/mdi:palette.svg) | Use themes | Set `theme: seriph` or `theme: default` in frontmatter |
| ![search](https://api.iconify.design/mdi:magnify.svg) | Filter dev server | Use `--filter=@slides/{name}` to run one project |
| ![package](https://api.iconify.design/mdi:package-variant.svg) | Root dependencies | Keep Slidev CLI and themes at root level |

</details>

## Features

| Icon | Feature | Description | Benefit | Usage |
|------|---------|-------------|--------|-------|
| ![building](https://api.iconify.design/mdi:domain.svg) | Turborepo Monorepo | Task orchestration with caching | Fast builds, filtered dev servers | `bunx turbo run dev --filter=@slides/learn-rust` |
| ![puzzle](https://api.iconify.design/mdi:puzzle.svg) | Shared Components | Vue SFCs reusable across all slides | DRY, consistent UI | `import { TopicCard } from '@slides/shared'` |
| ![doc](https://api.iconify.design/mdi:file-presentation-box.svg) | Slidev Integration | Markdown-based slides with Vue | Rich presentations with code | `slidev slides.md --open` |
| ![palette](https://api.iconify.design/mdi:palette.svg) | Dual Themes | Seriph and default themes included | Visual variety | `theme: seriph` in frontmatter |
| ![export](https://api.iconify.design/mdi:file-export.svg) | PDF Export | Export slides to PDF | Share offline | `bunx turbo run export --filter=@slides/{name}` |
| ![build](https://api.iconify.design/mdi:hammer.svg) | Build Static | Build slides as static sites | Deploy anywhere | `bunx turbo run build --filter=@slides/{name}` |
| ![bolt](https://api.iconify.design/mdi:flash.svg) | Bun Runtime | Fast package management and scripts | Quick installs, native ESM | `bun install` |
| ![search](https://api.iconify.design/mdi:magnify.svg) | Smart Filtering | Run tasks on specific workspaces | Save time during dev | `--filter=@slides/{name}` |
| ![package](https://api.iconify.design/mdi:package-variant.svg) | Workspace Protocol | Internal deps via `workspace:*` | Version consistency | `"@slides/shared": "workspace:*"` |
| ![target](https://api.iconify.design/mdi:target.svg) | Per-Project Slides | Each app has its own `slides.md` | Isolated content | `apps/{name}/slides.md` |
| ![layout](https://api.iconify.design/mdi:view-quilt.svg) | Shared Layouts | SectionDivider, CenterLayout | Consistent slide layouts | `import { SectionDivider } from '@slides/shared'` |
| ![wrench](https://api.iconify.design/mdi:wrench.svg) | Slide Utils | `formatSlideTitle`, `slugify` helpers | Code reuse | `import { slugify } from '@slides/shared'` |

## Quick Start

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

## Usage

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

## API References

<details><summary>Shared Components (@slides/shared)</summary>

| Icon | Component | Props | Description |
|------|-----------|-------|-------------|
| ![code](https://api.iconify.design/mdi:code-tags.svg) | `CodeBlock` | `title?`, `filename?`, `lang?` | Code block wrapper with optional filename header |
| ![card](https://api.iconify.design/mdi:card-text.svg) | `TopicCard` | `title`, `description?`, `icon?` | Card component for topic highlights |
| ![table](https://api.iconify.design/mdi:table.svg) | `ComparisonTable` | `headers: string[]`, `rows: string[][]` | Table for side-by-side comparisons |
| ![layout](https://api.iconify.design/mdi:view-quilt.svg) | `SectionDivider` | `title?` | Full-height centered section divider layout |
| ![target](https://api.iconify.design/mdi:target.svg) | `CenterLayout` | `title?` | Centered content layout for slides |

</details>

<details><summary>Shared Utilities (@slides/shared)</summary>

| Icon | Function | Signature | Description |
|------|----------|-----------|-------------|
| ![tag](https://api.iconify.design/mdi:tag.svg) | `formatSlideTitle` | `(title: string) => string` | Convert `kebab-case` to `Title Case` |
| ![link](https://api.iconify.design/mdi:link-variant.svg) | `slugify` | `(text: string) => string` | Convert text to URL-safe slug |

</details>

<details><summary>Turbo Tasks</summary>

| Icon | Task | Command | Description |
|------|------|---------|-------------|
| ![rocket](https://api.iconify.design/mdi:rocket.svg) | `dev` | `turbo run dev` | Start Slidev dev servers (persistent) |
| ![package](https://api.iconify.design/mdi:package-variant.svg) | `build` | `turbo run build` | Build static sites with caching |
| ![export](https://api.iconify.design/mdi:file-export.svg) | `export` | `turbo run export` | Export slides to PDF |
| ![check](https://api.iconify.design/mdi:check-circle.svg) | `verify` | `turbo run verify` | Run verification checks |

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
| ![package](https://api.iconify.design/mdi:package-variant.svg) | `packages/shared` | `@slides/shared` | Shared Vue components, layouts, utils |
| ![doc](https://api.iconify.design/mdi:file-presentation-box.svg) | `apps/learn-rust` | `@slides/learn-rust` | Rust for TypeScript Developers |
| ![doc](https://api.iconify.design/mdi:file-presentation-box.svg) | `apps/solidjs` | `@slides/solidjs` | SolidJS Presentation |

</details>

## License

MIT License — see [LICENSE](LICENSE) for details.
