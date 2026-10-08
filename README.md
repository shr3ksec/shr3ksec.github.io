# ShrekSec, LLC website

Static site (HTML + CSS, no build step) for GitHub Pages, served at https://shreksec.com.

## Deploy

1. On GitHub (account `shr3ksec`), create a **public** repo named `shr3ksec.github.io`.
2. From this folder:
   ```
   git init -b main
   git add -A
   git commit -m "Initial site"
   git remote add origin git@github.com:shr3ksec/shr3ksec.github.io.git
   git push -u origin main
   ```
3. Repo **Settings → Pages**: Source = "Deploy from a branch", Branch = `main`, `/ (root)`.
4. Same page, **Custom domain** = `shreksec.com` (the `CNAME` file already contains it).
   Once the certificate is issued, tick **Enforce HTTPS**.

## Cloudflare DNS (shreksec.com → DNS → Records)

Set every record below to **DNS only** (grey cloud) until GitHub has issued its HTTPS certificate.

| Type  | Name  | Content                  |
|-------|-------|--------------------------|
| A     | `@`   | `185.199.108.153`        |
| A     | `@`   | `185.199.109.153`        |
| A     | `@`   | `185.199.110.153`        |
| A     | `@`   | `185.199.111.153`        |
| AAAA  | `@`   | `2606:50c0:8000::153`    |
| AAAA  | `@`   | `2606:50c0:8001::153`    |
| AAAA  | `@`   | `2606:50c0:8002::153`    |
| AAAA  | `@`   | `2606:50c0:8003::153`    |
| CNAME | `www` | `shr3ksec.github.io`  |

(Verify these IPs against GitHub's docs, "Managing a custom domain for your GitHub Pages site".)
Email Routing in Cloudflare adds its own MX/TXT records; those don't conflict.
Optional hardening: verify the domain under GitHub account/org Settings → Pages to prevent takeover.

## Still to replace


- Team bios and certifications in the About section (optional)
- Update the `Expires:` date in `.well-known/security.txt` yearly

`.nojekyll` is included so the `.well-known` folder is served.
