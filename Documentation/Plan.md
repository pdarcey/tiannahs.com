# Plan

## Stage 1: Project set-up ✅
- git repo, `.gitignore`, `README.md`, project docs, and the Clarity project (`tiannahs.com`)

## Stage 2: Five holding-page designs ✅ built (Clarity #505 open until a design is chosen)

### Shared across all five
- **Tech:** one self-contained `index.html` per design, using **HTML and CSS only, with no JavaScript** (Paul, 2026-10-09). Fonts come from Google Fonts. Animation uses CSS keyframes and inline SVG.
- **Layout:** the title "Tiannah's", a one-line teaser (for example "Something good is coming."), the portrait, and the contact form.
- **Palette:** cobalt `#0047AB`, cerulean `#2A9FD6`, transformative teal `#00A6A6`. Each design adds its own near-black or near-white neutral and one accent.
- **Motion:** the background moves gently and loops slowly. It stops for visitors who set `prefers-reduced-motion`. Browsers already throttle CSS animation in hidden tabs, so no pause code is needed.
- **Contact form:** name, email and message fields in a plain HTML `<form method="post">` to Web3Forms. A hidden `redirect` field sends the visitor back to `/#thanks`, and CSS `:target` shows a thank-you message. Required fields and email format are checked by the browser's own validation. The form also has a `botcheck` honeypot field, proper `<label>`s, and works with the keyboard.
- **Responsive:** looks good from phone width to desktop.
- **Assets:** a shared portrait at `assets/tiannah.png`, also exported as an optimised WebP.
- **Gallery:** `designs/index.html` links to all five for side-by-side comparison. It shows **still WebP screenshots** in `designs/thumbs/`. Live iframes crashed iOS Safari (Clarity #508), so if a design changes, retake its screenshot at 1440×900 and resize it to 960×600.

### The five directions
1. **Electric Tide:** sophisticated and calm. Large, soft blobs (fading radial gradients, not a blur filter) of cobalt, cerulean and teal drift slowly across a deep-navy background, like an aurora. The title is set in an elegant high-contrast serif. The punk touch is a hand-scrawled teal underline and a small safety-pin glyph. The form sits on a frosted-glass card (solid on phones).
2. **Cover Story:** an editorial magazine cover. The title runs huge in a condensed display face behind the cut-out portrait. A cerulean halftone dot field (a CSS `radial-gradient` pattern) slowly drifts and pulses behind everything. The punk touch is a torn-paper edge on the form panel and a ransom-note "COMING SOON" sticker.
3. **Swell:** a nod to the Gold Coast. Layered SVG waves roll slowly from teal at the shoreline to cobalt deep water. The sans-serif type is clean and confident, and the portrait sits in a soft arch frame. The punk touch is a neon "OPEN SOON" stamp, slightly rotated.
4. **Zine:** the most punk, but still tidy. The portrait gets a cobalt-and-teal duotone, with photocopy grain over the page, tape strips, and stencil type. Faint "TIANNAH'S" lettering scrolls slowly in rows across the background. The grid stays disciplined so it still reads as professional.
5. **Constellation:** minimal luxury. An inline SVG of nodes joined by fine lines drifts slowly in layers that move at different speeds (animated with CSS transforms), suggesting someone connected and reliable. There's plenty of white space and thin serif type on a near-white background. The punk touch is a single neon-teal studded border on the portrait and the form.

### Verification
- The designs are live at https://tiannahs.com/designs/. Paul checked them on his iPhone (2026-10-09).
- **Next:** Paul has sent the link to Tiannah. Waiting on her feedback and choice, which may mix elements from several designs. Then go to Stage 3.

## Stage 3: Finalise the chosen design (next)
- Apply Tiannah's feedback to the chosen design.
- Promote it to the root `index.html`, replacing the temporary redirect to `/designs/`. Fix the asset paths (`../../assets/` becomes `assets/`).
- Add a favicon and Open Graph tags for link previews, including a share image.
- Add the Web3Forms key (Clarity #506). The form's `redirect` already points to `https://tiannahs.com/#thanks`, which matches the root page. Then send a real test message.
- Decide whether to keep or remove `/designs/` once the real page is live.
- Check on Paul's iPhone before calling it done.

## Stage 4: Deploy ✅ (Clarity #507, closed)
- Repo `pdarcey/tiannahs.com` (public). Pages serves from the `main` root. DNS is at Hover. HTTPS is enforced, and the Let's Encrypt certificate renews automatically.
- Deploying from here on is just `git push`. GitHub rebuilds in under a minute.
