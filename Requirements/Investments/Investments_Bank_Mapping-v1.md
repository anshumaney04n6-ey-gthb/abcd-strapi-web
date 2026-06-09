# Investments Bank Mapping - Complete Schema Documentation

## Content-Type: Investments Bank Mapping

**Collection Name:** `investments_bank_details`  
**Singular Name:** `investments-bank-detail`  
**Plural Name:** `investments-bank-details`  
**Draft & Publish:** Enabled

---

## All Content-Type Fields (Exact Strapi Field Names)

| Field Name | Type | Required | Default | Max | Description |
|------------|------|----------|---------|-----|-------------|
| `fsiCode` | string | Yes | - | - | Primary mapping key used by journey response |
| `bankCode` | string | No | - | - | Alternate key (fallback when fsiCode is missing) |
| `bankName` | string | Yes | - | - | Bank display name |
| `bankLogo` | media (image) | No | - | - | Bank logo media |
| `bankLogoUrl` | string | No | - | - | Direct logo URL fallback when media not used |
| `interestRate` | string | No | - | - | Display interest rate value, e.g. `8.05%` |
| `interestRateUnit` | string | No | `%` | - | Unit shown with interest rate |
| `interestLabel` | string | No | `Interest now` | - | Supporting label text |

---

## API Endpoints

### Base URL
```
/api/investments-bank-details
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/investments-bank-details` | List all bank mappings |
| GET | `/api/investments-bank-details/:id` | Get single bank mapping |
| POST | `/api/investments-bank-details` | Create bank mapping |
| PUT | `/api/investments-bank-details/:id` | Update bank mapping |
| DELETE | `/api/investments-bank-details/:id` | Delete bank mapping |

### Query Parameters
```
?populate=*
```

---

## Complete JSON Structure

> **Note:** `fsiCode` is used first; `bankCode` is used only as fallback key in code.

```json
{
  "data": [
    {
      "id": 1,
      "fsiCode": "SMCBIN",
      "bankCode": "SMCBIN",
      "bankName": "Suryoday Bank",
      "bankLogo": { "media_object" },
      "bankLogoUrl": "https://cdn.example.com/logos/suryoday.svg",
      "interestRate": "8.05%",
      "interestRateUnit": "%",
      "interestLabel": "Interest now"
    }
  ]
}
```

---

## Field Resolution Logic (Used in Code)

1. Mapping key: `fsiCode` -> fallback `bankCode`
2. Logo resolution: `bankLogo` media URL -> fallback `bankLogoUrl` -> fallback empty string
3. Label defaults:
- `interestRateUnit`: `%`
- `interestLabel`: `Interest now`

---

## Defaults Summary

| Field | Default Value |
|-------|---------------|
| `interestRateUnit` | `%` |
| `interestLabel` | `Interest now` |

---

## API Response Example (Actual Runtime Shape Expected)

```json
{
  "data": [
    {
      "id": 11,
      "attributes": {
        "fsiCode": "UTKSIN",
        "bankCode": "UTKSIN",
        "bankName": "Shivalik SF Bank",
        "interestRate": "7%",
        "interestRateUnit": "%",
        "interestLabel": "Interest now",
        "bankLogo": {
          "data": {
            "id": 401,
            "attributes": {
              "url": "/uploads/shivalik_logo.svg"
            }
          }
        }
      }
    }
  ],
  "meta": {}
}
```

---

## Populate Query for Full Response

```
/api/investments-bank-details?populate=deep
```

---

## Fallback Content Mapping

> Maps dashboard fallback `BANK_MAPPING` entries to Strapi field names used by `getBankMappingCMSContent`.

| Fallback Path | Strapi Field Name |
|---------------|-------------------|
| `BANK_MAPPING.<fsiCode key>` | `fsiCode` |
| `bankName` | `bankName` |
| `bankLogoUrl` | `bankLogo` (media) or `bankLogoUrl` (string) |
| `interestRate` | `interestRate` |
| `interestRateUnit` | `interestRateUnit` |
| `interestLabel` | `interestLabel` |

---

## Source Files

| File | Purpose |
|------|---------|
| `abcd-investments-web/src/app/[subProduct]/customer/@dashboard/content/index.ts` | Fetcher + mapper (`getBankMappingCMSContent`) |
| `abcd-investments-web/src/app/[subProduct]/customer/@dashboard/content/fallback.ts` | Fallback `BANK_MAPPING` values |
| `Dashboard_Page.md` | Main dashboard page schema (excluding journey-level bank mapping) |
