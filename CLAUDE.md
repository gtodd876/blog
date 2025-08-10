# CLAUDE.md - Project Documentation for Claude Code

## Project Overview

This is **ToddMatthews.dev** - a personal game development blog built with **Astro 5** and deployed on **Cloudflare Workers**. The blog documents Todd's journey learning game development, particularly with Godot, and includes posts about game jams, technical challenges, and creative projects.

### Project Type
- **Static Site Generator**: Astro 5.8.0 with SSG (Static Site Generation)
- **Deployment**: Cloudflare Workers/Pages via Wrangler
- **Content Management**: File-based using Astro's Content Collections
- **Styling**: Custom CSS with Bear Blog-inspired design
- **Package Manager**: pnpm

## Quick Start

### Development
```bash
pnpm install          # Install dependencies
pnpm dev              # Start dev server at localhost:4321
```

### Build & Deploy
```bash
pnpm build            # Build for production to ./dist/
pnpm preview          # Local preview of production build
pnpm deploy           # Deploy to Cloudflare Workers
```

### Content Management
```bash
# Add new blog posts to:
src/content/blog/new-post.md

# With frontmatter:
---
title: 'Post Title'
description: 'Post description'
pubDate: 'Jul 08 2022'
heroImage: '/image.jpg'
---
```

## Architecture & Structure

### Directory Overview
```
├── public/                 # Static assets (images, fonts, favicon)
├── src/
│   ├── components/        # Reusable Astro components
│   ├── content/          # Content collections (blog posts)
│   ├── layouts/          # Page layouts
│   ├── pages/           # File-based routing
│   ├── styles/          # Global CSS
│   ├── consts.ts        # Site configuration constants
│   └── content.config.ts # Content collection schemas
├── astro.config.mjs      # Astro configuration
├── wrangler.jsonc       # Cloudflare Workers config
└── tsconfig.json        # TypeScript configuration
```

### Key Files & Their Purpose

#### Configuration Files
- **astro.config.mjs**: Main Astro config with Cloudflare adapter, MDX, and sitemap
- **wrangler.jsonc**: Cloudflare Workers deployment configuration
- **src/consts.ts**: Site metadata (SITE_TITLE, SITE_DESCRIPTION)
- **src/content.config.ts**: Content collection schemas and validation

#### Core Components
- **src/components/BaseHead.astro**: HTML head with SEO, Open Graph, fonts
- **src/components/Header.astro**: Site navigation
- **src/components/Footer.astro**: Site footer
- **src/components/FormattedDate.astro**: Date formatting utility

#### Page Structure
- **src/pages/index.astro**: Homepage with blog post grid
- **src/pages/blog/index.astro**: Blog archive page
- **src/pages/blog/[...slug].astro**: Dynamic blog post pages
- **src/layouts/BlogPost.astro**: Blog post layout template

#### Styling
- **src/styles/global.css**: Global styles based on Bear Blog design
- Uses Atkinson font family (loaded from `/public/fonts/`)
- CSS custom properties for theming
- Responsive design with mobile-first approach

### Content Collections

The blog uses Astro's Content Collections for type-safe content management:

```typescript
// src/content.config.ts
const blog = defineCollection({
  loader: glob({ base: './src/content/blog', pattern: '**/*.{md,mdx}' }),
  schema: z.object({
    title: z.string(),
    description: z.string(),
    pubDate: z.coerce.date(),
    updatedDate: z.coerce.date().optional(),
    heroImage: z.string().optional(),
  }),
});
```

Posts are stored in `src/content/blog/` and support both Markdown and MDX.

### Deployment Architecture

- **Build Target**: Cloudflare Workers with static assets
- **Build Output**: `./dist/` directory
- **Worker Script**: `./dist/_worker.js/index.js`
- **Static Assets**: Served via Cloudflare's asset binding
- **Preview**: `pnpm preview` uses Wrangler dev server

## Development Guidelines

### Adding New Blog Posts

1. Create a new `.md` or `.mdx` file in `src/content/blog/`
2. Include required frontmatter:
   ```yaml
   ---
   title: 'Your Post Title'
   description: 'Brief description'
   pubDate: 'Jul 08 2022'
   heroImage: '/hero-image.jpg'  # Optional
   ---
   ```
3. Add hero image to `public/` if used
4. Posts automatically appear on homepage and blog index

### Styling Guidelines

- Global styles in `src/styles/global.css`
- Component-specific styles use Astro's `<style>` blocks
- CSS custom properties defined in `:root`
- Mobile-first responsive design
- Bear Blog aesthetic: minimal, clean, readable

### Content Guidelines

- Focus on game development topics (Godot, game jams, technical challenges)
- Include code examples and technical details
- Use hero images for visual appeal
- Write engaging, personal narratives about the development journey

## Key Features

### SEO & Performance
- ✅ 100/100 Lighthouse performance (as claimed in README)
- ✅ SEO-friendly with canonical URLs and OpenGraph data
- ✅ Automatic sitemap generation
- ✅ RSS feed support (`/rss.xml`)
- ✅ Font preloading for performance

### Content Features
- ✅ Markdown & MDX support
- ✅ Type-safe frontmatter validation
- ✅ Automatic date formatting
- ✅ Hero images for posts
- ✅ Blog post sorting by date (newest first)

### Technical Features
- ✅ TypeScript with strict configuration
- ✅ Cloudflare Workers deployment
- ✅ Static site generation
- ✅ Content collections for type safety
- ✅ Responsive design

## Current Content

The blog currently has one post: **"First post"** (published May 25, 2025) covering:
- Slippery Socks - first Ludum Dare game jam entry
- Technical challenges with mixing pixel art and smooth fonts in Godot
- Triads - a musical memory game exploring Godot's UI capabilities
- Plans for future Frogger clone with hand-drawn animations

## Troubleshooting

### Common Issues
- **Build failures**: Check Astro and TypeScript configurations
- **Deployment issues**: Verify Wrangler configuration and Cloudflare credentials
- **Content not appearing**: Ensure proper frontmatter format and file location
- **Styling issues**: Check CSS custom properties and responsive breakpoints

### Development Tips
- Use `pnpm dev` with hot reload for efficient development
- Test builds locally with `pnpm preview` before deployment
- Images should be placed in `public/` and referenced with absolute paths
- Content collections provide type safety - leverage TypeScript for better DX

## Dependencies

### Core Dependencies
- **astro**: ^5.8.0 - Main framework
- **@astrojs/cloudflare**: ^12.5.3 - Cloudflare adapter
- **@astrojs/mdx**: ^4.3.0 - MDX support
- **@astrojs/rss**: ^4.0.11 - RSS feed generation
- **@astrojs/sitemap**: ^3.4.0 - Sitemap generation

### Development Dependencies
- **@types/node**: ^22.15.21 - Node.js types
- **wrangler**: ^4.16.1 - Cloudflare Workers CLI

This is a mature, well-structured Astro blog with a clean architecture suitable for ongoing game development blogging.