# S. Taylor Bookkeeping — One-Page Website

A hand-coded, mobile-first landing page. Every piece of text, every image, and every link is driven by a single **`config.js`** file — you never need to edit `index.html`.

---

## 🚀 Quick Start

1. Open `config.js` in any text editor (VS Code, Notepad, etc.)
2. Change any text between the quotes (`"..."`)
3. Save the file
4. Refresh the page — changes appear instantly

---

## 📁 File Structure

```
staylor-bookkeeping/
├── index.html              # The page template — don't edit this
├── config.js               # ← EDIT THIS for all content
├── README.md               # This file
└── assets/
    └── images/
        ├── sophia.jpg      # Sophia's profile photo (you upload)
        └── logo.png        # Custom logo if you want to replace the default (optional)
```

---

## ✏️ Editing Content

Open **`config.js`**. Everything is grouped into sections:

- `brand` — logo + business name
- `nav` — navigation menu links
- `hero` — the big headline at the top
- `marquee` — the scrolling banner
- `about` — About The Practice + Sophia's profile
- `services` — service cards
- `differentiators` — "What Sets Us Apart"
- `caseStudy` — client story
- `audience` — "Who We Serve"
- `contact` — contact section + form settings
- `footer` — footer links

### Special formatting:
- Wrap words in `<em>...</em>` to make them **orange handwritten script** (e.g., `"Clean, <em>accountant-ready</em> books."`)
- Wrap words in `<strong>...</strong>` in case study paragraphs to make them **gold bold**
- Use `<br/>` for a line break inside a heading

---

## 🖼️ Replacing the Logo

The site ships with a built-in hibiscus logo. To use your own:

1. Add your logo to `assets/images/` (SVG or PNG recommended, square aspect ratio)
2. In `config.js`, change:
   ```js
   logo: "default",
   ```
   to:
   ```js
   logo: "assets/images/your-logo.svg",
   ```

---

## 📸 Adding Sophia's Photo

1. Save her photo to `assets/images/sophia.jpg` (recommended: 600×750px or larger, portrait orientation)
2. The site auto-picks it up — no config change needed
3. To use a different filename, edit `about.owner.photo` in `config.js`

If no photo is uploaded, a placeholder with her initial shows up.

---

## 📧 Connecting the Contact Form (Formspree)

The form is pre-wired to use **Formspree** — free tier = 50 submissions/month, which should be plenty for a new practice. Upgrade to $10/mo later if volume grows.

### Setup (5 minutes):

1. **Sign up** at [formspree.io](https://formspree.io) using `sophia@staylorbookkeeping.com`
2. Click **"+ New Form"** → name it *"Bookkeeping Cleanup Inquiries"*
3. Formspree shows you a **form endpoint** that looks like:
   ```
   https://formspree.io/f/mvgpzyqk
   ```
   (the letters after `/f/` will be unique to her form)
4. In `config.js`, find the `contact` section and paste that URL:
   ```js
   formAction: "https://formspree.io/f/mvgpzyqk",
   ```
5. Save and push to GitHub
6. Submit a test message on the live site — Formspree will email Sophia asking her to **confirm her email address once**. After that, every submission lands in her inbox + Formspree dashboard.

### What happens when someone submits:
- Sophia gets an email with the person's name, email, and message
- Submissions are also archived in her Formspree dashboard (searchable)
- The user sees a friendly "✿ Message Sent — We'll be in touch soon!" message inline (no redirect)
- If the form isn't configured yet, it shows a warning instead of failing silently

### Switching providers later (optional):
If you outgrow Formspree or move to Netlify, change `formProvider` in `config.js` to one of: `"netlify"`, `"web3forms"`, `"mailto"`, or `"demo"` (for testing).

---

## 🌐 Deploying

### Easiest: Netlify
1. Drag the folder onto [app.netlify.com/drop](https://app.netlify.com/drop)
2. Done. You'll get a free URL like `staylor-bookkeeping.netlify.app`
3. Add a custom domain in site settings

### GitHub Pages
1. Push to GitHub
2. Settings → Pages → Deploy from `main` branch
3. Site is live at `yourusername.github.io/repo-name`

### Vercel
1. Push to GitHub
2. Import at [vercel.com](https://vercel.com)
3. Auto-deploys on every commit

---

## 🎨 Color & Font Customization

The core colors are CSS variables at the top of `index.html` (inside `<style>`). Look for `:root { ... }`.

Current palette:
- `--cream: #F8F1E4` — background
- `--coral: #E8704C` — main accent (buttons, script text)
- `--palm: #2C5E4F` — headings, navy-equivalent
- `--gold: #D4A341` — secondary accent

Change those values and the whole site updates.

---

## ⚡ Performance Notes

- No external dependencies except Google Fonts (preconnected for speed)
- All animations are CSS (GPU-accelerated) or IntersectionObserver-based
- SVG illustrations inline — no extra requests
- Should score 95+ on Lighthouse / PageSpeed Insights

---

## 🐛 Troubleshooting

**Nothing shows up?** Open the browser console (F12 → Console). You probably have a typo in `config.js` — missing comma or quote. JSON-like files are picky.

**Photo won't show?** Double-check the path. If `sophia.jpg` is in `assets/images/`, the path in config should be exactly `"assets/images/sophia.jpg"` (lowercase, no leading slash).

**Form doesn't submit?** Make sure `formProvider` is set and, if using Formspree/Web3Forms, that `formAction` has your real endpoint.
