# ClutchReframe Support Website

Static support site for the ClutchReframe Clips Overwolf app.

Production URL:

```text
https://support.clutchreframe.com/
```

## Local Preview

```bash
cd /mnt/c/Dev/Support-website
python -m http.server 8080
```

Open:

```text
http://localhost:8080/
http://localhost:8080/privacy.html
http://localhost:8080/terms.html
```

## Deployment

Use GitHub Pages with the repository custom domain:

```text
support.clutchreframe.com
```

Cloudflare DNS:

```text
Type: CNAME
Name: support
Target: clutchreframe.github.io
Proxy status: DNS only
TTL: Auto
```

After GitHub Pages validates the domain, enable HTTPS.

## Checks

```bash
curl -I https://support.clutchreframe.com/
curl -I https://support.clutchreframe.com/privacy.html
curl -I https://support.clutchreframe.com/terms.html
```

Expected: `200 OK` for all three pages.
