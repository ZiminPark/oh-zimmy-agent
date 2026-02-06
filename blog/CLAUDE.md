# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Astro-powered static blog for the agent-zym Claude Code plugin marketplace. Deployed to https://agent-zym.vercel.app with Vercel.

## Development Commands

```bash
# Install dependencies
npm install

# Start dev server (with hot reload)
npm run dev

# Build for production
npm run build

# Preview production build locally
npm run preview
```

## Architecture

### Content System

The blog uses Astro's Content Collections API for type-safe content management:

- **Schema**: Defined in `src/content/config.ts` with Zod validation
- **Posts**: Located in `src/content/posts/*.mdx` with frontmatter validation
- **Draft filtering**: Posts with `draft: true` are excluded from production builds (filtered in RSS, search index, and post listings)

### Routing

- **Homepage**: `src/pages/index.astro` - Lists all published posts
- **Post pages**: `src/pages/[...slug].astro` - Dynamic catch-all route using `getStaticPaths()` from content collection
- **Tag pages**: `src/pages/tags/[tag].astro` - Dynamic tag filtering
- **RSS feed**: `src/pages/rss.xml.ts` - API route generating RSS XML
- **Search index**: `src/pages/search.json.ts` - API route generating JSON for client-side search

### Search Implementation

Client-side search without external dependencies:

1. `src/pages/search.json.ts` generates a JSON index of all posts at build time
2. `src/components/Search.astro` fetches `/search.json` and filters in-browser
3. Searches across title, description, and tags with instant results

### Layouts

- **BaseLayout**: `src/layouts/BaseLayout.astro` - HTML shell, SEO tags, dark mode setup
- **PostLayout**: `src/layouts/PostLayout.astro` - Blog post template with Giscus comments

### Styling

- Tailwind CSS 4.x with `@tailwindcss/vite` plugin
- Dark mode via `class` strategy (toggled with `ThemeToggle.astro`)
- Typography with Tailwind's `prose` classes for MDX content

## Writing Posts

Create `src/content/posts/your-post.mdx`:

```mdx
---
title: "Post Title"
description: "Brief description"
pubDate: 2025-02-04
tags: ["tag1", "tag2"]
image: "/images/cover.jpg"  # Optional
draft: false  # Set true to hide from production
---

Content here...
```

Place images in `public/images/` and reference as `/images/filename.jpg`.

## Deployment

Deploys to Vercel with configuration in `vercel.json`:

- **Build command**: `npm run build`
- **Output directory**: `dist`
- **Root directory**: Must be set to `blog` in Vercel dashboard (monorepo setup)
- **Vercel project**: `blog` under `zimmys-projects-be125baa` scope
- **Important**: The `blog/` directory must be committed as a regular subdirectory (not a git submodule). If it's registered as a submodule without a `.gitmodules` file, Vercel will fail to fetch it and the build will error with `ENOENT: package.json not found`.

Site URL is configured in `astro.config.mjs` (`site` property) and used for RSS feed generation.

### Debugging Vercel Deployment Failures

```bash
# List recent deployments and find the failed one
vercel ls blog

# Inspect a deployment for basic info (works on errored deployments)
vercel inspect <deployment-url>

# For errored deployments, `vercel logs` won't work. Use the API instead:
VERCEL_TOKEN=$(python3 -c "import json; print(json.load(open('$HOME/Library/Application Support/com.vercel.cli/auth.json'))['token'])")
curl -s "https://api.vercel.com/v2/deployments/<deployment-id>/events" \
  -H "Authorization: Bearer $VERCEL_TOKEN" | python3 -c "
import json, sys
for e in json.load(sys.stdin):
    text = e.get('payload', {}).get('text', '')
    if text: print(e['type'], text)
"
```

## Giscus Comments

Comments are integrated via `src/components/Giscus.astro` using GitHub Discussions. To enable:

1. Enable Discussions on the GitHub repository
2. Configure at https://giscus.app
3. Update `data-repo-id`, `data-category`, and `data-category-id` in `Giscus.astro`
