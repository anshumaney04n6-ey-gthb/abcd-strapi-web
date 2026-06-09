# Investments Bank Mapping - Schema Addendum

## Content-Type: Investments Bank Mapping

**Collection Name:** `investments_bank_details`  
**Singular Name:** `investments-bank-detail`  
**Plural Name:** `investments-bank-details`  
**Draft & Publish:** Enabled

---

## Scope

This addendum documents only the NEW fields to be added to the existing `investments_bank_details` content-type.

For the baseline schema and existing field definitions, refer to `Bank_Mapping.md`.

---

## New Content-Type Fields (Exact Strapi Field Names)

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `fdDeepLink` | string | No | - | Deep-link URL for starting the FD journey |
| `rdDeepLink` | string | No | - | Deep-link URL for starting the RD journey |
| `providerAlias` | string[] | No | `[]` | Alternate provider names used for matching and normalization |
| `rateTableColumns` | component[] | No | - | Rate table header schema for bank details |
| `rateTableRows` | component[] | No | - | Rate table row values for bank details |
| `actionSheetProps` | component | No | - | Bank details action labels and enable flags |
| `featureListProps` | component | No | - | Why choose this bank content |
| `infoItems` | component[] | No | - | Bank details metadata rows |
| `highlightCardProps` | component | No | - | Product highlight card content |

---

## Component Structures

### `rateTableColumns`

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `key` | string | Yes | - | Column key used by row `values` |
| `label` | string | Yes | - | Column header label |
| `align` | enumeration | No | `left` | Supported values: `left`, `center`, `right` |

### `rateTableRows`

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `id` | string | No | `row-{index+1}` | Unique row identifier |
| `values` | JSON | Yes | - | Key-value map aligned to `rateTableColumns[].key` |

### `actionSheetProps`

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `enableRdAction` | boolean | No | - | Enable RD CTA |
| `enableFdAction` | boolean | No | - | Enable FD CTA |
| `openRdLabel` | string | No | - | RD button text |
| `openFdLabel` | string | No | - | FD button text |
| `discoveryLabel` | string | No | - | Discovery form label |

### `featureListProps`

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `heading` | string | No | - | Feature list heading |
| `items` | component[] | No | - | Feature list items |

**`featureListProps.items` fields**

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `id` | string | No | `feature-{index+1}` | Feature row identifier |
| `iconSrc` | string | No | - | Direct icon URL fallback |
| `iconAlt` | string | No | - | Icon alt text |
| `title` | string | No | - | Feature title |
| `description` | string | No | - | Feature description |

### `infoItems`

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `id` | string | No | `info-{index+1}` | Metadata row identifier |
| `label` | string | No | - | Metadata label |
| `value` | string | No | - | Metadata value |
| `description` | string | No | - | Optional supporting description |
| `showChevron` | boolean | No | `false` | Whether to show trailing chevron |

### `highlightCardProps`

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `headerLabel` | string | No | `Earn Guaranteed Returns` | Card header label |
| `productName` | string | No | `FD SIP` | Product name |
| `description` | string | No | `Monthly FD for stable growth` | Product description |
| `startingAmount` | string | No | `Starting from ₹1000` | Minimum amount label |
| `securityBadge` | string | No | `100% secured` | Security badge text |
| `backgroundColor` | string | No | `#fff4ce` | Card background color |
| `imageUrl` | string | No | - | Direct image URL fallback |
| `imageAlt` | string | No | `FD SIP product` | Product image alt text |

---

## JSON Examples

### Journey Deep-Links

```json
{
  "fdDeepLink": "https://adityabirlaapp.blostem.com/purchase/80f5547d-9238-4006-8e67-4dee91f64642",
  "rdDeepLink": "https://adityabirlaapp.blostem.com/purchase/80f5547d-9238-4006-8e67-4dee91f64642"
}
```

### Provider Alias

```json
{
  "providerAlias": ["Shivalik", "Shivalik SF Bank"]
}
```

### Rate Table

**rateTableColumns:**

```json
{
  "rateTableColumns": [
    { "key": "tenure", "label": "Tenure", "align": "left" },
    { "key": "general", "label": "General", "align": "center" },
    { "key": "seniorCitizen", "label": "Sr. Citizen", "align": "center" }
  ]
}
```

**rateTableRows:**

```json
{
  "rateTableRows": [
    {
      "id": "2y",
      "values": { "tenure": "2Y", "general": "8.50%", "seniorCitizen": "9.10%" }
    },
    {
      "id": "5y",
      "values": { "tenure": "5Y", "general": "11.50%", "seniorCitizen": "11.75%" }
    }
  ]
}
```

### Action Sheet Props

```json
{
  "actionSheetProps": {
    "enableRdAction": true,
    "enableFdAction": true,
    "openRdLabel": "Open RD",
    "openFdLabel": "Open FD",
    "discoveryLabel": "How did you learn about us?"
  }
}
```

### Feature List Props

