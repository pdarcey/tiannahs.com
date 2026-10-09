# The tiannahs.com Journal

## The Big Picture

Picture a shopfront on a Gold Coast street. The lease is signed and the sign is up, but the shelves are still in boxes. You wouldn't leave the windows bare. You'd put up something striking with a "back soon" card and a slot for letters.

That's this site. Tiannah is starting an online business, and we own `tiannahs.com`, but the business itself is still being worked out. This holding page makes the domain look alive and professional, with a bit of attitude, and lets people get in touch without her email address being scraped by every bot on the internet.

## Architecture Deep Dive

The architecture is about as simple as it gets, and that's deliberate.

- **GitHub Pages is the shopfront window.** It serves static files for free, provides HTTPS, and there's no server to patch.
- **The contact form is the letter slot.** A static site can't send email, so the form passes each message to **Web3Forms**, a service that acts like a mail-forwarding address. Visitors write to Web3Forms, and Web3Forms quietly passes it on to Tiannah. Her real address never appears in the page.
- **The animated background is the window display.** We have almost no content, so gentle motion keeps the eye busy for the few seconds it takes to read the page. It respects `prefers-reduced-motion`, because not everyone wants the window display moving.

## The Codebase Map

- `designs/`: five candidate designs, each in a single self-contained `index.html`
- `assets/`: Tiannah's portrait
- `index.html`: the winning design once chosen
- `Documentation/`: this journal, the plan, and the status

## Tech Stack & Why

- **Plain HTML and CSS, with no JavaScript at all.** It's one page that should live for a few months. React would be like hiring a removal truck to post a letter. Paul asked for no JS at all, and it turns out we don't need it: CSS keyframes handle the motion, and a good old-fashioned form POST handles the mail.
- **Google Fonts.** We get good type without worrying about self-hosting licences.
- **Web3Forms.** It's free, needs no backend, and its access key is safe in public HTML because it can only send to its registered address. We chose it over Formspree because Paul asked for it, and its free tier is generous.

## The Journey

- **2026-10-09: Day one.** The brief in `CLAUDE.md` gave the image path as `Documents/Tiannah.png`, but the file actually lives in `Documentation/`. It's a small thing, but it's exactly the kind of mismatch that turns into a broken image in production, so it's fixed in the brief now.

- **2026-10-09: The no-JS trick for the thank-you message.** With no JavaScript we can't show "Thanks!" inline after sending. Instead, Web3Forms' `redirect` field sends the visitor back to `tiannahs.com/#thanks`. The `#thanks` fragment makes that element the CSS `:target`, so a rule like `#thanks:target { display: block }` reveals the message. Think of the URL as a light switch and CSS as the bulb.

- **2026-10-09: Five looks, zero JavaScript.** Some no-JS tricks worth remembering:
  - *Seamless waves (Swell):* each wave is a background SVG tile whose path starts and ends at the same height **and slope**. Shifting `background-position` by exactly one tile width loops with no visible seam. Get the slope wrong and you see a kink every 1600 px.
  - *Duotone portrait (Zine):* an inline SVG `<filter>` with `feComponentTransfer` maps dark pixels to cobalt and light pixels to pale teal. CSS applies it with `filter: url(#duotone)`. Photoshop-style results, with no Photoshop involved.
  - *Constellation:* the nodes and lines are generated once by a little Python script and baked into the HTML as inline SVG. CSS then just nudges three layers at different speeds. Pre-computed beats computed-every-frame.
  - *Ransom note (Cover Story):* each word gets its own `white-space: nowrap` flex row. Without that, "COMING" broke as "COMIN / G", which looked more like a typo than punk.
- **Gotcha: headless Chrome lies about phone widths.** Screenshots at `--window-size=390,…` came out cropped, because headless Chrome on macOS won't make a window narrower than about 500 px. The fix was a test page that holds each design in a 390 px `<iframe>`, which gives a true phone-width viewport. Headless `--screenshot` also never quits on its own, so the helper script kills Chrome once the PNG appears.
- **Gotcha: `file://` doesn't serve `index.html` for folders.** The gallery's previews showed folder listings until the links pointed at `…/index.html` explicitly.

- **2026-10-09: The gallery that crashed iPhones (Clarity #508).** On Paul's iPhone, scrolling `/designs/` flashed white, then reloaded at the top. That's iOS Safari's tell-tale sign that the page ran out of memory and was killed. The gallery used live `<iframe>` previews, so it was really running all five animated pages at once. Each page had GPU-hungry effects: a `filter: blur(80px)` on blobs larger than the screen, frosted glass, and a grain layer four times the screen's area. At the iPhone's 3× pixel density, every one of those layers costs tens of megabytes. Desktop browsers shrug it off, so headless Chrome never noticed. The fix was still screenshots in the gallery, plus cheaper effects in the designs themselves: blobs drawn with fading `radial-gradient`s instead of a blur filter (same look, a fraction of the memory), grain sized to the screen, and no frosted glass or animated masks on phones. Lesson: a big blur filter is like asking the GPU to paint a mural through frosted glass, sixty times a second.

## Engineer's Wisdom

- Fit the tool to the lifespan. A holding page should be cheap to build, cheap to host, and easy to throw away.
- Test on a real phone early. A desktop browser has memory to spare, so it hides problems a phone won't survive.

## If I Were Starting Over...

Too early to say. Ask me after launch.
