# Plan

## Stage 1: Project set-up ✅
- git repo, `.gitignore`, `README.md`, project docs, and the Clarity project (`tiannahs.com`)

## Stage 2: Five holding-page designs (awaiting Paul's approval of this plan)

### Shared across all five
- **Tech:** one self-contained `index.html` per design, using **HTML and CSS only, with no JavaScript** (Paul, 2026-10-09). Fonts come from Google Fonts. Animation uses CSS keyframes and inline SVG.
- **Layout:** the title "Tiannah's", a one-line teaser (for example "Something good is coming."), the portrait, and the contact form.
- **Palette:** cobalt `#0047AB`, cerulean `#2A9FD6`, transformative teal `#00A6A6`. Each design adds its own near-black or near-white neutral and one accent.
- **Motion:** the background moves gently and loops slowly. It stops for visitors who set `prefers-reduced-motion`. Browsers already throttle CSS animation in hidden tabs, so no pause code is needed.
- **Contact form:** name, email and message fields in a plain HTML `<form method="post">` to Web3Forms. A hidden `redirect` field sends the visitor back to `/#thanks`, and CSS `:target` shows a thank-you message. Required fields and email format are checked by the browser's own validation. The form also has a `botcheck` honeypot field, proper `<label>`s, and works with the keyboard.
- **Responsive:** looks good from phone width to desktop.
- **Assets:** a shared portrait at `assets/tiannah.png`, also exported as an optimised WebP.
- **Gallery:** `designs/index.html` links to all five for side-by-side comparison.

### The five directions
1. **Electric Tide:** sophisticated and calm. Large, blurred blobs of cobalt, cerulean and teal drift slowly across a deep-navy background, like an aurora. The title is set in an elegant high-contrast serif. The punk touch is a hand-scrawled teal underline and a small safety-pin glyph. The form sits on a frosted-glass card.
2. **Cover Story:** an editorial magazine cover. The title runs huge in a condensed display face behind the cut-out portrait. A cerulean halftone dot field (a CSS `radial-gradient` pattern) slowly drifts and pulses behind everything. The punk touch is a torn-paper edge on the form panel and a ransom-note "COMING SOON" sticker.
3. **Swell:** a nod to the Gold Coast. Layered SVG waves roll slowly from teal at the shoreline to cobalt deep water. The sans-serif type is clean and confident, and the portrait sits in a soft arch frame. The punk touch is a neon "OPEN SOON" stamp, slightly rotated.
4. **Zine:** the most punk, but still tidy. The portrait gets a cobalt-and-teal duotone, with photocopy grain over the page, tape strips, and stencil type. Faint "TIANNAH'S" lettering scrolls slowly in rows across the background. The grid stays disciplined so it still reads as professional.
5. **Constellation:** minimal luxury. An inline SVG of nodes joined by fine lines drifts slowly in layers that move at different speeds (animated with CSS transforms), suggesting someone connected and reliable. There's plenty of white space and thin serif type on a near-white background. The punk touch is a single neon-teal studded border on the portrait and the form.

### Verification
- Paul previews each design locally (`python3 -m http.server`, then open `/designs/`).
- Paul picks one design, possibly mixing elements from others. Then go to Stage 3.

## Stage 3: Finalise the chosen design
- Promote the chosen design to the root `index.html`, add `CNAME`, a favicon, and Open Graph tags for link previews
- Add the Web3Forms key (Clarity #506)

## Stage 4: Deploy (Clarity #507)
- Create the GitHub repo, push, turn on Pages, update DNS at the registrar, and enforce HTTPS
