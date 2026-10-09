I want to build a website for a client. She's an early-20s woman from the Gold Coast in Queensland and is looking to start an online business. While we're getting the business details settled, I have already acquired the web domain `tiannahs.com` but currently that doesn't point anywhere.

I'd like to put in place a temporary holding website at that domain.

We can host it as a Page on my Github account, and point the domain there.

**Give me five designs for a holding website.**

* Project the owner, Tiannah, as a sophisticated, hardworking, professional, reliable person, with a touch of punk.
* You can use the `Documentation/Tiannah.png` image.
* The title should be "Tiannah's" (with the apostrophe S) or something similar.
* For colours, Vibrant Blues: Cobalt Blue, Cerulean Blue, and Transformative Teal are central to both spring/summer and autumn/winter collections, offering electric, high-voltage statements.
* Because we don't have any real content to put there, make the background dynamic, to add some gentle movement, so the viewer doesn't immediately get bored.
* Allow the viewer to contact Tiannah, without giving her direct contact details (so, maybe a form or something)



---

# Project Notes

## Overview
A static holding page for `tiannahs.com`, hosted on GitHub Pages, with an animated background and a contact form that hides Tiannah's email address. The brief is above; the plan is in `Documentation/Plan.md`.

## Tech Stack
- Language: HTML and CSS only. **No JavaScript** (Paul, 2026-10-09). No build step. Cloudflare Workers is allowed if server-side logic is ever needed.
- Hosting: GitHub Pages (`main` branch root, `CNAME` = `tiannahs.com`)
- Forms: Web3Forms (approved by Paul, 2026-10-09)
- Fonts: Google Fonts

## Commands
- `python3 -m http.server 8000` — serve locally, then open `http://localhost:8000/designs/`

## Architecture
- `designs/<n>-<name>/index.html` — candidate designs, each self-contained
- `designs/index.html` — gallery linking all designs
- `assets/` — shared images (portrait)
- `index.html` — the live page (the chosen design, promoted)
- `Documentation/` — Plan, Status, Journal

## Conventions
- Palette: cobalt `#0047AB`, cerulean `#2A9FD6`, teal `#00A6A6`
- All motion is CSS (keyframes or inline SVG) and must respect `prefers-reduced-motion`
- The contact form is a plain HTML POST to Web3Forms, with a `redirect` back to `/#thanks` (CSS `:target` shows the confirmation) and a `botcheck` honeypot field
- Australian English in copy and docs
- Clarity project: `tiannahs.com`

## Environment Variables
- None. The Web3Forms access key is public by design. Until Tiannah's key exists, use the placeholder `YOUR_WEB3FORMS_ACCESS_KEY`.
