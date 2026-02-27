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

## 5) Product Page Metadata at Scale

Context:
- Hundreds of product-specific pages are expected from the product catalog/listing.
- Metadata should be generated from a consistent template system, not written manually per SKU.

Implementation direction:
- Keep category/room pages as primary SEO targets.
- Product pages should still have unique, structured metadata for discoverability and CTR.
- Use deterministic templates with fallback rules to avoid empty or duplicated tags.

Suggested metadata templates:
- Title: `{Product Name} | {Category} in Chennai | Alex & Arms Ceramica`
- Meta description: `Explore {Product Name} in {Category}. Visit Alex & Arms Ceramica, Chennai for styles, sizes, and pricing support.`
- H1: `{Product Name}`
- URL: `/products/{category-slug}/{product-slug}`

Fallback rules:
- If `product_name` is missing, fallback to `{Brand} {Category}`.
- If `brand` is missing, do not force brand in title/description.
- Enforce length guardrails:
  - Title target: 50-60 characters
  - Meta description target: 140-160 characters
- Prevent duplicates by appending differentiators when needed:
  - size / finish / variant token (only if required)

Suggested product data fields:
- `product_name`
- `brand`
- `category_l1`
- `category_l2`
- `room_tags` (future-ready for room curation)
- `material_or_finish`
- `size_or_variant`
- `slug`
- `primary_keyword` (optional per product if available)
- `secondary_keywords` (optional)
- `meta_title`
- `meta_description`
- `h1`
- `canonical_url`

Note:
- Team may already have parts of this implemented. If so, treat this as alignment with SEO/content requirements for consistency and scale.
