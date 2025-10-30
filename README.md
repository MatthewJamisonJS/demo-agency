# Demo Agency Site

Professional agency services demo site built with Hugo and the Andromeda Light theme.

Part of Matthew Jamison's portfolio showcasing modern web development capabilities.

## Tech Stack
- Hugo Static Site Generator (v0.121+)
- Andromeda Light Theme
- Deployed on Cloudflare Pages
- TailwindCSS for styling

## Features

### Security
- Content Security Policy (CSP) headers configured
- HTTPS enforced via Strict-Transport-Security
- Safe markup rendering with `unsafe = false`
- Frame options and referrer policies configured

### Performance
- WebP image optimization (savings: 89-94% on blog images)
- Image quality tuned to 80% for optimal balance
- Long cache expiration (720 hours)
- Optimized build configuration

### SEO
- Open Graph and Twitter Card meta tags
- Schema.org JSON-LD for WebSite type
- Canonical URLs on all pages
- Preconnect/DNS prefetch for external resources
- Comprehensive sitemap and robots.txt

## Setup

### Prerequisites
- Hugo (v0.121+)
- Node.js (for PostCSS)

### Installation

```bash
# Clone repository
git clone <repo-url>
cd demo-agency

# Install dependencies
npm install

# Start development server
hugo server -D
```

Visit http://localhost:1313 in your browser.

## Building

```bash
# Production build
hugo --minify

# Output is in the ./public/ directory
```

## Deployment

The site is configured for Cloudflare Pages:

1. Connect your GitHub repository to Cloudflare Pages
2. Set Build command to: `hugo --minify`
3. Set Publish directory to: `public`
4. Domain: https://demo-agency.pages.dev

## Content Structure

- `/content/english/` - Main content pages and blog posts
- `/assets/images/` - Image assets (optimized WebP versions available)
- `/data/` - YAML data files for dynamic content
- `/static/` - Static files (robots.txt, _headers)

## Image Optimization

Large images are available in both original and WebP formats:
- JPG to WebP conversion saves 89-94% file size
- PNG to WebP conversion saves 41%+ file size
- Images processed at quality level 80 for visual fidelity

To use WebP images in content:
```markdown
![Description](image.webp)
```

Browsers that don't support WebP will need a fallback:
```html
<picture>
  <source srcset="image.webp" type="image/webp">
  <img src="image.jpg" alt="Description">
</picture>
```

## Configuration

Key Hugo configuration (`hugo.toml`):
- `baseURL`: https://demo-agency.pages.dev
- `theme`: andromeda-light
- `unsafe = false`: Safe markup rendering
- `quality = 80`: Image optimization level

## Performance Metrics

After optimization:
- Total image directory: 7.0 MB
- Individual blog images: 44-94 KB (WebP)
- Estimated bandwidth savings: 3-4 MB per unique visitor

## Links

- Portfolio: [matthewjamison.dev](https://matthewjamison.dev)
- GitHub: [@MatthewJamisonJS](https://github.com/MatthewJamisonJS)
