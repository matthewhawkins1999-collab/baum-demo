# Baum demo — publication record

Updated Saturday, November 7, 2026 (America/New_York), morning. **This file is an internal note.** It is not linked from `index.html`. `_config.yml` excludes it from the GitHub Pages build, so it is not served as site content.

## Publish approval

Matt (repo owner, matthewhawkins1999-collab) explicitly approved publication on the morning of November 7, 2026 (ET).

Live URL: https://matthewhawkins1999-collab.github.io/baum-demo/

Pages source (unchanged): branch `main`, path `/`, legacy Jekyll build.

No DocsBot account, bot id, training, starter, model, privacy, or other bot settings were changed for this publish. The page still embeds the existing iframe only.

## What this publish contains

Reviewed `index.html` from the November 6 review package, byte-for-byte, plus only the assets that page loads:

- `assets/baum_logo-0031024_1-1.webp` — original logo
- `assets/cropped-Baum-Logo-Red-Outline.png` — original logo fallback
- `assets/new_logo_van.png` — original van photo
- `assets/winner-2024.png` — 2024 Community’s Choice award badge
- `assets/baum-icon.jpg` — favicon the reviewed page already references (logo water-drop)

Kept as reviewed:

- Single responsive DocsBot iframe, `src` `https://docsbot.ai/iframe/uIrpTszTQ0NNqHtcoJN1/nHEbStVbHO8S8HtiqTCK`. No `allow` attribute (no microphone or camera). Host page does not load `DocsBotAI.init`.
- Separate scripted preview, labeled SCRIPTING PREVIEW, with NOT SENT wording.
- Demo disclosures (not the official site, not affiliated, review copy, business details from Baum’s public website).
- No safety-certification claims and no guarantees added.

Not added to the repo, and therefore not linked or served:

- `.bak` files, screenshots, `verify-docsbot.json`, `verify-final.json`
- Other internal notes (`FINAL-REVIEW.md`, `bob-final-checks.md`, `content-notes.md`, `setup-and-training.md`, `BAUM-REVIEW-NOTES-laptop.md`, `STATUS.txt`, `source-baum-demo.html`)
- Unused images `IMG_9806.jpg` and `unnamed.png`

## Blockers at publish time

- **Emergency-answer blocker: resolved.** Matt resolved it on the DocsBot side. Three tests passed: gas, flooding/electrical, and burst pipe.
- **Credit allowance: unverified.** The older figure of about 68 team credits remaining is outdated. Do not treat it as the current allowance. This publish did not recheck the DocsBot credit balance and did not send a live chat message.
- Other November 6 notes (hours conflict between listings, street ZIP 44702 vs 44703 in older public copy, limited prior Q&A coverage) were not re-tested in this publish and are not claimed fixed. The page still tells people to call the shop and does not certify emergency service or after-hours dispatch.

## Rollback

The site that was live before this publish is commit `1183ce3fc8a383a92f9446d7d0ad3f4a26530b2f` (tag `backup/pre-reviewed-publish-2026-11-07`). That tree is only the scripted `index.html`. Its SHA-256 is `123ee13f632ea42236da916ecbead12eab193982e1bf4f5e0af0b30ce50042e1`. A copy is in `_backup/index.html`. `_backup/` is not published.

To restore that page and take the reviewed demo off GitHub Pages:

1. `git fetch origin tag backup/pre-reviewed-publish-2026-11-07`
2. From an up-to-date `main`, restore the old tree without force-pushing. Either:
   - `git revert -m 1 <publish-merge-sha>` (use this when the publish landed as a merge commit), or
   - check out the tag’s `index.html`, then delete the paths this publish added: `assets/`, `_config.yml`, `REVIEW-NOTES.md`, and `_backup/`.
3. Commit on `main` and push. Do not force-push `main`.
4. Wait until the Pages build for that commit is `built`, then confirm https://matthewhawkins1999-collab.github.io/baum-demo/ matches the November 1 page (SHA-256 above) and that `/assets/` URLs are gone.

