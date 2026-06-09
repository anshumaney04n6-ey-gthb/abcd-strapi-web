# Explore `bankCode` Schema Addendum

## What Needs To Be Added

`bankCode` is a new field inside each item of the `fdMasterTable` repeatable component (and optionally the `cards` array) within the `explore` component.

This field maps each explore card to its corresponding entry in the `investments-bank-details` collection, enabling **exact bank-code lookup** when resolving FD/RD deep links from the sidebar.

| Property | Value |
|----------|-------|
| Component | `investments-dashboard.fd-master-table-item` (repeatable inside `explore`) |
| Field name | `bankCode` |
| Field type | `String` |
| Required | No |
| Default | `""` |
| Purpose | Maps the explore card to a bank entry in `investments-bank-details` (e.g. `UTKSIN`, `SMCBIN`) |

---

## Where It Lives

```
investments_dashboard_pages
  └── explore                                ← investments-dashboard.explore (component)
        ├── heading
        ├── filters
        ├── filterInfoBanners[]
        ├── fdMasterTable[]                  ← fd-master-table-item (repeatable sub-component)
        │     ├── id
        │     ├── bankCode                   ← NEW FIELD
        │     ├── bankName
        │     ├── logo
        │     ├── isBank
        │     ├── isNBFC
        │     ├── isTaxSaver
        │     ├── highlightBadge
        │     ├── subBadge
        │     ├── features
        │     ├── interestRate
        │     └── cta
        ├── cards[]
        │     ├── id
        │     ├── bankCode                   ← NEW FIELD (optional, mirrored from fdMasterTable)
        │     ├── bankName
        │     └── ...
        └── carousel
```

---

## Why This Field Is Needed

When a user clicks "Book FD" on an explore card, the sidebar opens and the "Open FD" / "Open RD" buttons resolve a deep-link URL via `resolveFdDeepLink` / `resolveRdDeepLink`.

**Without `bankCode`:** The resolution falls back to fuzzy name matching (`providerName` vs `bankName` / `providerAlias`), which can match the **wrong bank** if multiple entries share similar aliases.

**With `bankCode`:** The resolution uses **exact key lookup** (`bankMapping[bankCode]`), which is deterministic and always resolves to the correct bank's deep link.

---

## Strapi Schema Update

Add this field to the `fd-master-table-item` sub-component (and optionally to `explore-card-item`):

```json
{
  "bankCode": {
    "type": "string"
  }
}
```

---

## Strapi Admin

1. Open **Content Manager** → **investments-dashboard-pages**
2. Select the entry (e.g. `subProduct: fixed-deposits`, `partner: default`)
3. Scroll to the **Explore** component block
4. Open each item in the **fdMasterTable** repeatable zone
5. Fill in the **`bankCode`** field with the matching `fsiCode` from `investments-bank-details`

### Bank Code Reference

| Bank | bankCode (fsiCode) |
|------|--------------------|
| Suryoday Small Finance Bank | `SMCBIN` |
| Bank of Baroda | `BARB` |
| Shivalik Small Finance Bank | `UTKSIN` |

> Use the same codes that appear in the `investments-bank-details` collection's `fsiCode` / `bankCode` field.

---

## API Payload Addition

Add `bankCode` inside each `fdMasterTable` item (and optionally each `cards` item):

```json
{
  "data": {
    "explore": {
      "fdMasterTable": [
        {
          "id": "shivalik",
          "bankCode": "UTKSIN",
          "bankName": "Shivalik SF Bank",
          "logo": "media_or_url",
          "isBank": true,
          "isNBFC": false,
          "isTaxSaver": false,
          "highlightBadge": { "label": "High Returns", "theme": "yellow" },
          "features": ["0.50% extra for senior citizens", "RDs Available"],
          "interestRate": { "prefix": "up to", "value": 9.05, "unit": "p.a" },
          "cta": { "label": "Book FD", "action": "BOOK_FD" }
        },
        {
          "id": "suryoday",
          "bankCode": "SMCBIN",
          "bankName": "Suryoday SF Bank",
          "logo": "media_or_url",
          "isBank": true,
          "isNBFC": false,
          "isTaxSaver": false,
          "highlightBadge": { "label": "High Returns", "theme": "yellow" },
          "features": ["0.05% extra for women", "RDs Available"],
          "interestRate": { "prefix": "up to", "value": 8.05, "unit": "p.a" },
          "cta": { "label": "Book FD", "action": "BOOK_FD" }
        }
      ]
    }
  }
}
```

---

## Expected Response Addition

```json
{
  "data": [
    {
      "id": 1,
      "attributes": {
        "explore": {
          "fdMasterTable": [
            {
              "id": "shivalik",
              "bankCode": "UTKSIN",
              "bankName": "Shivalik SF Bank",
              "logo": { "url": "/uploads/shivalik.svg" },
              "isBank": true,
              "isNBFC": false,
              "isTaxSaver": false,
              "highlightBadge": { "label": "High Returns", "theme": "yellow" },
              "features": ["0.50% extra for senior citizens", "RDs Available"],
              "interestRate": { "prefix": "up to", "value": 9.05, "unit": "p.a" },
              "cta": { "label": "Book FD", "action": "BOOK_FD" }
            }
          ]
        }
      }
    }
  ]
}
```