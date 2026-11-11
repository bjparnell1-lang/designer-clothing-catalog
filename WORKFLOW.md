# Catalog Workflow — Agent Takeover Playbook

This file is the operating manual for the agent who takes over this
catalog from here. It tells you exactly what Robert sends, what to do
with it, and how to file it — so the work comes out the same way it did
before. The website builder reads `README.md`; this file is for the
agent doing the sourcing and filing. Last updated: 2026-11-09.

Architecture: this repo holds instructions and status only. All links
and IDs live in Google Workspace (Drive folders and Sheets) — never
copy them here. Find every file, folder, and sheet by name.

## Work queue — where your assignments come from

Robert speaks new items to Muse (voice) while away from the app.
Muse logs each one as a row in the **"Designer Catalog - Sourcing
Queue"** sheet — that sheet is your assignment list. Do not wait to be
told in chat; check the sheet.

- **Sheet:** "Designer Catalog - Sourcing Queue", inside the
  `designer clothing` Drive folder. You are integrated with Sheets —
  open it by name; no link needed.
- **Columns A–L:** Queue # | Date added | Store name | Numbering |
  Color identifier | DHGate source link | Category | Brand | Photo
  reference link | Status | Agent result — Drive folder + photo
  files | Notes.
- **How to work it:**
  1. Take the oldest row with Status = "Queued". Change it to
     "In progress" before you start.
  2. Work it exactly per Steps 1–6 below. Store + numbering are
     given. The color identifier is given when Robert knows it — if
     it is blank, derive it from DHGate (Step 1 verification: match
     the numbering, click a size, the color shows) and fill it in.
     The DHGate link is given when known — blank means it is the
     same as the previous item from that store. The photo reference
     link is given when Robert has one.
  3. When it is filed everywhere (Drive photos + tracker row +
     catalog entries), set Status = "Done" and fill in "Agent
     result" with the Drive folder path and the photo file names.
  4. If you are blocked (photo cannot be found, link missing), set
     Status = "Blocked" and say what you need in Notes — do not
     leave it as "Queued".
- The tracker sheet ("Designer Catalog - Product Cross-Reference") is
  the record of FINISHED items. The queue sheet is the record of
  items TO DO. An item moves from the queue to the tracker when it is
  done — it lives in both places, in different states.
- **Examples in this file:** when a rule names a numbering (7/100,
  11/100, 12/100), it means these queue rows — Q-001 (7/100,
  damai2023, source Gold, public Black), Q-002 (11/100, public
  White), Q-003 (12/100, public Black). Q-002 and Q-003 are the same
  item, one website listing. Once an item is done, its record is in
  the tracker sheet under its source label.
- If you cannot read or write this sheet, say so plainly and work
  from the rows Robert pastes to you instead; do not claim a status
  you did not set.

## What Robert sends (a "drop")

Robert drops items in the "D H Gate" chat, usually as screenshots plus
links. A normal drop has:

1. **Screenshots of the DHGate listing** — the product page, the color
   grid, sometimes the store/reviews page.
2. **A DHGate share link** — this is the **ordering source**. It
   resolves to a DHGate item page. Record the share link as the
   item's `source_link` in the tracker sheet (it lives there, not
   in this repo).
3. **A photo link** (Reversible, Grailed, Editorialist, Saks, StockX…)
   — this is **only** where the real photo lives. It is NOT a source
   and must NEVER be used to order. It also supplies the public-facing
   product name/description.
4. **Sometimes the real photo itself**, sent as an attachment, with a
   note like "Fourth is real pic to be used". Use it directly — no
   reverse search needed — after verifying the brand name is spelled
   out in full.

**If he gives no different DHGate link, it is the SAME DHGate link and
store as the previous item.** Do not ask — carry it forward.

**Screenshot numbering rule:** sometimes the photo comes from a
screenshot, not a link. Then he gives a number = the attachment's
position in the order he attached them (left to right as he sees them).
You receive them in the same left-to-right order. Example: "the photos
I want you to use is 3 and 4" means the 3rd and 4th attachments.

