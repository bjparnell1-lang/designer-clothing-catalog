# Designer Clothing Catalog — Website Handoff

This repo is the handoff for building the designer clothing catalog website
(ChatGPT Sites). It tells the website builder everything the catalog is, where
every photo lives, and — most importantly — which name to show customers vs.
which name to use when an order needs to be placed with the supplier.

Owner: Robert Anthony Parnell. GitHub: `bjparnell1-lang`.
Last updated: 2026-11-08.

## Where everything lives

- **Google Drive root:** `designer clothing`
  (ID `1elDDNrJSAvRaQrks5lQX7Zio2IBBGQCW`)
- **Cross-reference tracker (source of truth for names):**
  Google Sheet "Designer Catalog - Product Cross-Reference"
  (ID `14H5m_eVRyKjVrhe17sye2qA8EvGP5c17muO5HEvh9gA`),
  inside the `designer clothing` Drive folder.
  https://docs.google.com/spreadsheets/d/14H5m_eVRyKjVrhe17sye2qA8EvGP5c17muO5HEvh9gA/edit
- **Canva catalog (separate, built by another agent):**
  "Designer Clothes Website" (design `DAHYXtDPTuw`), nav categories
  Jeans, Outerwear, Hoodies, Tracksuits. Keep the Drive structure in sync
  with it; new folders get mirrored in Canva.

## The two names — the key rule

Every product has TWO names. Do not mix them up.

1. **Backend / order name = the source label.**
   This is the folder name and the file-name prefix, e.g. `LightPink 41/100`.
   It comes from the place the item is ordered from (usually a DHGate store
   listing). When a customer buys something, the order must carry this name
   (plus the store and the source link) so Robert can find the exact listing
   and order it. Never rename it, and keep the `N/100` suffix verbatim —
   it is part of the label.
2. **Public-facing name = the real product name.**
   This is the tracker's "Real product name" column, e.g.
   `Balenciaga Tape Type Hoodie Oversized, Faded Black`. It comes from the
   real retail/resale listing title (Grailed, Editorialist, Saks, StockX…).
   This is the name the website shows customers. It must match the photo.

The machine-readable version of this mapping is `catalog.json` (and
`catalog.csv`). The website should read the public name from there (or from
the tracker sheet) and keep the source label as the backend/order identifier.

**Source color name:** record the color name exactly as the supplier store
shows it (e.g. `Green 12/100`), next to the real color. The store's color
word often does NOT describe the garment — the `Green 12/100` garment is
black. The source color name is the name to use when ordering; the real
color is the name customers see. Never confuse the two.

## Store names — how ordering works (read this first)

**The folder directly under each brand folder IS the store name.**
That folder's name is the name of the supplier store the item is ordered
from — usually a DHGate store (e.g. `damai2023`, `casualyn`,
`museround27`). It is not a generic label. When a customer buys something,
the order must carry these three things together, because together they
point Robert to the exact listing to order from:

1. **Store name** — the folder name (also the `store` field on every item
   in `catalog.json` / `catalog.csv` and the `Store` column in the tracker
   sheet).
2. **Source label** — the color subfolder name (e.g. `LightPink 41/100`).
3. **Source link** — the exact listing page for that item.

Example: an order for the Tape Type hoodie reads store `damai2023`,
label `LightPink 41/100`, link = the DHGate listing for that item
(the DHGate link for the damai2023 batch has not been provided yet —
`source_link` is empty until it is). The public-facing name
(`Balenciaga Tape Type Hoodie Oversized, Faded Black`) is for customers
only — never use it to order. If an item's store is `TBD`, the store is
not known yet and the order cannot be placed until it is found.

**Source links vs photo reference links — do not mix these up.**
There are two different kinds of link on every item, and they are never
interchangeable:

- **Source link** — where the item is BOUGHT: the DHGate listing (or
  the YUPOO category for the Purple Brand drop). This is the only link
  that belongs in an order, together with the store name and source
  label.
