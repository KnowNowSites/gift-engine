# Gift Engine - Emotional Gift Recommendations

A high-performance, SEO-optimized static affiliate website built with Astro. Provides thoughtful gift recommendations for emotional situations, relationships, and constraints.

## Features

- **Static Site Generation**: Fast, secure, and scalable with Astro
- **SEO Optimized**: Automatic sitemap generation, meta tags, Open Graph support
- **Markdown Content**: Easy content management with Markdown files
- **Responsive Design**: Mobile-first, accessible design
- **Category Pages**: Organized gift guides by category
- **Blog/Article Template**: Full-featured article layout with metadata
- **Fast Performance**: Optimized for Core Web Vitals
- **GitHub Ready**: Compatible with GitHub Pages and GitHub Actions
- **Netlify Ready**: One-click deployment to Netlify

## Project Structure

```
gift-engine-astro/
├── src/
│   ├── content/
│   │   └── guides/           # Markdown content for gift guides
│   ├── layouts/
│   │   ├── BaseLayout.astro  # Main layout with header/footer
│   │   └── BlogLayout.astro  # Article-specific layout
│   ├── pages/
│   │   ├── index.astro       # Homepage
│   │   ├── guides/
│   │   │   ├── index.astro   # All guides listing
│   │   │   └── [slug].astro  # Individual guide pages
│   │   └── categories/
│   │       ├── index.astro   # Categories listing
│   │       └── [category].astro # Category-specific pages
│   ├── styles/
│   │   └── global.css        # Global styles
│   └── env.d.ts              # TypeScript definitions
├── public/
│   └── robots.txt            # SEO robots file
├── astro.config.mjs          # Astro configuration
├── tsconfig.json             # TypeScript configuration
├── package.json              # Dependencies
└── README.md                 # This file
```

## Getting Started

### Prerequisites

- Node.js 18.14.0 or higher
- npm, yarn, or pnpm

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/gift-engine-astro.git
cd gift-engine-astro
```

2. Install dependencies:
```bash
npm install
# or
pnpm install
# or
yarn install
```

3. Start the development server:
```bash
npm run dev
```

The site will be available at `http://localhost:3000`

## Development

### Adding New Content

Create new Markdown files in `src/content/guides/`:

```markdown
---
title: "Your Gift Guide Title"
description: "Brief description of the guide"
category: "Relationships"  # or "Emotions", "Constraints"
publishDate: 2024-01-15
updatedDate: 2024-01-20
author: "Gift Engine"
tags: ["tag1", "tag2"]
---

# Your content here

Use standard Markdown formatting...
```

### Available Categories

- **Relationships**: Gifts for partners, spouses, family members
- **Emotions**: Gifts for difficult times, celebrations, emotional moments
- **Constraints**: Gifts for specific budgets or situations

### Customizing Styles

Edit `src/styles/global.css` to customize:
- Color scheme (CSS variables at `:root`)
- Typography (font families and sizes)
- Spacing and layout
- Responsive breakpoints

### Updating Site Configuration

Edit `astro.config.mjs`:
- Change `site` URL to your domain
- Modify sitemap settings
- Add additional integrations

## Building for Production

### Build the static site:
```bash
npm run build
```

This generates a `dist/` folder with all static files ready for deployment.

### Preview the build locally:
```bash
npm run preview
```

## Deployment

### Option 1: Deploy to Netlify

**Easiest Option - One-Click Deploy**

