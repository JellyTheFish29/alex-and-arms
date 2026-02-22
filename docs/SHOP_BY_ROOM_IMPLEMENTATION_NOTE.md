# Shop by Room - Implementation Note (For Dev Team)

## Current direction

- Keep `Products` and `Shop by Room` as separate top-nav items.
- `Products` remains the primary taxonomy path.
- `Shop by Room` is a secondary, solution-oriented discovery path.

## Page intent split

- Product/L2 pages: product-first browsing.
- Shop by Room pages: use-case/room-first browsing.
- Reuse the same design system, but with room-page layout and copy emphasizing solutions.

## Immediate implementation (Phase 1)

- Create room landing pages (example: Bathroom, Kitchen, Outdoor/Parking, Utility, Commercial/Public).
- On these room pages, link to existing product/category pages.
- Do not duplicate product catalogs on room pages.
- Room pages should act as curated hubs with clear internal links to existing taxonomy pages.

## URL structure guidance

- There is no separate `Shop by Room` index page for now.
- Use direct room landing URLs, for example:
  - `/bathroom-solutions`
  - `/kitchen-essentials`
  - `/outdoor-parking`
  - `/utility-solutions`
  - `/commercial-restroom-solutions`
- Keep URLs lowercase and hyphenated.
- If grouping is needed later without launching a hub page, use path-based grouping:
  - `/rooms/bathroom-solutions`
  - `/rooms/kitchen-essentials`
  - etc.

## Future implementation (Phase 2)

- Add data support so each product/category can be tagged to one or more rooms.
- Use these room tags to drive dynamic curation on Shop by Room pages.
- Keep canonical SEO ownership on primary product/category pages, while room pages remain curated entry points.

## Summary

For now: curated room pages linking to existing categories.  
Later: full room-tagging model for products/categories.
