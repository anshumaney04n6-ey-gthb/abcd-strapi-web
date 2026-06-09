# Tracks Dashboard - Consent Screen Schemas

This document provides schema documentation for the Tracks Dashboard consent screen components.

---

## Table of Contents

1. [Overview](#overview)
2. [Components](#components)
   - [Consent Modal](#consent-modal)
   - [Renew Consent Banner](#renew-consent-banner)
3. [API Endpoints](#api-endpoints)
4. [Sample API Response](#sample-api-response)

---

## Overview

The Tracks Dashboard consent screen schemas define the content structure for consent renewal flows in the Credit Tracking dashboard. These components are part of the Tracks Dashboard collection type.

**API Identifier:** `api::dashboard-pages.dashboard-pages`

**Location:** `/src/components/dashboard-pages/`

---

## Components

All components are located in `/src/components/tracks-dashboard/`

### Consent Modal

**File:** `consent-modal.json`

Consent renewal modal configuration appearing in sidebar.

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `title` | text | Yes | `Renew permission\nfor credit report access` | Modal title (supports newline) |
| `subtitle` | text | Yes | `Continue to enjoy seamless access to your credit score.` | Modal subtitle |
| `infoIconTooltip` | text | No | - | Tooltip text for info icon |
| `warningMessage` | string | No | `Expiring in 15 days` | Warning badge message |
| `consentLabel` | string | Yes | `I accept the` | Consent checkbox label prefix |
| `termsText` | string | Yes | `terms and conditions` | Terms link text |
| `termsUrl` | string | Yes | `/terms` | Terms link URL |
| `readMoreText` | string | No | `Read more` | Expand consent text link |
| `readLessText` | string | No | `Read less` | Collapse consent text link |
| `representativeTextCollapsed` | text | Yes | - | Collapsed consent representative text |
| `representativeTextExpanded` | text | Yes | - | Expanded consent representative text |
| `updateButtonText` | string | Yes | `Update` | Primary CTA button text |
| `doLaterLinkText` | string | Yes | `Do this later` | Secondary link text |

**Schema:**
```json
{
  "collectionName": "components_dashboard_pages_consent_modals",
  "info": {
    "displayName": "Consent Modal",
    "description": "Consent renewal modal configuration"
  },
  "options": {},
  "attributes": {
    "title": {
      "type": "text",
      "required": true,
      "default": "Renew permission\nfor credit report access"
    },
    "subtitle": {
      "type": "text",
      "required": true,
      "default": "Continue to enjoy seamless access to your credit score."
    },
    "infoIconTooltip": {
      "type": "text",
      "default": "Your consent expires every 6 months. After expiry, you will need to fetch your score once again."
    },
    "warningMessage": {
      "type": "string",
      "default": "Expiring in 15 days"
    },
    "consentLabel": {
      "type": "string",
      "required": true,
      "default": "I accept the"
    },
    "termsText": {
      "type": "string",
      "required": true,
      "default": "terms and conditions"
    },
    "termsUrl": {
      "type": "string",
      "required": true,
      "default": "/terms"
    },
    "readMoreText": {
      "type": "string",
      "default": "Read more"
    },
    "readLessText": {
      "type": "string",
      "default": "Read less"
    },
    "representativeTextCollapsed": {
      "type": "text",
      "required": true,
      "default": " and appoint ABCD as my authorized representative to receive my credit information from Experian..."
    },
    "representativeTextExpanded": {
      "type": "text",
      "required": true,
      "default": " and appoint ABCD as my authorized representative to receive my credit information from Experian for the purpose of providing credit tracking services."
    },
    "updateButtonText": {
      "type": "string",
      "required": true,
      "default": "Update"
    },
    "doLaterLinkText": {
      "type": "string",
      "required": true,
      "default": "Do this later"
    }
  }
}
```

**Example:**
```json
{
  "title": "Renew permission\nfor credit report access",
  "subtitle": "Continue to enjoy seamless access to your credit score.",
  "infoIconTooltip": "Your consent expires every 6 months. After expiry, you will need to fetch your score once again.",
  "warningMessage": "Expiring in 15 days",
  "consentLabel": "I accept the",
  "termsText": "terms and conditions",
  "termsUrl": "/terms",
  "readMoreText": "Read more",
  "readLessText": "Read less",
  "representativeTextCollapsed": " and appoint ABCD as my authorized representative to receive my credit information from Experian...",
  "representativeTextExpanded": " and appoint ABCD as my authorized representative to receive my credit information from Experian for the purpose of providing credit tracking services.",
  "updateButtonText": "Update",
  "doLaterLinkText": "Do this later"
}
```

---

### Renew Consent Banner

**File:** `renew-consent-banner.json`

Dashboard banner for consent renewal.

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `title` | string | Yes | `Renew consent before your Credit Data is removed` | Banner title |
| `badgeText` | string | No | `Expiring soon` | Warning badge text |
| `consentLabel` | string | Yes | `I accept the` | Consent checkbox label prefix |
| `termsText` | string | Yes | `terms and conditions` | Terms link text |
| `termsUrl` | string | Yes | `/terms` | Terms link URL |
| `consentContinuationText` | text | Yes | - | Continuation consent text |
| `readMoreText` | string | No | `Read more` | Expand text link |
| `readLessText` | string | No | `Read less` | Collapse text link |
| `updateButtonText` | string | Yes | `Update` | Update button text |

**Schema:**
```json
{
  "collectionName": "components_dashboard_pages_renew_consent_banners",
  "info": {
    "displayName": "Renew Consent Banner",
    "description": "Dashboard banner for consent renewal"
  },
  "options": {},
  "attributes": {
    "title": {
      "type": "string",
      "required": true,
      "default": "Renew consent before your Credit Data is removed"
    },
    "badgeText": {
      "type": "string",
      "default": "Expiring soon"
    },
    "consentLabel": {
      "type": "string",
      "required": true,
      "default": "I accept the"
    },
    "termsText": {
      "type": "string",
      "required": true,
      "default": "terms and conditions"
    },
    "termsUrl": {
      "type": "string",
      "required": true,
      "default": "/terms"
    },
    "consentContinuationText": {
      "type": "text",
      "required": true,
      "default": " and appoint ABCD as my authorized representative to receive my credit information from Experian..."
    },
    "readMoreText": {
      "type": "string",
      "default": "Read more"
    },
    "readLessText": {
      "type": "string",
      "default": "Read less"
    },
    "updateButtonText": {
      "type": "string",
      "required": true,
      "default": "Update"
    }
  }
}
```

**Example:**
```json
{
  "title": "Renew consent before your Credit Data is removed",
  "badgeText": "Expiring soon",
  "consentLabel": "I accept the",
  "termsText": "terms and conditions",
  "termsUrl": "/terms",
  "consentContinuationText": " and appoint ABCD as my authorized representative to receive my credit information from Experian...",
  "readMoreText": "Read more",
  "readLessText": "Read less",
  "updateButtonText": "Update"
}
```

---

## API Endpoints

The Tracks Dashboard uses Strapi's default REST API routes.

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tracks-dashboard-pages` | Get all dashboards |
| GET | `/api/tracks-dashboard-pages/:id` | Get dashboard by ID |
| GET | `/api/tracks-dashboard-pages?filters[subProduct][$eq]=tracks&populate[consentModal]=*&populate[renewConsentBanner]=*` | Get tracks dashboard with consent schemas |

---

## Sample API Response

**GET** `/api/tracks-dashboard-pages?filters[subProduct][$eq]=tracks&populate[consentModal]=*&populate[renewConsentBanner]=*`

```json
{
  "data": [
    {
      "id": 1,
      "attributes": {
        "subProduct": "tracks",
        "createdAt": "2026-01-15T10:00:00.000Z",
        "updatedAt": "2026-04-24T15:30:00.000Z",
        "publishedAt": "2026-01-15T12:00:00.000Z",
        
        "consentModal": {
          "id": 1,
          "title": "Renew permission\nfor credit report access",
          "subtitle": "Continue to enjoy seamless access to your credit score.",
          "infoIconTooltip": "Your consent expires every 6 months. After expiry, you will need to fetch your score once again.",
          "warningMessage": "Expiring in 15 days",
          "consentLabel": "I accept the",
          "termsText": "terms and conditions",
          "termsUrl": "/terms",
          "readMoreText": "Read more",
          "readLessText": "Read less",
          "representativeTextCollapsed": " and appoint ABCD as my authorized representative to receive my credit information from Experian...",
          "representativeTextExpanded": " and appoint ABCD as my authorized representative to receive my credit information from Experian for the purpose of providing credit tracking services.",
          "updateButtonText": "Update",
          "doLaterLinkText": "Do this later"
        },
        
        "renewConsentBanner": {
          "id": 1,
          "title": "Renew consent before your Credit Data is removed",
          "badgeText": "Expiring soon",
          "consentLabel": "I accept the",
          "termsText": "terms and conditions",
          "termsUrl": "/terms",
          "consentContinuationText": " and appoint ABCD as my authorized representative to receive my credit information from Experian...",
          "readMoreText": "Read more",
          "readLessText": "Read less",
          "updateButtonText": "Update"
        }
      }
    }
  ],
  "meta": {
    "pagination": {
      "page": 1,
      "pageSize": 25,
      "pageCount": 1,
      "total": 1
    }
  }
}
```

---



## Usage Flow

### Consent Modal Flow

1. **Trigger**: Modal appears when user's consent is expiring or expired
2. **Display**: Opens in sidebar with `consentModal` data
3. **User Actions**:
   - Check consent checkbox → enables "Update" button
   - Click "Update" (updateButtonText) → proceeds to consent update flow
   - Click "Do this later" (doLaterLinkText) → closes sidebar, shows renew banner
   - Click back button → closes sidebar, shows renew banner

### Renew Consent Banner Flow

1. **Display**: Appears on dashboard when consent needs renewal
2. **Data Source**: Uses `renewConsentBanner` component data
3. **User Actions**:
   - Check consent checkbox → enables update action
   - Click update → opens consent update flow
   - Click close → dismisses banner

---

## Notes

- All text content is Strapi-driven and can be updated without code changes
- The `title` field in `consentModal` supports newline character (`\n`) for multi-line titles
- Both components share similar consent text structure for consistency
- Representative text has collapsed and expanded states for better UX
