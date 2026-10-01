# P929 Mechanical Punch List – site tracker

Static web app for ticking off punch list items on site. Hosted on GitHub Pages.
The punch list data is **encrypted** (`punchlist.enc.json`, AES-256-GCM). The repo and the
Pages site can be seen by anyone with the link, but the data only opens with the passcode.

## Files
| File | What it is |
|---|---|
| `index.html` | The app (site team + PM tools) |
| `punchlist.enc.json` | Encrypted master punch list. Replace this file to publish a new revision |

## One-time setup (about 5 minutes)
1. GitHub > New repository. Give it a neutral name (e.g. `pl-tracker-929`), no client name.
2. Upload `index.html` and `punchlist.enc.json` to the root of the repo. Commit.
3. Settings > Pages > Source: *Deploy from a branch* > Branch `main`, folder `/ (root)` > Save.
4. After a minute the site is live at `https://<your-user>.github.io/<repo>/`.
5. Optional: edit `CONFIG.updateEmail` near the top of the script in `index.html` so the
   Email button pre-fills your address.

## Site team
1. Open the link on the phone, enter name + passcode (remembered on that phone).
   Add to Home Screen for an app icon.
2. Tap an item > set status, date, sign-offs, note, photos > Save.
3. Tap **Send update** > Share > WhatsApp / email to the PM.
   The update is a small `.txt` file plus photos. Changes stay on the phone (marked
   "Sent") until the PM publishes a master that includes them.
4. Works with poor signal: the last downloaded list and all unsent changes are kept on the phone.

## Project manager
Open the site with `?pm` on the end: `https://<your-user>.github.io/<repo>/?pm`
1. **Import update files** (pick one or many `.txt` updates from WhatsApp/email).
2. Review, untick anything you don't accept, **Apply ticked changes**.
3. **Download master** > enter revision > upload the downloaded `punchlist.enc.json`
   to GitHub, replacing the old one (Add file > Upload files > Commit).
4. Site phones pick it up on **Refresh** or next open.
5. **Export Excel** produces an area summary plus one sheet per area, with site notes.

Duplicate or older updates are skipped automatically, so importing the same file twice is safe.

## Passcode
Initial passcode is sent separately (not stored in this repo). To change it: PM mode >
**Change passcode** > commit the downloaded file > send the new passcode to the team.
Phones with the old passcode are asked for the new one on their next refresh.

## Limits to know
- Not real-time multi-user: phones don't see each other's ticks until the PM publishes.
- "Closed" on the app is a site claim. QC/Proxa sign-off is captured per item, and items closed
  without Proxa initials are flagged "Proxa sign-off outstanding".
- Photos are not stored in GitHub; they travel with the update. File them in the project folder.
- Clearing browser data on a phone deletes its unsent changes.
