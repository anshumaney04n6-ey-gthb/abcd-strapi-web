# Quote Buy Fallback CMS Requirements

---

**Date:** 2026-04-19
**Purpose:** Sync UAT Strapi with LOCAL configuration for Quote Buy fallback journey content

## Table of Contents

1. [Overview](#1-quote-buy-page-overview)
2. [Content Keys (Buy Flow)](#content-keys-buy-flow)
3. [Pages (Phase 1)](#pages-phase-1)
   - [Page - Capture Quote Plan](#page---capture-quote-plan)
   - [Page - Quote Plan Details](#page---quote-plan-details)
4. [Configurations](#configurations)
   - [Configuration - Insurers](#configuration---insurers)
   - [Configuration - Add-ons](#configuration---add-ons)
5. [Sample API Response](#sample-api-response)


---

## 1. Quote Buy Page Overview

**Content Type:** `insurance-journey-page`
**API Endpoint:** `GET /api/insurance-journey-pages?filters[$eq]=motor&populate=*`

---

## Content Keys (Buy Flow)

| Page Name | CMS Key | Fallback Constant | Content Type |
|-----------|---------|-------------------|-----------|
| Capture Quote Plan | `captureQuotePlan` | `DEFAULT_CAPTURE_QUOTE_PLAN_CONTENT` | page |
| Quote Plan Details | `quotePlanDetails` | `DEFAULT_QUOTE_PLAN_DETAILS_CONTENT` | page |
| Add-ons | `addOns`  | `DEFAULT_ADDONS_CONTENT` | configuration |
| Insurers | `insurers` | `DEFAULT_INSURER_DETAILS_CONTENT` | configuration |

---

## Pages (Phase 1)

### Page - Capture Quote Plan

**CMS Key:** `captureQuotePlan`
**Fallback Constant:** `DEFAULT_CAPTURE_QUOTE_PLAN_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (object)
    ├── title (String)
    ├── subtitle (String)
    ├── submitButtonText (String)
    ├── helpAriaLabel (String)
    ├── minIdv (Number)
    ├── maxIdv (Number)
    ├── notificationCount (Number)
    ├── pageId (String)
    ├── policyExpiryThresholdDays (Number)
    ├── quotePageIcons (Object)
    │   ├── networkGarages (String)
    │   ├── claimRatio (String)
    │   ├── footerBulbIcon (String)
    │   ├── checkWhite (String)
    │   ├── promoBannerPercentIcon (String)
    │   ├── promoBannerArrow (String)
    │   ├── retryIcon (String)
    │   ├── unlockIcon (String)
    │   ├── infoIcon (String)
    │   ├── closeCircle (String)
    │   ├── addOnIcon (String)
    │   ├── chevronUp (String)
    │   ├── chevronDown (String)
    │   └── payAsYouDriveIcon (String)
    ├── filters (Object)
    │   ├── policyType (Object)
    │   │   ├── label (String)
    │   │   ├── value (String)
    │   │   └── options (Array, Repeatable)
    │   │       ├── id (Number)
    │   │       ├── label (String)
    │   │       ├── value (String)
    │   │       ├── description (String)
    │   │       ├── isPopular (Boolean)
    │   │       ├── overview (String)
    │   │       ├── coveredItems (Array of Strings)
    │   │       └── notCoveredItems (Array of Strings)
    │   ├── idv (Object)
    │   │   ├── label (String)
    │   │   ├── value (String)
    │   │   └── options (Array, Repeatable)
    │   │       ├── label (String)
    │   │       └── value (String)
    │   └── sortBy (Object)
    │       ├── label (String)
    │       ├── value (String)
    │       └── options (Array, Repeatable)
    │           ├── label (String)
    │           └── value (String)
    ├── popularAddOns (Object)
    │   ├── title (String)
    │   └── items (Array, Repeatable)
    │       ├── id (String)
    │       ├── name (String)
    │       ├── label (String)
    │       ├── checked (Boolean)
    │       ├── logo (String)
    │       ├── description (String)
    │       └── minAmount (Number, Optional)
    ├── addOns (Array, Repeatable) - references DEFAULT_ADDONS_CONTENT
    └── insurers (Array, Repeatable) - references DEFAULT_INSURER_DETAILS_CONTENT
```

---

#### Sample JSON Data
```json
{
  "captureQuotePlan": {
    "enabled": true,
    "content": 
      {
        "title": "Select Plan",
        "subtitle": "Select the plan that best fits your needs and budget",
        "submitButtonText": "",
        "helpAriaLabel": "Get help with selecting an insurance plan",
        "minIdv": 370000,
        "maxIdv": 470000,
        "notificationCount": 13,
        "pageId": "1365",
        "policyExpiryThresholdDays": 7,
        "quotePageIcons": {
          "networkGarages": "${ASSETS_BASE}/motor/Icon.svg",
          "claimRatio": "${ASSETS_BASE}/motor/check-circle.svg",
          "footerBulbIcon": "${ASSETS_BASE}/motor/Icon-Bulb.svg",
          "checkWhite": "${ASSETS_BASE}/motor/check-white.svg",
          "promoBannerPercentIcon": "${ASSETS_BASE}/motor/percent.svg",
          "promoBannerArrow": "${ASSETS_BASE}/motor/chevron-right-circle.svg",
          "retryIcon": "${ASSETS_BASE}/motor/refresh.svg",
          "unlockIcon": "${ASSETS_BASE}/motor/percentage.webp",
          "infoIcon": "${ASSETS_BASE}/motor/info.webp",
          "closeCircle": "${ASSETS_BASE}/motor/unavailable.svg",
          "addOnIcon": "${ASSETS_BASE}/motor/shield-plus.svg",
          "chevronUp": "${ASSETS_BASE}/motor/chevron-up-red-circle.svg",
          "chevronDown": "${ASSETS_BASE}/motor/chevron-down-red-circle.svg",
          "payAsYouDriveIcon": "${ASSETS_BASE}/motor/road.svg"
        },
        "filters": {
          "policyType": {
            "label": "Policy Type",
            "value": "Comprehensive",
            "options": [
              {
                "id": 1,
                "label": "Own damage",
                "value": "own-damage",
                "description": "Covers your vehicle only. Choose if you already have an active Third-party policy",
                "isPopular": false,
                "overview": "This plan covers any damage done to your vehicle as well as damage done by you to any third-party vehicle or person.",
                "coveredItems": [
                  "Accidental damage to your car",
                  "Theft or total loss of the vehicle",
                  "Fire, explosion, or self‑ignition damage",
                  "Natural calamities (e.g., floods, earthquakes, storms)",
                  "Man‑made disasters (e.g., riots, strikes, vandalism)",
                  "Third‑party liability (injury, death, property damage)"
                ],
                "notCoveredItems": [
                  "Consequential losses (e.g., engine damage due to delay in repair)",
                  "Damage due to illegal racing or reckless driving",
                  "If policy is expired or not renewed on time",
                  "Regular wear and tear or depreciation",
                  "Mechanical or electrical breakdown",
                  "Driving under the influence of alcohol or drugs",
                  "Driving without a valid licence",
                  "Damage outside geographical coverage (e.g., outside India)"
                ]
              },
              {
                "id": 2,
                "label": "Comprehensive",
                "value": "comprehensive",
                "description": "Covers your vehicle and Mandatory liability cover for damage/injury to others. Best all-round protection",
                "isPopular": true,
                "overview": "This plan covers any damage done to your vehicle as well as damage done by you to any third-party vehicle or person.",
                "coveredItems": [
                  "Accidental damage to your car",
                  "Theft or total loss of the vehicle",
                  "Fire, explosion, or self‑ignition damage",
                  "Natural calamities (e.g., floods, earthquakes, storms)",
                  "Man‑made disasters (e.g., riots, strikes, vandalism)",
                  "Third‑party liability (injury, death, property damage)"
                ],
                "notCoveredItems": [
                  "Consequential losses (e.g., engine damage due to delay in repair)",
                  "Damage due to illegal racing or reckless driving",
                  "If policy is expired or not renewed on time",
                  "Regular wear and tear or depreciation",
                  "Mechanical or electrical breakdown",
                  "Driving under the influence of alcohol or drugs",
                  "Driving without a valid licence",
                  "Damage outside geographical coverage (e.g., outside India)"
                ]
              },
              {
                "id": 3,
                "label": "Third party",
                "value": "third-party",
                "description": "Mandatory liability cover for damage/injury to others. Doesn't cover your vehicle.",
                "isPopular": false,
                "overview": "This plan covers any damage done to your vehicle as well as damage done by you to any third-party vehicle or person.",
                "coveredItems": [
                  "Accidental damage to your car",
                  "Theft or total loss of the vehicle",
                  "Fire, explosion, or self‑ignition damage",
                  "Natural calamities (e.g., floods, earthquakes, storms)",
                  "Man‑made disasters (e.g., riots, strikes, vandalism)",
                  "Third‑party liability (injury, death, property damage)"
                ],
                "notCoveredItems": [
                  "Consequential losses (e.g., engine damage due to delay in repair)",
                  "Damage due to illegal racing or reckless driving",
                  "If policy is expired or not renewed on time",
                  "Regular wear and tear or depreciation",
                  "Mechanical or electrical breakdown",
                  "Driving under the influence of alcohol or drugs",
                  "Driving without a valid licence",
                  "Damage outside geographical coverage (e.g., outside India)"
                ]
              },
              {
                "id": 4,
                "label": "Pay as you drive",
                "value": "pay-as-you-drive",
                "description": "Pay lower premium based on the kilometres you actually drive",
                "isPopular": false,
                "overview": "This plan covers any damage done to your vehicle as well as damage done by you to any third-party vehicle or person.",
                "coveredItems": [
                  "Accidental damage to your car",
                  "Theft or total loss of the vehicle",
                  "Fire, explosion, or self‑ignition damage",
                  "Natural calamities (e.g., floods, earthquakes, storms)",
                  "Man‑made disasters (e.g., riots, strikes, vandalism)",
                  "Third‑party liability (injury, death, property damage)"
                ],
                "notCoveredItems": [
                  "Consequential losses (e.g., engine damage due to delay in repair)",
                  "Damage due to illegal racing or reckless driving",
                  "If policy is expired or not renewed on time",
                  "Regular wear and tear or depreciation",
                  "Mechanical or electrical breakdown",
                  "Driving under the influence of alcohol or drugs",
                  "Driving without a valid licence",
                  "Damage outside geographical coverage (e.g., outside India)"
                ]
              }
            ]
          },
          "idv": {
            "label": "IDV",
            "value": "Minimum",
            "options": [
              { "label": "Minimum", "value": "min" },
              { "label": "Recommended", "value": "recommended" },
              { "label": "Maximum", "value": "max" }
            ]
          },
          "sortBy": {
            "label": "Sort by",
            "value": "Claim settlement ratio",
            "options": [
              { "label": "Claim settlement ratio", "value": "claim-ratio" },
              { "label": "Premium (low to high)", "value": "premium-low-to-high" },
              { "label": "Premium (high to low)", "value": "premium-high-to-low" },
              { "label": "Network garages", "value": "network-garages" }
            ]
          }
        },
        "popularAddOns": {
          "title": "Popular add-ons",
          "items": [
            {
              "id": "4",
              "name": "Zero Depreciation",
              "label": "Zero dep",
              "checked": false,
              "logo": "",
              "description": "Zero depreciation cover"
            },
            {
              "id": "1",
              "name": "Personal Accident Cover",
              "label": "PA cover",
              "checked": false,
              "logo": "",
              "description": "Personal accident cover",
              "minAmount": 1500000
            }
          ]
        },
        "addOns": [],
        "insurers": []
      }
    
  }
}
```

---

### Page - Quote Plan Details

**CMS Key:** `quotePlanDetails`
**Fallback Constant:** `DEFAULT_QUOTE_PLAN_DETAILS_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (object)
    ├── order (Integer)
    ├── title (String)
    ├── policyYear (String)
    ├── vehicleIconSrc (String)
    ├── vehicleIconSrcBike (String)
    ├── helpAriaLabel (String)
    ├── showCreditScorePromo (Boolean)
    ├── promoText (String)
    ├── promoCtaText (String)
    ├── quotePlanDetailsIcons (Object)
        ├── networkGarages (String)
        ├── claimRatio (String)
        ├── roadsideAssistanceIcon (String, Optional)
        ├── creditScorePromoIconSrc (String, Optional)
        ├── creditScorePromoIconAlt (String, Optional)
        ├── creditScoreChevronIconSrc (String, Optional)
        ├── availabilityIcon (String, Optional)
        ├── availabilityIconAlt (String, Optional)
        ├── unlockIcon (String, Optional)
        ├── infoIcon (String, Optional)
        ├── creditScoreUnlockIconSrc (String, Optional)
        └── creditScoreUnlockIconAlt (String, Optional)

```

---

#### Sample JSON Data
```json
{
  "quotePlanDetails": {
    "enabled": true,
    "content": [
      {
        "order": 1,
        "title": "Select Plan",
        "policyYear": "1-yr plan",
        "vehicleIconSrc": "${ASSETS_BASE}/landing/motor/car-side.svg",
        "vehicleIconSrcBike": "${ASSETS_BASE}/landing/motor/motorbike.svg",
        "helpAriaLabel": "Get help with quote plan details",
        "showCreditScorePromo": false,
        "promoText": "Save more on car insurance with a good credit score",
        "promoCtaText": "Check now",
        "quotePlanDetailsIcons": {
          "networkGarages": "${ASSETS_BASE}/motor/Icon.svg",
          "claimRatio": "${ASSETS_BASE}/motor/check-circle.svg",
          "roadsideAssistanceIcon": "${ASSETS_BASE}/motor/tow-truck.svg",
          "creditScorePromoIconSrc": "${ASSETS_BASE}/motor/percent.svg",
          "creditScorePromoIconAlt": "Credit Score",
          "creditScoreChevronIconSrc": "${ASSETS_BASE}/motor/chevron-right-circle.webp",
          "availabilityIcon": "${ASSETS_BASE}/vehicle-insurance/information.svg",
          "availabilityIconAlt": "Information",
          "unlockIcon": "${ASSETS_BASE}/motor/percentage.webp",
          "infoIcon": "${ASSETS_BASE}/vehicle-insurance/information.svg",
          "creditScoreUnlockIconSrc": "${ASSETS_BASE}/motor/percentage.webp",
          "creditScoreUnlockIconAlt": "Unlock savings"
        },
      }
    ]
  }
}
```

---

### Configuration - Insurers

**CMS Key:** `insurers`
**Fallback Constant:** `DEFAULT_INSURER_DETAILS_CONTENT`

#### Component Structure
```

├── enabled (Boolean)
└── content (object)
    ├── order (Integer)
    ├── insurers (Array, Repeatable)
    ├── insurerId (String)
    ├── insurerLogo (String)
    ├── insurerName (String)
    ├── idvAmount (Number)
    ├── buttonText (String)
    ├── isPopular (Boolean)
    ├── networkGarages (Number)
    ├── claimRatio (Number)
    ├── isPayAsYouDriveEnabled (Boolean)
    ├── showCreditScorePromo (Boolean, Optional)
    ├── kmsAllowed (Array of Numbers, Optional)
    ├── idvDescription (String, Optional)
    └── addonsSection (Object)
        ├── icon (Object)
        │   ├── src (String)
        │   ├── alt (String)
        │   └── style (Object)
        │       ├── width (Number)
        │       └── height (Number)
        ├── availableCount (Number)
        ├── totalCount (Number)
        ├── toggleLabel (String)
        ├── hideLabel (String)
        ├── isExpanded (Boolean)
        ├── available (Array, Repeatable)
        │   ├── id (String)
        │   ├── label (String)
        │   └── price (Number)
        └── unavailable (Array, Repeatable)
            ├── id (String)
            └── label (String)
```

#### Sample JSON Data
```json
{
  "insurers": {
    "enabled": true,
    "content": [
      {
        "order": 1,
        "insurers": [
          {
            "insurerId": "1",
            "insurerLogo": "${ASSETS_BASE}/motor/acko-icon.svg",
            "insurerName": "Acko",
            "idvAmount": 420000,
            "buttonText": "₹8,245",
            "isPopular": false,
            "networkGarages": 100,
            "claimRatio": 78,
            "isPayAsYouDriveEnabled": false,
            "showCreditScorePromo": false,
            "addonsSection": {
              "icon": {
                "src": "${ASSETS_BASE}/motor/shield-plus.svg",
                "alt": "",
                "style": { "width": 20, "height": 20 }
              },
              "availableCount": 3,
              "totalCount": 4,
              "toggleLabel": "add-ons available",
              "hideLabel": "Hide",
              "isExpanded": true,
              "available": [
                { "id": "zero-dep", "label": "Zero depreciation", "price": 4580 },
                { "id": "engine-protect", "label": "Engine protection", "price": 2200 },
                { "id": "roadside", "label": "24x7 roadside assistance", "price": 1450 }
              ],
              "unavailable": [
                { "id": "tyre-protect", "label": "Tyre protection" }
              ]
            }
          },
          {
             "insurerId": "2",
            "insurerLogo": "${ASSETS_BASE}/motor/icici.svg",
             "insurerName": "ICICI Lombard",
             "idvAmount": 420000,
             "buttonText": "₹8,245",
             "isPopular": true,
             "networkGarages": 100,
             "claimRatio": 78,
            "idvDescription": "IDV (Insured Declared Value) is your vehicle's current market value and the maximum payout for theft or total loss. It's based on the manufacturer's listed price (plus accessories) at policy start, adjusted for depreciation.",
             "showCreditScorePromo": true,
             "isPayAsYouDriveEnabled": true,
             "kmsAllowed": [5000, 7500],
             "addonsSection": {
              "icon": {
                "src": "${ASSETS_BASE}/motor/shield-plus.svg",
                "alt": "",
                "style": { "width": 20, "height": 20 }
              },
              "availableCount": 3,
              "totalCount": 4,
              "toggleLabel": "add-ons available",
              "hideLabel": "Hide",
              "isExpanded": true,
              "available": [
                { "id": "zero-dep", "label": "Zero depreciation", "price": 4580 },
                { "id": "engine-protect", "label": "Engine protection", "price": 2200 },
                { "id": "roadside", "label": "24x7 roadside assistance", "price": 1450 }
              ],
              "unavailable": [
                { "id": "tyre-protect", "label": "Tyre protection" }
              ]
            }
          },
          {
            "insurerId": "3",
            "insurerLogo": "${ASSETS_BASE}/motor/digit-icon.svg",
            "insurerName": "Digit",
            "idvAmount": 420000,
            "buttonText": "₹8,455",
            "isPopular": false,
            "networkGarages": 150,
            "claimRatio": 82,
            "isPayAsYouDriveEnabled": true,
            "kmsAllowed": [5000, 7500],
            "addonsSection": {
              "icon": {
                "src": "${ASSETS_BASE}/motor/shield-plus.svg",
                "alt": "",
                "style": { "width": 20, "height": 20 }
              },
              "availableCount": 4,
              "totalCount": 4,
              "toggleLabel": "add-ons available",
              "hideLabel": "Hide",
              "isExpanded": true,
              "available": [
                { "id": "zero-dep", "label": "Zero depreciation", "price": 4680 },
                { "id": "engine-protect", "label": "Engine protection", "price": 2300 },
                { "id": "roadside", "label": "24x7 roadside assistance", "price": 1550 },
                { "id": "key-replacement", "label": "Key replacement", "price": 850 }
              ],
              "unavailable": []
            }
          },
          {
            "insurerId": "4",
            "insurerLogo": "${ASSETS_BASE}/motor/tata-AIG.svg",
            "insurerName": "TATA AIG",
            "idvAmount": 420000,
            "buttonText": "₹8,345",
            "isPopular": false,
            "networkGarages": 120,
            "claimRatio": 75,
            "isPayAsYouDriveEnabled": false,
            "addonsSection": {
              "icon": {
                "src": "${ASSETS_BASE}/motor/shield-plus.svg",
                "alt": "",
                "style": { "width": 20, "height": 20 }
              },
              "availableCount": 3,
              "totalCount": 5,
              "toggleLabel": "add-ons available",
              "hideLabel": "Hide",
              "isExpanded": true,
              "available": [
                { "id": "zero-dep", "label": "Zero depreciation", "price": 4480 },
                { "id": "engine-protect", "label": "Engine protection", "price": 2150 },
                { "id": "roadside", "label": "24x7 roadside assistance", "price": 1350 }
              ],
              "unavailable": [
                { "id": "tyre-protect", "label": "Tyre protection" },
                { "id": "consumables", "label": "Consumables cover" }
              ]
            }
          }
        ]
      }
    ]
  }
}
```

---

### Configuration - Add-ons

**CMS Key:** `addOns`
**Fallback Constant:** `DEFAULT_ADDONS_CONTENT`

#### Component Structure
```
├── enabled (Boolean)
└── content (Array, Repeatable)
    ├── order (Integer)
    └── addOns (Array, Repeatable)
        ├── id (Integer)
        ├── name (String)
        ├── logo (String)
        ├── isMandatory (Boolean)
        ├── isPopular (Boolean)
        ├── description (String)
        ├── isInputRequired (Boolean)
        ├── inputType (String, Optional)
        ├── minAmount (Number, Optional)
        ├── maxAmount (Number, Optional)
        ├── isAmountLocked (Boolean, Optional)
        ├── dropdownOptions (Array, Optional)
        │   ├── id (String)
        │   ├── label (String)
        │   └── value (Number)
        └── checked (Boolean)
```

#### Sample JSON Data
```json
{
  "addOns": {
    "enabled": true,
    "content": [
      {
        "order": 1,
        "addOns": [
          {
            "id": 1,
            "name": "Personal Accident Cover",
            "logo": "${ASSETS_BASE}/motor/shield-check.svg",
            "isMandatory": true,
            "isPopular": false,
            "description": "A personal accident or PA cover is an add-on that provides financial protection in case of accidental injury or death.\n\nYou can opt out if:\na) The car is registered in a company's name.\n\nb) You already have a PA cover of 15 lakhs. (from any other vehicle owned by you or from a separate standalone PA Cover Policy).\n\nc) Registered Owner of the vehicle does not have a valid driving license.",
            "isInputRequired": true,
            "minAmount": 1500000,
            "maxAmount": 1500000,
            "isAmountLocked": true,
            "checked": false
          },
          {
            "id": 2,
            "name": "Passenger Cover",
            "logo": "${ASSETS_BASE}/motor/account-group.svg",
            "isMandatory": false,
            "isPopular": false,
            "description": "This Covers all the passengers (maximum 3) of your car in case of death or disability due to an accident. Important to note that no other person can avail of those financial benefits even if they are paid to drive the insured car.",
            "isInputRequired": true,
            "inputType": "dropdown",
            "minAmount": 100000,
            "maxAmount": 1000000,
            "dropdownOptions": [
              {
                "id": "100000",
                "label": "₹1,00,000",
                "value": 100000
              },
              {
                "id": "200000",
                "label": "₹2,00,000",
                "value": 200000
              },
              {
                "id": "300000",
                "label": "₹3,00,000",
                "value": 300000
              },
              {
                "id": "500000",
                "label": "₹5,00,000",
                "value": 500000
              },
              {
                "id": "1000000",
                "label": "₹10,00,000",
                "value": 1000000
              }
            ],
            "checked": false
          },
          {
            "id": 3,
            "name": "Driver Cover",
            "logo": "${ASSETS_BASE}/motor/account-circle.svg",
            "isMandatory": false,
            "isPopular": false,
            "description": "This Covers the paid driver of your car in case of death or disability due to an accident. Important to note that no other person can avail of those financial benefits even if they are paid to drive the insured car.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "id": 4,
            "name": "Zero Depreciation",
            "logo": "${ASSETS_BASE}/motor/shield-car.svg",
            "isMandatory": false,
            "isPopular": true,
            "description": "The Zero Depreciation Cover, also known as bumper-to-bumper cover or Nil Depreciation cover, is an add-on feature designed to provide coverage for the full value of your vehicle without deducting the depreciating value of the vehicle.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "id": 5,
            "name": "Roadside Assistance",
            "logo": "${ASSETS_BASE}/motor/tow-truck-black.svg",
            "isMandatory": false,
            "isPopular": false,
            "description": "The 24×7 roadside assistance cover provides policyholders with valuable assistance in case their vehicle breaks down or faces any mechanical or electrical failure while on the road. This cover offers a range of services such as emergency fuel delivery, battery jump start, flat tyre change, towing facility, etc.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "id": 6,
            "name": "Consumables",
            "logo": "${ASSETS_BASE}/motor/barrel.svg",
            "isMandatory": false,
            "isPopular": false,
            "description": "Consumables cover is an add-on that offers coverage for the cost of replacing consumable items that need to be frequently or periodically replaced, such as engine oil, coolant, brake oil, power steering oil, etc which are not covered under standard motor insurance policy.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "id": 7,
            "name": "Engine Protection",
            "logo": "${ASSETS_BASE}/motor/engine.svg",
            "isMandatory": false,
            "isPopular": false,
            "description": "A standard comprehensive motor insurance policy may not cover certain damages such as malfunction of the engine, water ingression, and leakage of lubricant oil or hydrostatic lock but an Engine Protection cover is particularly useful for those who live in areas that are prone to flooding or waterlogging, as these can cause significant damage to the engine.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "id": 8,
            "name": "NCB Protection",
            "logo": "${ASSETS_BASE}/icons/check-decagram.svg",
            "isMandatory": false,
            "isPopular": false,
            "description": "A No Claim Bonus Protection cover protects the NCB of your vehicle even if you raise a claim. It keeps the NCB amount intact even if you raise a claim in the previous policy year.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "id": 9,
            "name": "Return to Invoice",
            "logo": "${ASSETS_BASE}/motor/script-text.svg",
            "isMandatory": false,
            "isPopular": false,
            "description": "Invoice cover or Return to Invoice (RTI) is an add-on that covers the gap between IDV and the invoice price of your vehicle.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "id": 10,
            "name": "Key Protection",
            "logo": "${ASSETS_BASE}/motor/shield-key.svg",
            "isMandatory": false,
            "isPopular": false,
            "description": "This add-on covers any expense in case of damaged lock or lost keys. It also covers the cost of replacing locks and keys in the event of attempted theft or break-in.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "id": 11,
            "name": "Loss of Personal Belonging",
            "logo": "${ASSETS_BASE}/motor/bag-personal.svg",
            "isMandatory": false,
            "isPopular": false,
            "description": "Loss of personal belongings cover is an add-on which will cover for the loss of any personal items from the insured car, inside or with the car. It covers various personal items including electronic equipments.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "id": 12,
            "name": "Tyre Protect",
            "logo": "${ASSETS_BASE}/motor/tire.svg",
            "isMandatory": false,
            "isPopular": false,
            "description": "Tyre Protection add-on covers any expenses incurred towards the repair or replacement of the tyre/s of the insured car which is otherwise not covered in the normal insurance policy.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "id": 13,
            "name": "Fire & Theft Cover",
            "logo": "${ASSETS_BASE}/motor/fire-circle.svg",
            "isMandatory": false,
            "isPopular": false,
            "description": "A third-party fire and theft insurance policy safeguards you against potential damages caused to others and shields your vehicle in the unfortunate events of fire or theft.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "id": 14,
            "name": "Non-electrical accessories",
            "logo": "${ASSETS_BASE}/motor/toolbox.svg",
            "isMandatory": false,
            "isPopular": false,
            "description": "This add-on covers any extra fitted non-electrical accessories in the vehicle.",
            "isInputRequired": true,
            "minAmount": 1000,
            "maxAmount": 100000,
            "checked": false
          },
          {
            "id": 15,
            "name": "Electrical accessories",
            "logo": "${ASSETS_BASE}/motor/battery-charging.svg",
            "isMandatory": false,
            "isPopular": false,
            "description": "This add-on covers any extra fitted electrical accessories in the vehicle.",
            "isInputRequired": true,
            "minAmount": 1000,
            "maxAmount": 100000,
            "checked": false
          }
        ]
      }
    ]
  }
}
```

---

## Sample API Response

**Endpoint:** `GET /api/insurance-buy-pages?filters[subProduct][$eq]=motor&populate=*`

```json
{
  "data": [
    {
      "captureQuotePlan": {
        "enabled": true,
        "content": 
          {
            "title": "Select Plan",
            "subtitle": "Select the plan that best fits your needs and budget",
            "submitButtonText": "",
            "helpAriaLabel": "Get help with selecting an insurance plan",
            "minIdv": 370000,
            "maxIdv": 470000,
            "notificationCount": 13,
            "pageId": "1365",
            "policyExpiryThresholdDays": 7,
            "quotePageIcons": {
              "networkGarages": "${ASSETS_BASE}/motor/Icon.svg",
              "claimRatio": "${ASSETS_BASE}/motor/check-circle.svg",
              "footerBulbIcon": "${ASSETS_BASE}/motor/Icon-Bulb.svg",
              "checkWhite": "${ASSETS_BASE}/motor/check-white.svg",
              "promoBannerPercentIcon": "${ASSETS_BASE}/motor/percent.svg",
              "promoBannerArrow": "${ASSETS_BASE}/motor/chevron-right-circle.svg",
              "retryIcon": "${ASSETS_BASE}/motor/refresh.svg",
              "unlockIcon": "${ASSETS_BASE}/motor/percentage.webp",
              "infoIcon": "${ASSETS_BASE}/motor/info.webp",
              "closeCircle": "${ASSETS_BASE}/motor/unavailable.svg",
              "addOnIcon": "${ASSETS_BASE}/motor/shield-plus.svg",
              "chevronUp": "${ASSETS_BASE}/motor/chevron-up-red-circle.svg",
              "chevronDown": "${ASSETS_BASE}/motor/chevron-down-red-circle.svg",
              "payAsYouDriveIcon": "${ASSETS_BASE}/motor/road.svg"
            },
            "filters": {
              "policyType": {
                "label": "Policy Type",
                "value": "Comprehensive",
                "options": [
                  {
                    "id": 1,
                    "label": "Own damage",
                    "value": "own-damage",
                    "description": "Covers your vehicle only. Choose if you already have an active Third-party policy",
                    "isPopular": false,
                    "overview": "This plan covers any damage done to your vehicle as well as damage done by you to any third-party vehicle or person.",
                    "coveredItems": [
                      "Accidental damage to your car",
                      "Theft or total loss of the vehicle",
                      "Fire, explosion, or self‑ignition damage",
                      "Natural calamities (e.g., floods, earthquakes, storms)",
                      "Man‑made disasters (e.g., riots, strikes, vandalism)",
                      "Third‑party liability (injury, death, property damage)"
                    ],
                    "notCoveredItems": [
                      "Consequential losses (e.g., engine damage due to delay in repair)",
                      "Damage due to illegal racing or reckless driving",
                      "If policy is expired or not renewed on time",
                      "Regular wear and tear or depreciation",
                      "Mechanical or electrical breakdown",
                      "Driving under the influence of alcohol or drugs",
                      "Driving without a valid licence",
                      "Damage outside geographical coverage (e.g., outside India)"
                    ]
                  },
                  {
                    "id": 2,
                    "label": "Comprehensive",
                    "value": "comprehensive",
                    "description": "Covers your vehicle and Mandatory liability cover for damage/injury to others. Best all-round protection",
                    "isPopular": true,
                    "overview": "This plan covers any damage done to your vehicle as well as damage done by you to any third-party vehicle or person.",
                    "coveredItems": [
                      "Accidental damage to your car",
                      "Theft or total loss of the vehicle",
                      "Fire, explosion, or self‑ignition damage",
                      "Natural calamities (e.g., floods, earthquakes, storms)",
                      "Man‑made disasters (e.g., riots, strikes, vandalism)",
                      "Third‑party liability (injury, death, property damage)"
                    ],
                    "notCoveredItems": [
                      "Consequential losses (e.g., engine damage due to delay in repair)",
                      "Damage due to illegal racing or reckless driving",
                      "If policy is expired or not renewed on time",
                      "Regular wear and tear or depreciation",
                      "Mechanical or electrical breakdown",
                      "Driving under the influence of alcohol or drugs",
                      "Driving without a valid licence",
                      "Damage outside geographical coverage (e.g., outside India)"
                    ]
                  },
                  {
                    "id": 3,
                    "label": "Third party",
                    "value": "third-party",
                    "description": "Mandatory liability cover for damage/injury to others. Doesn't cover your vehicle.",
                    "isPopular": false,
                    "overview": "This plan covers any damage done to your vehicle as well as damage done by you to any third-party vehicle or person.",
                    "coveredItems": [
                      "Accidental damage to your car",
                      "Theft or total loss of the vehicle",
                      "Fire, explosion, or self‑ignition damage",
                      "Natural calamities (e.g., floods, earthquakes, storms)",
                      "Man‑made disasters (e.g., riots, strikes, vandalism)",
                      "Third‑party liability (injury, death, property damage)"
                    ],
                    "notCoveredItems": [
                      "Consequential losses (e.g., engine damage due to delay in repair)",
                      "Damage due to illegal racing or reckless driving",
                      "If policy is expired or not renewed on time",
                      "Regular wear and tear or depreciation",
                      "Mechanical or electrical breakdown",
                      "Driving under the influence of alcohol or drugs",
                      "Driving without a valid licence",
                      "Damage outside geographical coverage (e.g., outside India)"
                    ]
                  },
                  {
                    "id": 4,
                    "label": "Pay as you drive",
                    "value": "pay-as-you-drive",
                    "description": "Pay lower premium based on the kilometres you actually drive",
                    "isPopular": false,
                    "overview": "This plan covers any damage done to your vehicle as well as damage done by you to any third-party vehicle or person.",
                    "coveredItems": [
                      "Accidental damage to your car",
                      "Theft or total loss of the vehicle",
                      "Fire, explosion, or self‑ignition damage",
                      "Natural calamities (e.g., floods, earthquakes, storms)",
                      "Man‑made disasters (e.g., riots, strikes, vandalism)",
                      "Third‑party liability (injury, death, property damage)"
                    ],
                    "notCoveredItems": [
                      "Consequential losses (e.g., engine damage due to delay in repair)",
                      "Damage due to illegal racing or reckless driving",
                      "If policy is expired or not renewed on time",
                      "Regular wear and tear or depreciation",
                      "Mechanical or electrical breakdown",
                      "Driving under the influence of alcohol or drugs",
                      "Driving without a valid licence",
                      "Damage outside geographical coverage (e.g., outside India)"
                    ]
                  }
                ]
              },
              "idv": {
                "label": "IDV",
                "value": "Minimum",
                "options": [
                  { "label": "Minimum", "value": "min" },
                  { "label": "Recommended", "value": "recommended" },
                  { "label": "Maximum", "value": "max" }
                ]
              },
              "sortBy": {
                "label": "Sort by",
                "value": "Claim settlement ratio",
                "options": [
                  { "label": "Claim settlement ratio", "value": "claim-ratio" },
                  { "label": "Premium (low to high)", "value": "premium-low-to-high" },
                  { "label": "Premium (high to low)", "value": "premium-high-to-low" },
                  { "label": "Network garages", "value": "network-garages" }
                ]
              }
            },
            "popularAddOns": {
              "title": "Popular add-ons",
              "items": [
                {
                  "id": "4",
                  "name": "Zero Depreciation",
                  "label": "Zero dep",
                  "checked": false,
                  "logo": "",
                  "description": "Zero depreciation cover"
                },
                {
                  "id": "1",
                  "name": "Personal Accident Cover",
                  "label": "PA cover",
                  "checked": false,
                  "logo": "",
                  "description": "Personal accident cover",
                  "minAmount": 1500000
                }
              ]
            },
         } 
       ]
      },
      "quotePlanDetails": {
        "enabled": true,
        "content": [
          {
            "order": 1,
            "title": "Select Plan",
            "policyYear": "1-yr plan",
            "vehicleIconSrc": "${ASSETS_BASE}/landing/motor/car-side.svg",
            "vehicleIconSrcBike": "${ASSETS_BASE}/landing/motor/motorbike.svg",
            "helpAriaLabel": "Get help with quote plan details",
            "showCreditScorePromo": false,
            "promoText": "Save more on car insurance with a good credit score",
            "promoCtaText": "Check now",
            "quotePlanDetailsIcons": {
              "networkGarages": "${ASSETS_BASE}/motor/Icon.svg",
              "claimRatio": "${ASSETS_BASE}/motor/check-circle.svg",
              "roadsideAssistanceIcon": "${ASSETS_BASE}/motor/tow-truck.svg",
              "creditScorePromoIconSrc": "${ASSETS_BASE}/motor/percent.svg",
              "creditScorePromoIconAlt": "Credit Score",
              "creditScoreChevronIconSrc": "${ASSETS_BASE}/motor/chevron-right-circle.webp",
              "availabilityIcon": "${ASSETS_BASE}/vehicle-insurance/information.svg",
              "availabilityIconAlt": "Information",
              "unlockIcon": "${ASSETS_BASE}/motor/percentage.webp",
              "infoIcon": "${ASSETS_BASE}/vehicle-insurance/information.svg",
              "creditScoreUnlockIconSrc": "${ASSETS_BASE}/motor/percentage.webp",
              "creditScoreUnlockIconAlt": "Unlock savings"
            },
          }
        ]
      },
      "insurers": {
        "enabled": true,
        "content": [
          {
            "order": 1,
            "insurers": [
              {
                "insurerId": "1",
                "insurerLogo": "${ASSETS_BASE}/motor/acko-icon.svg",
                "insurerName": "Acko",
                "idvAmount": 420000,
                "buttonText": "₹8,245",
                "isPopular": false,
                "networkGarages": 100,
                "claimRatio": 78,
                "isPayAsYouDriveEnabled": false,
                "showCreditScorePromo": false,
                "addonsSection": {
                  "icon": {
                    "src": "${ASSETS_BASE}/motor/shield-plus.svg",
                    "alt": "",
                    "style": { "width": 20, "height": 20 }
                  },
                  "availableCount": 3,
                  "totalCount": 4,
                  "toggleLabel": "add-ons available",
                  "hideLabel": "Hide",
                  "isExpanded": true,
                  "available": [
                    { "id": "zero-dep", "label": "Zero depreciation", "price": 4580 },
                    { "id": "engine-protect", "label": "Engine protection", "price": 2200 },
                    { "id": "roadside", "label": "24x7 roadside assistance", "price": 1450 }
                  ],
                  "unavailable": [
                    { "id": "tyre-protect", "label": "Tyre protection" }
                  ]
                }
              },
              {
                "insurerId": "2",
                "insurerLogo": "${ASSETS_BASE}/motor/icici.svg",
                "insurerName": "ICICI Lombard",
                "idvAmount": 420000,
                "buttonText": "₹8,245",
                "isPopular": true,
                "networkGarages": 100,
                "claimRatio": 78,
                "idvDescription": "IDV (Insured Declared Value) is your vehicle's current market value and the maximum payout for theft or total loss. It's based on the manufacturer's listed price (plus accessories) at policy start, adjusted for depreciation.",
                "showCreditScorePromo": true,
                "isPayAsYouDriveEnabled": true,
                "kmsAllowed": [5000, 7500],
                "addonsSection": {
                  "icon": {
                    "src": "${ASSETS_BASE}/motor/shield-plus.svg",
                    "alt": "",
                    "style": { "width": 20, "height": 20 }
                  },
                  "availableCount": 3,
                  "totalCount": 4,
                  "toggleLabel": "add-ons available",
                  "hideLabel": "Hide",
                  "isExpanded": true,
                  "available": [
                    { "id": "zero-dep", "label": "Zero depreciation", "price": 4580 },
                    { "id": "engine-protect", "label": "Engine protection", "price": 2200 },
                    { "id": "roadside", "label": "24x7 roadside assistance", "price": 1450 }
                  ],
                  "unavailable": [
                    { "id": "tyre-protect", "label": "Tyre protection" }
                  ]
                }
              },
              {
                "insurerId": "3",
                "insurerLogo": "${ASSETS_BASE}/motor/digit-icon.svg",
                "insurerName": "Digit",
                "idvAmount": 420000,
                "buttonText": "₹8,455",
                "isPopular": false,
                "networkGarages": 150,
                "claimRatio": 82,
                "isPayAsYouDriveEnabled": true,
                "kmsAllowed": [5000, 7500],
                "addonsSection": {
                  "icon": {
                    "src": "${ASSETS_BASE}/motor/shield-plus.svg",
                    "alt": "",
                    "style": { "width": 20, "height": 20 }
                  },
                  "availableCount": 4,
                  "totalCount": 4,
                  "toggleLabel": "add-ons available",
                  "hideLabel": "Hide",
                  "isExpanded": true,
                  "available": [
                    { "id": "zero-dep", "label": "Zero depreciation", "price": 4680 },
                    { "id": "engine-protect", "label": "Engine protection", "price": 2300 },
                    { "id": "roadside", "label": "24x7 roadside assistance", "price": 1550 },
                    { "id": "key-replacement", "label": "Key replacement", "price": 850 }
                  ],
                  "unavailable": []
                }
              },
              {
                "insurerId": "4",
                "insurerLogo": "${ASSETS_BASE}/motor/tata-AIG.svg",
                "insurerName": "TATA AIG",
                "idvAmount": 420000,
                "buttonText": "₹8,345",
                "isPopular": false,
                "networkGarages": 120,
                "claimRatio": 75,
                "isPayAsYouDriveEnabled": false,
                "addonsSection": {
                  "icon": {
                    "src": "${ASSETS_BASE}/motor/shield-plus.svg",
                    "alt": "",
                    "style": { "width": 20, "height": 20 }
                  },
                  "availableCount": 3,
                  "totalCount": 5,
                  "toggleLabel": "add-ons available",
                  "hideLabel": "Hide",
                  "isExpanded": true,
                  "available": [
                    { "id": "zero-dep", "label": "Zero depreciation", "price": 4480 },
                    { "id": "engine-protect", "label": "Engine protection", "price": 2150 },
                    { "id": "roadside", "label": "24x7 roadside assistance", "price": 1350 }
                  ],
                  "unavailable": [
                    { "id": "tyre-protect", "label": "Tyre protection" },
                    { "id": "consumables", "label": "Consumables cover" }
                  ]
                }
              }
            ]
          }
        ]
      },
      "addOns": {
        "enabled": true,
        "content": [
          {
            "order": 1,
            "addOns": [
              {
                "id": 1,
                "name": "Personal Accident Cover",
                "logo": "${ASSETS_BASE}/motor/shield-check.svg",
                "isMandatory": true,
                "isPopular": false,
                "description": "A personal accident or PA cover is an add-on that provides financial protection in case of accidental injury or death.\n\nYou can opt out if:\na) The car is registered in a company's name.\n\nb) You already have a PA cover of 15 lakhs. (from any other vehicle owned by you or from a separate standalone PA Cover Policy).\n\nc) Registered Owner of the vehicle does not have a valid driving license.",
                "isInputRequired": true,
                "minAmount": 1500000,
                "maxAmount": 1500000,
                "isAmountLocked": true,
                "checked": false
              },
              {
                "id": 2,
                "name": "Passenger Cover",
                "logo": "${ASSETS_BASE}/motor/account-group.svg",
                "isMandatory": false,
                "isPopular": false,
                "description": "This Covers all the passengers (maximum 3) of your car in case of death or disability due to an accident. Important to note that no other person can avail of those financial benefits even if they are paid to drive the insured car.",
                "isInputRequired": true,
                "inputType": "dropdown",
                "minAmount": 100000,
                "maxAmount": 1000000,
                "dropdownOptions": [
                  {
                    "id": "100000",
                    "label": "₹1,00,000",
                    "value": 100000
                  },
                  {
                    "id": "200000",
                    "label": "₹2,00,000",
                    "value": 200000
                  },
                  {
                    "id": "300000",
                    "label": "₹3,00,000",
                    "value": 300000
                  },
                  {
                    "id": "500000",
                    "label": "₹5,00,000",
                    "value": 500000
                  },
                  {
                    "id": "1000000",
                    "label": "₹10,00,000",
                    "value": 1000000
                  }
                ],
                "checked": false
              },
              {
                "id": 3,
                "name": "Driver Cover",
                "logo": "${ASSETS_BASE}/motor/account-circle.svg",
                "isMandatory": false,
                "isPopular": false,
                "description": "This Covers the paid driver of your car in case of death or disability due to an accident. Important to note that no other person can avail of those financial benefits even if they are paid to drive the insured car.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "id": 4,
                "name": "Zero Depreciation",
                "logo": "${ASSETS_BASE}/motor/shield-car.svg",
                "isMandatory": false,
                "isPopular": true,
                "description": "The Zero Depreciation Cover, also known as bumper-to-bumper cover or Nil Depreciation cover, is an add-on feature designed to provide coverage for the full value of your vehicle without deducting the depreciating value of the vehicle.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "id": 5,
                "name": "Roadside Assistance",
                "logo": "${ASSETS_BASE}/motor/tow-truck-black.svg",
                "isMandatory": false,
                "isPopular": false,
                "description": "The 24×7 roadside assistance cover provides policyholders with valuable assistance in case their vehicle breaks down or faces any mechanical or electrical failure while on the road. This cover offers a range of services such as emergency fuel delivery, battery jump start, flat tyre change, towing facility, etc.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "id": 6,
                "name": "Consumables",
                "logo": "${ASSETS_BASE}/motor/barrel.svg",
                "isMandatory": false,
                "isPopular": false,
                "description": "Consumables cover is an add-on that offers coverage for the cost of replacing consumable items that need to be frequently or periodically replaced, such as engine oil, coolant, brake oil, power steering oil, etc which are not covered under standard motor insurance policy.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "id": 7,
                "name": "Engine Protection",
                "logo": "${ASSETS_BASE}/motor/engine.svg",
                "isMandatory": false,
                "isPopular": false,
                "description": "A standard comprehensive motor insurance policy may not cover certain damages such as malfunction of the engine, water ingression, and leakage of lubricant oil or hydrostatic lock but an Engine Protection cover is particularly useful for those who live in areas that are prone to flooding or waterlogging, as these can cause significant damage to the engine.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "id": 8,
                "name": "NCB Protection",
                "logo": "${ASSETS_BASE}/icons/check-decagram.svg",
                "isMandatory": false,
                "isPopular": false,
                "description": "A No Claim Bonus Protection cover protects the NCB of your vehicle even if you raise a claim. It keeps the NCB amount intact even if you raise a claim in the previous policy year.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "id": 9,
                "name": "Return to Invoice",
                "logo": "${ASSETS_BASE}/motor/script-text.svg",
                "isMandatory": false,
                "isPopular": false,
                "description": "Invoice cover or Return to Invoice (RTI) is an add-on that covers the gap between IDV and the invoice price of your vehicle.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "id": 10,
                "name": "Key Protection",
                "logo": "${ASSETS_BASE}/motor/shield-key.svg",
                "isMandatory": false,
                "isPopular": false,
                "description": "This add-on covers any expense in case of damaged lock or lost keys. It also covers the cost of replacing locks and keys in the event of attempted theft or break-in.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "id": 11,
                "name": "Loss of Personal Belonging",
                "logo": "${ASSETS_BASE}/motor/bag-personal.svg",
                "isMandatory": false,
                "isPopular": false,
                "description": "Loss of personal belongings cover is an add-on which will cover for the loss of any personal items from the insured car, inside or with the car. It covers various personal items including electronic equipments.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "id": 12,
                "name": "Tyre Protect",
                "logo": "${ASSETS_BASE}/motor/tire.svg",
                "isMandatory": false,
                "isPopular": false,
                "description": "Tyre Protection add-on covers any expenses incurred towards the repair or replacement of the tyre/s of the insured car which is otherwise not covered in the normal insurance policy.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "id": 13,
                "name": "Fire & Theft Cover",
                "logo": "${ASSETS_BASE}/motor/fire-circle.svg",
                "isMandatory": false,
                "isPopular": false,
                "description": "A third-party fire and theft insurance policy safeguards you against potential damages caused to others and shields your vehicle in the unfortunate events of fire or theft.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "id": 14,
                "name": "Non-electrical accessories",
                "logo": "${ASSETS_BASE}/motor/toolbox.svg",
                "isMandatory": false,
                "isPopular": false,
                "description": "This add-on covers any extra fitted non-electrical accessories in the vehicle.",
                "isInputRequired": true,
                "minAmount": 1000,
                "maxAmount": 100000,
                "checked": false
              },
              {
                "id": 15,
                "name": "Electrical accessories",
                "logo": "${ASSETS_BASE}/motor/battery-charging.svg",
                "isMandatory": false,
                "isPopular": false,
                "description": "This add-on covers any extra fitted electrical accessories in the vehicle.",
                "isInputRequired": true,
                "minAmount": 1000,
                "maxAmount": 100000,
                "checked": false
              }
            ]
          }
        ]
      },

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

