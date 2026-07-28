# Cookie Lab — Google Tag Manager

A minimal static site for gtag/GTM and CookieYes banner QA testing, on a dark teal-on-slate theme.

**Live:** https://arunshaju-mozilor.github.io/cookie-lab/

## Pages

| Page | Purpose |
|---|---|
| `index.html` | **Cookie Lab** home page — loads real third-party trackers and sets cookies in every category on load, with a live consent-status dashboard |
| `about.html` | About page for multi-page navigation tests |
| `privacy-policy.html` | Privacy policy (linked from banner) |

## Adding the CookieYes script

In each HTML file, uncomment and replace the script tag in `<head>`:

```html
<script id="cookieyes" type="text/javascript"
  src="https://cdn-cookieyes.com/client_data/YOUR_CLIENT_ID/script.js">
</script>
```

Get `YOUR_CLIENT_ID` from: CookieYes Dashboard → Settings → Installation.

## Hosting

GitHub Pages is already configured on this repo: **Deploy from a branch → `main` → `/` (root)**.
Pushing to `main` redeploys the site within a minute or two.

Use https://arunshaju-mozilor.github.io/cookie-lab/ as the domain when adding a website
in the CookieYes dashboard.
