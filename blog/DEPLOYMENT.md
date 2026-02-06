# Deployment Guide

## Vercel Deployment (Recommended)

### Initial Setup

1. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Add Astro blog"
   git push origin main
   ```

2. **Create Vercel Project**
   - Go to [vercel.com](https://vercel.com)
   - Click "New Project"
   - Import your GitHub repository (ZiminPark/agent-zym)
   - Configure project settings:
     - **Root Directory**: `blog`
     - **Build Command**: `npm run build` (auto-detected)
     - **Output Directory**: `dist` (auto-detected)
     - **Install Command**: `npm install` (auto-detected)

3. **Deploy**
   - Click "Deploy"
   - Wait for build to complete
   - Your blog will be live at `https://agent-zym.vercel.app` (or your custom domain)

### Subsequent Deployments

Vercel automatically deploys on every push to the main branch. No manual action needed!

## Environment Setup

No environment variables are required for basic functionality.

### Optional: Giscus Comments

To enable comments:

1. Enable GitHub Discussions on the repository:
   - Go to repository Settings
   - Scroll to "Features"
   - Check "Discussions"

2. Configure Giscus:
   - Visit [giscus.app](https://giscus.app)
   - Enter repository: `ZiminPark/agent-zym`
   - Choose mapping: `pathname` (recommended)
   - Choose discussion category (create one if needed)
   - Copy the configuration values

3. Update `src/components/Giscus.astro`:
   ```html
   <script
     src="https://giscus.app/client.js"
     data-repo="ZiminPark/agent-zym"
     data-repo-id="YOUR_REPO_ID"
     data-category="YOUR_CATEGORY"
     data-category-id="YOUR_CATEGORY_ID"
     data-mapping="pathname"
     data-strict="0"
     data-reactions-enabled="1"
     data-emit-metadata="0"
     data-input-position="bottom"
     data-theme="preferred_color_scheme"
     data-lang="en"
     crossorigin="anonymous"
     async
   ></script>
   ```

4. Commit and push to deploy

## Custom Domain

1. In Vercel project settings, go to "Domains"
2. Add your custom domain
3. Configure DNS records as instructed by Vercel
4. Update `astro.config.mjs`:
   ```js
   export default defineConfig({
     site: 'https://your-custom-domain.com',
     // ...
   });
   ```
5. Commit and push to redeploy

## Troubleshooting

### Build fails on Vercel

- Check build logs in Vercel dashboard
- Verify `blog` is set as Root Directory
- Ensure all dependencies are in `package.json`

### Images not loading

- Images must be in `public/images/` directory
- Reference with `/images/filename.ext` in frontmatter
- Rebuild and redeploy

### Dark mode not working

- Clear browser cache
- Check browser console for JavaScript errors
- Verify BaseHead.astro inline script is present

### Comments not showing

- Verify GitHub Discussions is enabled
- Check Giscus configuration IDs match
- Ensure repository is public or app has access

## Performance

The blog is statically generated, resulting in:
- Near-instant page loads
- Excellent SEO performance
- Zero runtime JavaScript for content (except interactive features)
- Optimized images and assets

## Monitoring

After deployment, monitor:
- Vercel Analytics (if enabled)
- RSS feed: `https://your-domain.com/rss.xml`
- Search index: `https://your-domain.com/search.json`
