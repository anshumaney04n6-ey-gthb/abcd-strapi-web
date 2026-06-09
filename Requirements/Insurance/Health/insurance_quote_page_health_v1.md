# Health Insurance Quote Page - Complete Schema Documentation

## Content-Type: Insurance Quote Page (selectQuotePlanDetails)

**Collection Key:** `health-insurance-journey-pages`  
**Operation Key:** `apply`  
**Partner Variant:** `default`

---

## All Content-Type Fields (Exact Strapi Field Names)

| Field Name | Type | Required | Default | Max | Description |
|------------|------|----------|---------|-----|-------------|
| `apply.selectQuotePlanDetails.filterDropdowns` | component (repeatable) | Yes | fallback | - | Quote filters such as sum insured and tenure |
| `apply.selectQuotePlanDetails.hiPlansFilterOptions` | component (repeatable) | Yes | fallback | - | Filter chips shown inside Filter bottom sheet |
| `apply.selectQuotePlanDetails.sortOptions` | component (repeatable) | Yes | fallback | - | Sort options with sortBy and value configuration |
| `apply.selectQuotePlanDetails.promoBannerCards` | component (repeatable) | No | fallback | - | Promotional offer banners/cards |
| `apply.selectQuotePlanDetails.educationDrawer` | component | Yes | fallback | - | Educational drawer content with positive/negative considerations |
| `apply.selectQuotePlanDetails.disclaimer` | component | Yes | fallback | - | disclaimer content |
| `apply.selectQuotePlanDetails.termsAndConditions` | component | Yes | fallback | - | Terms and Conditons |

---

## API Endpoints & CMS Content Fetching

### Base URL
```
/api/health-insurance-journey-pages
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/health-insurance-journey-pages` | List journey entries |
| GET | `/api/health-insurance-journey-pages/:id` | Get single entry by ID |
| POST | `/api/health-insurance-journey-pages` | Create entry |
| PUT | `/api/health-insurance-journey-pages/:id` | Update entry |
| DELETE | `/api/health-insurance-journey-pages/:id` | Delete entry |

### Query Parameters


**Effective app fetch intent:**

```
GET /api/health-insurance-journey-pages?
  filters[partner][$eq]=default&
  populate=*
```

## Complete JSON Structure

> **Note:** Keep this structure aligned with selectQuotePlanDetails client props and fallback constants.

