# Deployment Guide - Gift Engine

Complete step-by-step instructions for deploying your Astro gift recommendation site to various platforms.

## Pre-Deployment Checklist

Before deploying, ensure:

- [ ] All content is finalized and proofread
- [ ] `astro.config.mjs` has correct `site` URL
- [ ] `public/robots.txt` is configured correctly
- [ ] All links are working (test locally with `npm run preview`)
- [ ] Images are optimized
- [ ] Meta descriptions are written for all pages
- [ ] Affiliate disclosure is in place
- [ ] Privacy policy and terms are added (if required)
- [ ] Build completes successfully: `npm run build`

## Option 1: Netlify (Recommended)

Netlify is the easiest option with automatic deployments and free HTTPS.

### Method A: GitHub Integration (Recommended)

1. **Push to GitHub**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/yourusername/gift-engine-astro.git
   git branch -M main
   git push -u origin main
   ```

2. **Connect to Netlify**
   - Go to [netlify.com](https://netlify.com)
   - Click "New site from Git"
   - Choose GitHub
   - Authorize Netlify
   - Select your repository

3. **Configure Build Settings**
   - Build command: `npm run build`
   - Publish directory: `dist`
   - Click "Deploy site"

4. **Custom Domain (Optional)**
   - Go to Site Settings → Domain Management
   - Add your custom domain
   - Update DNS records as instructed

### Method B: Manual Deployment

1. **Install Netlify CLI**
   ```bash
   npm install -g netlify-cli
   ```

2. **Build the Site**
   ```bash
   npm run build
   ```

3. **Deploy**
   ```bash
   netlify deploy --prod --dir=dist
   ```

### Netlify Environment Variables (if needed)

In Netlify dashboard:
1. Go to Site Settings → Build & Deploy → Environment
2. Add any environment variables
3. Redeploy

### Netlify Functions (Optional)

For affiliate link tracking or analytics:
1. Create `netlify/functions/` directory
2. Add serverless functions
3. Deploy automatically

## Option 2: GitHub Pages

Free hosting directly from your GitHub repository.

### Setup

1. **Update Configuration**
   
   Edit `astro.config.mjs`:
   ```javascript
   export default defineConfig({
     site: 'https://yourusername.github.io/gift-engine-astro',
     // ... rest of config
   });
   ```

2. **Create GitHub Actions Workflow**
   
   Create `.github/workflows/deploy.yml`:
   ```yaml
   name: Deploy to GitHub Pages

   on:
     push:
       branches: [ main ]
     pull_request:
       branches: [ main ]

   permissions:
     contents: read
     pages: write
     id-token: write

   concurrency:
     group: pages
     cancel-in-progress: false

   jobs:
     build:
       runs-on: ubuntu-latest
       steps:
         - name: Checkout your repository
           uses: actions/checkout@v3

         - name: Install, build, and upload your site
           uses: withastro/action@v1
           with:
             node-version: '18'
             package-manager: npm

     deploy:
       needs: build
       runs-on: ubuntu-latest
       environment:
         name: github-pages
         url: ${{ steps.deployment.outputs.page_url }}
       steps:
         - name: Deploy to GitHub Pages
           id: deployment
           uses: actions/deploy-pages@v1
   ```

3. **Enable GitHub Pages**
   - Go to repository Settings
   - Navigate to Pages
   - Source: GitHub Actions
   - Save

4. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Add GitHub Pages deployment"
   git push origin main
   ```

### Custom Domain with GitHub Pages

1. **Add Domain**
   - Go to Settings → Pages
   - Enter custom domain
   - Save

2. **Update DNS**
   - Add CNAME record pointing to `yourusername.github.io`
   - Or add A records (see GitHub docs)

3. **Enable HTTPS**
   - GitHub automatically provisions SSL certificate
   - May take a few minutes

## Option 3: Vercel

Excellent performance with automatic deployments.

### Setup

1. **Push to GitHub**
   ```bash
   git push origin main
   ```

