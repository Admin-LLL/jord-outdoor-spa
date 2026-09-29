# Editing your website — a quick guide for Drew

You can now change jorooutdoorspa.com yourself by asking Claude in plain English. Claude makes the
edit, shows you a preview, and nothing goes live until you say so.

## One-time setup (about 20 minutes)

1. **GitHub account** — create one at github.com if you don't have one, and send your username to
   Johnathon. Accept the invite email ("Admin-LLL invited you to jord-outdoor-spa").
2. **GitHub Desktop** — install from desktop.github.com and sign in. Then *File → Clone repository*
   → choose `Admin-LLL/jord-outdoor-spa` → pick a folder you'll remember (e.g. `Documents\Joro Website`).
3. **Claude** — a Claude Pro subscription (claude.ai) and the Claude desktop app (claude.ai/download).
   On Windows, also install Git from git-scm.com (defaults are fine). Open the **Code** tab and
   choose the website folder from step 2. The first time Claude uploads a change, a browser window
   asks you to sign in to GitHub — approve it.

## Making a change

1. Open the Claude app → **Code** tab → your website folder.
2. Say what you want, as specifically as you can:
   - *"Change the drop-in price from $54.95 to $59.95 everywhere it appears."*
   - *"Add a line to the Getting Here page saying the gravel lot is plowed in winter."*
   - *"Write a new journal post about sauna etiquette, about 600 words, using the photo I put in
     the assets folder called winter-steam.jpg."*
3. Claude makes the edit on a separate copy (a "branch") and gives you a link to a **pull request**
   on GitHub (if the page shows a green *Create pull request* button, click it).
4. On that pull request page, wait a minute for the **Deploy Preview** link from Netlify. Open it —
   that's your website with the change, not yet live. Check it on your phone too.
5. Happy? Click the green **Merge pull request** button, then **Confirm**. It's live within a minute.
   Not happy? Tell Claude what to fix; the preview updates. Nothing is live until *you* click Merge.

## Good to know

- **Nothing you do is permanent.** Every version of the site is saved. If something goes wrong,
  any past version can be restored.
- **Don't edit files in the website folder by hand** unless you're comfortable — let Claude do it,
  so the rules it follows (keep prices consistent, don't break the booking or forms) are applied.
- **Photos:** drop them in the `assets` folder and tell Claude the file name. Phone photos are fine;
  ask Claude to resize them.
- **Things to leave to Launch Local:** new pages, big design changes, the booking system, the contact
  forms, ad tracking (Meta Pixel), and anything about the domain or email. Claude will tell you if a
  request falls in this bucket.

## Stuck?

Tell Claude what happened — it can usually explain and fix it. If not, email Johnathon at Launch Local
with the pull request link and a description of what you were trying to do.
