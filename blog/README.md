# agent-zym Blog

Astro-powered blog for the agent-zym Claude Code plugin marketplace.

## Development

```bash
# Install dependencies
npm install

# Start dev server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Features

- **Static Site Generation** - Fast, SEO-friendly static pages
- **MDX Support** - Write posts in MDX with full React component support
- **Dark Mode** - System-aware theme with manual toggle
- **Search** - Client-side search with instant results
- **RSS Feed** - `/rss.xml` for feed readers
- **Tags** - Browse posts by topic
- **Comments** - Giscus integration (requires GitHub Discussions setup)
- **Responsive Design** - Mobile-first Tailwind CSS styling

## Project Structure

```
blog/
├── src/
│   ├── components/        # Reusable UI components
│   ├── content/
│   │   ├── config.ts      # Content collection schema
│   │   └── posts/         # Blog posts (MDX)
│   ├── layouts/           # Page layouts
│   ├── pages/             # Routes
│   │   ├── index.astro    # Homepage
│   │   ├── [...slug].astro # Dynamic post routes
│   │   ├── tags/          # Tag pages
│   │   ├── rss.xml.ts     # RSS feed
│   │   └── search.json.ts # Search index
│   └── styles/
│       └── global.css     # Global styles + Tailwind
├── public/
│   └── images/            # Static images
└── astro.config.mjs       # Astro configuration
```

## Writing Posts

Create a new `.mdx` file in `src/content/posts/`:

```mdx
---
title: "Your Post Title"
description: "A brief description"
pubDate: 2025-02-04
tags: ["tag1", "tag2"]
image: "/images/your-image.jpg"  # Optional
draft: false  # Set to true to hide from production
---

Your post content here...
```

## Deployment

### Vercel (Recommended)

1. Push to GitHub
2. Import project in Vercel
3. Set **Root Directory** to `blog`
4. Deploy

The site will be available at the configured domain.

## Enabling Comments

To enable Giscus comments:

1. Enable GitHub Discussions on the repository
2. Visit [giscus.app](https://giscus.app)
3. Configure and get the required IDs
4. Update `src/components/Giscus.astro` with:
   - `data-repo-id`
   - `data-category`
   - `data-category-id`

## Configuration

Edit `astro.config.mjs`:

```js
export default defineConfig({
  site: 'https://your-domain.com', // Your site URL
  output: 'static',
  // ...
});
```
