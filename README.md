# tiannahs.com

A temporary holding page for **Tiannah's**, a Gold Coast business that is still taking shape. It stays up until the real site launches. It gives visitors something polished to look at and a way to get in touch, without showing Tiannah's contact details.

## What's here

| Path | Purpose |
| --- | --- |
| `index.html` | The live holding page (added once a design is chosen) |
| `designs/` | Five candidate designs, plus a gallery page for comparing them |
| `assets/` | Shared images (Tiannah's portrait) |
| `CNAME` | Custom domain for GitHub Pages (`tiannahs.com`) |
| `Documentation/` | Plan, status and the project journal |

## Running locally

It's plain HTML, CSS and JavaScript, so there's no build step. Serve the folder and open it in a browser:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000/designs/
```

## Contact form

The form posts to [Web3Forms](https://web3forms.com), which forwards each message to Tiannah's inbox. The page needs a Web3Forms **access key** in place of the `YOUR_WEB3FORMS_ACCESS_KEY` placeholder. Web3Forms access keys are designed to sit in public HTML, because they can only send mail to the address they were registered with. Even so, the key is generated for Tiannah's email and added only at deploy time.

## Hosting

The site is hosted on GitHub Pages from the `main` branch root. DNS for `tiannahs.com` points to GitHub Pages: apex `A` records plus a `www` `CNAME`. See `Documentation/Plan.md` for the steps.
