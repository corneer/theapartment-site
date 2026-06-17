# theapartment.se

Static rebuild of **theapartment.se** — the website of the creative agency *the Apartment*.

This repository contains the Webflow static export (2023/2024) with the dynamic
(CMS-driven) content re-integrated so the site is self-hosting and no longer
depends on Webflow's editor or CMS.

## What's here

- `index.html` and other top-level pages (home, showreel, 404, etc.)
- `projects/` — individual project / case study pages
- `css/`, `js/`, `fonts/` — Webflow theme assets
- `images/` — all images, **including the dynamic content restored from the live site**
- `documents/` — Lottie/JSON animations and other documents

## Dynamic content that was restored

A Webflow static export leaves CMS-bound collections empty. The following dynamic
data was downloaded from the live site and baked into the static files:

- **Client logos** — the homepage "Clients" collection (32 logos) was empty in the
  export (`w-dyn-bind-empty`). All 32 SVG logos were downloaded into `images/` and
  the collection markup was populated in `index.html`.
- **CDN images** — 95 images referenced from Webflow's CDN (video poster frames and
  the OpenGraph image) were downloaded into `images/` and all references rewritten
  to local paths.

## Pending: videos (~2 GB)

The work tiles reference background videos (`.mp4` / `.webm`) that are still hosted
on Webflow's CDN (`uploads-ssl.webflow.com`). They were **not** downloaded here to
keep the repo size manageable. When the `Videos/` folder is added, the video URLs in
the HTML should be repointed to local files (and the videos tracked with **Git LFS**,
since they exceed GitHub's 100 MB per-file limit).

## Local preview

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```
