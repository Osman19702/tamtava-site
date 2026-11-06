# tamtava.com

The static website for the Tamtava app, served by GitHub Pages at <https://tamtava.com>.

| Page | File | Used by |
|---|---|---|
| `/` | `index.html` | Marketing URL (optional in App Store Connect) |
| `/privacy` | `privacy.html` | The app's Me → About → Privacy policy row (`src/features/me/links.ts` in the app repo) and App Store Connect's Privacy Policy URL (`/privacy#tr` for the Turkish localisation) |
| `/support` | `support.html` | The app's Me → About → Support row and App Store Connect's Support URL |

Do not rename `privacy.html` or `support.html`: the app's released builds link to `/privacy` and `/support`.

## Changing a page

Edit the HTML, commit and push to `main`; GitHub Pages republishes within a minute or two. When the privacy policy changes, update its date ("Effective from" / "Yürürlük tarihi") in both languages, and keep the app's behaviour and the policy in step: the policy must change before the app ships analytics, crash reporting, accounts, sync, anything that calls a server, or EAS Update.

## Before the first publish

`privacy.html` holds `{{ADDRESS}}`, `{{DATE_EN}}` and `{{DATE_TR}}`. Replace every one; this must print nothing before you push:

```bash
grep -n '{{' *.html
```

No cookies, no analytics, no third-party scripts or fonts: keep it that way, or the privacy policy's "This website" section must change.
