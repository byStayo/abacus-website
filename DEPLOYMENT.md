# Abacus Website - Deployment Guide

## Bundle Contents
- **Total Size:** ~2.1 MB
- **Pages:** 19 HTML files
- **Games:** 14 interactive games

## Before Deploying

### 1. Update Domain References
Replace `yourdomain.com` with your actual domain in:
- `sitemap.xml` - Update all URLs
- `robots.txt` - Update sitemap URL
- `index.html` - Update og:url meta tag

```bash
# Quick find/replace (run from deploy folder)
sed -i '' 's/yourdomain.com/your-actual-domain.com/g' sitemap.xml robots.txt index.html
```

### 2. Update Contact Information
In `contact.html` and footer sections:
- Email address (currently `hello@abacus.dev`)
- Social media links (currently `#` placeholders)

### 3. Optional: Add Analytics
Add your analytics script before `</head>` in all HTML files:
```html
<!-- Google Analytics or similar -->
<script async src="https://..."></script>
```

## Deployment Options

### Option A: Static Hosting (Recommended)
Works with: **Netlify, Vercel, GitHub Pages, Cloudflare Pages**

1. Upload the entire `deploy/` folder contents
2. Set the root directory to the uploaded folder
3. Configure custom domain
4. Enable HTTPS (usually automatic)

**Netlify Drop:** Just drag the `deploy` folder to [netlify.com/drop](https://app.netlify.com/drop)

### Option B: Traditional Web Host
1. FTP/SFTP upload all files to `public_html` or `www` folder
2. Ensure `.html` files are served correctly
3. Configure 404 page in hosting panel

### Option C: GitHub Pages
1. Create a repository
2. Push the `deploy` folder contents to `main` branch
3. Enable GitHub Pages in Settings → Pages
4. Select source: "Deploy from a branch" → `main`

## Post-Deployment Checklist

- [ ] All pages load correctly
- [ ] Navigation works (click through all links)
- [ ] Games load and play properly
- [ ] Favicon appears in browser tab
- [ ] 404 page works (visit /nonexistent-page)
- [ ] Mobile responsive (test on phone)
- [ ] HTTPS enabled and working
- [ ] Submit sitemap to Google Search Console

## File Structure
```
/
├── index.html          # Homepage
├── about.html          # About page
├── services.html       # Services page
├── case-studies.html   # Case studies
├── contact.html        # Contact page
├── 404.html            # Error page
├── favicon.svg         # Site icon
├── robots.txt          # Search engine rules
├── sitemap.xml         # SEO sitemap
└── games/
    ├── index.html      # Games hub
    ├── great-game.html # Main strategy game
    └── [12 more games]
```

## Support
All files are static HTML/CSS/JS - no server-side code required.
No database, no build step, no dependencies.
