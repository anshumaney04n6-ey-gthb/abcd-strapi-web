# Credit Cards Apply Flow — Basic Details & Redirection CMS Schema

**Related document:** [Credit-Cards-Dashboard-v2.md](./Credit-Cards-Dashboard-v2.md)

---

## Overview

This document defines the Strapi CMS content-type for the **Apply flow** pages.

All three pages are served from a **single collection** — `cards-journey-pages` — following the same pattern used across other verticals (e.g. digimetal). One entry per `subProduct` + `partner` combination contains all apply-flow copy as **top-level fields** on the entry.

| Page | Top-level key in entry |
|------|------------------------|
| Unsecured Basic Details | `unsecuredBasicDetails` |
| Secured Basic Details | `securedBasicDetails` |
| Redirection | `redirection` |

**Unified API endpoint:** `GET /api/cards-journey-pages`  
**Filter by subProduct:** `?filters[subProduct][$eq]=<subProduct>`  
**Partner fallback:** SDK tries partner-specific entry first, then falls back to `default`.

Both basic-details blocks share a reusable component:
- **`cards-apply.consent-config`** — consent checkbox label/link copy

---

## Shared Component: `cards-apply.consent-config`

Used in both `unsecured_basic_details` and `secured_basic_details` as:
- `abcdConsentConfig` — ABCD T&C / Privacy consent
- `crediloConsentConfig` — Credilio T&C / Privacy consent

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `labelPrefix` | string | No | `"I have read and agree to the"` |
| `termsText` | string | Yes | `"Terms and Conditions"` |
| `termsUrl` | string | No | _(empty — deep-link handled by app)_ |
| `connector` | string | No | `"and"` |
| `privacyText` | string | Yes | `"Privacy policy"` |
| `privacyUrl` | string | No | _(empty — deep-link handled by app)_ |
| `labelSuffix` | string | No | `"of ABCD."` / `"of Credilio."` |

> **Note:** `termsUrl` and `privacyUrl` are optional string fields. When blank the client falls back to its internal navigation handler (`onTermsClick` / `onPrivacyClick`). Populate these only when the destination is an external URL.

---

## Section 1: `unsecuredBasicDetails`

**Collection:** `cards-journey-pages`  
**Top-level key:** `unsecuredBasicDetails`  
**Draft & Publish:** Enabled  
**Entry scope:** One per `subProduct` (+ optional `partner`)

### Fields

| Field | Type | Required | Default | Description |
|-------|------|----------|---------|-------------|
| `title` | string | No | `"Basic information"` | Page/sidebar title |
| `bannerTitle` | string | No | `"Get Rewarded every time you spend on credit cards"` | Top banner headline |
| `proceedButtonText` | string | No | `"Proceed"` | Primary CTA button label |
| `learnMoreText` | string | No | `"How did you learn about us?"` | Secondary CTA link text |
| `mobileNumberLabel` | string | No | `"Mobile Number"` | Form field label |
| `mobileNumberPlaceholder` | string | No | `"Enter mobile number"` | Form field placeholder |
| `panLabel` | string | No | `"PAN"` | Form field label |
| `fullNameLabel` | string | No | `"Full Name"` | Form field label |
| `dateOfBirthLabel` | string | No | `"Date of Birth"` | Form field label |
| `employmentTypeLabel` | string | No | `"Employment Type"` | Form field label |
| `monthlySalaryLabel` | string | No | `"Monthly Salary"` | Form field label |
| `monthlySalaryPlaceholder` | string | No | `"Enter monthly salary"` | Form field placeholder |
| `annualIncomeLabel` | string | No | `"Annual Income"` | Form field label |
| `annualIncomePlaceholder` | string | No | `"Enter annual income"` | Form field placeholder |
| `datePickerTitle` | string | No | `"Select Date of Birth"` | Date-picker modal title |
| `pincodeLabel` | string | No | `"Pincode"` | Form field label |
| `ageRangeText` | string | No | `"Your age should range between 18-65 years"` | Helper/error copy below DOB field |
| `minMonthlySalary` | number | No | `10000` | Minimum monthly salary allowed for validation |
| `maxMonthlySalary` | number | No | `1000000` | Maximum monthly salary allowed for validation |
| `minAnnualIncome` | number | No | `10000` | Minimum annual income allowed for validation |
| `maxAnnualIncome` | number | No | `10000000` | Maximum annual income allowed for validation |
| `abcdConsentConfig` | component (`cards-apply.consent-config`) | No | See component defaults | ABCD consent checkbox copy |
| `crediloConsentConfig` | component (`cards-apply.consent-config`) | No | See component defaults | Credilio consent checkbox copy |
| `disclaimerFooterText` | text | No | `"By proceeding, you are required to accept the Terms and Conditions as well as Privacy Policy of both ABCD and Company, as applicable."` | Footer disclaimer below consent checkboxes |