The publish merge SHA is the merge commit on `main` that introduced this file. `git log origin/main --grep 'reviewed Baum demo'` finds it after the merge.

---

# Historical review record (November 6, 2026)

The sections below are the pre-publish review. Lines that say the copy was “not published” or “not final” described November 6, before Matt’s November 7 approval. They are history, not the current status.

Separate review artifact. Updated Friday, November 6, 2026 (America/New_York), ~9:55 AM ET. At that time nothing had been deployed. `/workspace/baum-demo/` (including its git tree and `index.html`) was not modified by the review pass.

- Review page at the time: `/workspace/baum-demo-review/index.html`
- Source preserved (not edited during review): `/workspace/baum-demo/index.html`
- SHA-256 of the pre-publish `/workspace/baum-demo/index.html`: `123ee13f632ea42236da916ecbead12eab193982e1bf4f5e0af0b30ce50042e1`
- Source mtime unchanged during review: 2026-11-01 10:10:37 AM ET
- Backup of review HTML before the DocsBot pass: `/workspace/baum-demo-review/index.html.bak-pre-docsbot` (not included in this repo)

## Embed method chosen (ONE only)

**Inline DocsBot iframe (“Frame”)** inside the existing chat panel — not the floating `DocsBotAI.init` script widget.

Why iframe for this branded review:

- The page already has a red FAB + chat panel; putting DocsBot inside that panel keeps **one** primary chat launcher.
- Avoids a second competing DocsBot floating button fighting `#fab`.
- Mobile fullscreen and desktop floating panel sizing already existed; iframe fills `#docsbotFrameWrap` with CSS (`width/max-width:100%; height:100%; flex:1`).

Floating `DocsBotAI.init({id: "uIrpTszTQ0NNqHtcoJN1/nHEbStVbHO8S8HtiqTCK"})` + `https://widget.docsbot.ai/chat.js` was **not** mounted on the host page. (The iframe page itself loads `widget.docsbot.ai/chat.js` internally — that is DocsBot’s own page, not a second host-page embed.)

### Owner-provided iframe snippet (verbatim evidence)

```html
<iframe src="https://docsbot.ai/iframe/uIrpTszTQ0NNqHtcoJN1/nHEbStVbHO8S8HtiqTCK" width="600" height="650" frameborder="0" allowtransparency="true" scrolling="no" allow="microphone; camera"></iframe>
```

### Adjustments from that snippet (markup / accessibility only)

| Owner snippet | Review copy |
| --- | --- |
| Fixed `width="600" height="650"` | Kept those HTML attributes for provenance; CSS forces `width:100%; max-width:100%; height:100%` so the panel is responsive on ~390 and ~1280 |
| `allow="microphone; camera"` | **Omitted** (`allow` attribute absent) — chat does not need mic/camera for this demo |
| `frameborder` / `scrolling` / `allowtransparency` | Dropped obsolete attributes; equivalent via CSS `border:0` |
| (none) | Added `id="docsbotFrame"`, `title="Baum Plumbing live AI assistant (DocsBot)"`, `loading="lazy"`, `referrerpolicy="no-referrer-when-downgrade"` |

Bot id path used exactly: `uIrpTszTQ0NNqHtcoJN1/nHEbStVbHO8S8HtiqTCK`

Owner-provided floating-widget loader (not used on host page; kept here for record):

```html
<script type="text/javascript">window.DocsBotAI=window.DocsBotAI||{},DocsBotAI.init=function(e){return new Promise((t,r)=>{var n=document.createElement("script");n.type="text/javascript",n.async=!0,n.src="https://widget.docsbot.ai/chat.js";let o=document.getElementsByTagName("script")[0];o.parentNode.insertBefore(n,o),n.addEventListener("load",()=>{let n;Promise.all([new Promise((t,r)=>{window.DocsBotAI.mount(Object.assign({}, e)).then(t).catch(r)}),(n=function e(t){return new Promise(e=>{if(document.querySelector(t))return e(document.querySelector(t));let r=new MutationObserver(n=>{if(document.querySelector(t))return e(document.querySelector(t)),r.disconnect()});r.observe(document.body,{childList:!0,subtree:!0})})})("#docsbotai-root"),]).then(()=>t()).catch(r)}),n.addEventListener("error",e=>{r(e.message)})})};</script>
<script type="text/javascript">
  DocsBotAI.init({id: "uIrpTszTQ0NNqHtcoJN1/nHEbStVbHO8S8HtiqTCK"});
</script>
```

