# My Slambook

A dynamic, single-page slambook. Friends open the site, answer 30 questions
(about themselves and about our friendship), and their page is saved to a
Supabase database. A separate, passcode-protected admin dashboard shows every
entry with ratings and averages.

## Files
- `index.html` — the public fill-in slambook (the page friends use)
- `admin.html` — private admin dashboard (also at `/admin`)

## Tech
- Paper Design **Swirl** shader background + halftone texture
- **GSAP** wind-blown text reveal on each question
- Line-art SVG icons, editorial Inter Tight / JetBrains Mono type
- **Supabase** for storage (public page can only insert; reads are gated by a
  passcode enforced inside the database via a SECURITY DEFINER function)

## Deploy on Netlify
1. Push this folder to a GitHub repo (see below).
2. On https://app.netlify.com → **Add new site → Import an existing project**.
3. Pick this repo. No build command needed; publish directory is `.`.
4. Deploy. Your slambook is live at the Netlify URL; admin is at `/admin`.

## Admin passcode
Reads are protected by a passcode checked inside the Supabase function
`get_slambook_entries`. Ask the owner to rotate it anytime.

## Notes
- The Supabase URL + publishable key in the code are safe to expose publicly;
  row-level security prevents anyone from reading entries without the passcode.
- The shader and GSAP load from a CDN, so they need internet to appear; the
  form itself still works against the maroon gradient fallback.
