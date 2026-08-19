# idledominion.app

The site for **Idle Dominion**, served by GitHub Pages from this repository.

Three static pages and a stylesheet. No build step, no dependencies, and **no
requests to any third party** — not a web font, not an analytics tag, not an
embed. Still deliberate, and the reason is narrower than it used to be: the app
now serves one optional advert, so it is no longer true that nothing here talks
to anybody. What is still true is that **the page explaining that does not**, and
a privacy policy delivered over a page that phones home is an argument against
itself.

    index.html     the pitch
    privacy.html   linked from App Store Connect as the Privacy Policy URL
    support.html   linked from App Store Connect as the Support URL
    style.css      the game's own palette, taken from Theme/Palette.swift
    CNAME          idledominion.app
    app-ads.txt    see below

## `app-ads.txt`, which is not optional now there are adverts

One line, naming AdMob as an authorised seller of this app's inventory:

    google.com, pub-6164822901218959, DIRECT, f08c47fec0942fa0

The publisher ID is the one inside `GADApplicationIdentifier` in
`Config/Info.plist`, and the file is identical to the one in every other
`*-site` repo here. It has to sit at the **root of the domain App Store Connect
lists as the developer website**, which is why it lives in this repo rather than
in the app.

Buyers check it. Without it, inventory reads as unauthorised and a real share of
the bidding simply does not happen — it costs revenue quietly rather than
breaking anything, which is the worst way for a file to be missing. AdMob shows
the crawl result under **Apps → app-ads.txt**; it takes a day or so after the
domain resolves.

## Publishing

1. Copy these files to the root of the `idle-dominion-site` repository and push.
2. In that repo: **Settings → Pages → Source: Deploy from a branch**, branch
   `main`, folder `/ (root)`.
3. **Settings → Pages → Custom domain:** `idledominion.app`. The `CNAME` file
   here does the same thing and one of them is enough, but having both is
   harmless and the file survives a settings mishap.
4. At the registrar, point the domain at GitHub Pages:
   - Four `A` records for the apex `idledominion.app` →
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - One `CNAME` for `www` → `<user>.github.io`
5. Wait for DNS, then tick **Enforce HTTPS** in Settings → Pages. Apple will not
   accept a privacy policy URL that fails to load, so check both
   `https://idledominion.app/privacy` and `/support` in a browser before
   pasting them into App Store Connect.

## The URLs App Store Connect wants

| ASC field | URL |
|---|---|
| Privacy Policy URL (required) | `https://idledominion.app/privacy` |
| Support URL (required) | `https://idledominion.app/support` |
| Marketing URL (optional) | `https://idledominion.app` |

GitHub Pages serves `privacy.html` at `/privacy` without the extension, so those
URLs work as written.
