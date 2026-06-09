# Health Insurance AddonsData Strapi Reference

**Date:** 2026-06-05
**Purpose:** Reference document for Strapi configuration of `health-insurance-journey-page` for the Health Insurance add-ons flow in `abcd-insurance-orchestrator`.

---

## 1. Overview

**API Endpoint:**

```http
GET /api/health-insurance-journey-page?filters[partner][$eq]=default&populate=*
```
---

## 2. In Scope

This document covers the following CMS areas:

- `apply.addons`

These fields are consumed by the Health Insurance add-ons transformation and then used in the UI for:

- Add-on display type
- Add-on icon
- Add-on description
- Member sum insured options
- Nature of duty options
- Room type options
- Chronic add-on routing

---

## 3. Required Components

### 3.1 `health-insurance-journey-page`

Collection type for the Health Insurance journey page. The add-on CMS catalog must be added inside the existing `apply` field.

```text
health-insurance-journey-page
└── apply (Existing field/component)
  └── addons (Component: health-insurance-addons-config)
    ├── addonsData[] (Repeatable component: health-insurance-addon-content)
    └── ChronicDataList (JSON array of numbers)
```

### 3.2 `health-insurance-addons-config`

Component wrapper for the add-ons configuration.

```text
apply.addons
├── addonsData[] (Repeatable component: health-insurance-addon-content)
└── ChronicDataList (JSON array of numbers)
```

### 3.3 `health-insurance-addon-content`

Repeatable component for one add-on CMS item.

```text
apply.addons.addonsData[]
├── addonId (String) (required)
├── name (String) (required)
├── type (Enumeration) (required)
├── order (Number) (required)
├── description (Text) (required)
├── icon (Media)
└── formValues (Component: health-insurance-addon-form-values)
```

### 3.4 `health-insurance-addon-form-values`

Nested component for add-on option lists.

```text
formValues
├── memberSiValues (JSON array of strings)
├── natureOfDutyValues (JSON array of strings)
└── roomTypeValues (JSON array of strings)
```

Important:

- `apply` already exists on `health-insurance-journey-page`; add `addons` inside `apply`.
- `apply.addons` must be a component/object wrapper.
- `apply.addons.addonsData` must remain a repeatable component field/array and contains the current add-on catalog data.
- `apply.addons.ChronicDataList` must be a JSON array of numbers and contains add-on IDs that should trigger the chronic add-ons step when selected.
- `addonId` must be stored as a string because the orchestrator normalizes fetched add-on IDs to strings before matching.
- `order` must be stored as a number and is used by the orchestrator to sort `filteredAddonData` before the next step.
- `icon` should be a Strapi media field.
- Empty option lists should be returned as empty arrays, not `null`.

---

## 4. Fields To Keep In Strapi

### 4.1 Required Top-Level Fields

| Field | Type | Required | Notes |
|------|------|----------|------|
| `apply` | Existing field/component | Yes | Existing Health Insurance apply page content |
| `apply.addons` | Component/object | Yes | Health add-ons configuration wrapper |
| `apply.addons.addonsData` | Repeatable component | Yes | Current health add-on CMS catalog array |
| `apply.addons.ChronicDataList` | JSON array of numbers | Yes | Add-on IDs that should trigger the chronic add-ons flow when selected |

### 4.2 Required `apply.addons.addonsData[]` Fields

| Path | Type | Required | Notes |
|------|------|----------|------|
| `apply.addons.addonsData[].addonId` | String | Yes | Matched with ABHI add-on `addonId` |
| `apply.addons.addonsData[].name` | String | Yes | CMS display name and admin reference |
| `apply.addons.addonsData[].type` | Enumeration | Yes | Must use one of the allowed type values in section 5 |
| `apply.addons.addonsData[].order` | Number | Yes | Ascending display order used to sort transformed add-ons |
| `apply.addons.addonsData[].description` | Text | Yes | Display description for the add-on |
| `apply.addons.addonsData[].icon` | Media | No | Recommended; app fallback is `/insurance/icons/crosshair.svg` |
| `apply.addons.addonsData[].formValues` | Component | No | Required only for add-ons that need selectable options |

### 4.3 Required `formValues` Fields

| Path | Type | Required | Notes |
|------|------|----------|------|
| `apply.addons.addonsData[].formValues.memberSiValues` | JSON array of strings | No | Required for sum insured add-ons |
| `apply.addons.addonsData[].formValues.natureOfDutyValues` | JSON array of strings | No | Required for personal accident duty selection |
| `apply.addons.addonsData[].formValues.roomTypeValues` | JSON array of strings | No | Required for room rent type selection |

---

## 5. Allowed Type Values

`apply.addons.addonsData[].type` must be one of the following enum values:

| Type | UI behavior | Required form values |
|------|-------------|----------------------|
| `SINGLE_SELECT` | Add-on can be selected directly | None |
| `MEMBER_SELECT` | Add-on applies to selected members | None |
| `MEMBER_SUM_INSURED` | Member selection with sum insured dropdown | `memberSiValues` |
| `MEMBER_SUM_INSURED_DUTY` | Member selection with sum insured and nature of duty dropdowns | `memberSiValues`, `natureOfDutyValues` |
| `ROOM_RENT_SELECT` | Room type radio selection | `roomTypeValues` |

Important:

- Keep enum values uppercase exactly as documented.
- Do not use display labels like `Single select` or `Member Sum Insured` in the `type` field.

---

### 7.2 `apply.addons` Sample