1. Push your repository to GitHub
2. Go to [Netlify](https://netlify.com)
3. Click "New site from Git"
4. Select your repository
5. Build settings:
   - Build command: `npm run build`
   - Publish directory: `dist`
6. Click "Deploy site"

**Manual Deployment**

1. Install Netlify CLI:
```bash
npm install -g netlify-cli
```

2. Build the site:
```bash
npm run build
```

3. Deploy:
```bash
netlify deploy --prod --dir=dist
```

### Option 2: Deploy to GitHub Pages

1. Update `astro.config.mjs` with your repository name:
```javascript
export default defineConfig({
  site: 'https://yourusername.github.io/gift-engine-astro',
  // ... rest of config
});
```

2. Create `.github/workflows/deploy.yml`:
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '18'
      - run: npm install
      - run: npm run build
      - uses: actions/upload-artifact@v3
        with:
          name: dist
          path: dist/

  deploy:
    needs: build
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    steps:
      - uses: actions/checkout@v3
      - uses: actions/download-artifact@v3
        with:
          name: dist
          path: dist/
      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

3. Push to GitHub and enable GitHub Pages in repository settings

### Option 3: Deploy to Vercel

1. Push your repository to GitHub
2. Go to [Vercel](https://vercel.com)
3. Click "New Project"
4. Select your repository
5. Build settings:
   - Framework: Astro
   - Build command: `npm run build`
   - Output directory: `dist`
6. Click "Deploy"

### Option 4: Deploy to Any Static Host

1. Build the site:
```bash
npm run build
```

2. Upload the `dist/` folder to your hosting provider:
   - AWS S3 + CloudFront
   - Google Cloud Storage
   - Azure Static Web Apps
   - Any FTP/SFTP server
   - Any web hosting provider supporting static sites

## SEO Features

### Automatic Sitemap
- Generated at `/sitemap-index.xml`
- Automatically includes all pages and guides
- Updates on each build

### Robots.txt
- Located at `/robots.txt`
- Configured to allow all content
- Disallows admin paths

### Meta Tags
- Automatic title generation
- Meta descriptions
- Open Graph tags for social sharing
- Twitter Card support
- Canonical URLs

### Performance
- Minimal JavaScript
- Optimized CSS
- Fast page load times
- Mobile-responsive
- Accessibility-focused

## Content Strategy

### Recommended Structure

1. **Homepage**: Overview and featured guides
2. **Guides Index**: All guides with filtering/sorting
3. **Category Pages**: Guides grouped by category
4. **Individual Guides**: Full article pages with metadata
5. **Static Pages**: Privacy, terms, affiliate disclosure

### SEO Best Practices

- Use descriptive titles (50-60 characters)
- Write compelling meta descriptions (150-160 characters)
- Include relevant keywords naturally
- Use header hierarchy (H1, H2, H3)
- Add internal links between related guides
- Include external affiliate links contextually

## Customization

### Adding Pages

Create new `.astro` files in `src/pages/`:

```astro
---
import BaseLayout from '../layouts/BaseLayout.astro';
---

<BaseLayout title="Page Title" description="Page description">
  <section class="container">
    <h1>Your Content</h1>
  </section>
</BaseLayout>
```

### Adding Components

Create reusable components in `src/components/`:

```astro
---
interface Props {
  title: string;
}

const { title } = Astro.props;
---

<div class="component">
  <h2>{title}</h2>
  <slot />
</div>

<style>
  .component {
    /* Your styles */
  }
</style>
```

### Custom Styling

- Global styles: `src/styles/global.css`
- Component styles: Use `<style>` tags in `.astro` files
- CSS Variables: Defined in `:root` selector

## Performance Optimization

### Current Optimizations

- Static generation (no server needed)
- Minimal CSS (~15KB)
- No JavaScript frameworks in production
- Optimized images
- Gzip compression
- Browser caching headers

### Further Optimization

1. **Image Optimization**:
   - Use WebP format
   - Implement lazy loading
   - Optimize image sizes

2. **CSS**:
   - Minify CSS
   - Remove unused styles
   - Use CSS variables

3. **Monitoring**:
   - Set up analytics
   - Monitor Core Web Vitals
   - Track user behavior

## Scaling to Thousands of Pages

### Content Organization

- Use consistent Markdown frontmatter
- Organize guides by category
- Use consistent naming conventions
- Create content templates

### Performance at Scale

- Astro handles thousands of pages efficiently
- Build times remain reasonable
- Static generation is predictable
- CDN distribution ensures fast delivery

### Content Management

For large content libraries:
1. Use a headless CMS (optional)
2. Automate content import
3. Implement content versioning
4. Use CI/CD for automated builds

## Troubleshooting

### Build Errors

**Issue**: Build fails with content errors
- **Solution**: Check Markdown frontmatter format
- Ensure all required fields are present
- Validate date formats

**Issue**: Images not loading
- **Solution**: Check image paths
- Ensure images are in `public/` or referenced correctly
- Use absolute paths for images

### Performance Issues

**Issue**: Slow build times
- **Solution**: Check for large assets
- Optimize images
- Consider splitting content

**Issue**: Large bundle size
- **Solution**: Review CSS
- Remove unused styles
- Check for unnecessary dependencies

## Contributing

To contribute to this project:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

MIT License - feel free to use this project for personal or commercial purposes.

## Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Check existing documentation
- Review Astro documentation at [astro.build](https://astro.build)

## Resources

- [Astro Documentation](https://docs.astro.build)
- [Astro Integrations](https://astro.build/integrations/)
- [Netlify Deployment](https://docs.netlify.com/integrations/frameworks/astro/)
- [GitHub Pages Deployment](https://docs.github.com/en/pages)

## Affiliate Disclosure

This website contains affiliate links. When you click on an affiliate link and make a purchase, we may earn a commission at no additional cost to you. This helps support the development and maintenance of this site.

---

**Built with [Astro](https://astro.build)** - The web framework for content-driven websites.
