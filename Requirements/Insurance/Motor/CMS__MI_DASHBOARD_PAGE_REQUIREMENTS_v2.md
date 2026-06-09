# Insurance CMS Dashboard Page Requirements v1

**Date:** 2026-03-26  
**Purpose:** Sync UAT Strapi with LOCAL configuration for Insurance Dashboard Page

---

## Table of Contents
- [Insurance CMS Dashboard Page Requirements v1](#insurance-cms-dashboard-page-requirements-v1)
  - [Table of Contents](#table-of-contents)
  - [1. Dashboard Page Overview](#1-dashboard-page-overview)
  - [2. Component Requirements](#2-component-requirements)
    - [2.1 New Components](#21-new-components)
    - [2.2 Update Component](#22-update-component)
      - [exploreItems (Component Structure)](#exploreitems-component-structure)
  - [3. Sample Values](#3-sample-values)
    - [exploreItems](#exploreitems)
  - [4. Expected API Response](#4-expected-api-response)
  - [5. Summary](#5-summary)

---

## 1. Dashboard Page Overview

**Content Type:** `insurance-dashboard-page`  
**API Endpoint:** `GET /api/insurance-dashboard-pages?filters[subProduct][$eq]=motor&populate=*`


---

## 2. Component Requirements

### 2.1 New Components

| Component Name      | Type       | Description                            |
|--------------------|------------|----------------------------------------|
| `vehicleTrackExternalUrl`      | String| URL to navigate vehicle track      |

### 2.2 Update Component

#### exploreItems (Component Structure)
```
├── enabled (Boolean)
└── content (Repeatable)
    ├── order (Integer)
    ├── id (String)//itemid
    ├── title (String)
    ├── icon (String)
    ├── isExternal (Boolean, optional) //to be added
    └── externalUrl (String, optional)//need to be added
    
```

---

## 3. Sample Values

### exploreItems
```json
{
  "actionCards": {
    "enabled": true,
    "content": [
      {
        "order": 1,
        "id": "car",
        "title": "Car insurance",
        "subtitle": "Starts at just ₹1,999",
        "image": "${LANDING_ASSETS}/dashboard/insuranceCar.svg",
        "type": "car"
      },
      {
        "order": 2,
        "id": "bike",
        "title": "Bike insurance",
        "subtitle": "Starts at just ₹999",
        "image": "${LANDING_ASSETS}/dashboard/insuranceBike.svg",
        "type": "bike"
      }
    ]
  }
}
```

## 4. Expected API Response

```json
{
  "data": [
    {
      "id": 1,
      "subProduct": "motor",
      "vehicleTrackExternalUrl": "https://abcd.adityabirlacapital.com/vehicleTrackHome/",
      
      "exploreItems": {
        "enabled": true,
        "content": [
          {
            "order": 1,
            "id": "renew-policy",
            "title": "Renew instantly - Upload your policy",
            "icon": "${LANDING_ASSETS}/mobile-nav/icon-motor-insurance.png",
            "isExternal": true,
            "externalUrl": null
          },
          {
            "order": 2,
            "id": "policies",
            "title": "My Policies",
            "icon": "${LANDING_ASSETS}/mobile-nav/icon-pocket-insurance.png",
            "isExternal": true,
            "externalUrl": null
          },
          {
            "order": 3,
            "id": "track-insurance",
            "title": "Track insurance, challans, & more, all in one place.",
            "icon": "${LANDING_ASSETS}/mobile-nav/icon-vehicle-track.png",
            "isExternal": true,
            "externalUrl": "https://abcd.adityabirlacapital.com/vehicleTrackHome/"
          }
        ]
      },

      "navigation": {
        "id": 9,
        "enabled": true,
        "content": []
      }
    }
  ]
}
```

---

## 5. Summary

| Category         | Count |
|------------------|-------|
| New Components   | 1    |
| Update Components   | 1    |
| Sample Values    | 1    |
| API Response     | 1     |

---

**Contact:** Motor Insurance Dashboard Team  
**Environment:** UAT Strapi
