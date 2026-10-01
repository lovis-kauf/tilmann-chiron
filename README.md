# tilmann-chiron.com

Static website for the practice of Dr. med. Barbara Tilmann, Peißenberg.
Plain HTML and one stylesheet — no build step, no framework, no database.
Whatever is on the `main` branch is what the live site shows.

## How it's put together

| Path | What it is |
|---|---|
| `<lange-slugs>/index.html` | The pages themselves, each at its original Joomla URL |
| `index.html` | The homepage |
| `assets/style.css` | The only stylesheet. Colours are CSS variables at the top |
| `bilder/` | Photos, already resized and compressed |
| `behandlung.html`, `termin.html`, … | Short-name redirects into the long folders |
| `sitemap.xml`, `robots.txt` | For search engines |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is |

Every page shares the same header, navigation and footer, copied into each file.
Changing the navigation means changing it in each page — ask Claude to do it.

## URLs — do not rename these folders

Every page lives at the **exact address it had on the old Joomla site**, because
those addresses are what Google has indexed and what existing links point at.
That is why the folders have 200-character names: they are not clutter, they are
the URLs.

`homoeopathie-allergien-abwehrschwaeche-…/index.html` is served at
`/homoeopathie-allergien-abwehrschwaeche-…`.

Renaming a folder changes that page's URL and throws away its search ranking. If
a page ever genuinely needs a new address, keep the old folder and put a
redirect in it — there are examples in this repository.

The short names (`behandlung.html`, `termin.html`, …) are **redirects only**.
They exist so shorthand links keep working. The real page is always the
`index.html` inside the long folder.

Trailing slashes: GitHub Pages serves `/slug/` directly and sends `/slug` there
with a permanent redirect. Both forms of every old address work, and Google
treats a permanent redirect as the same page.

## Before this goes live

1. **Contact form — done, but check the destination.** The form posts to
   Formspark form `Hlu0y0VAH`. One form serves both websites; each sends a
   different subject line, so enquiries are distinguishable in the inbox.
   In the Formspark dashboard, set the notification address to the mailbox that
   should receive them — while `drbarbara@tilmann-chiron.com` does not exist
   yet, it goes to the account owner's address.
2. **Impressum.** The entries marked `<!-- BITTE PRÜFEN -->` in `impressum.html`
   are best guesses about the responsible medical chamber and supervisory
   authority. Confirm them with Barbara before publishing — a wrong Impressum
   on a doctor's site is the kind of thing that attracts a Abmahnung.
3. **Praxisinformation.** The notice about the practice being closed lives in
   one place: the `NOTICE` block. It appears on `index.html` and `termin.html`.
   The old site's version promised a return "Mitte/Ende Februar", which has
   passed, so that sentence was dropped. Update or remove it when the situation
   is clear.
4. **Custom domain.** In the repository: Settings → Pages → Custom domain →
   `tilmann-chiron.com`, then tick "Enforce HTTPS". Only after the DNS for the
   domain points at GitHub.

## Privacy, deliberately

The site makes no third-party requests at all: no web fonts, no embedded maps,
no analytics, no cookies. That is why the Datenschutzerklärung is short and why
no cookie banner is needed. If anything is ever embedded from another server —
a Google Map, a font, a video — the Datenschutzerklärung has to change and a
consent banner probably becomes necessary. Worth avoiding.

## Making changes

Ask Claude for the change, review the diff in GitHub Desktop, commit and push.
The live site updates about a minute later. Every version is kept, so a bad
change can be reverted with two clicks.
