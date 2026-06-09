# Tracks Credit Activity Strapi Reference

**Date:** 2026-04-27
**Purpose:** Reference document for Strapi configuration of `tracks-dashboard-pages` for the Credit Activity section in `abcd-tracks-web`

---

## 1. Overview

**Content Type:** `tracks-dashboard-pages`

**API Endpoint:**

```http
GET /api/tracks-dashboard-pages?filters[subProduct][$eq]=credit&filters[partner][$eq]=default&populate=*
```

This document is intended for the Strapi team and covers the `creditActivity` CMS fields that should remain available for the Credit dashboard flow.

---

## 2. In Scope

This document covers the following dashboard CMS area:

- `creditActivity`

These fields are consumed in the dashboard CMS transformation layer and then used in the UI for:

- Credit activity section header and CTA labels
- Card visibility configuration for the dashboard activity list
- Repayment tip copy
- Need help bottom sheet content
- Need help reason options

---

## 3. Required Components

### 3.1 `creditActivity`

Dashboard-level configuration for the activity section and need help content.

```text
creditActivity
├── sectionHeader (String)
├── viewAllText (String)
├── visibleCardsCount (Integer)
├── payBillCTAText (String)
├── viewDetailsCTAText (String)
├── repaymentTipText (Text)
└── needHelp (Component: credit-activity-need-help)
```

### 3.2 `credit-activity-need-help`

Nested component used for the Need Help bottom sheet content.

```text
credit-activity-need-help
├── icon (Media)
├── title (String)
├── subtitle (Text)
├── reasonPlaceholder (String)
├── continueButtonText (String)
├── reasonRequiredOptionId (String)
└── options (Repeatable component: credit-activity-help-option)
```

### 3.3 `credit-activity-help-option`

Repeatable nested component used for the selectable help reasons.

```text
credit-activity-help-option[]
├── id (String)
├── label (String)
└── icon (Media, optional)
```

Important:

- `creditActivity` should remain a top-level component under `tracks-dashboard-pages`
- `needHelp.options` should remain an array
- `reasonRequiredOptionId` should match one of the configured option `id` values
- `needHelp.icon` should be configured as a Strapi media field

---

## 4. Fields To Keep In Strapi

### 4.1 Required Top-Level Fields

| Field | Type | Required | Notes |
|------|------|----------|------|
| `subProduct` | String | Yes | Filter key used by the app |
| `partner` | String | Yes | Filter key used by the app |
| `creditActivity` | Component | Yes | Credit activity content block |

### 4.2 Required `creditActivity` Fields

| Path | Required | Notes |
|------|----------|------|
| `creditActivity.sectionHeader` | Yes | Section title shown above the activity cards |
| `creditActivity.viewAllText` | Yes | Label for the view-all action |
| `creditActivity.visibleCardsCount` | Yes | Number of activity cards shown by default on dashboard |
| `creditActivity.payBillCTAText` | Yes | CTA label used for bill payment action |
| `creditActivity.viewDetailsCTAText` | Yes | CTA label used for details action |
| `creditActivity.repaymentTipText` | Yes | Informational repayment tip copy |
| `creditActivity.needHelp` | Yes | Need Help modal or bottom sheet content |

### 4.3 Required `creditActivity.needHelp` Fields

| Path | Required | Notes |
|------|----------|------|
| `creditActivity.needHelp.icon` | Yes | Media icon shown in the Need Help header |
| `creditActivity.needHelp.title` | Yes | Need Help heading |
| `creditActivity.needHelp.subtitle` | Yes | Need Help supporting copy |
| `creditActivity.needHelp.reasonPlaceholder` | Yes | Placeholder text for reason input or selector |
| `creditActivity.needHelp.continueButtonText` | Yes | Primary action label |
| `creditActivity.needHelp.reasonRequiredOptionId` | Yes | Option id that requires additional reason input |
| `creditActivity.needHelp.options` | Yes | Repeatable list of selectable help reasons |

### 4.4 Required `creditActivity.needHelp.options` Fields

| Path | Required | Notes |
|------|----------|------|
| `creditActivity.needHelp.options[].id` | Yes | Stable option identifier |
| `creditActivity.needHelp.options[].label` | Yes | Option label shown in the UI |
| `creditActivity.needHelp.options[].icon` | No | Optional media icon for the option |

---

## 7. Sample Values

### 7.1 `creditActivity`

```json
{
  "creditActivity": {
    "sectionHeader": "Your activity",
    "viewAllText": "View all",
    "visibleCardsCount": 3,
    "payBillCTAText": "Pay bill",
    "viewDetailsCTAText": "View details",
    "repaymentTipText": "Just a few payments away from improving your score",
    "needHelp": {
      "icon": "/uploads/alert_circle_filled.svg",
      "title": "NEED SOME HELP?",
      "subtitle": "Tell us more about it",
      "reasonPlaceholder": "Specify reason",
      "continueButtonText": "Continue",
      "reasonRequiredOptionId": "other",
      "options": [
        {
          "id": "missing-account",
          "label": "A Loan account/credit Card missing",
          "icon": "/uploads/account_icon.svg"
        },
        {
          "id": "not-mine",
          "label": "A Loan account/credit Card is not mine",
          "icon": "/uploads/user_icon.svg"
        },
        {
          "id": "incorrect-details",
          "label": "Details of the Loan/credit account is incorrect",
          "icon": "/uploads/information_outline.svg"
        },
        {
          "id": "other",
          "label": "Other",
          "icon": "/uploads/messenger_icon.svg"
        }
      ]
    }
  }
}
```

---

## 8. Expected API Response

```json
{
  "data": [
    {
      "id": 1,
      "subProduct": "credit",
      "partner": "default",
      "creditActivity": {
        "sectionHeader": "Your activity",
        "viewAllText": "View all",
        "visibleCardsCount": 3,
        "payBillCTAText": "Pay bill",
        "viewDetailsCTAText": "View details",
        "repaymentTipText": "Just a few payments away from improving your score",
        "needHelp": {
          "icon": {
            "url": "/uploads/alert_circle_filled.svg"
          },
          "title": "NEED SOME HELP?",
          "subtitle": "Tell us more about it",
          "reasonPlaceholder": "Specify reason",
          "continueButtonText": "Continue",
          "reasonRequiredOptionId": "other",
          "options": [
            {
              "id": "missing-account",
              "label": "A Loan account/credit Card missing",
              "icon": {
                "url": "/uploads/account_icon.svg"
              }
            },
            {
              "id": "not-mine",
              "label": "A Loan account/credit Card is not mine",
              "icon": {
                "url": "/uploads/user_icon.svg"
              }
            },
            {
              "id": "incorrect-details",
              "label": "Details of the Loan/credit account is incorrect",
              "icon": {
                "url": "/uploads/information_outline.svg"
              }
            },
            {
              "id": "other",
              "label": "Other",
              "icon": {
                "url": "/uploads/messenger_icon.svg"
              }
            }
          ]
        }
      }
    }
  ]
}
```

Important:

- The documented response above uses the same `tracks-dashboard-pages` API endpoint as the dashboard reference
- `creditActivity` is expected as a nested top-level component in the response
- `needHelp.options[]` should remain a repeatable array in the API response

---


## 10. Summary

| Category | Count |
|----------|-------|
| Core components in scope | 3 |
| Top-level fields in scope | 3 |
| Required `creditActivity` direct fields | 7 |
| Required `needHelp` direct fields | 7 |
| Required option item fields | 3 |
| Primary API endpoint | 1 |

---

**Owner:** Tracks Dashboard CMS
**Environment:** UAT / QA Strapi
**Reference App:** `abcd-tracks-web`