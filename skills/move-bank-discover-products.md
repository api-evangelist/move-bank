---
name: Discover MOVE Bank banking products
description: >
  Browse and inspect MOVE Bank's publicly available banking products (accounts,
  loans, term deposits, cards) via its unauthenticated Consumer Data Right (CDR)
  Product Reference Data API. No credentials required.
api: openapi/move-bank-cds-banking-products-openapi.yml
operations: [listBankingProducts, getBankingProductDetail]
method: generated
generated: '2026-07-20'
---

# Discover MOVE Bank banking products

MOVE Bank exposes a public, unauthenticated CDR Product Reference Data (PRD) API.
You can list and inspect every published product with no API key, token, or
consent — this is a data-holder obligation under Australia's Consumer Data Right.

**Base URL:** `https://openbanking.movebank.com.au/OpenBanking/cds-au/v1`
**Required header on every request:** `x-v: 4` (Get Products currently supports
only version 4; other values return HTTP 406 `Header/UnsupportedVersion`).

## Step 1 — List products (`listBankingProducts`)

`GET /banking/products` with header `x-v: 4`.

Optional query params:
- `product-category` — filter to one category (e.g. `TRANS_AND_SAVINGS_ACCOUNTS`, `TERM_DEPOSITS`, `RESIDENTIAL_MORTGAGES`, `PERS_LOANS`).
- `effective` — `CURRENT` (default), `FUTURE`, or `ALL`.
- `updated-since` — DateTimeString to return only products changed since then.
- `page`, `page-size` — 1-based paging (default page-size 25, max 1000).

The response is a `data.products[]` array plus `links` (self/first/prev/next/last)
and `meta` (`totalRecords`, `totalPages`). Each product carries a `productId`,
`name`, `description`, `productCategory`, and `brand`.

## Step 2 — Get product detail (`getBankingProductDetail`)

For any `productId` from Step 1: `GET /banking/products/{productId}` with header
`x-v: 4`. Returns the full `data` object including `fees[]`, `depositRates[]`,
`lendingRates[]` (with `tiers[]`), `features[]`, `constraints[]`, `eligibility[]`,
and `additionalInformation`. A missing/invalid id returns HTTP 404
`Resource/NotFound` or `Resource/Invalid`.

## Rules

- Always send `x-v: 4`. Omitting the version header returns 400 `Header/Missing`.
- Paginate to completion using `meta.totalPages`; an out-of-range `page` returns 422 `Field/InvalidPage`.
- The API is read-only — there is no idempotency key and no write surface here.
- Errors follow the CDS `ResponseErrorListV2` envelope (`errors[].code` is a
  `urn:au-cds:...` code), NOT RFC 9457 problem+json. See
  `errors/move-bank-problem-types.yml`.
- Account, balance, transaction, direct-debit, scheduled-payment and payee data
  is NOT on this public surface — it requires ACCC accreditation and consumer
  consent under the CDR Security Profile. See
  `authentication/move-bank-authentication.yml`.
