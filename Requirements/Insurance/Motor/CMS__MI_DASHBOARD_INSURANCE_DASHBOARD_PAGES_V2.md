# Insurance CMS Dashboard Page Requirements v1

**Date:** 2026-03-26  
**Purpose:** Sync UAT Strapi with LOCAL configuration for Insurance Dashboard Page

---

## Table of Contents
- [1. Dashboard Page Overview](#1-dashboard-page-overview)
- [2. Component Requirements](#1-component-requirements)
  - [2.1 Action Cards](action-cards)
- [3. Sample data](#3-sample-values)
- [4. Sample API Response](#4-expected-api-response)

---

## 1. Dashboard Page Overview

**Content Type:** `insurance-dashboard-page`  
**API Endpoint:** `GET /api/insurance-dashboard-pages?filters[subProduct][$eq]=motor&populate=*`


---

## 2. Component Requirements

### 2.1 New Components

| Component Name      | Type       | Description                            |
|--------------------|------------|----------------------------------------|
| `actionCards`      | Component| Action cards for insurance types       |
            

### 2.1 Action Cards

#### actionCards (Component Structure)
```
├── enabled (Boolean)
└── content (Repeatable)
    ├── order (Integer)
    ├── id (String)
    ├── title (String)
    ├── subtitle (String)
    ├── image (String)
    ├── type (String, e.g., "car", "bike")
    └── enabled (Boolean) - Control visibility per card type
```

## 3. Sample data

### actionCards
```json
{
  "actionCards": {
    "enabled": true,
    "content": [
      {
        "order": 1,
        "title": "Car insurance",
        "subtitle": "Starts at just ₹1,999",
        "image": "${LANDING_ASSETS}/dashboard/insuranceCar.svg",
        "type": "car",
        "enabled": true
      },
      {
        "order": 2,
        "title": "Bike insurance",
        "subtitle": "Starts at just ₹999",
        "image": "${LANDING_ASSETS}/dashboard/insuranceBike.svg",
        "type": "bike",
        "enabled": true
      }
    ]
  }
}
```



## 4. Sample API Response

```json
{
  "data": [
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
            "type": "car",
            "enabled": true
          },
          {
            "order": 2,
            "id": "bike",
            "title": "Bike insurance",
            "subtitle": "Starts at just ₹999",
            "image": "${LANDING_ASSETS}/dashboard/insuranceBike.svg",
            "type": "bike",
            "enabled": true
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


