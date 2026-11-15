# Designer Depot photo picker and connected workflow

Updated 2026-11-15. Owner-requested process reference for future catalog and storefront agents.

## Sources and locations

| Resource | Location |
| --- | --- |
| Public photo picker (read-only) | https://designer-depot-picker.vercel.app |
| Protected owner Google settings | https://designer-depot-picker.vercel.app/setup.html |
| Source Drive root — designer clothing | https://drive.google.com/drive/folders/1elDDNrJSAvRaQrks5lQX7Zio2IBBGQCW |
| Excluded subtree — Pending Pictures | https://drive.google.com/drive/folders/1K2pKeMjEGkn_eqgaCd46WILnYXnLWpib |
| Backend/frontend implementation | https://github.com/bjparnell1-lang/homegrown/tree/photo-picker-backend/photo-picker |
| Initial connected-backend source commit | https://github.com/bjparnell1-lang/homegrown/commit/67bcf93dc606956ce6cf09988297a6a5c14c75eb |
| Public storefront — separate publication target | https://streetwear-site.vercel.app |
| Earlier browser-only picker — export/migration fallback | https://designer-depot-photo-picker.bj-parnell10000000.chatgpt.site |

The Product Cross-Reference and Sourcing Queue remain Google Sheets inside designer clothing. Find them by name. Product names, real colors, source labels, source ordering links, and photo-reference links keep their existing meanings. Never mistake a photo reference for a supplier ordering source.

## Activation status

The Vercel application and private persistent storage are deployed. Robert approved public browsing on the production URL; shared saving and Google settings remain in the authenticated owner view. The baseline catalog contains 226 product/color entries, 49 with two photo sources, and 1,408 thumbnail previews; 109 supplier-reference images were excluded. This is a dated starting inventory, not a permanent count.

**Google Drive is not connected to the deployed backend yet.** The owner must complete the protected settings page once. Until then, the picker can save its existing selections centrally, but it cannot discover future Drive arrivals. Do not claim unattended Drive sync is active before `/api/connection` reports connected and a successful refresh appears in the picker.

The existing ChatGPT Drive connection does not authorize unattended code on Vercel. The setup page explains enabling the Drive API, creating a dedicated Google service account, sharing only the catalog root with that account as Viewer, and uploading its JSON key through the private page. The server verifies root access and encrypts the key in private storage. Never ask for the key in chat or commit it to GitHub. The service uses read-only Drive scope.

## Automatic discovery and exclusions

After the owner connects Google:

1. The backend scans the allowed root and descendants. It follows folders, not Drive shortcuts. It handles provider pagination before replacing the catalog.
2. **Skip Pending Pictures and its entire subtree**, for all brands/categories, at every nesting depth. The known excluded ID is `1K2pKeMjEGkn_eqgaCd46WILnYXnLWpib`; it stays excluded even if renamed. Any folder named Pending Pictures, case-insensitive, is also skipped. Never traverse it and filter only the direct children afterward.
3. Exclude files beginning with `DO-NOT-USE`, including every `DO-NOT-USE-SUPPLIER-REFERENCE-*` file, even in green source folders.
4. Newly eligible images appear in the picker automatically. New images start unselected. Surviving per-file selections remain; added, removed, or replaced photos return the affected product to Needs review.
5. New photos directly under the root appear in an Unsorted photos group. Agents should still file finished photos into the normal category/brand/source/product hierarchy.
6. Image requests recheck current Drive ancestry once connected, so an image moved into Pending Pictures is not served simply because an older snapshot included it.
7. A failed scan keeps the last successful catalog and existing choices. It must not replace the catalog with an empty or partially fetched result.

**Cadence:** the current Vercel Hobby plan permits a daily background check, configured around 06:00 UTC. While the owner view is visible it checks Drive every two hours. The public view refreshes the saved catalog every two hours without triggering Drive scans. Refresh Drive in the owner view requests a check immediately. This is scheduled discovery, not an instant Google Drive webhook. A 15-minute Vercel background schedule was rejected by Hobby limits; upgrading scheduling is separate from the current setup.

## Selecting and saving

- Two source folders open side by side through Compare both. Each photo can be included independently; combining photos from both sources is supported.
- Each product/color has exactly one display photo, which must also be included. Selecting display automatically includes it.
- Owner choices save centrally in private Vercel Blob storage and are available on other devices through the Owner login link. Public visitors can view and compare photos but cannot change shared selections.
- Saves use revision/ETag concurrency checks. If another session saved first, the picker preserves the local draft and offers retry/merge instead of silently overwriting it.
- Browser backups can be restored explicitly after a save failure or reload. Export/import JSON remains available for backup and for moving choices from the earlier Sites picker. Older Sites browser storage is on a different origin; export from that picker and import into the Vercel picker.
- Mark a product Reviewed when finished. Exported applicable changes include reviewed entries only; unfinished selections remain drafts.
- Legacy green folder colors and `display` comments are context, not a substitute for exact per-file choices. A green folder does not auto-include newly discovered files. Shared legacy folders do not receive contradictory per-product color proposals.

## Publication, privacy, and maintenance

Central saving and discovery do **not** automatically publish photos to the public storefront and do not change Drive comments or folder colors. Those are separate actions requiring the reviewed selection data. Keep source labels, supplier names, ordering links, warehouse and costs out of the public catalog.

The production aliases are **public read-only views**, as approved by Robert. They show photos and existing selections without requiring login. Shared saves, manual Drive refreshes, and Google connection settings remain private.

The required Vercel setting is **`ssoProtection.deploymentType = all_except_custom_domains`** together with the application owner-host guards. This intentionally makes production aliases public while keeping unique deployment URLs behind Vercel Authentication. Never disable SSO entirely. The Owner login link targets the current server-owned unique deployment URL. All mutations and private connection reads require both the request URL hostname and Host to match `VERCEL_URL`. `/setup.html` redirects the public alias to the protected owner URL. Cron uses its independent secret.

Do not use this setting with the older backend that relied entirely on all-URL protection: deploy the owner-host guards first, then change the Vercel setting. Verify that anonymous public page/catalog/image reads succeed, public and spoofed-forwarded-header writes fail, and unique owner URLs still require Vercel login. Restore all-URL protection if any test fails.

Private Blob storage still holds previews, catalog data, decisions and encrypted connection data. Credentials never enter public responses or either GitHub repository. Pending Pictures remains excluded.

Runtime source is under `photo-picker/` on `homegrown`'s `photo-picker-backend` branch; it is separate from the storefront production branch. Deploy that directory to the `designer-depot-picker` Vercel project with `public/` output and its `vercel.json`. This instructions repository stays focused on process and status.

Verification included exclusion/state tests, browser tests for mixed-source selection/mobile comparison/draft recovery, live protected catalog/image reads, and private-storage integration tests. A live Google scan remains unverified until the owner completes Google connection. Any future agent should read current connection/sync status before reporting this flow active.