- **Photo reference link** — where the real, unedited photo was FOUND
  (Grailed, Vestiaire Collective, Editorialist, Saks, StockX,
  Reversible, Kering DAM, etc.). DHGate photos are edited — brand
  names blocked or truncated, e.g. "balen" instead of "Balenciaga" —
  so the real photo is found by reverse image search and saved as the
  product image customers see. The link only records where that photo
  came from. It is NOT a source and must NEVER be used to order.

A past mistake, corrected 2026-11-08: the Grailed, Vestiaire,
Editorialist, and Reversible links for the damai2023 items were
recorded as source links. They have been moved to
`photo_reference_link` in `catalog.json` / `catalog.csv` and to the
"Photo reference link" column in the tracker sheet. Their `source_link`
is empty until the DHGate ordering links are provided.

**Per-item record — every product carries all five, when available:**
store name, source link (DHGate ordering link), color identifier,
numbering, and photo reference link. They are separate fields on every
item in `catalog.json` / `catalog.csv` (and separate columns in the
tracker sheet), so nothing has to be parsed out of a label:

- **Store name** — e.g. `damai2023` (see above).
- **Source link** — the DHGate listing where the item is bought, when
  there is one. Never a photo reference link.
- **Photo reference link** — where the real photo was found (Grailed,
  Vestiaire, Editorialist, etc.). Provenance for the public-facing
  image only. Never used to order.
- **Color identifier** — the color word on its own, e.g. `LightPink`.
- **Numbering** — the item's number in the store's listing, written
  `N/100`, e.g. `41/100` means item 41 out of 100. So the label
  `LightPink 41/100` splits into color identifier `LightPink` +
  numbering `41/100`. A label like `3/100` would mean item 3 out of 100.
  If a listing has no numbering, the field is left blank.

(Sets that predate this system don't have per-item numbering: the
`casualyn` files use the store's option codes `a1`–`a30` in their file
names, and the `museround27` files use `color1`–`color7`.)

## Drive structure

```
designer clothing/
├── hoodies/                                  (ID 1VF9SrirUMgwGutQZmnR5jwgnjpyowNUv)
│   ├── Balenciaga/                           (ID 1oekTNZ4pi3Ob74TH7w10Mf05ZAeff56r)
│   │   ├── casualyn/                         (STORE — DHGate store; item 1119231452)
│   │   └── damai2023/                        (STORE — DHGate store; ID 1I7cWey4y-7fTWWR-tCgSdwFSX9tZZe0G)
│   │       ├── Green 12/100/
│   │       ├── Olive 40/100/
│   │       ├── LightPink 41/100/
│   │       └── Black 11/100/                 (pending — link missing)
│   └── Louis Vuitton/                       (ID 1vZiT9efdXISdIkIC1wdbRaNZVHBBmS5E)
│       └── museround27/                      (STORE; ID 1k9rBCOabFhXurNWa4OXGgOaLShixMFDw)
├── jeans/
│   └── Purple Brand/                         (YUPOO drop — PAUSED, see below)
├── outerwear/
├── tracksuits/
└── sneakers/                                 (not created yet — pending)
```

Folder rules:

- Category first, then brand, then store, then one subfolder per color,
  named by the color label (e.g. `Green 12/100`).
- Store for the current batch is `damai2023` unless Robert says different.
- Photo files inside a color folder are named
  `<label>-front.jpg`, `<label>-back.jpg` (and `-detail`, `-model-front`,
  etc. when more views exist), where `<label>` is the source label
  lowercased with spaces as hyphens (e.g. `lightpink-41-100-front.jpg`).

## Photo rules

- **Hoodies:** use only the first 2 photos in the listing carousel
  (front + back), unless Robert says otherwise for that item.
  (LightPink 41/100 was the exception: all 6 photos.)
- **Sneakers:** up to 3 pics per color, from a reverse image search.
  Check the first source found online for other views of the same listing
  first — it usually has them. If only 2 can be found, use 2; if only 1,
  use 1. If a color can't be found online at all, use the cropped DHGate
  photo (crop the top "hot selling" header and the bottom words off).