**Photo count per item (global rule, set 2026-11-09): 3 photos per
product at least** — front, back, and one more angle. If a source has
different angles of the garment, include them only if they are not
redundant or repetitive. If you cannot get 3 photos, 2 is fine. If you
cannot get 2, 1 is fine. His per-item instruction overrides this
("use all photos" for LightPink 41/100, "use the first 3 photos" for
Black 11/81).

## Step 1 — Read the drop: store, color, numbering

Read these **from the screenshots**. He will not tell you — you read
them from the pics.

- **Store name** — the DHGate store shown on the store/reviews page
  (e.g. `hzqsq901208`, `damai2023`, `xiaobaie`). The folder directly
  under each brand folder IS the store name.
- **Color identifier** — the color word (e.g. `Black`, `LightPink`).
  The store's color word often does NOT describe the garment (the
  "Green 12/100" garment is black). File under his label exactly as
  given, flag the mismatch, never rename.
- **Numbering** — the item's position within the store's listing,
  written `N/total` (e.g. `10/29` = option 10 of 29, `41/100` =
  item 41 of 100). The source label is color identifier + numbering:
  `LightPink 41/100` = `LightPink` + `41/100`.
- **Store quirks (confirmed):**
  - `hzqsq901208`: the DHGate color names lag the option position by
    2 — "Colour 8" is option 10 of 29. Numbering uses the POSITION,
    so this item is `Black 10/29`. For future items from this store:
    numbering = option position, DHGate color name = position minus 2.
  - `damai2023`: labels are his batch sequence; garment color
    frequently mismatches the label word.
  - `xiaobaie`: 81 options (`/81`); its DHGate share link is in the
    tracker sheet.

If the numbering is ambiguous (e.g. the color name and the position
disagree), pick the position, file it, and **flag the discrepancy to
Robert in your reply** so he can correct you. When he confirms, record
the reason (like the 2-place lag above) in the tracker notes, the
catalog notes, and this file, so it sticks.

### Verify the product on DHGate before you search for the photo

Use the DHGate link (from the queue row or the tracker sheet) to open
the store and find the product. Do this for every item — it is how you
know you have the right one:

1. Use the numbering for the product you are working on (e.g. `10/29`)
   and compare it with the numbering shown at the bottom of the picture
   on DHGate (the option thumbnails show the number). Find the one
   where the numbering matches.
2. When the numbering matches, click on the product — the color should
   show. If the color does not show, select a size, and the color
   should come up then.
3. If that color matches the color you are working on, you can be sure
   it is the correct product and the correct picture. That is the
   confirmation — do not skip it.
   **If the color identifier was not given** (queue row blank — Robert
   only gave store + numbering to go fast), this is also how you find
   it: the color that shows after you click a size IS the color
   identifier. Record it in the tracker and the catalog.
4. If the numbering and the color do not line up, stop and flag it to
   Robert — do not guess.

## Step 2 — Get the real photo (reverse image search first)

**DHGate alters branding** — a letter or number changed, the name
blocked or truncated (e.g. "balen" instead of "Balenciaga"). DHGate
images and screenshots are **leads only. Never save a DHGate image as
the catalog photo.** This rule was corrected firmly on 2026-11-08
after 53 DHGate images were saved by mistake and had to be deleted
(the whole `casualyn` folder and the `museround27` folder were trashed
the same day — do not re-add DHGate photos there or anywhere).

**Check Drive and the tracker first.** Before any reverse image
search, check whether the same item / photo is already in Drive or in
the tracker list. If it is, keep the photo that is already there — no
reverse image search needed. Still record the new source (store +
DHGate source link) for the new item, so Robert has the option of
which source to order from. The photo then has two sources.

Order of search for the real, unedited photo:

1. **Reverse image search first** — the highest priority. If it finds
   a site with the actual image, use that. **Always include the brand
   name in the search** (e.g. Balenciaga) so the results are only that
   brand's pictures — a reverse image search without the brand pulls in
   unrelated lookalikes.