```json
{
  "data": [
    {
      "id": 1,
      "attributes": {
        "partner": "default",
        "apply": {
          "selectQuotePlanDetails": {
            "filterDropdowns": [
              {
                "filterId": "sum_insured",
                "title": "Sum Insured",
                "subtitle": "A higher sum insured offers stronger protection when you need it most",
                "defaultValue": "1000000",
                "options": [
                  { "label": "₹5 L", "value": "500000", "order": 1 },
                  { "label": "₹7 L", "value": "700000", "order": 2 },
                  { "label": "₹10 L", "value": "1000000", "badge": "Popular", "order": 3 },
                  { "label": "₹15 L", "value": "1500000", "order": 4 },
                  { "label": "₹20 L", "value": "2000000", "order": 5 },
                  { "label": "₹50 L", "value": "5000000", "order": 6 }
                ]
              },
              {
                "filterId": "plan_tenure",
                "title": "Plan tenure",
                "subtitle": "This helps us understand your current health insurance status",
                "defaultValue": "1",
                "options": [
                  { "label": "1 year", "value": "1", "order": 1 },
                  { "label": "2 years", "value": "2", "discount": "7.5%", "order": 2 },
                  { "label": "3 years", "value": "3", "discount": "10%", "order": 3 }
                ]
              }
            ],

            "hiPlansFilterOptions": [
              {
                "icon": "noCopayIcon",
                "title": "No Co-pay",
                "description": "No out-of-pocket share during claims",
                "checked": false,
                "order": 1
              },
              {
                "icon": "noRoomRentIcon",
                "title": "No room rent limit",
                "description": "No cap on hospital room charges",
                "checked": false,
                "order": 2
              },
              {
                "icon": "maternityIcon",
                "title": "Maternity plans",
                "description": "Includes maternity-related expenses",
                "checked": false,
                "order": 3
              }
            ],

            "sortOptions": [
              {
                "sortId": "relevance-sort",
                "label": "Relevance",
                "sortBy": "relevance",
                "sortByLabel": "Relevance",
                "default": true,
                "value": [
                  { "planId": "1", "order": 1 },
                  { "planId": "4", "order": 2 },
                  { "planId": "3", "order": 3 },
                  { "planId": "20", "order": 4 },
                  { "planId": "19", "order": 5 },
                  { "planId": "15", "order": 6 }
                ]
              },
              {
                "sortId": "premium-desc-sort",
                "label": "Premium (Highest to Lowest)",
                "sortBy": "premium",
                "sortByLabel": "Premium",
                "value": "desc"
              },
              {
                "sortId": "premium-asc-sort",
                "label": "Premium (Lowest to Highest)",
                "sortBy": "premium",
                "sortByLabel": "Premium",
                "value": "asc"
              }
            ],

            "promoBannerCards": [
              {
                "promoId": "offer-1",
                "title": "Go Long. Get up to 19% OFF!",
                "subtitle": "Select a 3-year plan and get an extra 10% discount.",
                "iconSrc": "/assets/health-insurance/offer-icon.webp", //media
                "iconAlt": "Discount offer",
                "order": 1
              },
              {
                "promoId": "offer-2",
                "title": "Save more with annual premium payment",
                "subtitle": "Pay once and get additional savings on your selected plan.",
                "iconSrc": "/assets/health-insurance/offer-icon.webp", //media
                "iconAlt": "Savings offer",
                "order": 2
              }
            ],

            "educationDrawer": {
              "title": "Key Considerations for Choosing Your Health Plan",
              "description": [
                {
                  "type": "positive",
                  "title": "Good for you plan",
                  "points": [
                    "Zero or low co-payment",
                    "Low waiting period for pre-existing diseases",
                    "No limit on room rent or room types"
                  ],
                  "order": 1
                },
                {
                  "type": "negative",
                  "title": "Not good for your plan",
                  "points": [
                    "Low claim settlement % of insurer",
                    "High waiting period"
                  ],
                  "order": 2
                }
              ]
            },

            "disclaimer": {
              "title": "Disclaimer",
              "content": "Aditya Birla Capital Digital Ltd (ABCDL) is a Corporate Agent (IRDAI Reg No. CA0871) of Aditya Birla Health Insurance Co. Limited and does not underwrite the risk or act as an insurer. All health insurance products are underwritten by the Aditya Birla Health Insurance company and are subject to the terms and conditions of the relevant policy. For more details on risk factors, terms and conditions please read terms and conditions and prospectus carefully before concluding a sale. Aditya Birla Capital Digital Ltd (ABCDL) having its Registered office at Aditya Birla Capital Digital Limited, 18th Floor, One World Center, Tower 1, Jupiter Mills Compound, 841 Senapati Bapat Marg, Elphinstone Road, Mumbai 400013. ABCDL is a Corporate Agent of Aditya Birla Health Insurance Co. Ltd (IRDAI Reg No:153)",
              "ctaLabel": "Got it",
            },
            "termsAndConditions": {
              "label": "Terms and Conditions",
              "content": ""
            },
          }
        }
      }
    }
  ]    
}
```

---

## Components Detail

### 1. filter-dropdown

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `filterId` | string | Yes | - |
| `title` | string | Yes | - |
| `subtitle` | string | No | "" |
| `defaultValue` | string | No | - |
| `options` | component repeatable (`filter-option`) | No | [] |

### 2. filter-option

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `label` | string | Yes | - |
| `value` | string | Yes | - |
| `badge` | string | No | - |
| `discount` | string | No | - |
| `order` | number | No | 0 |

### 3. hi-plans-filter-option

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `icon` | string | No | - |
| `title` | string | Yes | - |
| `description` | string | No | "" |
| `checked` | boolean | No | `false` |
| `order` | number | No | 0 |

### 4. sort-option

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `label` | string | Yes | - |
| `sortBy` | string | Yes | - |
| `sortByLabel` | string | No | - |
| `default` | boolean | No | `false` |
| `value` | json | Yes | - |

### 5. promo-banner-card

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `title` | string | Yes | - |
| `subtitle` | string | No | "" |
| `iconSrc` | media | No | - |
| `iconAlt` | string | No | - |
| `order` | number | No | 0 |

### 6. education-drawer

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | Yes | - |
| `description` | component repeatable (`education-section`) | No | [] |

### 7. education-section

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `type` | enumeration (`positive`, `negative`) | Yes | - |
| `title` | string | Yes | - |
| `points` | string[] | No | [] |
| `order` | number | No | 0 |

---

### 8. disclaimer

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | Yes | - |
| `content` | string | Yes | - |
| `ctaLabel` | string | No | - |

---

### 9. terms-and-condiitons

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | Yes | - |
| `content` | string | Yes | - |

---

## Populate Query for Full Response

```
GET /api/health-insurance-journey-pages?
filters[partner][$eq]=default&
populate=*
```

---

## Notes
- `promoBannerCards.iconSrc` fields are Strapi media relations.