- **Authentic photos only, in general:** DHGate/seller images are leads,
  not catalog images — find the real, unedited photo showing the full brand
  name (reverse image search first, then StockX, eBay, Mercari, Grailed,
  retailer sites). Exception: when Robert explicitly says to save the
  screenshots he sent (cropped), save those as instructed.
- Product-only images. Never whole webpages, listing UI, or review text.

## Current items

See `catalog.json` / `catalog.csv` and the tracker sheet for the full data.
Summary (2026-11-08):

| Source label | Store | Real product name | Status |
|---|---|---|---|
| Green 12/100 | damai2023 | Balenciaga Retro Printed Hoodie (Top League multi-logo design) | Done — front + back in Drive |
| Olive 40/100 | damai2023 | TBD — Balenciaga stencil logo hoodie (BALENC AGA) | Done — front + back in Drive; real name still needed |
| LightPink 41/100 | damai2023 | Balenciaga Tape Type Hoodie Oversized, Faded Black | Done — all 6 photos in Drive |
| Black 11/100 | damai2023 | Balenciaga Racing Logo Print Long Sleeve Hoodie | Link found (Reversible) — photos pending |
| casualyn (53 files) | casualyn | 15 Balenciaga designs, real names in REPLACEMENTS log | DELETED 2026-11-08 — all 53 photos trashed (DHGate-sourced, incl. the 15 real replacements; restorable from trash) |
| museround27 (6 files) | museround27 | Louis Vuitton monogram crewneck sweatshirts | DELETED 2026-11-08 — all 6 cropped DHGate screenshots trashed |
| Sneakers, DHGate 1085634430 | TBD | Balenciaga Track trainers | Blocked — DHGate page unreadable (see below) |
| Purple Brand, YUPOO | thomamiri | Purple Brand jeans | PAUSED by Robert — 399 picks selected, not yet downloaded |

Notes:

- The source labels often do NOT describe the garment color (e.g. the
  "Green 12/100" and "Olive 40/100" photos both show a black hoodie).
  Trust the photo and the "Real color" column, not the label word.
- The `casualyn` set's 15 authentic replacements and their sources are
  logged in `authentic/REPLACEMENTS.md` (local working files, not in Drive).

## Pending / blocked items

- **Sneakers (DHGate item 1085634430, "designer track tracks mens women
  trainers"):** the DHGate page cannot be read — the browser never loads,
  DHGate blocks direct reads, and search has no trace of the listing.
  Store name and colors are unknown. Unblock by opening the link in the
  live browser and handing control back, or by sending screenshots of the
  page (store name + color options).
- **Black 11/100:** link found — Reversible listing 583629410, brand new, size JP 1. Photos still pending: Reversible blocks direct reads (Cloudflare) and the browser could not load the page. Needs the first 2 photos as screenshots, or the link opened in the live browser.
- **Olive 40/100 real name:** not yet identified.

## How to add a new item

1. Robert sends a link (or photos) plus a source label like `Color N/100`.
2. Save the photos to Drive under
   `designer clothing/<category>/<brand>/<store>/<label>/`
   following the photo rules above.
3. Add a row to the tracker sheet AND to `catalog.json` / `catalog.csv`
   with the source label, store, real product name, real color, source
   link, photo file names, and price ONLY if the user provided it —
   never take a price from a photo-reference link.
4. If the real product name can't be found, put `TBD` and keep the source
   label — never invent a real name.

## Useful methods (verified)

- **Grailed listings:** `https://www.grailed.com/api/listings/<id>` returns
  full JSON (including the `photos` array in carousel order with direct
  `media-assets.grailed.com` URLs) via a plain page fetch. Download with
  curl + `Referer: https://www.grailed.com/`.
- **Editorialist:** the page HTML blocks curl (AWS WAF), but the thumbnail
  CDN works:
  `https://editorialist.com/thumbnails/600/<path>/<id>~<color>_<ts>_<n>.webp`
  (indices from 0 upward; 403 means no more photos). Files arrive
  gzip-compressed — gunzip before opening. Convert webp to JPEG for Drive.
- **Google Lens** is unusable (requires sign-in). **Browser automation**
  is unreliable (windows frequently never load). Reliable route:
  text search + direct page/API reads + curl + visual verification.
