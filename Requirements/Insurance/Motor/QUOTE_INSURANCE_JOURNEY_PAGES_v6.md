
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
    │   │       ├── policyId (Number)
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
    │   │   ├── modalTitle (String)
    │   │   ├── description (String)
    │   │   └── options (Array, Repeatable)
    │   │       ├── label (String)
    │   │       └── value (String)
    │   └── sortBy (Object)
    │       ├── label (String)
    │       ├── value (String)
    │       └── options (Array, Repeatable)
    │           ├── id (Number)
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
    │       ├── minAmount (Number, Optional)
    │       └── isAvailableForThirdParty (Boolean)
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
                "policyId": 1,
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
              "description": "Zero depreciation cover",
              "isAvailableForThirdParty": false
            },
            {
              "id": "1",
              "name": "Personal Accident Cover",
              "label": "PA cover",
              "checked": false,
              "logo": "",
              "description": "Personal accident cover",
              "minAmount": 1500000,
              "isAvailableForThirdParty": true
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
    ├── title (String)
    ├── policyYear (String)
    ├── logoSrc (String)
    ├── logoAlt (String)
    ├── quotePlanDetailsIcons (Object)
    │   ├── networkGarages (String)
    │   ├── claimRatio (String)
    │   ├── roadsideAssistanceIcon (String)
    │   ├── creditScorePromoIconSrc (String)
    │   ├── creditScorePromoIconAlt (String)
    │   ├── creditScoreChevronIconSrc (String)
    │   ├── availabilityIcon (String)
    │   ├── availabilityIconAlt (String)
    │   ├── unlockIcon (String)
    │   ├── infoIcon (String)
    │   ├── creditScoreUnlockIconSrc (String)
    │   └── creditScoreUnlockIconAlt (String)
    └── upsellAddons (Array, Repeatable)
        ├── id (String)
        ├── name (String)
        ├── label (String)
        ├── checked (Boolean)
        ├── logo (String)
        ├── description (String)
        ├── minAmount (Number, Optional)
        └── isAvailableForThirdParty (Boolean)

```

---

#### Sample JSON Data
```json
{
  "quotePlanDetails": {
    "enabled": true,
    "content": {
      "title": "Select Plan",
      "policyYear": "1-yr plan",
      "logoSrc": "${ASSETS_BASE}/dashboard/icic.webp",
      "logoAlt": "ICICI Lombard",
      "quotePlanDetailsIcons": {
        "networkGarages": "${ASSETS_BASE}/motor/Icon.webp",
        "claimRatio": "${ASSETS_BASE}/motor/check-circle.webp",
        "roadsideAssistanceIcon": "${ASSETS_BASE}/motor/tow-truck.webp",
        "creditScorePromoIconSrc": "${ASSETS_BASE}/motor/percent.webp",
        "creditScorePromoIconAlt": "Credit Score",
        "creditScoreChevronIconSrc": "${ASSETS_BASE}/motor/chevron-right-circle.webp",
        "availabilityIcon": "${ASSETS_BASE}/vehicle-insurance/information.webp",
        "availabilityIconAlt": "Information",
        "unlockIcon": "${ASSETS_BASE}/motor/percentage.webp",
        "infoIcon": "${ASSETS_BASE}/vehicle-insurance/information.webp",
        "creditScoreUnlockIconSrc": "${ASSETS_BASE}/motor/percentage.webp",
        "creditScoreUnlockIconAlt": "Unlock savings"
      },
      "upsellAddons": [
        {
          "id": "4",
          "name": "Zero Depreciation",
          "label": "Zero dep",
          "checked": false,
          "logo": "",
          "description": "Zero depreciation cover",
          "isAvailableForThirdParty": false
        },
        {
          "id": "1",
          "name": "Personal Accident Cover",
          "label": "PA cover",
          "checked": false,
          "logo": "",
          "description": "Personal accident cover",
          "minAmount": 1500000,
          "isAvailableForThirdParty": true
        }
      ]
    }
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
        ├── addOnId (Integer)
        ├── name (String)
        ├── logo (String)
        ├── isMandatory (Boolean)
        ├── isPopular (Boolean)
        ├── isAvailableForThirdParty (Boolean)
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
            "addOnId": 1,
            "name": "Personal Accident Cover",
            "logo": "${ASSETS_BASE}/motor/shield-check.svg",
            "isMandatory": true,
            "isPopular": false,
            "isAvailableForThirdParty": true,
            "description": "A personal accident or PA cover is an add-on that provides financial protection in case of accidental injury or death.\n\nYou can opt out if:\na) The car is registered in a company's name.\n\nb) You already have a PA cover of 15 lakhs. (from any other vehicle owned by you or from a separate standalone PA Cover Policy).\n\nc) Registered Owner of the vehicle does not have a valid driving license.",
            "isInputRequired": true,
            "minAmount": 1500000,
            "maxAmount": 1500000,
            "isAmountLocked": true,
            "checked": false
          },
          {
            "addOnId": 2,
            "name": "Passenger Cover",
            "logo": "${ASSETS_BASE}/motor/account-group.svg",
            "isMandatory": false,
            "isPopular": false,
            "isAvailableForThirdParty": true,
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
            "addOnId": 3,
            "name": "Driver Cover",
            "logo": "${ASSETS_BASE}/motor/account-circle.svg",
            "isMandatory": false,
            "isPopular": false,
            "isAvailableForThirdParty": true,
            "description": "This Covers the paid driver of your car in case of death or disability due to an accident. Important to note that no other person can avail of those financial benefits even if they are paid to drive the insured car.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "addOnId": 4,
            "name": "Zero Depreciation",
            "logo": "${ASSETS_BASE}/motor/shield-car.svg",
            "isMandatory": false,
            "isPopular": true,
            "isAvailableForThirdParty": false,
            "description": "The Zero Depreciation Cover, also known as bumper-to-bumper cover or Nil Depreciation cover, is an add-on feature designed to provide coverage for the full value of your vehicle without deducting the depreciating value of the vehicle.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "addOnId": 5,
            "name": "Roadside Assistance",
            "logo": "${ASSETS_BASE}/motor/tow-truck-black.svg",
            "isMandatory": false,
            "isPopular": false,
            "isAvailableForThirdParty": false,
            "description": "The 24×7 roadside assistance cover provides policyholders with valuable assistance in case their vehicle breaks down or faces any mechanical or electrical failure while on the road. This cover offers a range of services such as emergency fuel delivery, battery jump start, flat tyre change, towing facility, etc.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "addOnId": 6,
            "name": "Consumables",
            "logo": "${ASSETS_BASE}/motor/barrel.svg",
            "isMandatory": false,
            "isPopular": false,
            "isAvailableForThirdParty": false,
            "description": "Consumables cover is an add-on that offers coverage for the cost of replacing consumable items that need to be frequently or periodically replaced, such as engine oil, coolant, brake oil, power steering oil, etc which are not covered under standard motor insurance policy.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "addOnId": 7,
            "name": "Engine Protection",
            "logo": "${ASSETS_BASE}/motor/engine.svg",
            "isMandatory": false,
            "isPopular": false,
            "isAvailableForThirdParty": false,
            "description": "A standard comprehensive motor insurance policy may not cover certain damages such as malfunction of the engine, water ingression, and leakage of lubricant oil or hydrostatic lock but an Engine Protection cover is particularly useful for those who live in areas that are prone to flooding or waterlogging, as these can cause significant damage to the engine.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "addOnId": 8,
            "name": "NCB Protection",
            "logo": "${ASSETS_BASE}/icons/check-decagram.svg",
            "isMandatory": false,
            "isPopular": false,
            "isAvailableForThirdParty": false,
            "description": "A No Claim Bonus Protection cover protects the NCB of your vehicle even if you raise a claim. It keeps the NCB amount intact even if you raise a claim in the previous policy year.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "addOnId": 9,
            "name": "Return to Invoice",
            "logo": "${ASSETS_BASE}/motor/script-text.svg",
            "isMandatory": false,
            "isPopular": false,
            "isAvailableForThirdParty": false,
            "description": "Invoice cover or Return to Invoice (RTI) is an add-on that covers the gap between IDV and the invoice price of your vehicle.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "addOnId": 10,
            "name": "Key Protection",
            "logo": "${ASSETS_BASE}/motor/shield-key.svg",
            "isMandatory": false,
            "isPopular": false,
            "isAvailableForThirdParty": false,
            "description": "This add-on covers any expense in case of damaged lock or lost keys. It also covers the cost of replacing locks and keys in the event of attempted theft or break-in.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "addOnId": 11,
            "name": "Loss of Personal Belonging",
            "logo": "${ASSETS_BASE}/motor/bag-personal.svg",
            "isMandatory": false,
            "isPopular": false,
            "isAvailableForThirdParty": false,
            "description": "Loss of personal belongings cover is an add-on which will cover for the loss of any personal items from the insured car, inside or with the car. It covers various personal items including electronic equipments.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "addOnId": 12,
            "name": "Tyre Protect",
            "logo": "${ASSETS_BASE}/motor/tire.svg",
            "isMandatory": false,
            "isPopular": false,
            "isAvailableForThirdParty": false,
            "description": "Tyre Protection add-on covers any expenses incurred towards the repair or replacement of the tyre/s of the insured car which is otherwise not covered in the normal insurance policy.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "addOnId": 13,
            "name": "Fire & Theft Cover",
            "logo": "${ASSETS_BASE}/motor/fire-circle.svg",
            "isMandatory": false,
            "isPopular": false,
            "isAvailableForThirdParty": false,
            "description": "A third-party fire and theft insurance policy safeguards you against potential damages caused to others and shields your vehicle in the unfortunate events of fire or theft.",
            "isInputRequired": false,
            "checked": false
          },
          {
            "addOnId": 14,
            "name": "Non-electrical accessories",
            "logo": "${ASSETS_BASE}/motor/toolbox.svg",
            "isMandatory": false,
            "isPopular": false,
            "isAvailableForThirdParty": false,
            "description": "This add-on covers any extra fitted non-electrical accessories in the vehicle.",
            "isInputRequired": true,
            "minAmount": 1000,
            "maxAmount": 50000,
            "checked": false
          },
          {
            "addOnId": 15,
            "name": "Electrical accessories",
            "logo": "${ASSETS_BASE}/motor/battery-charging.svg",
            "isMandatory": false,
            "isPopular": false,
            "isAvailableForThirdParty": false,
            "description": "This add-on covers any extra fitted electrical accessories in the vehicle.",
            "isInputRequired": true,
            "minAmount": 1000,
            "maxAmount": 50000,
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
                  "description": "Zero depreciation cover",
                  "isAvailableForThirdParty": false
                },
                {
                  "id": "1",
                  "name": "Personal Accident Cover",
                  "label": "PA cover",
                  "checked": false,
                  "logo": "",
                  "description": "Personal accident cover",
                  "minAmount": 1500000,
                  "isAvailableForThirdParty": true
                }
              ]
            },
         } 
       ]
      },
      "quotePlanDetails": {
        "enabled": true,
        "content": {
          "title": "Select Plan",
          "policyYear": "1-yr plan",
          "logoSrc": "${ASSETS_BASE}/dashboard/icic.webp",
          "logoAlt": "ICICI Lombard",
          "quotePlanDetailsIcons": {
            "networkGarages": "${ASSETS_BASE}/motor/Icon.webp",
            "claimRatio": "${ASSETS_BASE}/motor/check-circle.webp",
            "roadsideAssistanceIcon": "${ASSETS_BASE}/motor/tow-truck.webp",
            "creditScorePromoIconSrc": "${ASSETS_BASE}/motor/percent.webp",
            "creditScorePromoIconAlt": "Credit Score",
            "creditScoreChevronIconSrc": "${ASSETS_BASE}/motor/chevron-right-circle.webp",
            "availabilityIcon": "${ASSETS_BASE}/vehicle-insurance/information.webp",
            "availabilityIconAlt": "Information",
            "unlockIcon": "${ASSETS_BASE}/motor/percentage.webp",
            "infoIcon": "${ASSETS_BASE}/vehicle-insurance/information.webp",
            "creditScoreUnlockIconSrc": "${ASSETS_BASE}/motor/percentage.webp",
            "creditScoreUnlockIconAlt": "Unlock savings"
          },
          "upsellAddons": [
            {
              "id": "4",
              "name": "Zero Depreciation",
              "label": "Zero dep",
              "checked": false,
              "logo": "",
              "description": "Zero depreciation cover",
              "isAvailableForThirdParty": false
            },
            {
              "id": "1",
              "name": "Personal Accident Cover",
              "label": "PA cover",
              "checked": false,
              "logo": "",
              "description": "Personal accident cover",
              "minAmount": 1500000,
              "isAvailableForThirdParty": true
            }
          ]
        }
      },
      "addOns": {
        "enabled": true,
        "content": [
          {
            "order": 1,
            "addOns": [
              {
                "addOnId": 1,
                "name": "Personal Accident Cover",
                "logo": "${ASSETS_BASE}/motor/shield-check.svg",
                "isMandatory": true,
                "isPopular": false,
                "isAvailableForThirdParty": true,
                "description": "A personal accident or PA cover is an add-on that provides financial protection in case of accidental injury or death.\n\nYou can opt out if:\na) The car is registered in a company's name.\n\nb) You already have a PA cover of 15 lakhs. (from any other vehicle owned by you or from a separate standalone PA Cover Policy).\n\nc) Registered Owner of the vehicle does not have a valid driving license.",
                "isInputRequired": true,
                "minAmount": 1500000,
                "maxAmount": 1500000,
                "isAmountLocked": true,
                "checked": false
              },
              {
                "addOnId": 2,
                "name": "Passenger Cover",
                "logo": "${ASSETS_BASE}/motor/account-group.svg",
                "isMandatory": false,
                "isPopular": false,
                "isAvailableForThirdParty": true,
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
                "addOnId": 3,
                "name": "Driver Cover",
                "logo": "${ASSETS_BASE}/motor/account-circle.svg",
                "isMandatory": false,
                "isPopular": false,
                "isAvailableForThirdParty": true,
                "description": "This Covers the paid driver of your car in case of death or disability due to an accident. Important to note that no other person can avail of those financial benefits even if they are paid to drive the insured car.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "addOnId": 4,
                "name": "Zero Depreciation",
                "logo": "${ASSETS_BASE}/motor/shield-car.svg",
                "isMandatory": false,
                "isPopular": true,
                "isAvailableForThirdParty": false,
                "description": "The Zero Depreciation Cover, also known as bumper-to-bumper cover or Nil Depreciation cover, is an add-on feature designed to provide coverage for the full value of your vehicle without deducting the depreciating value of the vehicle.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "addOnId": 5,
                "name": "Roadside Assistance",
                "logo": "${ASSETS_BASE}/motor/tow-truck-black.svg",
                "isMandatory": false,
                "isPopular": false,
                "isAvailableForThirdParty": false,
                "description": "The 24×7 roadside assistance cover provides policyholders with valuable assistance in case their vehicle breaks down or faces any mechanical or electrical failure while on the road. This cover offers a range of services such as emergency fuel delivery, battery jump start, flat tyre change, towing facility, etc.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "addOnId": 6,
                "name": "Consumables",
                "logo": "${ASSETS_BASE}/motor/barrel.svg",
                "isMandatory": false,
                "isPopular": false,
                "isAvailableForThirdParty": false,
                "description": "Consumables cover is an add-on that offers coverage for the cost of replacing consumable items that need to be frequently or periodically replaced, such as engine oil, coolant, brake oil, power steering oil, etc which are not covered under standard motor insurance policy.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "addOnId": 7,
                "name": "Engine Protection",
                "logo": "${ASSETS_BASE}/motor/engine.svg",
                "isMandatory": false,
                "isPopular": false,
                "isAvailableForThirdParty": false,
                "description": "A standard comprehensive motor insurance policy may not cover certain damages such as malfunction of the engine, water ingression, and leakage of lubricant oil or hydrostatic lock but an Engine Protection cover is particularly useful for those who live in areas that are prone to flooding or waterlogging, as these can cause significant damage to the engine.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "addOnId": 8,
                "name": "NCB Protection",
                "logo": "${ASSETS_BASE}/icons/check-decagram.svg",
                "isMandatory": false,
                "isPopular": false,
                "isAvailableForThirdParty": false,
                "description": "A No Claim Bonus Protection cover protects the NCB of your vehicle even if you raise a claim. It keeps the NCB amount intact even if you raise a claim in the previous policy year.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "addOnId": 9,
                "name": "Return to Invoice",
                "logo": "${ASSETS_BASE}/motor/script-text.svg",
                "isMandatory": false,
                "isPopular": false,
                "isAvailableForThirdParty": false,
                "description": "Invoice cover or Return to Invoice (RTI) is an add-on that covers the gap between IDV and the invoice price of your vehicle.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "addOnId": 10,
                "name": "Key Protection",
                "logo": "${ASSETS_BASE}/motor/shield-key.svg",
                "isMandatory": false,
                "isPopular": false,
                "isAvailableForThirdParty": false,
                "description": "This add-on covers any expense in case of damaged lock or lost keys. It also covers the cost of replacing locks and keys in the event of attempted theft or break-in.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "addOnId": 11,
                "name": "Loss of Personal Belonging",
                "logo": "${ASSETS_BASE}/motor/bag-personal.svg",
                "isMandatory": false,
                "isPopular": false,
                "isAvailableForThirdParty": false,
                "description": "Loss of personal belongings cover is an add-on which will cover for the loss of any personal items from the insured car, inside or with the car. It covers various personal items including electronic equipments.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "addOnId": 12,
                "name": "Tyre Protect",
                "logo": "${ASSETS_BASE}/motor/tire.svg",
                "isMandatory": false,
                "isPopular": false,
                "isAvailableForThirdParty": false,
                "description": "Tyre Protection add-on covers any expenses incurred towards the repair or replacement of the tyre/s of the insured car which is otherwise not covered in the normal insurance policy.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "addOnId": 13,
                "name": "Fire & Theft Cover",
                "logo": "${ASSETS_BASE}/motor/fire-circle.svg",
                "isMandatory": false,
                "isPopular": false,
                "isAvailableForThirdParty": false,
                "description": "A third-party fire and theft insurance policy safeguards you against potential damages caused to others and shields your vehicle in the unfortunate events of fire or theft.",
                "isInputRequired": false,
                "checked": false
              },
              {
                "addOnId": 14,
                "name": "Non-electrical accessories",
                "logo": "${ASSETS_BASE}/motor/toolbox.svg",
                "isMandatory": false,
                "isPopular": false,
                "isAvailableForThirdParty": false,
                "description": "This add-on covers any extra fitted non-electrical accessories in the vehicle.",
                "isInputRequired": true,
                "minAmount": 1000,
                "maxAmount": 50000,
                "checked": false
              },
              {
                "addOnId": 15,
                "name": "Electrical accessories",
                "logo": "${ASSETS_BASE}/motor/battery-charging.svg",
                "isMandatory": false,
                "isPopular": false,
                "isAvailableForThirdParty": false,
                "description": "This add-on covers any extra fitted electrical accessories in the vehicle.",
                "isInputRequired": true,
                "minAmount": 1000,
                "maxAmount": 50000,
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