2. Then the priority sites in order — Reversible, Vestiaire Collective,
   Grailed, Editorialist, Saks Fifth Avenue, StockX — then Kering DAM,
   MR PORTER, eBay, Mercari, and other listing/retailer sites.
3. The photo link Robert posted, if he posted one.

The real photo must show the **full brand name, unedited** — never a
version with the name blocked out or edited out, and never a version
where a letter has been changed or the brand made to look different
(e.g. "balen" instead of "Balenciaga"). Search for that same exact
design until you find the real, unedited version — front and back.
Product-only images: never whole webpages, listing UI, review text, or
add-to-cart elements. Include the **back view** when the listing shows
one (t-shirts, hoodies); skip it when it doesn't make sense (socks).
If Robert sent the real photo himself, use it as-is after a visual
check.

**Duplicate photo — same image, two sources.** If the search turns
up the SAME real photo already used for another item from a different
store, tell Robert you already have an image for it — but still save
the source for the new one. Do not save a second copy of the photo;
reuse the existing file. The image then has TWO sources: record both
— the first item's store + source link, and the new item's store +
source link — in the tracker notes and catalog notes for both items,
so either order resolves to the right source.

### Photo sources — priority order (set by Robert, 2026-11-09)

When a search surfaces several of these sites, use them in this order.
If one of these sites comes up, prioritize it over other sites.

1. Reversible (reversible.com)
2. Vestiaire Collective (vestiairecollective.com)
3. Grailed (grailed.com)
4. Editorialist (editorialist.com)
5. Saks Fifth Avenue (saksfifthavenue.com)
6. StockX (stockx.com)

Still usable, below the priority list: Kering DAM — Balenciaga official
photo library (balenciaga.dam.kering.com); MR PORTER (mrporter.com) —
photos came through Reversible listings whose details are "provided by
MR PORTER", not directly.

Also seen in search results but not used for a photo yet: Farfetch,
Bergdorf Goodman, Cettire, Lyst. eBay and Mercari were in the original
search order but have not been used for this catalog.

