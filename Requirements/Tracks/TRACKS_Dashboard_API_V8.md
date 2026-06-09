# TRACKS Update Consent API Documentation

## Overview

The **Update Consent** schema is a component of the **tracks-dashboard-pages** collection type in Strapi. It manages the configuration and content for the Update Consent page in the TRACKS (Investment Tracking & Analysis) application.

## Schema Structure

### Update Consent Schema

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| `sidebarHeaderTitle` | String | No | Sidebar title for the Update Consent section (e.g., "Update Consent") |
| `title` | String | No | Main page title (e.g., "Update Your Details") |
| `submitButtonText` | String | No | Text displayed on submit button (e.g., "Save Changes") |
| `submittingButtonText` | String | No | Text displayed while form is submitting (e.g., "Saving...") |
| `mobilePlaceholder` | String | No | Placeholder text for mobile number input field |
| `namePlaceholder` | String | No | Placeholder text for name input field |
| `panPlaceholder` | String | No | Placeholder text for PAN (Personal Account Number) input field |
| `emailPlaceholder` | String | No | Placeholder text for email input field |
| `editMobileText` | String | No | Label or instruction text for mobile number edit field |
| `mobileHelperText` | String | No | Helper/validation text below mobile field (e.g., validation messages) |
| `consentConfig` | Component | No | Complex object containing consent-related configuration (see below) |

### Consent Config Component

The `consentConfig` object contains the following fields:

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| `consentLabel` | String | No | Label for the consent checkbox (e.g., "I consent to terms") |
| `termsText` | String | No | Button/link text for viewing terms (e.g., "View Terms & Conditions") |
| `termsUrl` | String | No | URL/link to terms and conditions page |
| `representativeTextCollapsed` | String | No | Collapsed representative information text (accordion header) |
| `representativeTextExpanded` | String | No | Expanded representative information text (full details) |
| `readMoreText` | String | No | "Read More" button/link text |
| `readLessText` | String | No | "Read Less" button/link text |


## API Endpoints

### Get Update Consent Configuration

**Endpoint:** `GET /api/tracks-dashboard-pages`

**Example Request:**
```bash
curl -X GET "http://localhost:1337/api/tracks-dashboard-pages?filters[page][$eq]=updateConsent&populate=*"
```

### Update Update Consent Configuration

**Request Body:**
```json
{
  "data": {
    "updateConsent": {
      "title": "Update Your Details",
      "mobilePlaceholder": "Enter your mobile number",
      "consentLabel": "I agree to the terms"
    }
  }
}
```

## Sample Request/Response

### Response (Success)

```json
{
  "data": [
    {
      "id": 1,
      "attributes": {
        "page": "updateConsent",
        "updateConsent": {
          "sidebarHeaderTitle": "Update Consent",
          "title": "Update Your Details",
          "submitButtonText": "Save Changes",
          "submittingButtonText": "Saving...",
          "mobilePlaceholder": "Enter your mobile number",
          "namePlaceholder": "Enter your name",
          "panPlaceholder": "Enter your PAN",
          "emailPlaceholder": "Enter your email",
          "editMobileText": "Edit Mobile Number",
          "mobileHelperText": "Please enter a valid 10-digit mobile number",
          "consentLabel": "I understand and agree to the consent terms",
          "termsText": "I agree to the Terms & Conditions",
          "termsUrl": "/terms-and-conditions",
          "representativeTextCollapsed": "View Representative Information",
          "representativeTextExpanded": "Your dedicated investment representative is available to assist you with any questions or concerns regarding your investment portfolio.",
          "readMoreText": "Read More",
          "readLessText": "Read Less"
        },
        "createdAt": "2024-01-15T10:30:00.000Z",
        "updatedAt": "2024-01-20T14:45:22.000Z",
        "publishedAt": "2024-01-20T14:45:22.000Z"
      }
    }
  ],
  "meta": {
    "pagination": {
      "start": 0,
      "limit": 25,
      "total": 1
    }
  }
}
```


