# Singhe Logistics — Website (Frontend)

Static frontend for the Singhe Logistics company website. Built from the
purchased "Tanspot" HTML5 logistics template — only branding and service
content are Singhe Logistics's own; page markup, styling, and scripts come
from the template.

There is no backend in this repo. It is plain HTML/CSS/JS — no build step,
no `npm install`, no bundler. Open a page directly in a browser or serve
the folder with any static file server (e.g. VS Code's "Live Server"
extension) to preview it.

## Folder structure

```
.
├── index.html, about.html, ...   # page files — added directly at the root,
│                                  # same as the original template, so its
│                                  # relative links (href="about.html",
│                                  # href="assets/css/...") keep working
│                                  # unmodified
└── assets/
    ├── css/
    │   ├── vendor/                # third-party CSS: bootstrap.min.css,
    │   │                          # all.css (Font Awesome), animate.min.css,
    │   │                          # magnific-popup.css — copy from the
    │   │                          # template as-is, don't hand-edit
    │   └── module-css/            # per-section/component CSS split out by
    │                              # the template (e.g. header, footer, hero)
    ├── js/
    │   └── vendor/                # third-party JS: jquery, bootstrap.min.js,
    │                              # gsap, swiper, wow.js, aos.js — copy as-is
    ├── images/
    │   ├── backgrounds/ blog/ brand/ favicons/ home-showcase/
    │   └── icon/ project/ resources/ services/ shapes/ team/ testimonial/
    └── fonts/
```

Only add files under a directory that matches what's already in it — e.g.
a new services photo goes in `assets/images/services/`, not loose in
`assets/images/`. If a new template asset doesn't fit any existing
category, create a new subdirectory under the matching parent
(`assets/images/`, `assets/css/`, etc.) rather than dropping it at the top
level.

## Where the source template lives

The full purchased template (all page variants, documentation, licensing)
is kept **outside** this repo at:

```
E:\01_Companies\Oora Labs\Singhe Logistics\tanspot-logistics-html5-template-2025-09-14-15-50-33-utc
```

The actual page files are under that folder's `pack-file\01-html-file\`.
Its own documentation page (`pack-file\02-documentation-file\index.html`)
explains what each page file is (e.g. `index.html` = Home One) and how the
CSS/JS is organized — useful background if you're adding a page this repo
doesn't have yet.

## Adding a new page

1. Copy the page's `.html` file from the template's `01-html-file/` folder
   into this repo's root, unchanged.
2. Copy any image/CSS/JS files that page uniquely needs into the matching
   `assets/` subdirectory (check the page's `<link>`/`<script>`/`<img>`
   tags for what it references).
3. Update the site's shared navigation menu (in the header markup that's
   repeated across pages) to link to the new page.
4. Open the page locally and click through the nav to confirm every link
   and asset resolves.

## Forms

Every form on the template (contact, quote requests, etc.) is currently
**UI-only** — the markup and client-side validation exist, but submissions
are not wired to anything yet. This is intentional: the site is launching
on Vercel (static hosting) before eventually moving to cPanel hosting with
PHP support, and the two hosts need different approaches:

- **On cPanel (final host):** the template ships a PHP mail script under
  `assets/inc/` (configured via a `.env` file with recipient details) that
  can be wired back in once the site is live on PHP-capable hosting.
- **Before that, on Vercel (static):** PHP won't run. If forms need to work
  before the cPanel migration, use a static-friendly form endpoint service
  (e.g. Web3Forms or Formspree) instead — point each form's `action` at the
  service's endpoint, no server code needed.

Whoever wires up form submission should update this section once a backend
approach is chosen and implemented.

## Deployment

- **Now:** deployed to Vercel as a static site. Push to the connected
  branch (see Vercel project settings) to deploy — no build command
  needed, it's static HTML.
- **Later:** moving to cPanel/PHP hosting once the frontend build is
  complete. At that point, re-enable the PHP contact form (see Forms
  above) and upload the site files via FTP/cPanel File Manager as
  described in the template's own documentation.

## Git

- Remote: `https://github.com/minurajayasingha/Singhe_Logistics_Website_FE.git`
- `.gitignore` excludes `.claude/` and `docs/superpowers/` (AI-tooling and
  planning files kept local, not shown in the public repo), `.env`
  (secrets), and standard OS/editor junk. If you use different AI tooling
  that drops its own dotfiles, add them to `.gitignore` too rather than
  committing them.
- Commit messages and workflow are left to whoever is working on the repo
  at the time — no enforced convention.
