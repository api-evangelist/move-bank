# MOVE Bank (move-bank)

MOVE Bank is a 100% customer-owned Australian mutual bank operated by MoveBank Ltd (ABN 91 087 651 090, AFSL/Australian credit licence 234 536), headquartered in Brisbane, Queensland. Founded in 1968 as Railways Credit Union to serve railway workers and their families, it rebranded to MOVE Bank in 2018 to serve the broader transport and logistics community nationally. As an authorised deposit-taking institution (ADI), MOVE Bank participates in Australia's Consumer Data Right (CDR / Open Banking) as a data holder, exposing a public Product Reference Data (PRD) API conforming to the Data Standards Body's Consumer Data Standards.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/move-bank/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/move-bank/refs/heads/main/apis.yml)

## Tags

- Financial
- Banks
- Open Banking
- CDR
- Consumer Banking
- Mutual Bank
- Australia
- Product Reference Data

## Timestamps

- **Created:** 2026-07-20
- **Modified:** 2026-07-20

## APIs

### MOVE Bank CDR Product Reference Data API

Public, unauthenticated Consumer Data Right Product Reference Data (PRD) API exposing MOVE Bank's banking product catalogue (home loans, personal loans, transaction and savings accounts, term deposits, and card facilities) under the standard CDS path `/cds-au/v1/banking/products`. Confirmed live (HTTP 200, `x-v: 4`) returning a `data.products` array and CDS-compliant error envelopes. Conforms to the Data Standards Body Consumer Data Standards banking APIs — a shared standard, not a bank-proprietary contract.

- **Human URL:** [https://openbanking.movebank.com.au/OpenBanking](https://openbanking.movebank.com.au/OpenBanking)
- **Base URL:** `https://openbanking.movebank.com.au/OpenBanking`
- **Confirmed endpoint:** `GET https://openbanking.movebank.com.au/OpenBanking/cds-au/v1/banking/products` (x-v: 4)

#### Tags

- CDR
- Open Banking
- Product Reference Data
- Banking
- Australia

#### Properties

- [Documentation](https://openbanking.movebank.com.au/OpenBanking)
- [API Reference](https://www.movebank.com.au/about-us/corporate-information/open-banking/)
- [OpenAPI](openapi/move-bank-cds-banking-products-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [Website](https://www.movebank.com.au/)
- [Developer Portal](https://openbanking.movebank.com.au/OpenBanking)
- [Documentation](https://www.movebank.com.au/about-us/corporate-information/open-banking/)
- [LinkedIn](https://www.linkedin.com/company/movebanksocial)
- [Blog](https://www.movebank.com.au/about-us/news/)
- [Privacy Policy](https://www.movebank.com.au/about-us/corporate-information/privacy-policy-summary/)
- [Terms of Service](https://www.movebank.com.au/about-us/corporate-information/conditions-of-use/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
