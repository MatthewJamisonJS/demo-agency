# Cloudflare Pages Deployment Guide - demo-agency

**Live Domain:** `https://demo-agency.pages.dev`

This site is configured for automatic deployment on Cloudflare Pages.

## Quick Start

1. **Push to GitHub**: Simply push to the `main` branch
2. **Automatic Build**: Cloudflare Pages automatically builds and deploys
3. **Live at**: `https://demo-agency.pages.dev`

```bash
git add .
git commit -m "Update demo content"
git push origin main
```

Cloudflare Pages will automatically build and deploy within 1-2 minutes.

## Setup Instructions (First Time Only)

### 1. Connect Repository to Cloudflare Pages

1. Log in to [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. Navigate to **Pages** → **Create a project**
3. Select **Connect to Git** → **GitHub**
4. Authorize Cloudflare and select your GitHub account
5. Find and select repository: `MatthewJamisonJS/demo-agency`

### 2. Configure Build Settings

When Cloudflare asks for build configuration:

| Setting | Value |
|---------|-------|
| **Production branch** | `main` |
| **Build command** | `hugo --minify --gc` |
| **Build output directory** | `public` |
| **Root directory** | (leave empty) |

### 3. Add Environment Variables

Click **Settings** → **Environment variables** and add:

```
HUGO_VERSION = 0.152.2
HUGO_ENV = production
```

### 4. Verify Domain

Cloudflare Pages will automatically assign: `demo-agency.pages.dev`

No additional DNS configuration needed for `.pages.dev` domains.

## Build Verification

Test the build locally before deploying:

```bash
# Run the deployment helper script
bash .cloudflare/deploy.sh

# Or manually:
rm -rf public
HUGO_ENV=production hugo --minify --gc

# Verify output
ls -la public/
find public -type f | wc -l
```

Expected output:
- `public/index.html` - Homepage
- `public/_headers` - Security headers
- `public/sitemap.xml` - SEO sitemap
- `public/robots.txt` - Robot instructions
- ~50+ files
- Processed images optimized

## Security Features

### Security Headers

Security headers are automatically applied via `static/_headers`:

```
X-Frame-Options: SAMEORIGIN
X-Content-Type-Options: nosniff
Strict-Transport-Security: max-age=31536000; includeSubDomains
```

### Verify Headers

After deployment, verify headers are applied:

```bash
curl -I https://demo-agency.pages.dev
```

## Deploy Previews

Cloudflare Pages automatically creates preview URLs for:
- **Pull requests**: `[branch-name]--[project-name].pages.dev`
- **Commits**: `[commit-hash].[project-name].pages.dev`

## Performance Targets

After deployment, aim for these metrics:

- **Lighthouse Score**: 90+
- **First Contentful Paint (FCP)**: < 2s
- **Time to Interactive (TTI)**: < 3s
- **Page Size**: < 5MB

Test at: https://pagespeed.web.dev/

## Troubleshooting

### Site doesn't load after deployment

1. Check Cloudflare Pages build logs:
   - Dashboard → Pages → demo-agency → All deployments
   - Look for error messages in the build logs

2. Verify Hugo config:
   ```bash
   grep "baseURL" hugo.toml
   # Should output: baseURL = "https://demo-agency.pages.dev"
   ```

### Images not loading

1. Verify images are in WebP format
2. Check image paths are relative to domain root
3. Verify image optimization completed during build

### Security headers not applied

1. Verify `public/_headers` file exists:
   ```bash
   ls -la public/_headers
   ```

2. Rebuild site:
   ```bash
   rm -rf public
   hugo --minify --gc
   ```

## Useful Links

- **Cloudflare Pages Docs**: https://developers.cloudflare.com/pages/
- **Hugo Deployment Guide**: https://gohugo.io/hosting-and-deployment/hosting-on-cloudflare-pages/
- **Lighthouse Testing**: https://pagespeed.web.dev/

## Files Reference

- `.cloudflare/deploy.sh` - Deployment helper script
- `.cloudflare/CHECKLIST.md` - Pre/post deployment checklist
- `hugo.toml` - Hugo configuration
- `static/_headers` - Security headers configuration
