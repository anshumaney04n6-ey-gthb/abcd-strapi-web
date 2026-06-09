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

- fields to add from `sidebarFAQs[]`

---

## 4. `sidebarFAQs[]` Changes

`sidebarFAQs` remains an array.

add the following fields from each `sidebarFAQs[]` item:

| Field | description |
|------|------|
| `isExternal` | (boolean) optional field
| `externalUrl` | (string) if the isExternal is true this is required field. otherwise optional field

### Updated `sidebarFAQs[]` Shape

```text
sidebarFAQs[]
├── faqId (String)
├── title (String)
├── icon (Media)
└── content (Text)
├── isExternal (boolean)
└── externalUrl (string)
```

Important:

- keep `sidebarFAQs` as a repeatable array field
- FAQ items should be content-only entries