### API Endpoint

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/cards-journey-pages` | Fetch all entries (filter by `subProduct`) |

### Populate Query

```
/api/cards-journey-pages?filters[subProduct][$eq]=credit-card&populate[unsecuredBasicDetails][populate]=*
```

### cURL Example

```bash
curl -s 'http://localhost:1337/api/cards-journey-pages?filters[subProduct][$eq]=credit-card&populate[unsecuredBasicDetails][populate]=*'
```

### Example JSON Response

```json
{
  "data": [
    {
      "id": 1,
      "documentId": "abc123",
      "subProduct": "credit-card",
      "partner": "default",
      "unsecuredBasicDetails": {
          "title": "Basic information",
          "bannerTitle": "Get Rewarded every time you spend on credit cards",
        "proceedButtonText": "Proceed",
        "learnMoreText": "How did you learn about us?",
        "mobileNumberLabel": "Mobile Number",
        "mobileNumberPlaceholder": "Enter mobile number",
        "panLabel": "PAN",
        "fullNameLabel": "Full Name",
        "dateOfBirthLabel": "Date of Birth",
        "employmentTypeLabel": "Employment Type",
        "monthlySalaryLabel": "Monthly Salary",
        "monthlySalaryPlaceholder": "Enter monthly salary",
        "annualIncomeLabel": "Annual Income",
        "annualIncomePlaceholder": "Enter annual income",
        "datePickerTitle": "Select Date of Birth",
        "pincodeLabel": "Pincode",
        "ageRangeText": "Your age should range between 18-65 years",
        "minMonthlySalary": 10000,
        "maxMonthlySalary": 1000000,
        "minAnnualIncome": 10000,
        "maxAnnualIncome": 10000000,
        "abcdConsentConfig": {
          "labelPrefix": "I have read and agree to the",
          "termsText": "Terms and Conditions",
          "termsUrl": null,
          "connector": "and",
          "privacyText": "Privacy policy",
          "privacyUrl": null,
          "labelSuffix": "of ABCD."
        },
        "crediloConsentConfig": {
          "labelPrefix": "I have read and agree to the",
          "termsText": "Terms and Conditions",
          "termsUrl": null,
          "connector": "and",
          "privacyText": "Privacy policy",
          "privacyUrl": null,
          "labelSuffix": "of Credilio."
        },
        "disclaimerFooterText": "By proceeding, you are required to accept the Terms and Conditions as well as Privacy Policy of both ABCD and Company, as applicable."
      }
    }
  ],
  "meta": {
    "pagination": { "page": 1, "pageSize": 25, "pageCount": 1, "total": 1 }
  }
}
```

---

## Section 2: `securedBasicDetails`

**Collection:** `cards-journey-pages`  
**Top-level key:** `securedBasicDetails`  
**Draft & Publish:** Enabled  
**Entry scope:** One per `subProduct` (+ optional `partner`)

### Fields

| Field | Type | Required | Default | Description |
|-------|------|----------|---------|-------------|
| `title` | string | No | `"Basic information"` | Page/sidebar title |
| `bannerTitle` | string | No | `"Start with FD-backed secured card"` | Top banner headline |
| `bannerImagePath` | string | No | `"/images/safe-box.svg"` | Relative path or absolute URL for banner illustration. Upgrade to `media` field in a future iteration. |
| `proceedButtonText` | string | No | `"Proceed"` | Primary CTA button label |
| `learnMoreText` | string | No | `"How did you learn about us?"` | Secondary CTA link text |
| `mobileNumberLabel` | string | No | `"Mobile number"` | Form field label |
| `mobileNumberPlaceholder` | string | No | `"Enter mobile number"` | Form field placeholder |
| `fullNameLabel` | string | No | `"Full name"` | Form field label |
| `pincodeLabel` | string | No | `"Pincode"` | Form field label |
| `abcdConsentConfig` | component (`cards-apply.consent-config`) | No | See component defaults | ABCD consent checkbox copy |
| `crediloConsentConfig` | component (`cards-apply.consent-config`) | No | See component defaults | Credilio consent checkbox copy |
| `disclaimerFooterText` | text | No | `"By proceeding, you are required to accept the Terms and Conditions as well as Privacy Policy of both ABCD and Credilio, as applicable."` | Footer disclaimer below consent checkboxes |
| `visibleFields` | string | No | `"mobileNumber,fullName,pincode"` | Comma-separated list of fields to show. Allowed values: `mobileNumber`, `fullName`, `pincode`. Controls which fields render in `BasicInformationPage` (secured variant). |

> **`visibleFields` note:** Stored as a plain comma-separated string (e.g. `"mobileNumber,fullName,pincode"`) because Strapi's multi-select enum maps cleanly to this. The BFF mapper parses and validates it against the allowed set, ignoring unknown values.

### API Endpoint

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/cards-journey-pages` | Fetch all entries (filter by `subProduct`) |

