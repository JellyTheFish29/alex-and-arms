# Dev Team Implementation Brief

This is the consolidated source of truth for:

- Shop by Room behavior
- Brand page behavior (major vs smaller brands)

## 1) Navigation and Information Architecture

- Keep `Products` and room-based discovery as separate concepts.
- Top navigation should support:
  - `Products` (primary taxonomy path)
  - Room pages (solution/use-case path)

## 2) Shop by Room Requirements

## Current direction

- `Products` remains the primary taxonomy path.
- Room pages are a secondary, solution-oriented discovery path.

## Page intent split

- Product/L2 pages: product-first browsing.
- Room pages: use-case/room-first browsing.
- Reuse the same design system, but with room-page layout and copy emphasizing solutions.

## Phase 1 (current)

- Create room landing pages (example: Bathroom, Kitchen, Outdoor/Parking, Utility, Commercial/Public).
- On room pages, link to existing product/category pages.
- Do not duplicate full product catalogs on room pages.
- Room pages should act as curated hubs with strong internal links to primary taxonomy pages.

## URL guidance (current)

- There is no separate `Shop by Room` index page for now.
- Use direct room landing URLs, e.g.:
  - `/bathroom-solutions`
  - `/kitchen-essentials`
  - `/outdoor-parking`
  - `/utility-solutions`
  - `/commercial-restroom-solutions`
- Keep URLs lowercase and hyphenated.
- Optional future grouping (without hub launch):
  - `/rooms/bathroom-solutions`
  - `/rooms/kitchen-essentials`

## Phase 2 (future)

- Add support for tagging each product/category to one or more rooms.
- Use room tags to drive dynamic curation on room pages.
- Keep canonical SEO ownership on primary product/category pages.

## 3) Brand Page Requirements

Support two brand experiences based on demand and catalog depth.

### Major brands

Flow:

1. Home -> Brands section
2. Click brand
3. Land on dedicated brand page

Dedicated brand page should include:

- Brand intro
- Brand-specific category blocks (from taxonomy)
- Links to category/product listings filtered to that brand

### Smaller brands

Flow:

1. Home -> Brands section
2. Click brand
3. Land on product listing page with brand filter pre-applied

## Backend/admin requirement

Each brand must have a toggle:

- `dedicated_brand_page_enabled` (`true/false`)

Behavior:

- If `true`: route to dedicated brand page.
- If `false`: route to filtered listing page.

## Suggested brand data fields

- `name`
- `slug`
- `is_major_brand` (optional planning helper)
- `dedicated_brand_page_enabled` (required)
- `brand_description` (for dedicated pages)
- `hero_image` (optional)
- `seo_title` (optional)
- `seo_description` (optional)

## Routing guidance

- Dedicated brand page: `/brands/{brand-slug}`
- Fallback listing route: `/products?brand={brand-slug}` (or equivalent)

## SEO guidance

- Dedicated brand pages should be indexable with unique brand-focused content.
- Filter-result fallback pages should avoid thin/duplicate indexing issues.
- Keep Home -> Brands links consistent regardless of page mode.

## Rollout recommendation

- Enable dedicated pages for major brands first.
- Keep smaller brands on filtered listing fallback.
- Expand dedicated brand pages over time based on search demand and catalog depth.

## 4) Practical Summary

- Now:
  - Room pages = curated links to existing categories.
  - Brand behavior = dedicated page for major brands, filtered listing for smaller brands.
- Later:
  - Add room-tagging model for products/categories and expand dynamic curation.