```json
{
  "apply": {
    "addons": {
      "addonsData": [
        {
          "addonId": "30",
          "name": "Preferred Provider Network",
          "type": "SINGLE_SELECT",
          "order": 1,
          "description": "Get access to preferred provider network benefits as defined in the policy terms.",
          "icon": "/insurance/icons/network.svg",
          "formValues": {
            "memberSiValues": [],
            "natureOfDutyValues": [],
            "roomTypeValues": []
          }
        },
      {
        "addonId": "34",
        "name": "Room Rent Type",
        "type": "ROOM_RENT_SELECT",
        "order": 2,
        "description": "Choose the room type for in-patient hospitalization.",
        "icon": "/insurance/icons/room.svg",
        "formValues": {
          "memberSiValues": [],
          "natureOfDutyValues": [],
          "roomTypeValues": ["Single", "Shared", "Any"]
        }
      },
      {
        "addonId": "23",
        "name": "Tele OPD consultation",
        "type": "SINGLE_SELECT",
        "order": 3,
        "description": "Offers cover for tele-consultation from medical practitioners within ABHI network.",
        "icon": "/insurance/icons/crosshair.svg",
        "formValues": {
          "memberSiValues": [],
          "natureOfDutyValues": [],
          "roomTypeValues": []
        }
      },
      {
        "addonId": "10",
        "name": "Vaccine Cover",
        "type": "SINGLE_SELECT",
        "order": 4,
        "description": "Covers expenses for selected preventive vaccines.",
        "icon": "/insurance/icons/diamond.svg",
        "formValues": {
          "memberSiValues": [],
          "natureOfDutyValues": [],
          "roomTypeValues": []
        }
      },
      {
        "addonId": "12",
        "name": "Critical Illness Cover",
        "type": "MEMBER_SUM_INSURED",
        "order": 5,
        "description": "Get lump sum payout as defined in the policy document if diagnosed with a listed critical illness.",
        "icon": "/insurance/icons/fast-protection.svg",
        "formValues": {
          "memberSiValues": ["INR 500000", "INR 1000000", "INR 1500000"],
          "natureOfDutyValues": [],
          "roomTypeValues": []
        }
      },
      {
        "addonId": "11",
        "name": "Personal Accident Cover",
        "type": "MEMBER_SUM_INSURED_DUTY",
        "order": 6,
        "description": "Get financial protection against accidental death, permanent total disablement and permanent partial disability.",
        "icon": "/insurance/icons/briefcase.svg",
        "formValues": {
          "memberSiValues": ["INR 500000", "INR 1000000", "INR 1500000"],
          "natureOfDutyValues": [
            "Accountant",
            "Administrative Worker",
            "Business Owner",
            "Salaried",
            "Self-employed"
          ],
          "roomTypeValues": []
        }
      },
      {
        "addonId": "24",
        "name": "Durable Equipment Cover",
        "type": "SINGLE_SELECT",
        "order": 7,
        "description": "Covers eligible durable medical equipment expenses as per policy terms.",
        "icon": "/insurance/icons/health-plan.svg",
        "formValues": {
          "memberSiValues": [],
          "natureOfDutyValues": [],
          "roomTypeValues": []
        }
      },
      {
        "addonId": "25",
        "name": "Second Medical Opinion for listed Major Illness per person",
        "type": "SINGLE_SELECT",
        "order": 8,
        "description": "Provides a second medical opinion for listed major illnesses.",
        "icon": "/insurance/icons/help-red.svg",
        "formValues": {
          "memberSiValues": [],
          "natureOfDutyValues": [],
          "roomTypeValues": []
        }
      },
      {
        "addonId": "26",
        "name": "Annual Screening Package for Cancer Diagnosed Patients",
        "type": "SINGLE_SELECT",
        "order": 9,
        "description": "Adds an annual screening package for eligible cancer diagnosed patients.",
        "icon": "/insurance/icons/health-plan.svg",
        "formValues": {
          "memberSiValues": [],
          "natureOfDutyValues": [],
          "roomTypeValues": []
        }
      },
      {
        "addonId": "27",
        "name": "Compassionate Visit",
        "type": "SINGLE_SELECT",
        "order": 10,
        "description": "Covers eligible compassionate visit benefits as defined in the policy terms.",
        "icon": "/insurance/icons/hi-group.svg",
        "formValues": {
          "memberSiValues": [],
          "natureOfDutyValues": [],
          "roomTypeValues": []
        }
      },
      {
        "addonId": "28",
        "name": "Cancer Booster",
        "type": "SINGLE_SELECT",
        "order": 11,
        "description": "Adds extra protection for listed cancer-related benefits as per policy terms.",
        "icon": "/insurance/icons/fast-protection.svg",
        "formValues": {
          "memberSiValues": [],
          "natureOfDutyValues": [],
          "roomTypeValues": []
        }
      },
      {
        "addonId": "29",
        "name": "Per Claim Deductible",
        "type": "SINGLE_SELECT",
        "order": 12,
        "description": "Applies the selected deductible at claim level as per policy terms.",
        "icon": "/insurance/icons/information.svg",
        "formValues": {
          "memberSiValues": [],
          "natureOfDutyValues": [],
          "roomTypeValues": []
        }
      },
      {
        "addonId": "31",
        "name": "Chronic Care",
        "type": "SINGLE_SELECT",
        "order": 13,
        "description": "Get protection against listed chronic conditions from day one.",
        "icon": "/insurance/icons/chronicCare.svg",
        "formValues": {
          "memberSiValues": [],
          "natureOfDutyValues": [],
          "roomTypeValues": []
        }
      },
      {
        "addonId": "32",
        "name": "Chronic Management Program (OPD)",
        "type": "MEMBER_SELECT",
        "order": 14,
        "description": "Adds OPD-based chronic condition management benefits for selected insured members.",
        "icon": "/insurance/icons/opd.svg",
        "formValues": {
          "memberSiValues": [],
          "natureOfDutyValues": [],
          "roomTypeValues": []
        }
      }
      ],
      "ChronicDataList": [31, 32]
    }
  }
}
```