**Verify every photo visually before filing it** — open it and look:
front/back as labeled, full branding, no UI, no gallery badges
(crop a badge off if one is baked into a screenshot he sent, the way
the `6/10` badge was cropped off Pink 13/81's detail shot).

### Verified photo-source methods

- **Grailed:** `https://www.grailed.com/api/listings/<id>` returns the
  full listing JSON, including the `photos` array in carousel order
  with direct `media-assets.grailed.com` URLs (1440×1440). Download
  with `Referer: https://www.grailed.com/`.
- **Editorialist:** the page HTML blocks direct reads, but the
  thumbnail CDN works:
  `https://editorialist.com/thumbnails/600/<path>~<color>_<ts>_<n>.webp`
  (indices from 0 upward in carousel order; 403 means no more photos;
  only the 600px size works). Files arrive gzip-compressed — decompress
  before use. Convert webp to JPEG for Drive.
- **Vestiaire Collective:** image pattern
  `https://images.vestiairecollective.com/images/resized/w=1024,q=75,f=auto,/produit/<slug>-<id>-<n>_2.jpg`
  (n = 1..N in carousel order; files arrive as webp — convert to JPEG).
- **MR PORTER** (Reversible listings whose details are "provided by MR
  PORTER" use this set): variant pattern
  `https://www.mrporter.com/variants/images/<product_id>/<variant>/w2000_q60.jpg`
  — variants `in` (front flat), `ou` (on-model front), `cu` (close-up)
  are the ones that exist.
- **Saks Fifth Avenue:** `https://cdn.saksfifthavenue.com/is/image/saks/<productID>_<COLOR>?wid=1200&hei=1600&qlt=90&resMode=sharp2&op_usm=0.9%2C1.0%2C8%2C0`
  — a 404 returns a small placeholder JPEG; real photos are much larger.
- **StockX:** `https://images.stockx.com/images/<Product-Name-Slug>.jpg?fit=fill&bg=FFFFFF&w=1200&h=800&q=80&dpr=1&trim=color`
  (wrong slugs 404).
- **Kering DAM (Balenciaga official):**
  `https://balenciaga.dam.kering.com/asset/<uuid>/Medium/<style>_F.jpg?v=3`.

### When the photo cannot be found

- **Reversible** blocks direct reads (Cloudflare challenge) and the
  live browser frequently never loads — ask Robert for screenshots of
  the photos, or for him to open the link in the live browser and hand
  control back. Record the link/title in the catalog with status
  "link found - photos pending" and move on; do not invent a photo.
- **DHGate pages** block direct reads (403) and are blocked for plain
  page fetches. The share link's redirect target (the item URL) can
  usually still be resolved from the redirect headers — that gives you
  the item ID. Screenshots from Robert are the reliable unblock path.
- Never claim a photo exists until it is verified in the Drive folder.

## Step 3 — Get the real product name and real color

From the photo's source listing (the photo reference link), take the
**real product name** (the retailer's title) and the **real color**
(what the garment actually is). The real color is what the AI detects
from the garment in the photo — never the store's color name (the store
called 7/100 "Gold"; the garment is black, so the public color is
Black). If no retailer listing can be found,
use a working title (e.g. "Balenciaga BB Logo Crewneck Sweatshirt —
working title, real name TBD") and mark the status accordingly — never
invent a real name.

**Prices: never take a price from a photo-reference link.** The price
on those pages is irrelevant and must not be recorded. Prices go in
ONLY when Robert provides them himself — he will tell you later. The
DHGate ordering cost (e.g. $20.50, $62.12) may be noted in the notes
field; it is an ordering cost, not a retail price.

**Same item, different colors = one website listing.** When two items
are the same real product in different colors (different source
numberings, e.g. 11/100 and 12/100), they are ONE listing on the
website, told apart by public-facing color — not two listings. Record
each item's public color (Robert gives it, e.g. 11 = white, 12 = black)
in the tracker / catalog notes. The website shows small color circles
on the listing itself (see README.md "Listings — one item, several
colors"): the shopper sees the other colors without opening the listing,
and clicking a circle swaps the color shown on the listing card. Robert
may group items this way again — apply the same rule whenever he says
two items are the same product in different colors.

**The cart must remember the exact variant.** When a shopper adds a
color to the cart, the order must carry that color's backend record —
source label, store, DHGate source link, and numbering — so Robert
knows exactly which one to order. The public color alone is not enough.
Each color variant keeps its own backend record in the tracker and the
catalog; the site builder must pass the selected variant's record
through to the order, never the listing's default variant.

**The swatch circle must match the garment.** For each color variant,
look at the photo and use AI vision to read the garment's overall /
dominant color, then record it as the item's swatch color (a hex value
when possible, otherwise the closest named color) in the tracker notes
and the catalog notes, next to the public color. The circle on the
listing is filled with that swatch color — never a generic color from
the name alone. A hoodie that photographs cream gets a cream circle,
not pure white.

## Step 4 — File it in Drive

Structure: `designer clothing` → `<category>` → `<brand>` →
`<store>` → `<color label>` (one subfolder per color, named by the
label, e.g. `Black 10/29` — Drive accepts `/` in the name).

- **Drive root:** `designer clothing` — find it by name in Drive.
  (Folder IDs are not kept in this repo; open folders by name.)
- Category folders: hoodies, sweatshirts, tracksuits, outerwear, jeans.
  **Sweatshirts go in their own `sweatshirts` folder under the right
  brand; hoodies go in `hoodies`.** A crewneck with no hood is a
  sweatshirt, not a hoodie. Under the category folder the structure is
  the same: brand → store → products (one subfolder per color label).
- **The AI detects the garment type from the photo** — hoodie,
  sweatshirt, or long-sleeve t-shirt — and that decides the category.
  A hood means hoodie; a crewneck with no hood is a sweatshirt; a
  lighter, thinner long-sleeve without a hood is a long-sleeve
  t-shirt. The category in the queue or tracker is only a starting
  guess — if the AI's detection differs, file it under the detected
  category and update the sheet.
- Brand folders: Balenciaga under hoodies and under sweatshirts; Louis
  Vuitton under hoodies; Purple Brand under jeans.
- Store folders (under Balenciaga unless noted): damai2023,
  xiaobaie, hzqsq901208; museround27 under Louis Vuitton (empty —
  photos deleted, see below). `hzqsq901208` also has a folder under
  `sweatshirts > Balenciaga` (Black 10/29, moved 2026-11-09 — it is a
  crewneck sweatshirt). Create a store folder when a new store
  appears.
- Photo files inside a color folder are named
  `<label>-front.jpg`, `<label>-back.jpg` (plus `-detail`,
  `-model.jpg`, etc. when more views exist), where `<label>` is the
  source label lowercased with spaces as hyphens
  (e.g. `black-10-29-front.jpg`).
- **File names (global rule, set 2026-11-09):** the actual file names
  can be different versions of the file name so they do not duplicate
  each other (different suffixes — `-front`, `-back`, `-detail`,
  `-model-front` — are versions of the same file name). But the
  **folder must have the closest match** — the folder name is the exact
  color identifier + numbering label (e.g. `Black 10/29`), never a
  paraphrase.
- **Verify after uploading:** list the folder and confirm the files
  are there with the right names. Never report an item as filed until
  the Drive listing confirms it.
- Standing permission: uploads, renames, moves, and organizing within
  folders proceed without asking. **Confirm before permanent
  deletion** — prefer reversible trash.

## Step 5 — Update the tracker sheet (same time as Drive)

Google Sheet **"Designer Catalog - Product Cross-Reference"**,
inside the `designer clothing` Drive folder. Open it by name — you
are integrated with Sheets.

Columns A–N: Source label | Store | Category | Real product name
(for website) | Real color | **Source link (DHGate — order from
here)** | Photo files in Drive | Retail price (leave blank unless
Robert gave it) | Date added | Notes | Source color name | Color
identifier | Numbering | **Photo reference link (NOT a source —
never order from here)**.

- **Every new item gets a row at the same time its photos go to
  Drive.** Append after the last row.
- **The tracker is ONLY for updating after the reverse image search
  finds the pictures that will actually be used.** Do not put an item
  in the tracker while it is still to do — until its photos are found
  and filed, it lives ONLY in the queue. Write the row only after the
  AI color identification in Step 3 — the Real color column takes the
  AI-identified actual color of the garment, not the source color
  identifier.
- **Fill every gap when you update the tracker.** When you write or
  update a row, check the whole row for missing links and missing
  data. If the source link (column F) or the photo reference link
  (column N) is missing, get it there — from the queue row, the drop,
  or the source where you found the photo. If any other data is
  missing (real name, real color, photo files), get that there too.
  If you cannot find it, say so in Notes and flag it to Robert — do
  not leave a blank silently.
- **Rows 8–21 are 14 legacy placeholder rows** ("Not recorded (legacy
  site ID lv-7090…)") that predate this work. Do not delete them
  without Robert's say-so — new appends land after them.
- **Always read the sheet back to verify** the row landed correctly.
  A successful write proves the API accepted the request, not that the
  sheet reads correctly.
- If a **new store** appears, also add a row to the **"Designer
  Clothing Source List"** sheet (in the `designer clothing` folder,
  open it by name):
  Source name | Link | Use (Photo reference / Ordering / Both) |
  Type | Brands — best for | Clothing types — best for | Status
  (Confirmed / Potential) | Notes | Date added.

## Step 6 — Update this repo and commit

Update all three files, then commit them together:

- **`catalog.json`** — one object per item. Fields: `source_label`,
  `source_color_name`, `color_identifier`, `numbering`, `store`,
  `category`, `brand`, `public_name`, `public_color`, `drive_folder`
  (path by folder names), `photo_files` (array), `retail_price_usd`
  (null unless Robert gave it), `date_added`, `status`, `notes`,
  `source_type`. The two links (`source_link`, the DHGate ordering
  link, and `photo_reference_link`, where the real photo was found)
  live ONLY in the tracker sheet — never in this repo. The `meta` and `naming_rules` sections at the end
  are the standing rules — keep them current if a rule changes.
- **`catalog.csv`** — same items, flat, same column order as the
  header row. Keep it in sync with `catalog.json`.
- **`README.md`** — add a row to the "Current items" table and, if
  anything is still pending on the item (name TBD, photos pending),
  a bullet under "Pending / blocked items".
- Commit with a clear message naming the item, e.g.
  "Add Black 10/29 hzqsq901208 BB logo crewneck sweatshirt (real
  photo supplied by Robert)".
- **Verify by reading the file back from the repo** after the commit.

## The rules, in one place (do not break these)

1. **Authentic photos only.** DHGate/seller images are leads, never
   the saved image. Reverse image search first, then the priority
   sites in order (Reversible, Vestiaire Collective, Grailed,
   Editorialist, Saks Fifth Avenue, StockX), then other retailer /
   listing sites. The real image does not have to come from the
   brand's own website — but the full brand name must be visible and
   unedited.
2. **Two names, never mixed.** Source label (folder/file names) is
   for ordering; real product name is what customers see. The
   public-facing name must match the photo.
3. **Two links, never mixed.** Source link = DHGate ordering link
   ONLY. Photo reference link = where the real photo was found ONLY.
   The photo reference link is never part of an order. Both links
   live in the tracker sheet — never in this repo.
4. **Per-item record.** Every product carries store name, source
   link, color identifier, numbering, and photo reference link as
   separate fields in the tracker sheet — nothing parsed out of a
   label at order time. This repo carries the store, color
   identifier, and numbering; the two links stay in the tracker.
5. **Prices only from Robert.** Never from a photo-reference link.
6. **File it everywhere at once.** Drive photos + tracker row +
   catalog.json/csv + README, in the same pass. Verify each one by
   reading it back.
7. **If a store is TBD, the order cannot be placed.** Say so plainly.
8. **When Robert corrects you, record the reason** — in the tracker
   notes, the catalog notes, and this file — so the correction never
   has to be made twice. (Example: the hzqsq901208 2-place lag.)
9. **Photo count (global rule, 2026-11-09).** 3 photos per product at
   least; extra angles only if they are not redundant or repetitive;
   2 if 3 is not possible, 1 if 2 is not possible. Robert's per-item
   instruction overrides.
10. **File names may vary; the folder must match (global rule,
    2026-11-09).** File names can be different versions of the file
    name so they do not duplicate; the folder name must be the closest
    match — the exact color identifier + numbering label.
11. **Public color comes from AI, not the source label (2026-11-10).**
    Use AI to identify the actual color of the garment from the photo
    — that is the public-facing color in the tracker and on the
    website. The source color identifier stays in its own column;
    never use it as the public color. Robert's word for the public
    color wins over the AI reading; a disagreement gets flagged.
12. **No blank left silently (2026-11-10).** When you update the
    tracker, fill every missing link and every missing piece of data
    you can find; flag what you cannot find in Notes.
11. **Same item, different colors = one listing (2026-11-09).**
    Group them; tell them apart by public-facing color. The listing
    shows color circles on the card itself — clicking a circle swaps
    the shown color without opening the listing.
12. **Swatch circles match the garment (2026-11-09).** Read the
    garment's overall / dominant color from the photo with AI vision;
    the circle is filled with that color, as closely as possible —
    never a generic color from the name alone. Record the swatch color
    (hex when possible) in the tracker and catalog notes, next to the
    public color.
13. **The cart carries the variant's backend record (2026-11-09).**
    When a color is added to the cart, the order carries that
    variant's source label, store, source link, and numbering — so
    Robert knows exactly which one to order. Never substitute the
    listing's default variant. The order must also translate the
    public-facing color back into the source color: a customer orders
    public Black, the order gives Robert source Gold 7/100 (the
    garment is black; the store calls it Gold). And the order shows
    Robert both ends: what the customer saw and ordered (public name,
    public color, photo) AND what is source-facing (source label,
    store, source link, numbering) — so he knows what they see and
    what to order.
14. **The AI detects the garment type (2026-11-09).** The AI looks at
    the photo and detects whether the garment is a hoodie, a
    sweatshirt, or a long-sleeve t-shirt — and that decides the
    category on the website, so it is categorized correctly. A hood
    means hoodie; a crewneck with no hood is a sweatshirt; a lighter,
    thinner long-sleeve without a hood is a long-sleeve t-shirt. The
    category in the queue or tracker is only a starting guess — if the
    AI's detection differs, file it under the detected category and
    update the sheet.
15. **Duplicate photo, two sources (2026-11-09).** If the same real
    photo is already used for another store's item, tell Robert you
    already have an image for it — but still save the new source.
    Reuse the existing photo file (no second copy); record BOTH
    sources in the tracker and catalog notes for both items, so the
    image carries two sources and either order resolves to the right
    one. Check Drive and the tracker first, before any reverse image
    search: if the photo is already there, keep it and skip the
    search — but still record the new source, so Robert has the
    option of which source to order from.

## Current state (2026-11-08)

- 11 items in `catalog.json` (8 real/done or in-progress, 2 deleted
  sets, 1 paused YUPOO drop, 1 blocked sneakers item).
- Latest filed item: Black 10/29, hzqsq901208 (tracker row 24) —
  **moved to the new `sweatshirts` category 2026-11-09** (crewneck,
  no hood).
- **Sweatshirts is a new Drive category (2026-11-09).** The website
  nav does not have a Sweatshirts category yet — flag to Robert / the
  site builder when it matters.
- **Links per item: confirmed 2026-11-09** — as long as every item has
  its links in the tracker sheet (columns F and N), the repo stays
  link-free. No change.
- **Photo-source priority: set 2026-11-09** — Reversible >
  Vestiaire Collective > Grailed > Editorialist > Saks Fifth Avenue >
  StockX. If one of these sites comes up, prioritize it over other
  sites (see Step 2).
- Source list: 14 entries.
- Work queue: "Designer Catalog - Sourcing Queue" sheet, created
  2026-11-08 — Robert adds rows by voice; the agent works the oldest
  "Queued" row first (see "Work queue" above).
- **Pending:** Black 11/100 (damai2023) — Reversible link found
  (link in the tracker sheet), first 2 photos still needed; Sneakers
  (DHGate Track trainers listing — item number in the tracker sheet)
  — page unreadable, store name + colors unknown, needs screenshots
  or live-browser takeover; Purple Brand YUPOO drop — PAUSED by Robert,
  399 picks selected, do not resume without a new direction; Olive
  40/100 and Pink 13/81 and Black 10/29 real names still TBD
  (working titles in use); DHGate ordering links still missing for
  the four damai2023 items (Green 12/100, Olive 40/100, LightPink
  41/100, Black 11/100).
- **Deleted, do not restore without asking:** all 53 `casualyn`
  files and all 6 `museround27` files were trashed 2026-11-08
  (DHGate-sourced). The 15 authentic casualyn replacements are in
  the trash and restorable if Robert asks; the replacement log is in
  the local working files (`authentic/REPLACEMENTS.md`).

## If your Drive / Sheets access ever breaks

You are integrated with Google Sheets and Drive — open sheets and
folders by name. If that access ever breaks, say so plainly, do
everything above that you can (source the real photos, work out the
store / label / numbering / color identifier / real name), and prepare
the photo files plus the exact tracker row and catalog entries. Then
hand Robert the ready-to-append row and the files — do not claim
anything is in Drive or the tracker until it is verified there.
