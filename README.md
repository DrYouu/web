# DrYouu.uk Website

Personal website hosted on GitHub Pages with Cloudflare DNS/CDN.

## Cloudflare Configuration

For the domain redirection to work correctly, ensure the following settings in Cloudflare:

### DNS Records

| Type  | Name | Content                       | Proxy Status |
|-------|------|-------------------------------|--------------|
| A     | @    | 185.199.108.153              | DNS only     |
| A     | @    | 185.199.109.153              | DNS only     |
| A     | @    | 185.199.110.153              | DNS only     |
| A     | @    | 185.199.111.153              | DNS only     |
| CNAME | www  | DrYouu-Research-Lab.github.io | DNS only     |

> **Important:** Set Proxy Status to "DNS only" (grey cloud) for GitHub Pages to issue SSL certificates correctly.

### SSL/TLS Settings

1. Go to **SSL/TLS** → **Overview**
2. Set encryption mode to **Full** or **Full (Strict)**

> **Warning:** Do NOT use "Flexible" mode as it causes redirect loops.

### Page Rules (Optional)

To force HTTPS and www redirect:

1. Create Page Rules for HTTPS enforcement:
   - `http://dryouu.uk/*` → Setting: **Always Use HTTPS**
   - `http://www.dryouu.uk/*` → Setting: **Always Use HTTPS**

2. Create a Page Rule for `www.dryouu.uk/*`
   - Setting: **Forwarding URL (301)**
   - Destination: `https://dryouu.uk/$1`

## GitHub Pages Settings

1. Go to repository **Settings** → **Pages**
2. Set custom domain to `dryouu.uk`
3. Enable **Enforce HTTPS** (after DNS propagation)

## Files

- `CNAME` - Custom domain configuration for GitHub Pages
- `index.html` - Main website content
- `_redirects` - Cloudflare Pages redirect rules
- `_headers` - Cloudflare Pages security headers