2. **Connect to Vercel**
   - Go to [vercel.com](https://vercel.com)
   - Click "New Project"
   - Import your GitHub repository
   - Authorize Vercel

3. **Configure**
   - Framework: Astro
   - Build command: `npm run build`
   - Output directory: `dist`
   - Click "Deploy"

4. **Custom Domain**
   - Go to project Settings
   - Navigate to Domains
   - Add your custom domain
   - Update DNS records

## Option 4: AWS S3 + CloudFront

For enterprise-grade hosting with CDN.

### Setup

1. **Create S3 Bucket**
   ```bash
   aws s3 mb s3://gift-engine-astro --region us-east-1
   ```

2. **Enable Static Website Hosting**
   ```bash
   aws s3 website s3://gift-engine-astro \
     --index-document index.html \
     --error-document 404.html
   ```

3. **Build and Upload**
   ```bash
   npm run build
   aws s3 sync dist/ s3://gift-engine-astro --delete
   ```

4. **Create CloudFront Distribution**
   - AWS Console → CloudFront
   - Create distribution
   - Origin: S3 bucket
   - Default root object: index.html
   - Enable compression
   - Add custom domain (optional)

5. **Automate with GitHub Actions**
   
   Create `.github/workflows/deploy-aws.yml`:
   ```yaml
   name: Deploy to AWS S3

   on:
     push:
       branches: [ main ]

   jobs:
     deploy:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v3
         - uses: actions/setup-node@v3
           with:
             node-version: '18'
         - run: npm install
         - run: npm run build
         - uses: aws-actions/configure-aws-credentials@v1
           with:
             aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
             aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
             aws-region: us-east-1
         - run: aws s3 sync dist/ s3://gift-engine-astro --delete
   ```

## Option 5: Other Static Hosts

### Firebase Hosting

```bash
npm install -g firebase-tools
firebase init hosting
npm run build
firebase deploy
```

### Render

1. Connect GitHub repository
2. Build command: `npm run build`
3. Publish directory: `dist`
4. Deploy

### Surge.sh

```bash
npm install -g surge
npm run build
surge dist/
```

### Cloudflare Pages

1. Connect GitHub repository
2. Build command: `npm run build`
3. Build output directory: `dist`
4. Deploy

## Post-Deployment

### 1. Verify Deployment

- [ ] Site loads correctly
- [ ] All pages accessible
- [ ] Links working
- [ ] Images displaying
- [ ] Mobile responsive
- [ ] Navigation working

### 2. Test SEO

- [ ] Check sitemap: `/sitemap-index.xml`
- [ ] Verify robots.txt: `/robots.txt`
- [ ] Test meta tags in page source
- [ ] Submit sitemap to Google Search Console
- [ ] Submit to Bing Webmaster Tools

### 3. Set Up Analytics

Add analytics to track traffic:

```html
<!-- In astro.config.mjs or layout -->
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_ID"></script>

<!-- Or use Astro integrations -->
```

### 4. Configure Email

Set up contact form or newsletter:
- Formspree
- Netlify Forms
- AWS SES
- SendGrid

### 5. Monitor Performance

- Set up monitoring with:
  - Google PageSpeed Insights
  - Lighthouse CI
  - Sentry for error tracking
  - Datadog or New Relic

## Continuous Deployment

### Automated Deployments

Most platforms support automatic deployment on push:

1. **GitHub Integration**
   - Push to main branch
   - Automatic build and deploy
   - Status checks in PR

2. **Environment Variables**
   - Store secrets securely
   - Use platform-specific secret management
   - Never commit `.env` files

3. **Preview Deployments**
   - Most platforms create preview URLs for PRs
   - Test before merging to main

## Troubleshooting

### Build Fails

**Error: "Cannot find module"**
- Solution: Run `npm install` locally
- Ensure all dependencies in `package.json`

**Error: "Out of memory"**
- Solution: Increase Node memory
- Use `NODE_OPTIONS=--max-old-space-size=4096`

### Site Not Updating

**Issue: Old content showing**
- Solution: Clear CDN cache
- Purge cache in platform dashboard
- Wait for cache expiration (usually 24 hours)

**Issue: 404 errors**
- Solution: Check build output directory
- Verify `astro.config.mjs` settings
- Check routing configuration

### Performance Issues

**Slow site**
- Optimize images
- Enable compression
- Use CDN
- Check for large assets

**High build time**
- Check content volume
- Optimize Markdown files
- Review dependencies

## Rollback

If deployment has issues:

### GitHub Pages
```bash
git revert <commit-hash>
git push origin main
```

### Netlify
- Go to Deploys
- Click "Restore" on previous deployment

### Vercel
- Go to Deployments
- Click "Promote to Production" on previous deployment

## Maintenance

### Regular Tasks

- [ ] Monitor uptime
- [ ] Check error logs
- [ ] Update dependencies monthly
- [ ] Review analytics
- [ ] Update content
- [ ] Test all links quarterly
- [ ] Security updates

### Updating Content

1. Create new Markdown file in `src/content/guides/`
2. Commit and push to GitHub
3. Automatic deployment triggers
4. New content live within minutes

### Updating Dependencies

```bash
npm update
npm audit fix
npm run build
git commit -am "Update dependencies"
git push origin main
```

## Custom Domain Setup

### DNS Configuration

**For Netlify:**
- CNAME: `your-domain.com` → `your-site.netlify.app`

**For GitHub Pages:**
- CNAME: `your-domain.com` → `yourusername.github.io`
- Or A records: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`

**For Vercel:**
- CNAME: `your-domain.com` → `cname.vercel-dns.com`

### SSL Certificate

Most platforms provide free SSL:
- Netlify: Automatic
- GitHub Pages: Automatic
- Vercel: Automatic
- AWS: Use ACM (free)

## Performance Optimization

### Pre-Deployment

```bash
# Optimize images
npm run build

# Test performance
npm run preview
```

### Post-Deployment

1. **Enable Compression**
   - Most platforms do this automatically
   - Verify in response headers

2. **Set Cache Headers**
   - Static assets: 1 year
   - HTML: 1 hour
   - Configure in platform settings

3. **Enable CDN**
   - Netlify: Automatic
   - Vercel: Automatic
   - AWS: CloudFront
   - GitHub Pages: Cloudflare (optional)

## Security

### Best Practices

- [ ] Enable HTTPS (automatic on most platforms)
- [ ] Set security headers
- [ ] Keep dependencies updated
- [ ] Use environment variables for secrets
- [ ] Regular security audits
- [ ] Monitor for vulnerabilities

### Security Headers

Add to deployment configuration:
```
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block
Referrer-Policy: strict-origin-when-cross-origin
```

## Support

For deployment issues:
- Check platform documentation
- Review build logs
- Test locally with `npm run preview`
- Check Astro documentation
- Open issue on GitHub

---

**Happy deploying! Your gift recommendation site is now live! 🎁**
