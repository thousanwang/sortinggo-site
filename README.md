# SortingGo Site

Official website and legal documents for SortingGo（分揀高手）.

This repository hosts public pages required for Google Play distribution, including:

- Privacy Policy
- Terms of Service
- Copyright Notice
- Support Information

SortingGo is a mobile-first order sorting and picking assistant designed for small businesses, wholesalers, group-buy organizers, delivery operations and warehouse workflows.

## Multi-language structure

The site supports the same 9 languages as the app: Traditional Chinese (`tw`), Simplified Chinese (`cn`),
English (`en`), Japanese (`ja`), Thai (`th`), Vietnamese (`vi`), Indonesian (`id`), Korean (`ko`) and
Spanish (`es`).

Each of the 5 page types has one file per language, named `{page}_{lang}.html`, e.g. `index_en.html`,
`privacy_ja.html`. Every `index_*.html` (and every other page) includes a language-switcher row in the header
linking to the same page in every other supported language.

`index.html`, `privacy.html`, `terms.html`, `copyright.html` and `support.html` (no language suffix) are thin
redirector pages: they read `navigator.language` in JavaScript and `location.replace()` to the matching
`{page}_{lang}.html`. A bare `zh` (no region) resolves to `tw`; `zh-CN`/`zh-SG` resolve to `cn`; `id` and `in`
both resolve to `id`; `es-*` resolves to `es`; any unsupported language falls back to the `_en` version. Each
redirector also has a
`<noscript>` meta-refresh to the `_en` version (for environments without JavaScript) and a visible fallback link
to every language as a last resort.

## Pages

| File | Description |
|------|-------------|
| `index.html` | Homepage — auto-redirects to `index_{lang}.html` based on browser language |
| `privacy.html` | Privacy Policy — auto-redirects to `privacy_{lang}.html` |
| `terms.html` | Terms of Service — auto-redirects to `terms_{lang}.html` |
| `copyright.html` | Copyright Notice — auto-redirects to `copyright_{lang}.html` |
| `support.html` | Support & Contact — auto-redirects to `support_{lang}.html` |
| `{page}_tw.html` | Traditional Chinese content (繁體中文) |
| `{page}_cn.html` | Simplified Chinese content (简体中文) |
| `{page}_en.html` | English content (also the default fallback) |
| `{page}_ja.html` | Japanese content (日本語) |
| `{page}_th.html` | Thai content (ภาษาไทย) |
| `{page}_vi.html` | Vietnamese content (Tiếng Việt) |
| `{page}_id.html` | Indonesian content (Bahasa Indonesia) |
| `{page}_ko.html` | Korean content (한국어) |
| `{page}_es.html` | Spanish content (Español) |
| `style.css` | Shared stylesheet |
| `version.json` | Static update manifest read by the app before showing update reminders |

## GitHub Pages Setup

1. Go to **Settings → Pages**
2. Source: **Deploy from a branch**
3. Branch: `main` / Folder: `/ (root)`
4. Save — site will be published at:

```
https://thousanwang.github.io/sortinggo-site/
```

## Version Check Manifest

SortingGo checks `https://thousanwang.github.io/sortinggo-site/version.json` on app startup. Keep
`latestVersionCode` equal to the currently available Google Play version. After a newer release is available on
Google Play, increase `latestVersionCode` so older installed apps show the update reminder and open the Play Store.

If this file is missing, unavailable, or invalid JSON, the app skips the update reminder and continues launching.

## Play Store Links

Use the following URLs for Google Play Console:

- **Privacy Policy**: `https://thousanwang.github.io/sortinggo-site/privacy.html`
- **Terms of Service**: `https://thousanwang.github.io/sortinggo-site/terms.html`

---

© 2026 Thousan Wang. All Rights Reserved.