No CSP meta tag was added. Host page has no CSP that blocks `docsbot.ai` / `widget.docsbot.ai`.

## Live AI vs scripted preview

| Surface | How to open | Labeling |
| --- | --- | --- |
| **Live AI (DocsBot iframe)** | Red FAB: “Ask us anything · Live AI” → `#chat` | Header: “Live AI (DocsBot) · answers 24/7 · a real person follows up”; footer tag: “Live DocsBot embed · review copy…” |
| **SCRIPTING PREVIEW** | Secondary control left: “Scripted preview (demo answers · nothing sent)” → `#scriptedChat` | Gray header “SCRIPTING PREVIEW”; “Demo answers only · nothing is sent · not the live AI”; footer “NOT SENT”; callback form still “Demo: nothing is sent” |
| Owner view | “Owner view” | Unchanged sample leads; still device-local / nothing sent |

Hero pill: “Live AI chat · answers 24/7, even after we close · demo review” (the chat answers around the clock; this is not a claim that Baum dispatches 24/7 or is safety-certified).

Demo / review / not-affiliated banner and footer disclosures kept.

## Contact / location links preserved

- `tel:+13304563466` on Call button and Visit us / scripted answers
- Maps: `https://maps.google.com/?q=1012+Tuscarawas+St+W+Canton+OH+44702`
- Address text: 1012 Tuscarawas St W, Canton, OH 44702
- **No payment links invented** (none existed to preserve)

## Brand assets (unchanged from prior review pass)

Real Baum logo, van, winner badge, favicon. Colors `--red:#c62026` / `--dk:#1d2430`.

## Verification during review (widget load only — no credit-consuming chats)

Local server during review. Playwright Chromium headless opened the review page at viewports **390×844** and **1280×800**. Live panel opened via FAB; **no text typed into DocsBot and no send clicked.**

### Evidence — iframe / network loaded YES

- `#docsbotFrame` present, visible; `src` = `https://docsbot.ai/iframe/uIrpTszTQ0NNqHtcoJN1/nHEbStVbHO8S8HtiqTCK`
- iframe document HTTP **200**; `X-Frame-Options: ALLOWALL`
- Inside iframe: `https://widget.docsbot.ai/chat.js` **200**; `https://docsbot.ai/api/widget/uIrpTszTQ0NNqHtcoJN1/nHEbStVbHO8S8HtiqTCK` **200**
- Host page does **not** contain `DocsBotAI.init` or `#docsbotai-root` (iframe method only).
- Failed DocsBot/network requests: **none**. Console errors related to DocsBot/CSP: **none**.
- Machine-readable log from that pass (`verify-docsbot.json`) was not committed.

### Answer quality — November 6 note, superseded in part on November 7

No questions were sent to DocsBot during the November 6 HTML review. Render evidence only: greeting UI, suggested prompts, input chrome.

Matt later replaced Manny→Baum starters in DocsBot Configure. Suggested prompts observed in the final review screenshots said Baum, not Manny.

**November 7:** Matt reported the emergency-answer blocker resolved on the DocsBot side, with three passing tests (gas, flooding/electrical, burst pipe). Credit allowance was not rechecked; the old ~68 remaining figure is outdated.

## Explicit non-actions (review pass and this publish)

- **No DocsBot account, bot ID, or training changes** in the review pass or in this publish
- **No credit-consuming DocsBot test chats** from this repo change (panel open for render only; do not send a live message)
- Scripted callback form still NOT SENT
