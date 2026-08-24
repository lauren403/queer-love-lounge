# One more upload — the Perth page, 60 seconds

Both your uploads landed and both sites are live and correct. Deposit wording is fixed on all 8 QLL pages, the broken "Read more reviews on Google" button is gone from the QLL homepage, and the $50 deposit paragraph is rendering on the clinic fees page.

**One collision, and it's on me.** I staged the QLL files on 23 August. Later that same day you committed `4e0bd80` — "Add the November 2026 in-person option to the Perth page". My copy of `queer-couples-therapy-perth.html` predated it, so when you uploaded the batch it overwrote that commit. Perth was the only file where our edits touched the same page; the other seven were clean.

**What's currently missing from the live Perth page** — the same sentence in two places, the visible FAQ answer and the JSON-LD `FAQPage` block Google reads:

> …across Perth and all of WA, **with in-person sessions in Nedlands from November 2026.** This is a local practice, not a fly-in service.

The attached file has that restored **on top of** your deposit fix — so it has both, and nothing else changes.

---

## Do this

1. Open **https://github.com/lauren403/queer-love-lounge/upload/main**
2. Drag **`queer-couples-therapy-perth.html`** from this folder onto the page
3. Commit message:
   ```
   Restore the November 2026 in-person line on the Perth page
   ```
4. Commit directly to `main`

Then say "done" and I'll verify the live page.

---

## What I checked before writing this

- All 8 QLL pages fetched live: **zero** occurrences of "secures your booking" remaining, new wording present on every one
- QLL homepage: the `PASTE_YOUR_GOOGLE_REVIEWS_URL` 404 button is gone
- Repo-wide grep on current `main`: no old wording, no placeholders left anywhere
- Every other commit you made between my clone and your upload — `16da5e3` and `470bda5`, which touched `relationship-tune-up.html` and `pull-up-a-chair-intensive.html` — was **not** in my 8-file set, so nothing else was overwritten
- All three JSON-LD blocks on the corrected Perth file parse
- Clinic `/offerings`: the deposit paragraph renders with correct typography, once, in the fees section

## How I'll stop this happening again

Before staging files for you to upload, I'll fetch the current `origin/main` and rebase my edits onto it, rather than working from whatever I cloned earlier. A stale local copy is the same failure mode as the stale `~/Downloads/bbc-photo-recovery/` folder — the fix is to re-check the source, not to trust the copy.
