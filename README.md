# Cookie Lab — Google Tag Manager

A minimal static site for gtag/GTM and CookieYes banner QA testing, on a dark teal-on-slate theme.

**Live:** https://arunshaju-mozilor.github.io/cookie-lab-gtm/

## Pages

| Page | Purpose |
|---|---|
| `index.html` | **Cookie Lab** home page — loads real third-party trackers and sets cookies in every category on load, with a live consent-status dashboard |
| `about.html` | About page for multi-page navigation tests |
| `privacy-policy.html` | Privacy policy (linked from banner) |

## Google Tag Manager

Container `GTM-PCKZVT4H` is installed in `index.html` only — the snippet in `<head>`
and the `<noscript>` iframe as the first element in `<body>`. `about.html` and
`privacy-policy.html` carry no container, so navigation tests will not see it fire
there. Swap the ID in both places to point at a different container.

**Add GA4, Ads and any other Google tag as tags inside the container, never to the
page.** A second `gtm.js` push double-fires the container's Page View triggers, and a
hardcoded `gtag.js` takes over `window.gtag` and shares the `_ga` client id — which
makes consent assertions pass without testing anything. The cookie seeder in
`index.html` deliberately omits `_ga`, `_ga_<stream>` and `_gcl_au` for the same
reason: the container's own tags must be the thing that creates them.

## Adding the CookieYes script

No CMP is installed. Add the banner script to `<head>` in each HTML file:

```html
<script id="cookieyes" type="text/javascript"
  src="https://cdn-cookieyes.com/client_data/YOUR_CLIENT_ID/script.js">
</script>
```

Get `YOUR_CLIENT_ID` from: CookieYes Dashboard → Settings → Installation. Do not add
`type="text/plain"` or `data-cookieyes` to the trackers already on the page — that
pre-blocks them and defeats the point of the fixture.

## Hosting

Enable GitHub Pages on this repo: **Settings → Pages → Deploy from a branch → `main`
→ `/` (root)**. After that, pushing to `main` redeploys the site within a minute or two.

Use https://arunshaju-mozilor.github.io/cookie-lab-gtm/ as the domain when adding a
website in the CookieYes dashboard.
