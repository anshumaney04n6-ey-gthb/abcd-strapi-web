# CMS_TRACKS Strapi Schema Changes

**Date:** 2026-04-23
**Purpose:** Short reference for the Strapi team based on the CMS_TRACKS dashboard requirement. This document only captures the schema fields to remove and the revised API shape to expect.

---

## 1. API Reference

**Content Type:** `tracks-dashboard-pages`

**API Endpoint:**

```http
GET /api/tracks-dashboard-pages?filters[subProduct][$eq]=credit&filters[partner][$eq]=default&populate=*
```

Use this endpoint for the Credit dashboard CMS entry.

---

## 2. Scope Of This Note

This is a delta document for CMS_TRACKS only.

It does not restate the full dashboard schema. It only lists:

- top-level fields to remove from Strapi
- fields to remove from `sidebarFAQs[]`
- the reduced API contract expected after cleanup

---

## 3. Top-Level Fields To Remove From Strapi

Remove the following fields from the `tracks-dashboard-pages` schema:

| Field |
|------|
| `sectionTitleComparison` |
| `sectionSubtitleVideos` |
| `livePriceDisclaimer` |
| `sectionTitleReferral` |
| `heroImagePath` |
| `patternImagePath` |
| `maskImagePath` |
| `transactionsEmptyImagePath` |
| `mmtcLogoPath` |
| `footerBarsImagePath` |

Important:

- these fields should not exist in the schema going forward
- these fields should not be added to new CMS entries
- these fields should not be expected in the API response

---

## 4. `sidebarFAQs[]` Changes

`sidebarFAQs` remains an array.

Remove the following fields from each `sidebarFAQs[]` item:

| Field |
|------|
| `isExternal` |
| `externalUrl` |

### Updated `sidebarFAQs[]` Shape

```text
sidebarFAQs[]
├── faqId (String)
├── title (String)
├── icon (Media)
└── content (Text)
```

Important:

- keep `sidebarFAQs` as a repeatable array field
- FAQ items should be content-only entries
- external navigation should not be configured from Strapi for this sectio