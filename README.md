# Raffle Ticket Converter

A single-page web tool that converts a donations CSV into a ticket-by-ticket raffle list.
Everything runs in the browser — no server, no login, and donor data never leaves the
visitor's computer.

## What it does

- Reads a donations CSV (matched by column header, not position).
- Calculates tickets per donation as `floor(Amount ÷ price per ticket)` — default $5.
- Assigns sequential raffle ticket numbers across two rolls:
  - Roll 1 starts at **100001** (2,000 tickets: 100001–102000)
  - Roll 2 starts at **730161** once roll 1 is exhausted
- Carries two extra columns through to the output: **Child/Family** and **School (APS/PCS)**,
  pulled from spreadsheet columns **W** and **X** by default (both adjustable in Settings by
  column letter). The summary confirms which header each letter mapped to.
- Shows a summary (donations, total tickets, dollar total, ticket-number range, skipped rows),
  a preview table, and a **Download CSV** button.
- Warns when a run crosses into roll 2, and alerts if both rolls would be exceeded.

All settings (price, roll starts, roll size) are editable in the page before generating.

## Files

- `index.html` — the app (this is what gets served).
- `raffle-ticket-converter.html` — identical copy with a descriptive name (optional, can delete).

## Use it locally

Just double-click `index.html` to open it in any browser. No internet required.

## Host it on GitHub Pages (free, public URL)

1. Create a GitHub account at https://github.com if you don't have one.
2. Click **New repository**. Name it (e.g. `raffle-tickets`), set it to **Public**, and create it.
3. On the repo page, click **Add file → Upload files**, drag in `index.html`
   (and `README.md` if you like), then **Commit changes**.
4. Go to **Settings → Pages**.
5. Under **Build and deployment → Source**, choose **Deploy from a branch**.
6. Set the branch to **main** and the folder to **/ (root)**, then **Save**.
7. Wait ~1 minute. The public URL appears at the top of the Pages settings — it looks like:
   `https://YOUR-USERNAME.github.io/raffle-tickets/`

Share that URL with anyone. To update the tool later, edit/replace `index.html`
in the repo and the live site refreshes automatically within a minute.

### Optional: custom domain

In **Settings → Pages → Custom domain**, enter something like `raffle.yourschool.org`,
then add the DNS record GitHub shows you with your domain provider.

## Alternative one-click hosts

- **Netlify Drop** — https://app.netlify.com/drop — drag the file, get a URL instantly.
- **Cloudflare Pages** / **Vercel** — drag-drop or connect the GitHub repo.

## Notes

- The tool regenerates numbering fresh each run starting at 100001. It's designed to process
  one complete donations snapshot at a time, not to append new donations to an earlier batch.
- Because all processing is client-side, hosting it publicly does **not** expose any donor data —
  each visitor's CSV is processed only in their own browser.
