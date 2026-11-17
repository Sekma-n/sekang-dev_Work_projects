# README.md

```markdown
# sekang.dev — Personal Portfolio

A hand-built personal portfolio site for **Sekang Segotso**, a website developer based in South Africa. Built with plain HTML, CSS and vanilla JavaScript — no frameworks, no build step, no dependencies beyond a Google Font.

---

## Pages

| Page | File | Purpose |
|------|------|---------|
| Home | `index.html` | Landing page *(referenced, not included here)* |
| Work | `Work.html` | Project archive with category filtering |
| About | `About.html` | Story, skills, timeline and working values |
| Services | `Services.html` | Service offerings, process and FAQ |
| Booking | `Booking.html` | Request a call — date/time picker form |
| Contact | `Contact.html` | Contact form and direct contact details |

---

## Features

- **Fully static** — no build tools, no bundler, no `node_modules`. Open the files and they work.
- **Consistent design system** — shared CSS tokens (colours, type, spacing) across every page.
- **Dark, modern aesthetic** — subtle grid and glow backgrounds, glass-style nav, mono accents.
- **Responsive** — mobile-first breakpoints at `1024px`, `820px` and `640px`, with a slide-down mobile menu.
- **Scroll reveal animations** — via `IntersectionObserver`, with full `prefers-reduced-motion` support.
- **Working contact & booking forms** — powered by [Formspree](https://formspree.io), with client-side validation and a `mailto:` fallback if the request fails.
- **Project filtering** — client-side category filters on the Work page.
- **Live SAST clock** — footer shows the current South Africa time (UTC+2).
- **Accessible** — semantic HTML, ARIA labels, keyboard-friendly forms, visible focus states and error messaging.

---

## Project structure

```
.
├── index.html          # landing page
├── Work.html           # project archive
├── About.html          # about / story / skills
├── Services.html       # services / process / FAQ
├── Booking.html        # booking request form
├── Contact.html        # contact form
├── logo.png            # favicon / logo
└── README.md
```

Every page is fully self-contained: styles live in a `<style>` block and behaviour in a `<script>` block at the bottom of each file. Shared pages link to one another via relative paths (`Work.html`, `About.html`, etc.).

---

## Getting started

No installation required.

1. **Clone or download** the repository.
2. **Open `index.html`** in any modern browser — or serve the folder with any static server:

   ```bash
   # Python
   python3 -m http.server 8000

   # or Node
   npx serve .
   ```

3. Visit `http://localhost:8000`.

---

## Configuration

### Form endpoint

Both the contact and booking forms POST to Formspree. To point them at your own account, find this line in **`Contact.html`** and **`Booking.html`**:

```js
const FORMSPREE_URL = 'https://formspree.io/f/myeyergz';
```

Replace it with your own Formspree form ID.

### Email address

The fallback `mailto:` link and the visible contact details use:

```js
const EMAIL_ADDRESS = 'sekang.segotso@moov.life';
```

Update this in **`Contact.html`** and **`Booking.html`**, and in the visible `mailto:` links within the markup.

### Phone number

Search for `+27 61 454 8884` in `Contact.html` to update the displayed number.

### Social links

In **`Contact.html`**, the "Elsewhere" list links to LinkedIn, GitHub and Instagram. Replace the `href="#"` placeholders with your real profile URLs.

---

## Customisation

### Colours & type

All design tokens live in the `:root` block at the top of each page's `<style>` section:

```css
:root{
  --bg:#070a0f;
  --accent:#3d9dff;      /* primary blue   */
  --accent-2:#7ee787;    /* secondary green */
  --amber:#ffb454;       /* highlight       */
  --head:#e9f2fc;        /* headings        */
  --text:#b9c9da;        /* body text       */
  --muted:#6d8199;       /* secondary text  */
  /* … */
}
```

Change these once per file and the whole page updates.

> **Tip:** if you plan to grow the site, consider extracting the shared CSS into a single `styles.css` and the shared JS (nav, reveal, clock, back-to-top) into a `main.js` to avoid duplication across pages.

### Adding a project

In **`Work.html`**, duplicate a `<article class="project">` block and set its `data-category` to one of:

- `website`
- `app`
- `frontend`

The filter buttons will pick it up automatically.

### Adding a service

In **`Services.html`**, duplicate a `<article class="service-card">` block inside `.services-grid`.

### Adding an FAQ

In **`Services.html`**, duplicate a `<details class="faq-item">` block inside `.faq-list`.

---

## Browser support

Tested in current versions of Chrome, Firefox, Safari and Edge. Uses modern CSS (`:root` custom properties, `aspect-ratio`, `backdrop-filter`) and vanilla JS (`fetch`, `IntersectionObserver`, `URLSearchParams`), all of which are widely supported.

Graceful degradation:

- Reveal animations fall back to visible content if `IntersectionObserver` is unavailable or reduced motion is preferred.
- Form submission shows a `mailto:` fallback link if the network request fails.

---

## Accessibility notes

- Semantic landmarks (`header`, `nav`, `main`, `footer`, `section`, `aside`).
- The active nav item uses `aria-current="page"`.
- Form fields have associated `<label>`s, `aria-live` error regions and `aria-invalid` toggling.
- The mobile menu button exposes `aria-expanded`.
- `prefers-reduced-motion: reduce` disables animations and smooth scrolling.
- Colour contrast aims to meet WCAG AA for body text on the dark background.

---

## License

This project is personal work. The code is shared for reference — please don't republish the site or its content as your own. If you'd like to use the structure as a starting point, a credit or link back is appreciated.

---

## Contact

**Sekang Segotso**
- Email: [sekang.segotso@moov.life](mailto:sekang.segotso@moov.life)
- Location: South Africa (SAST, UTC+2)
- Booking: [Booking.html](Booking.html)
```

---

**Quick note on usage:** save this as `README.md` in the root of your repository. GitHub will render it automatically on the repo homepage. The links (e.g. `Work.html`) will resolve relative to the README, which works fine since they sit alongside it. If you later move pages into a `pages/` folder, update those paths accordingly.
