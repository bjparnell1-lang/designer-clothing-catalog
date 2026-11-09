# Designer Clothing Catalog — Website Handoff

This repo is the handoff for building the designer clothing catalog website
(ChatGPT Sites). It tells the website builder everything the catalog is, where
every photo lives, and — most importantly — which name to show customers vs.
which name to use when an order needs to be placed with the supplier.

Owner: Robert Anthony Parnell. GitHub: `bjparnell1-lang`.
Last updated: 2026-11-08.

**Agent handoff:** the step-by-step playbook for the agent doing the
sourcing and filing (reverse image search, reading store/label/
numbering from Robert's drops, Drive + tracker + catalog updates) is
in [`WORKFLOW.md`](WORKFLOW.md). The website builder reads this
README; the sourcing agent follows WORKFLOW.md.

## Where everything lives

- **Google Drive root:** `designer clothing` — find it by name in
  Drive.
- **Cross-reference tracker (source of truth for names and links):**
  Google Sheet "Designer Catalog - Product Cross-Reference",
  inside the `designer clothing` Drive folder. Open it by name.
- **Website (ChatGPT Sites):** the site is built in ChatGPT Sites
  from this repo. Keep the Drive structure in sync with the site's
  categories (Jeans, Outerwear, Hoodies, Tracksuits); new folders
  get mirrored on the site.

This repo holds instructions and status only. All links and IDs live
in Google Workspace (Drive folders and Sheets) — find things by name;
never copy an ID or a link into this repo.

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

## Listings — one item, several colors

When the same real product comes in different colors, it is ONE listing
on the website — not one listing per color. The items are different
numbers on the source side (different DHGate option numbers, e.g. 11/100
and 12/100), but they are the same item, so the website shows them as a
single listing and tells them apart by public-facing color (e.g. 11 =
white, 12 = black). Robert may do this again — whenever two items are
the same product in different colors, group them into one listing the
same way.

**Color swatches on the listing itself.** A person looking at the
listings must be able to see that other colors are available WITHOUT
opening the listing. Each listing shows small color circles (swatches) —
one per available color. The circle for the color currently shown is
selected; the other circles are small and unselected. Clicking a circle
changes the color shown right there on the listing — the listing card /
grid tile itself — so the shopper sees that color's photo without having
to click into the listing at all. Example: the listing is showing white,
so the white circle is selected and a small black circle sits next to it
unselected; clicking the black circle swaps the listing's photo to the
black one, still on the listings page.

**The circle must match the garment.** The color of each circle comes
from the garment itself — look at the photo and use AI to read the
overall / dominant color of the hoodie, then fill the circle with that
color so it matches as closely as possible. Do not use a generic color
from the name alone (a "white" hoodie that photographs cream gets a
cream circle, not pure white). Record the swatch color with the item —
in the tracker notes and the catalog notes, next to the public color —
as a hex value when possible, otherwise the closest named color, so the
site builder fills the circle with it.

**The cart must remember the exact variant.** When a shopper adds a
color to the cart, the order must carry that specific color's backend
record — its source label, store, DHGate source link, and numbering —
so Robert knows exactly which one to order. The public color alone is
not enough: black added to the cart must resolve to the black variant's
source (e.g. 12/100 from damai2023), never to the listing's default
variant. Each color variant keeps its own backend record; the cart
passes the selected variant's record through to the order.

**The order translates the public color back into the source color.**
When a customer orders by the public-facing color, the order must show
Robert the source color for that variant — the source label and
numbering — so he orders the exact source item. Example: a customer
orders public Black, and the order gives Robert source Gold 7/100 (the
garment is black; the store calls it Gold).

**The public-facing color is what the AI detects from the garment in
the photo — never the store's color name.** That is how the 7/100
example works: the store calls it Gold, but the garment is black, so
the public color is Black.

**Where to see the examples.** The examples in this section are live
rows in the Sourcing Queue sheet — open it by name ("Designer Catalog
- Sourcing Queue", inside the `designer clothing` Drive folder). Q-001
is the 7/100 item (source Gold, public Black); Q-002 is 11/100 (public
White); Q-003 is 12/100 (public Black). Q-002 and Q-003 are the same
item, one listing. Once an item is done, its record moves to the
tracker sheet ("Designer Catalog - Product Cross-Reference") under its
source label — look there for finished examples.

**The order shows Robert both ends.** When someone orders, the order
must show Robert what the customer saw and ordered — the public-facing
name, public color, and photo — AND what is source-facing — the source
label, store, DHGate source link, and numbering. He gets both sides of
the same order, so he knows what they see and what to order.

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
the Source link column in the tracker sheet is empty until it is). The public-facing name
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
recorded as source links. They belong in the "Photo reference link" column of the tracker
sheet only — never in this repo. The DHGate ordering links are still
missing for those items; the Source link column in the tracker sheet
stays empty until they are provided.

**Per-item record — every product carries all five, when available:**
store name, source link (DHGate ordering link), color identifier,
numbering, and photo reference link. They are separate fields on every item — the store, color
identifier, and numbering in `catalog.json` / `catalog.csv`, and all
five as separate columns in the tracker sheet (where the two links
live), so nothing has to be parsed out of a label:

- **Store name** — e.g. `damai2023` (see above).
- **Source link** — the DHGate listing where the item is bought, when
  there is one. Never a photo reference link. Lives in the tracker
  sheet only — not in this repo.
- **Photo reference link** — where the real photo was found (Grailed,
  Vestiaire, Editorialist, etc.). Provenance for the public-facing
  image only. Never used to order. Lives in the tracker sheet only —
  not in this repo.
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
├── hoodies/
│   ├── Balenciaga/
│   │   ├── casualyn/                         (STORE — DHGate store; DELETED 2026-11-08, folder empty)
│   │   ├── damai2023/                        (STORE — DHGate store)
│   │   │   ├── Green 12/100/
│   │   │   ├── Olive 40/100/
│   │   │   ├── LightPink 41/100/
│   │   │   └── Black 11/100/                 (pending — photos missing)
│   │   ├── xiaobaie/                         (STORE — DHGate store)
│   │   │   ├── Black 11/81/
│   │   │   └── Pink 13/81/
│   │   └── hzqsq901208/                     (STORE — DHGate store; empty — Black 10/29 moved to sweatshirts 2026-11-09)
│   └── Louis Vuitton/
│       └── museround27/                      (STORE; DELETED 2026-11-08, folder empty)
├── sweatshirts/
│   └── Balenciaga/
│       └── hzqsq901208/                     (STORE — DHGate store)
│           └── Black 10/29/                (crewneck — moved from hoodies 2026-11-09)
├── jeans/
│   └── Purple Brand/                         (YUPOO drop — PAUSED, see below)
├── outerwear/
├── tracksuits/
└── sneakers/                                 (not created yet — pending)
```

Folder rules:

- Category first, then brand, then store, then one subfolder per color,
  named by the color label (e.g. `Green 12/100`).
- Sweatshirts go in their own `sweatshirts` folder under the right
  brand; hoodies go in `hoodies`. A crewneck with no hood is a
  sweatshirt, not a hoodie.
- The AI detects the garment type from the photo — hoodie, sweatshirt,
  or long-sleeve t-shirt — and that decides the category on the
  website. A hood means hoodie; a crewneck with no hood is a
  sweatshirt; a lighter long-sleeve without a hood is a long-sleeve
  t-shirt. The category in the sheet is only a starting guess — update
  it if the AI's detection differs.
- File names can be different versions of the file name so they do not
  duplicate each other; the folder name must be the closest match — the
  exact color identifier + numbering label.
- Store comes from Robert's screenshots with each drop — read it
  from the pics (damai2023 was the batch store for the 2026-11-08
  hoodies; newer drops use xiaobaie, hzqsq901208, and whatever store
  the next screenshots show). If no different store is given, it is
  the same store as the previous item.
- Photo files inside a color folder are named
  `<label>-front.jpg`, `<label>-back.jpg` (and `-detail`, `-model-front`,
  etc. when more views exist), where `<label>` is the source label
  lowercased with spaces as hyphens (e.g. `lightpink-41-100-front.jpg`).

## Photo rules

- **Hoodies and sweatshirts (global rule, 2026-11-09):** 3 photos per
  product at least — front, back, and one more angle. Extra angles only
  if they are not redundant or repetitive. If 3 cannot be found, 2 is
  fine; if 2 cannot be found, 1 is fine. Robert's per-item instruction
  overrides (LightPink 41/100: all 6 photos; Black 11/81: first 3).
- **Sneakers:** up to 3 pics per color, from a reverse image search.
  Check the first source found online for other views of the same listing
  first — it usually has them. If only 2 can be found, use 2; if only 1,
  use 1. If a color can't be found online at all, use the cropped DHGate
  photo (crop the top "hot selling" header and the bottom words off).
- **Authentic photos only, in general:** DHGate/seller images are leads,
  not catalog images — find the real, unedited photo showing the full brand
  name (reverse image search first, then the priority sites in order:
  Reversible, Vestiaire Collective, Grailed, Editorialist, Saks Fifth
  Avenue, StockX, then other retailer sites). Always include the brand
  name in the search (e.g. Balenciaga) so the results are only that
  brand's pictures. Exception: when Robert
  explicitly says to save the screenshots he sent (cropped), save those
  as instructed. If the same real photo is already used for another
  store's item, tell Robert — but still save the new source, so the
  image carries two sources. Before searching, check Drive and the
  tracker first — if the photo is already there, keep it and skip the
  reverse image search, but still record the new source.
- Product-only images. Never whole webpages, listing UI, or review text.

## Current items

See `catalog.json` / `catalog.csv` and the tracker sheet for the full data.
Summary (2026-11-09):

| Source label | Store | Real product name | Status |
|---|---|---|---|
| Green 12/100 | damai2023 | Balenciaga Retro Printed Hoodie (Top League multi-logo design) | Done — front + back in Drive |
| Olive 40/100 | damai2023 | TBD — Balenciaga stencil logo hoodie (BALENC AGA) | Done — front + back in Drive; real name still needed |
| LightPink 41/100 | damai2023 | Balenciaga Tape Type Hoodie Oversized, Faded Black | Done — all 6 photos in Drive |
| Black 11/100 | damai2023 | Balenciaga Racing Logo Print Long Sleeve Hoodie | Link found (Reversible) — photos pending |
| Black 11/81 | xiaobaie | Balenciaga Crypto Logo-Print Bleached Cotton-Jersey Hoodie | Done — front, on-model front, detail in Drive |
| Pink 13/81 | xiaobaie | Balenciaga Logo Hoodie (white — black logo, red balenciaga text) — working title, real name TBD | Done — front + detail in Drive; real name still needed |
| Black 10/29 | hzqsq901208 | Balenciaga BB Logo Crewneck Sweatshirt — working title, real name TBD | Done — front photo only in Drive; no back photo; real name still needed |
| casualyn (53 files) | casualyn | 15 Balenciaga designs, real names in REPLACEMENTS log | DELETED 2026-11-08 — all 53 photos trashed (DHGate-sourced, incl. the 15 real replacements; restorable from trash) |
| museround27 (6 files) | museround27 | Louis Vuitton monogram crewneck sweatshirts | DELETED 2026-11-08 — all 6 cropped DHGate screenshots trashed |
| Sneakers (DHGate Track trainers) | TBD | Balenciaga Track trainers | Blocked — DHGate page unreadable (see below) |
| Purple Brand, YUPOO | thomamiri | Purple Brand jeans | PAUSED by Robert — 399 picks selected, not yet downloaded |

Notes:

- The source labels often do NOT describe the garment color (e.g. the
  "Green 12/100" and "Olive 40/100" photos both show a black hoodie).
  Trust the photo and the "Real color" column, not the label word.
- The `casualyn` set's 15 authentic replacements and their sources are
  logged in `authentic/REPLACEMENTS.md` (local working files, not in Drive).

## Pending / blocked items

- **Sneakers (DHGate "designer track tracks mens women trainers" listing — item number in the tracker sheet):** the DHGate page cannot be read — the browser never loads,
  DHGate blocks direct reads, and search has no trace of the listing.
  Store name and colors are unknown. Unblock by opening the link in the
  live browser and handing control back, or by sending screenshots of the
  page (store name + color options).
- **Black 11/100:** link found — Reversible listing (link in the tracker sheet), brand new, size JP 1. Photos still pending: Reversible blocks direct reads (Cloudflare) and the browser could not load the page. Needs the first 2 photos as screenshots, or the link opened in the live browser.
- **Olive 40/100 real name:** not yet identified.
- **Black 10/29 real name:** working title only (Balenciaga BB Logo Crewneck Sweatshirt), not verified against a retailer listing. Front photo only — no back photo was provided.

## How to add a new item

The full agent playbook is in [`WORKFLOW.md`](WORKFLOW.md) — follow
it step by step. Short version:

1. Robert sends a link (or photos) plus a source label like `Color N/100`.
2. Save the photos to Drive under
   `designer clothing/<category>/<brand>/<store>/<label>/`
   following the photo rules above.
3. Add a row to the tracker sheet AND to `catalog.json` / `catalog.csv`
   with the source label, store, real product name, real color, photo
   file names, and price ONLY if the user provided it —
   never take a price from a photo-reference link. (The source link
   and photo reference link go in the tracker sheet only — never in
   the repo files.)
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
