# Slides

Slidev presentations monorepo — Turborepo + Bun workspaces พร้อม `packages/shared` สำหรับ shared components/layouts/utils

## โครงสร้าง

```
slides/
├── package.json              # root — turbo + bun workspaces
├── turbo.json                # turbo config
├── packages/
│   └── shared/               # @slides/shared — shared Vue components, layouts, utils
│       ├── src/
│       │   ├── components/   # CodeBlock, TopicCard, ComparisonTable
│       │   ├── layouts/      # SectionDivider, CenterLayout
│       │   └── utils/        # slide-utils
│       └── package.json
└── apps/
    ├── learn-rust/           # Rust for TypeScript Developers
    │   ├── slides.md
    │   └── package.json
    └── solidjs/              # SolidJS Presentation
        ├── slides.md
        ├── components/
        ├── pages/
        ├── snippets/
        └── package.json
```

## การใช้งาน

### รัน dev server ผ่าน Turbo

```bash
# รันทั้งหมด
bun run dev

# รันเฉพาะ project
bunx turbo run dev --filter=@slides/learn-rust
bunx turbo run dev --filter=@slides/solidjs
```

### Build ผ่าน Turbo

```bash
bun run build
bunx turbo run build --filter=@slides/learn-rust
```

### Export เป็น PDF

```bash
bun run export
bunx turbo run export --filter=@slides/learn-rust
```

## สร้าง project ใหม่

1. สร้าง folder `apps/{project-name}/`
2. สร้าง `package.json` ที่ depends on `@slides/shared`:
   ```json
   {
     "name": "@slides/{project-name}",
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
3. สร้าง `slides.md` พร้อม headmatter
4. รัน `bun install` ที่ root
5. รัน `bunx turbo run dev --filter=@slides/{project-name}`

## ใช้ shared components

ใน `slides.md` สามารถ import จาก `@slides/shared` ได้:

```md
---
theme: seriph
---

# Title

import { TopicCard, ComparisonTable } from '@slides/shared'

<TopicCard title="Rust" description="Systems programming language" icon="🦀" />
```

## Dependencies

- `@slidev/cli` — Slidev CLI (root)
- `@slidev/theme-seriph` — Seriph theme (root)
- `@slidev/theme-default` — Default theme (root)
- `vue` — Vue 3 runtime (root + shared)
- `turbo` — Turborepo task orchestration (root devDependency)
- `@slides/shared` — Shared components, layouts, utils (workspace)
