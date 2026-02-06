# Blog Implementation Verification Checklist

Use this checklist to verify the blog is working correctly:

## Local Development

- [ ] `cd blog && npm install` completes without errors
- [ ] `npm run dev` starts dev server at http://localhost:4321
- [ ] Homepage loads and displays post card
- [ ] Dark mode toggle works (switches theme and persists)
- [ ] Clicking post card navigates to post detail page
- [ ] Post content renders with proper styling
- [ ] Images display correctly
- [ ] Tag links work
- [ ] Header navigation links work
- [ ] Search functionality filters posts
- [ ] `npm run build` completes successfully
- [ ] `npm run preview` serves the built site

## Generated Build

- [ ] `dist/` directory contains all static files
- [ ] `dist/index.html` exists (homepage)
- [ ] `dist/notebook-lm-generator/index.html` exists (post page)
- [ ] `dist/tags/index.html` exists (tags page)
- [ ] `dist/tags/claude-code/index.html` exists (tag filter page)
- [ ] `dist/rss.xml` is valid RSS feed
- [ ] `dist/search.json` contains post data
- [ ] `dist/images/notebook-generator.gif` exists

## Features

- [ ] **SEO**: Meta tags present in page source
- [ ] **Dark Mode**: 
  - [ ] System preference detection works
  - [ ] Manual toggle persists across page loads
  - [ ] No flash of wrong theme on page load
- [ ] **Search**:
  - [ ] Search input appears on homepage
  - [ ] Typing filters results in real-time
  - [ ] Results link to correct posts
- [ ] **Tags**:
  - [ ] All tags page shows tag list with counts
  - [ ] Clicking tag shows filtered posts
  - [ ] Tag counts are correct
- [ ] **RSS**:
  - [ ] Feed validates at https://validator.w3.org/feed/
  - [ ] Contains all published posts
  - [ ] Metadata is correct
- [ ] **Comments**:
  - [ ] Giscus placeholder loads (won't work until configured)
  - [ ] Instructions in component are clear

## Responsive Design

- [ ] Mobile view (< 768px) displays correctly
- [ ] Tablet view (768-1024px) displays correctly
- [ ] Desktop view (> 1024px) displays correctly
- [ ] Navigation collapses appropriately
- [ ] Images scale correctly
- [ ] Text remains readable at all sizes

## Performance

- [ ] Lighthouse score > 90 for Performance
- [ ] Lighthouse score > 90 for Accessibility
- [ ] Lighthouse score > 90 for Best Practices
- [ ] Lighthouse score > 90 for SEO
- [ ] Page load time < 2s on 3G connection

## Deployment (Vercel)

- [ ] Project created in Vercel dashboard
- [ ] Root directory set to `blog`
- [ ] Build succeeds on Vercel
- [ ] Production URL is accessible
- [ ] All routes work in production
- [ ] Assets load correctly (images, CSS, JS)
- [ ] Dark mode works in production
- [ ] Search works in production

## Optional: Giscus Setup

- [ ] GitHub Discussions enabled on repository
- [ ] Giscus app installed on repository
- [ ] Configuration IDs obtained from giscus.app
- [ ] `src/components/Giscus.astro` updated with IDs
- [ ] Comments widget loads on post pages
- [ ] Can post test comment
- [ ] Comments appear for other users

## Browser Testing

- [ ] Chrome/Edge (Chromium)
- [ ] Firefox
- [ ] Safari
- [ ] Mobile Safari (iOS)
- [ ] Mobile Chrome (Android)

## Content Management

- [ ] Can create new post in `src/content/posts/`
- [ ] Frontmatter validation works (build fails on invalid)
- [ ] Draft posts don't appear in production
- [ ] Images can be added to `public/images/`
- [ ] New tags automatically generate tag pages

## Issues Found

Document any issues discovered during verification:

1. _None yet_

---

## Quick Test Commands

```bash
# Development
cd blog
npm run dev

# Build test
npm run build

# Preview build
npm run preview

# Validate RSS
curl http://localhost:4321/rss.xml | xmllint --format -

# Check search index
curl http://localhost:4321/search.json | jq .

# Lighthouse test (requires Chrome)
npx lighthouse http://localhost:4321 --view
```