### Populate Query

```
/api/cards-journey-pages?filters[subProduct][$eq]=credit-card&populate[securedBasicDetails][populate]=*
```

### cURL Example

```bash
curl -s 'http://localhost:1337/api/cards-journey-pages?filters[subProduct][$eq]=credit-card&populate[securedBasicDetails][populate]=*'
```

### Example JSON Response

```json
{
  "data": [
    {
      "id": 1,
      "documentId": "def456",
      "subProduct": "credit-card",
      "partner": "default",
      "securedBasicDetails": {
        "title": "Basic information",
        "bannerTitle": "Start with FD-backed secured card",
        "bannerImagePath": "/images/safe-box.svg",
        "proceedButtonText": "Proceed",
        "learnMoreText": "How did you learn about us?",
        "mobileNumberLabel": "Mobile number",
        "mobileNumberPlaceholder": "Enter mobile number",
        "fullNameLabel": "Full name",
        "pincodeLabel": "Pincode",
        "abcdConsentConfig": {
          "labelPrefix": "I have read and agree to the",
          "termsText": "Terms and Conditions",
          "termsUrl": null,
          "connector": "and",
          "privacyText": "Privacy policy",
          "privacyUrl": null,
          "labelSuffix": "of ABCD."
        },
        "crediloConsentConfig": {
          "labelPrefix": "I have read and agree to the",
          "termsText": "Terms and Conditions",
          "termsUrl": null,
          "connector": "and",
          "privacyText": "Privacy policy",
          "privacyUrl": null,
          "labelSuffix": "of Credilio."
        },
        "disclaimerFooterText": "By proceeding, you are required to accept the Terms and Conditions as well as Privacy Policy of both ABCD and Credilio, as applicable.",
        "visibleFields": "mobileNumber,fullName,pincode"
      }
    }
  ],
  "meta": {
    "pagination": { "page": 1, "pageSize": 25, "pageCount": 1, "total": 1 }
  }
}
```

---

## Section 3: `redirection`

**Collection:** `cards-journey-pages`  
**Top-level key:** `redirection`  
**Draft & Publish:** Enabled  
**Entry scope:** One per `subProduct` (+ optional `partner`)

> The `redirection` page renders a fullscreen "please wait" message while the orchestrator resolves the bank redirect URL. Both strings are now CMS-editable via this nested block without requiring a code deploy.

### Fields

| Field | Type | Required | Default | Description |
|-------|------|----------|---------|-------------|
| `title` | string | No | `"Redirecting"` | Sidebar/page title shown during redirect |
| `redirectingText` | string | No | `"Redirecting, please wait…"` | Body copy shown in the centre panel while redirect resolves |

### API Endpoint

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/cards-journey-pages` | Fetch all entries (filter by `subProduct`) |

### Populate Query

```
/api/cards-journey-pages?filters[subProduct][$eq]=credit-card&populate[redirection]=*
```

### cURL Example

```bash
curl -s 'http://localhost:1337/api/cards-journey-pages?filters[subProduct][$eq]=credit-card&populate[redirection]=*'
```

### Example JSON Response

```json
{
  "data": [
    {
      "id": 1,
      "documentId": "ghi789",
      "subProduct": "credit-card",
      "partner": "default",
      "redirection": {
        "title": "Redirecting",
        "redirectingText": "Redirecting, please wait…"
      }
    }
  ],
  "meta": {
    "pagination": { "page": 1, "pageSize": 25, "pageCount": 1, "total": 1 }
  }
}
```
