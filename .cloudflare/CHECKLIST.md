# Deployment Checklist - demo-agency

**Site Domain:** `demo-agency.pages.dev`
**Cloudflare Project:** `demo-agency`
**Deployment Type:** Automatic (GitHub Push)

## Pre-Deployment

- [ ] Hugo version is 0.152.2+ (current: 0.152.2)
- [ ] `baseURL` in `hugo.toml` is correct: `https://demo-agency.pages.dev`
- [ ] All images are optimized
- [ ] `static/_headers` file exists
- [ ] `robots.txt` exists
- [ ] Local build succeeds: `bash .cloudflare/deploy.sh`
- [ ] No console errors

## Cloudflare Pages Setup

- [ ] Repository connected to Cloudflare Pages
- [ ] Build command configured: `hugo --minify --gc`
- [ ] Build output directory: `public`
- [ ] Environment variable set: `HUGO_VERSION=0.152.2`
- [ ] Environment variable set: `HUGO_ENV=production`
- [ ] Project name: `demo-agency`

## Post-Deployment Verification

- [ ] Site loads successfully at `https://demo-agency.pages.dev`
- [ ] Check security headers: `curl -I https://demo-agency.pages.dev`
- [ ] Test all internal links
- [ ] Test responsive design on mobile
- [ ] Verify images load correctly
- [ ] Check Lighthouse score (should be 90+)
- [ ] Verify sitemap is accessible: `/sitemap.xml`
- [ ] Verify robots.txt is accessible: `/robots.txt`

## Troubleshooting

If issues occur:

1. **Build fails**: Check Cloudflare Pages build logs
2. **Images missing**: Verify image formats and paths
3. **Headers not applied**: Verify `public/_headers` file exists
4. **Custom domain issues**: Check DNS propagation

## Commands for Testing

```bash
# Test local build
bash .cloudflare/deploy.sh

# Verify build output
ls -la public/
find public -type f | wc -l

# Check headers file
cat public/_headers
```
