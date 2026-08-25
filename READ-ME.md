# One file to re-upload — the Tune-Up page

**The switch is done and everything else is verified.** `queerlovelounge.com.au` is now the primary domain, the old subdomain 301s page-for-page, and all 13 pages carry canonicals on the new host.

This is one collision to undo.

---

## What happened

You committed **`b00ee7e` — "Route Tune-Up CTAs to enquiry, not the Zanda portal"** after I built the package. My copy of `relationship-tune-up.html` predated it, so the upload overwrote it.

**Live right now on that page:** 4 links back to the Zanda booking portal, 3 "Book a Tune-Up" buttons, and *"Booking opens in a secure new tab"*. Your enquiry routing is gone.

That matters more than a normal copy revert — it's the same class of thing as the couples-can't-self-book decision. The page is inviting people to self-book a Tune-Up through the portal again.

**Nothing else collided.** The other 16 QLL files and all 29 clinic files show only the domain change, and the clinic repo had no commits between my build and your upload.

---

## Do this

1. Open **https://github.com/lauren403/queer-love-lounge/upload/main**
2. Drag **`relationship-tune-up.html`** from this folder
3. Commit message:
   ```
   Restore the enquiry routing on the Tune-Up page
   ```
4. Commit directly to `main`

Then tell me and I'll verify it live.

---

## What's in the file

Your `b00ee7e` version — all four CTAs pointing at the enquiry mailto, *"Enquiries go straight to Lauren — she replies personally, usually within a day"* — **plus** the domain change applied on top.

Checked before packaging: 0 references to the old host, 0 Zanda booking links, 4 "Enquire about a Tune-Up" CTAs, all 3 JSON-LD blocks parse.

---

## Why this keeps happening, and what actually stops it

Twice now — the Perth page on Sunday, this today. The mechanism is always the same: **a GitHub drag-upload is a whole-file overwrite with no merge**, so a staged file that's even minutes stale silently reverts whatever landed in between. It never conflicts, never warns.

Rebuilding from `origin/main` immediately before packaging isn't enough, because the window between my build and your drag is exactly where the commit lands.

**The real fix is authorising `lauren403/queer-love-lounge` and `lauren403/bodybelongingclinic` for this session.** Then I push instead of staging — git merges, conflicts surface loudly instead of silently, and this failure mode disappears. Until then the workaround is narrow: tell me before you commit anything, and I rebuild.

---

## Verified after the switch

| Check | Result |
|---|---|
| Netlify primary domain | `queerlovelounge.com.au` ✓ |
| `www` | Redirects automatically to primary ✓ |
| All 13 pages on new domain | 200, canonical **and** `og:url` on the new host, zero old-host references ✓ |
| `sitemap.xml` | 12 entries, all new host ✓ |
| Old subdomain → new, page-for-page | `/queer-couples-therapy-perth.html` and `/relationship-tune-up.html` both land on the same path ✓ |
| Clinic site | Every checked page links to the new domain, zero old-host references ✓ |
| Certificate | Covers all four hostnames, auto-renews 23 Nov ✓ |

---

## Still yours, in order

1. **Google Workspace domain alias** for `queerlovelounge.com.au` → then the 74 `mailto:` references follow within the hour
2. **Meta domain verification** — before any spend
3. **GA4** data stream URL
4. **Search Console** — new property → verify → sitemap → **Change of Address**
5. **Instagram bio, Psychology Today, the three referral emails** — final URL from the start
6. **Auto-renew** on the domain in VIPcontrol — still off