```json
{
  "featureListProps": {
    "heading": "Why choose Shivalik SF bank?",
    "items": [
      {
        "id": "aum",
        "iconSrc": "media_or_url",
        "iconAlt": "AUM",
        "title": "AUM of 19,000 Cr+",
        "description": "Trusted by over 30 lakh+ users"
      },
      {
        "id": "ipo",
        "iconSrc": "media_or_url",
        "iconAlt": "IPO",
        "title": "Stellar IPO debut",
        "description": "Recent IPO with 60% premium"
      }
    ]
  }
}
```

### Info Items

```json
{
  "infoItems": [
    {
      "id": "min-investment",
      "label": "Min Investment",
      "value": "₹1,000"
    },
    {
      "id": "withdrawal",
      "label": "Withdrawal",
      "value": "ABCD app",
      "description": "Withdrawals processed within 2 days",
      "showChevron": true
    }
  ]
}
```

### Highlight Card Props

```json
{
  "highlightCardProps": {
    "headerLabel": "Earn Guaranteed Returns",
    "productName": "Shivalik FD SIP",
    "description": "Monthly FD for stable growth",
    "startingAmount": "Starting from ₹1000",
    "securityBadge": "100% secured",
    "backgroundColor": "#fff4ce",
    "imageUrl": "media_or_url",
    "imageAlt": "Shivalik FD SIP product"
  }
}
```

---

## Complete JSON Structure

> **Note:** This addendum extends the baseline schema in `Bank_Mapping.md` and lists only the newly added fields and their expected shapes.

```json
{
  "data": {
    "fdDeepLink": "https://adityabirlaapp.blostem.com/purchase/80f5547d-9238-4006-8e67-4dee91f64642",
    "rdDeepLink": "https://adityabirlaapp.blostem.com/purchase/80f5547d-9238-4006-8e67-4dee91f64642",
    "providerAlias": ["Shivalik", "Shivalik SF Bank"],
    "rateTableColumns": [
      { "key": "tenure", "label": "Tenure", "align": "left" },
      { "key": "general", "label": "General", "align": "center" },
      { "key": "seniorCitizen", "label": "Sr. Citizen", "align": "center" }
    ],
    "rateTableRows": [
      {
        "id": "2y",
        "values": {
          "tenure": "2Y",
          "general": "8.50%",
          "seniorCitizen": "9.10%"
        }
      }
    ],
    "actionSheetProps": {
      "enableRdAction": true,
      "enableFdAction": true,
      "openRdLabel": "Open RD",
      "openFdLabel": "Open FD",
      "discoveryLabel": "How did you learn about us?"
    },
    "featureListProps": {
      "heading": "Why choose this bank?",
      "items": [
        {
          "id": "feature-1",
          "iconSrc": "media_or_url",
          "iconAlt": "Secure",
          "title": "Safe and regulated",
          "description": "RBI regulated partner"
        }
      ]
    },
    "infoItems": [
      {
        "id": "min-investment",
        "label": "Min Investment",
        "value": "₹1,000",
        "description": "Optional description",
        "showChevron": false
      }
    ],
    "highlightCardProps": {
      "headerLabel": "Earn Guaranteed Returns",
      "productName": "FD SIP",
      "description": "Monthly FD for stable growth",
      "startingAmount": "Starting from ₹1000",
      "securityBadge": "100% secured",
      "backgroundColor": "#fff4ce",
      "imageUrl": "media_or_url",
      "imageAlt": "FD SIP product"
    }
  }
}
```

---

## Defaults Summary

| Field | Default Value |
|-------|---------------|
| `interestRateUnit` | `%` |
| `interestLabel` | `Interest now` |
| `providerAlias` | `[]` |
| `rateTableColumns[].align` | `left` |
| `rateTableRows[].id` | `row-{index+1}` |
| `highlightCardProps.headerLabel` | `Earn Guaranteed Returns` |
| `highlightCardProps.productName` | `FD SIP` |
| `highlightCardProps.description` | `Monthly FD for stable growth` |
| `highlightCardProps.startingAmount` | `Starting from ₹1000` |
| `highlightCardProps.securityBadge` | `100% secured` |
| `highlightCardProps.backgroundColor` | `#fff4ce` |
| `highlightCardProps.imageAlt` | `FD SIP product` |

---

## Fallback Content Mapping

> Maps dashboard fallback `BANK_MAPPING` additions to Strapi field names used by the CMS transformer.

| Fallback Path | Strapi Field Name |
|---------------|-------------------|
| `fdDeepLink` | `fdDeepLink` |
| `rdDeepLink` | `rdDeepLink` |
| `providerAlias` | `providerAlias` |
| `rateTableColumns` | `rateTableColumns` |
| `rateTableRows` | `rateTableRows` |
| `actionSheetProps` | `actionSheetProps` |
| `featureListProps` | `featureListProps` |
| `infoItems` | `infoItems` |
| `highlightCardProps` | `highlightCardProps` |

---