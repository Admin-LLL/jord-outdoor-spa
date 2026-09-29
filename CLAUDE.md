# Jörð Outdoor Spa — website

Source for the live site **https://www.jorooutdoorspa.com**. Plain HTML/CSS/JS, no build step.
Hosted on Netlify, which **auto-publishes every push to `main` within seconds**.

_Read this whole file before making any change. It applies to every session in this repo._

## The golden rule: never change `main` directly

`main` **is** the live website. All work happens on a branch and goes live through a pull request.

For every change, no matter how small:
1. `git switch main && git pull` — start from the latest live version.
2. `git switch -c edit/<short-description>` — e.g. `edit/winter-hours`, `edit/new-journal-post`.
3. Make the edits. Commit with a plain-English message.
4. `git push -u origin edit/<short-description>`
5. Open a pull request into `main`. If the `gh` CLI is installed and signed in, use
   `gh pr create`. Otherwise give the user this link to click **Create pull request**:
   `https://github.com/Admin-LLL/jord-outdoor-spa/compare/main...edit/<short-description>?expand=1`
6. Netlify posts a **Deploy Preview** link on the PR within a minute or two. Tell the user to open
   it and check the change on phone and desktop.
7. **The user merges, not you.** When they're happy, they click **Merge pull request** on the PR
   page. Merging = going live. If they ask for more changes, commit them to the same branch and
   push again; the preview updates.

Never: push to `main`, merge PRs, force-push, rewrite history, or delete branches you didn't create. If a git command fails or something looks off, **stop and explain** —
don't improvise a fix with destructive commands.

## Site structure

| File | Page |
|---|---|
| `index.html` | Home (hero, experience, newsletter signup) |
| `session-rates.html` | Rates & packages |
| `private.html` | Private events + inquiry form |
| `giftcards.html` | Gift cards |
| `journal.html` | Wellness Journal (article cards + full articles) |
| `faqs.html` | FAQ |
| `thestory.html` | Our Story (Drew's bio) |
| `getting-here.html` | Directions, parking, what to bring |
| `assets/` | Images and logo |
| `_redirects` | Netlify redirects (old Squarespace URLs → new pages) |

Each page is **self-contained**: its own `<style>` block, its own copy of the nav and footer.
So:
- **Nav or footer changes must be made on all 8 pages**, identically.
- **Prices appear in more than one place** (at least `session-rates.html`, `faqs.html`, often
  `index.html` and `private.html`). When changing a price, hour, temperature, phone number or email,
  search every `.html` file for the old value and update all of them. List what you changed.

## Do not touch (unless the user explicitly asks and understands the risk)

- **Meta Pixel** — the `fbq(...)` script in each page's `<head>` and the `fbq('track', ...)` calls on
  buttons. This is ad tracking; breaking it silently breaks ad reporting.
- **Forms** — anything with `data-netlify`, `name="form-name"`, or `bot-field`. The private-events
  and newsletter forms depend on these exact attributes to deliver submissions.
- **FlyBook booking links** (`go.theflybook.com/...`) — this is how guests pay. Don't change the URL.
- **`_redirects`** — keeps old links and Google results working, and hides these internal files.
- **`CLAUDE.md`, `EDITING-GUIDE.md`, `.claude/`** — the rules for editing this site.

## Look & feel

- Fonts: **Cormorant Garamond** (headings) + **Outfit** (body), loaded from Google Fonts.
- Colours are CSS variables in each page's `:root` — use them, don't invent new colours:
  `--dark #0e1510` (background) · `--ember #c8813a` (accent/buttons) · `--cream #f2ead8` (text).
- Tone: calm, warm, unhurried. Short sentences. Canadian spelling.
- Match existing sections — copy an existing card/section and change its content rather than
  designing new layouts from scratch.

## Images

- Put new images in `assets/` with lowercase-hyphenated names (`winter-sauna-steam.jpg`).
- Resize before adding: max ~1600px wide, ideally under 400 KB. Large photos slow the site on phones.
- Always write a meaningful `alt="..."` description.

## Journal posts

Articles live in `journal.html`: a card in the `.journal-grid` plus the full article content that
`openArticle(n)` displays. To add a post, copy the pattern of an existing one exactly, give it the
next index, and check both the card and the opened article in the Deploy Preview.

## Before opening the PR, check

- The page still opens without errors and looks right at phone width.
- Every edited value was updated on every page it appears.
- Nothing in the "Do not touch" list changed (`git diff` — review it and summarise it for the user).

## Help

Built and maintained by Launch Local. If a change is bigger than text/images/prices — new pages,
layout redesigns, forms, tracking, domain or hosting — or if something breaks, stop and suggest the
user contact Launch Local rather than attempting it.
