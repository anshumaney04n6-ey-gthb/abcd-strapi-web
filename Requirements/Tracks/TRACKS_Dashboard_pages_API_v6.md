# Tracks Dashboard - Manage Consent & Update Consent API Documentation v6

This document provides Strapi schema and API documentation for the Manage Consent and Update Consent sections used in Tracks Dashboard.

---

## Table of Contents

1. [Overview](#overview)
2. [Manage Consent Schema](#manage-consent-schema)
3. [Update Consent Schema](#update-consent-schema)
4. [API Endpoints](#api-endpoints)
5. [Sample API Request & Response](#sample-api-request--response)
6. [Implementation Notes](#implementation-notes)



## Manage Consent Schema

### Main Attributes

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `cardText` | string | No | `Manage your consent anytime` | Dashboard card label |
| `sidebarHeaderTitle` | string | No | `Manage Consent` | Sidebar header title |
| `sidebarTitle` | string | No | `Choose the permissions you wish to share` | Main title in sidebar |
| `sidebarSubtitle` | string | No | `Adjust your app settings to suit your preferences` | Subtitle in sidebar |
| `confirmModalIcon` | media/string | No | `/icons/alert.svg` | Confirmation modal icon |
| `confirmModalIconAlt` | string | No | `Alert` | Confirmation icon alt text |
| `confirmModalMessage` | string | No | `Are you sure you want to grant your consent?` | Confirmation modal message |
| `confirmButtonText` | string | No | `Yes` | Confirm button label |
| `cancelButtonText` | string | No | `No` | Cancel button label |
| `consentItems` | component[] | No | fallback list | Consent toggle items |

### Consent Item Component

Suggested component name: `tracks.consent-item`

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | string | Yes | Unique item id, ex: `credit-track` |
| `title` | string | Yes | Consent item title |
| `description` | text | Yes | Consent item description |
| `locked` | boolean | No | If item is non-editable |
| `enabled` | boolean | No | Initial toggle state |

### Example manageConsent Payload

```json
{
  "manageConsent": {
    "cardText": "Manage your consent anytime",
    "sidebarHeaderTitle": "Manage Consent",
    "sidebarTitle": "Choose the permissions you wish to share",
    "sidebarSubtitle": "Adjust your app settings to suit your preferences",
    "confirmModalIconAlt": "Alert",
    "confirmModalMessage": "Are you sure you want to grant your consent?",
    "confirmButtonText": "Yes",
    "cancelButtonText": "No",
    "consentItems": [
      {
        "id": "credit-track",
        "title": "Credit track",
        "description": "By providing this consent you appoint ABCD as your authorized representative to receive your credit information report",
        "locked": false,
        "enabled": true
      }
    ]
  }
}
```

---

## Update Consent Schema

### Main Attributes

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `sidebarHeaderTitle` | string | No | `Update Consent` | Sidebar header title |
| `submitButtonText` | string | No | `Update` | Primary action label |
| `submittingButtonText` | string | No | `Updating...` | Loading action label |
| `title` | string | No | `Verify your details to update consent` | Page title |
| `mobileLabel` | string | No | `Mobile number` | Mobile field label |
| `editMobileText` | string | No | `Edit number` | Mobile edit CTA label |
| `mobileHelperText` | string | No | `Mobile number should be linked to your credit accounts` | Mobile helper text |
| `nameLabel` | string | No | `Name` | Name field label |
| `panLabel` | string | No | `PAN` | PAN field label |
| `emailLabel` | string | No | `Personal email address` | Email field label |

### Example updateConsent Payload

```json
{
  "updateConsent": {
    "sidebarHeaderTitle": "Update Consent",
    "submitButtonText": "Update",
    "submittingButtonText": "Updating...",
    "title": "Verify your details to update consent",
    "mobileLabel": "Mobile number",
    "editMobileText": "Edit number",
    "mobileHelperText": "Mobile number should be linked to your credit accounts",
    "nameLabel": "Name",
    "panLabel": "PAN",
    "emailLabel": "Personal email address"
  }
}
```

---

## API Endpoints

### Get Dashboard Content (with Consent Sections)

**GET** `/api/tracks-dashboard-pages`

### Query Parameters

| Parameter | Description | Example |
|-----------|-------------|---------|
| `filters[subProduct][$eq]` | Filter by sub product | `credit` |
| `filters[partner][$eq]` | Filter by partner | `default`, `icici`, `hdfc` |
| `populate` | Populate all first-level sections | `*` |
| `populate[manageConsent][populate]` | Populate nested fields/media in manageConsent | `*` |

### Full Population Example

```bash
GET /api/tracks-dashboard-pages?filters[subProduct][$eq]=credit&filters[partner][$eq]=default&populate=*&populate[manageConsent][populate]=*&populate[manageConsent][populate][confirmModalIcon]=*&populate[manageConsent][populate][consentItems]=*
```

---

## Sample API Request & Response

### Request

```bash
GET /api/tracks-dashboard-pages?filters[subProduct][$eq]=credit&filters[partner][$eq]=default&populate=*&populate[manageConsent][populate]=*
```

### Response (relevant excerpt)

```json
{
  "data": [
    {
      "id": 1,
      "attributes": {
        "subProduct": "credit",
        "partner": "default",
        "manageConsent": {
          "cardText": "Manage your consent anytime",
          "sidebarHeaderTitle": "Manage Consent",
          "sidebarTitle": "Choose the permissions you wish to share",
          "sidebarSubtitle": "Adjust your app settings to suit your preferences",
          "confirmModalIconAlt": "Alert",
          "confirmModalMessage": "Are you sure you want to grant your consent?",
          "confirmButtonText": "Yes",
          "cancelButtonText": "No",
          "consentItems": [
            {
              "id": "credit-track",
              "title": "Credit track",
              "description": "By providing this consent you appoint ABCD as your authorized representative to receive your credit information report",
              "locked": false,
              "enabled": true
            }
          ],
          "confirmModalIcon": {
            "data": {
              "id": 501,
              "attributes": {
                "name": "alert.svg",
                "url": "/uploads/alert_abc123.svg",
                "mime": "image/svg+xml"
              }
            }
          }
        },
        "updateConsent": {
          "sidebarHeaderTitle": "Update Consent",
          "submitButtonText": "Update",
          "submittingButtonText": "Updating...",
          "title": "Verify your details to update consent",
          "mobileLabel": "Mobile number",
          "editMobileText": "Edit number",
          "mobileHelperText": "Mobile number should be linked to your credit accounts",
          "nameLabel": "Name",
          "panLabel": "PAN",
          "emailLabel": "Personal email address"
        }
      }
    }
  ]
}
```

---
