# GP Appointment Summary Builder

A free, privacy-first web tool from **Heard and Charted** that helps people prepare for a GP appointment. You answer six short sections (why you're there, how long it's been going on, your top three symptoms, the effect on daily life, what you've tried, what you'd like from the appointment), and it builds a one-page A4 summary to print or copy, updating as you type.

## Design decisions

- **No health data leaves the device.** Everything runs in the browser. Answers are kept in `localStorage` so people can come back to them, and *Clear everything* removes them. There's no backend, no database and no form submission. This avoids storing UK GDPR special category (health) data altogether.
- **Enforced, not just promised.** `_headers` sets a Content Security Policy with `connect-src 'none'` and `form-action 'none'`, so the page can't send data anywhere even by mistake.
- **No third-party requests.** The brand fonts (Lora and Poppins, SIL Open Font License) are subset and embedded in `fonts.css`, so visitors' browsers don't contact Google Fonts.
- **Print-first.** The summary is an exact A4 sheet (794 × 1123 px at 96 dpi), scaled to fit the screen, with print CSS that hides everything else. It warns if the content would run onto a second page.
- **Accessible.** Native form controls, labelled radio groups, visible focus states and `prefers-reduced-motion` support. It also works on phones.
- **Safe wording.** It organises what the user wants to say. It never scores or interprets answers, and it signposts 999, NHS 111 and Samaritans.

## Files

| File | Purpose |
|---|---|
| `index.html` | The tool: HTML, CSS and vanilla JavaScript in one file, with no build step |
| `privacy.html` | Plain-English privacy note |
| `fonts.css` | Embedded, subset brand fonts |
| `favicon.svg` | Logo mark |
| `_headers` | Security headers for Cloudflare Pages |

## Hosting

Static site on Cloudflare Pages, deployed automatically from this repository's `main` branch.

If cookie-free Cloudflare Web Analytics is turned on later, add `https://static.cloudflareinsights.com` to `script-src` and `https://cloudflareinsights.com` to `connect-src` in `_headers`, and update `privacy.html`.

## Not medical advice

This is an organisation tool. It doesn't diagnose, interpret or give treatment advice.

© Heard and Charted
