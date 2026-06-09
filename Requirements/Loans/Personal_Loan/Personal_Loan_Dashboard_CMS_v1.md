# PL Dashboard CMS Schema Documentation

## Content-Type: personal-loan-dashboard-pages

**Collection Name:** `personal-loan-dashboard-pages`  
**Singular Name:** `personal-loan-dashboard-pages`  
**Plural Name:** `personal-loan-dashboard-pages`  
**Draft & Publish:** Enabled

---

## All Content-Type Fields (Exact Strapi Field Names)

| Field Name | Type | Required | Default | Max | Description |
|------------|------|----------|---------|-----|-------------|
| `partner` | string | No | `default` | - | Optional partner-specific variant |
| `subProduct` | string | No | `personal` | - | Sub-product identifier (personal, gold, business, etc.) |
| `header` | component | No | fallback | - | Header logo and branding configuration |
| `hero` | component | No | fallback | - | Hero section with call-to-action |
| `calculator` | component | No | fallback | - | Financial tools & calculators section |
| `getStarted` | component | No | fallback | - | Process steps section (How to get started) |
| `benefitBlock` | component | No | fallback | - | Benefits and features section |
| `lenderLogos` | component[] | No | - | 10 | Partner/lender logos display |
| `ratesAndCharges` | component | No | fallback | - | Rates & Charges section with loan details |
| `trustedPartners` | component | No | fallback | - | Trusted lending partners section |
| `referralBanner` | component | No | fallback | - | Referral program promotional banner |
| `exclusiveBanner` | component | No | fallback | - | Exclusive offer banner section |
| `exclusiveEmployeeBanner` | component | No | fallback | - | Exclusive employee offer banner section |
| `inlineInfoBanner` | component | No | fallback | - | Inline informational banner |
| `faq` | component | No | fallback | - | FAQ section with tabs and items |
| `footer` | component | No | fallback | - | Footer details and features |
| `plCalculatorSidebar` | component | No | fallback | - | Personal loan calculator sidebar configuration |

---

## API Endpoints & CMS Content Fetching

### Base URL
```
/api/personal-loan-dashboard-pages
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/personal-loan-dashboard-pages` | List all dashboards |
| GET | `/api/personal-loan-dashboard-pages/:id` | Get single dashboard by ID |
| POST | `/api/personal-loan-dashboard-pages` | Create new dashboard |
| PUT | `/api/personal-loan-dashboard-pages/:id` | Update dashboard content |
| DELETE | `/api/personal-loan-dashboard-pages/:id` | Delete dashboard |

### Query Parameters

**Filtering by Partner:**
```
?filters[partner][$eq]=default
?populate=*
```

**Full Dashboard Query:**
```
GET /api/personal-loan-dashboard-pages?
  filters[partner][$eq]=default&
  filters[subProduct][$eq]=personal&
  populate=*
```

**Partner-Specific Content:**
```
GET /api/personal-loan-dashboard-pages?
  filters[partner][$eq]=partner_name&
  filters[subProduct][$eq]=personal&
  populate=*
```


### Response Payload Structure

**Success Response (200 OK):**
```json
{
  "data": [
    {
      "id": 97,
      "documentId": "e4wcy0tg7erp04n08tqw0kra",
        "partner": "default",
        "subProduct": "personal",
        "createdAt": "2026-03-08T04:53:48.947Z",
        "updatedAt": "2026-05-15T13:33:43.535Z",
        "publishedAt": "2026-05-15T13:33:50.827Z",
  "header": {
    "logo": {
      "src": "/logos/lob/abcd.webp",
      "alt": "ABCD Logo",
      "size": 40
    }
  },
  "hero": {
    "ctaText": "Apply Now",
    "eligibilityCriteria": [
      { "label": "Age:", "value": "21 to 65 years" },
      { "label": "Income:", "value": "Min. ₹30,000/m" },
      { "label": "Residency:", "value": "PAN India" }
    ],
    "highlighterContent": {
      "newJourney": {
        "title": "Get instant loans up to ₹ 15 Lakhs",
        "subtitle": "Instant Disbursal, ZERO Documentation, Flexible EMIs",
        "ctaText": "Apply now",
        "illustrationSrc": "/assets/personal-loan/icons/handcoins.webp"
      },
      "resumeJourney": {
        "title": "Welcome back, pick up where you left",
        "subtitle": "Resume your application in minutes and get faster disbursal",
        "ctaText": "Resume",
        "illustrationSrc": "/assets/personal-loan/icons/resume-app.webp"
      },
      "preApprovedOffer": {
        "title": "You have a ",
        "subtitle": "Check out your",
        "ctaText": "Apply",
        "illustrationSrc": "/assets/personal-loan/icons/handcoins.webp"
      },
      "exclusiveOffer": {
        "title": "Staff exclusive personal loan offer",
        "subtitle": "Check out your staff offer -",
        "ctaText": "Apply Now",
        "illustrationSrc": "/assets/personal-loan/icons/exclusive.webp",
        "redirectUrl": "https://google.com"
      },
      "progress": {
        "title": "Your disbursement is in progress",
        "subtitle": "We are processing your loan disbursement. This usually completes shortly.",
        "ctaText": "Check Status",
        "illustrationSrc": "/assets/personal-loan/icons/progress-app.webp"
      },
      "success": {
        "title": "Loan disbursed successfully",
        "subtitle": "Your loan amount has been credited to your account.",
        "ctaText": "Download Documents",
        "illustrationSrc": "/assets/personal-loan/icons/disb-success.webp"
      },
      "failed": {
        "title": "Disbursement failed",
        "subtitle": "We could not complete disbursement this time. Please retry or check details.",
        "ctaText": "Check Status",
        "illustrationSrc": "/assets/personal-loan/icons/disb-failed.webp"
      },
      "rejected": {
        "title": "Application rejected",
        "subtitle": "Your application could not be approved based on current checks.",
        "ctaText": "Check Status",
        "illustrationSrc": "/assets/personal-loan/icons/disb-failed.webp"
      }
    }
  },
  "referralBanner": {
    "isVisible": true,
    "title": "Help friends start their gold journey",
    "subtitle": "Refer friends & earn ₹250 in ABCD Coins.",
    "termsText": "*T&C",
    "assets": {
      "treasureChest": "/assets/personal-loan/referralBanner/treasure-chest.webp",
      "goldCoin": "/assets/personal-loan/referralBanner/gold-coin.webp",
      "chevron": "/assets/personal-loan/referralBanner/double-chevron.webp"
    }
  },
  "ratesAndCharges": {
    "text": "Rates and charges",
    "items": [
      {
        "ratesAndChargesId": "loan-amount",
        "title": "Loan Amount",
        "description": "Min. ₹25,000 and Max. 5 Lakhs",
        "image": "/assets/personal-loan/icons/goldhand.webp"
      },
      {
        "ratesAndChargesId": "repayment-tenure",
        "title": "Repayment Tenure",
        "description": "12 months to 36 months",
        "image": "/assets/personal-loan/icons/percentage.webp"
      },
      {
        "ratesAndChargesId": "rate-of-interest",
        "title": "Rate of Interest",
        "description": "10.99% to 30% per annum",
        "image": "/assets/personal-loan/icons/percentage.webp"
      },
      {
        "ratesAndChargesId": "processing-fees",
        "title": "Processing Fees",
        "description": "1.18% - 4.13% of Loan amount incl. GST.",
        "image": "/assets/personal-loan/icons/file.webp"
      }
    ],
    "cardBackground": "linear-gradient(90deg, rgba(255, 213, 108, 0.2) 0%, rgba(124, 34, 121, 0.05) 100%), linear-gradient(90deg, #fff 0%, #fff 100%)",
    "cardBorder": "1px solid rgba(124, 34, 121, 0.2)"
  },
  "inlineInfoBanner": {
    "isVisible": true,
    "highlightedText": "Get a free credit score!",
    "text": " Auto track your loans & credit card reports",
    "iconSrc": "/assets/personal-loan/icons/creditcard.webp",
    "iconAlt": "Info",
    "chevronSrc": "/assets/personal-loan/referralBanner/double-chevron.webp"
  },
  "getStarted": {
    "headingPrefix": "Only ",
    "headingHighlight": "3 steps",
    "headingSuffix": ", and you get the money!",
    "items": [
      {
        "id": "basic-details",
        "title": "Provide Basic Details",
        "description": "Choose your amount, pay online, and instantly own certified digital gold backed by real assets.",
        "image": "/assets/personal-loan/icons/document.webp"
      },
      {
        "id": "choose-offers",
        "title": "Choose & Apply Loan Offers",
        "description": "Choose your amount, pay online, and instantly own certified digital gold backed by real assets.",
        "image": "/assets/personal-loan/icons/filter.webp"
      },
      {
        "id": "get-cash",
        "title": "Get instant Cash in Bank",
        "description": "Choose your amount, pay online, and instantly own certified digital gold backed by real assets.",
        "image": "/assets/personal-loan/icons/money.webp"
      }
    ],
    "cardBackground": "linear-gradient(90deg, rgba(255, 213, 108, 0.2) 0%, rgba(124, 34, 121, 0.05) 100%), linear-gradient(90deg, #fff 0%, #fff 100%)",
    "cardBorder": "1px solid rgba(124, 34, 121, 0.2)"
  },
  "calculator": {
    "sectionTitle": "Financial tools & calculators",
    "title": "EMI for your Personal Loan",
    "description": "Calculate your potential EMI in seconds.",
    "ctaText": "Calculate",
    "illustrationIcon": "/assets/personal-loan/icons/calculator.webp",
    "ctaAriaLabel": "Calculate your EMI"
  },
  "plCalculatorSidebar": {
    "ranges": {
      "tenureMin": 12,
      "tenureMax": 60,
      "tenureDefault": 36,
      "loanAmountMin": 50000,
      "loanAmountMax": 1000000,
      "loanAmountDefault": 800000,
      "emiAmountMin": 1000,
      "emiAmountMax": 25000,
      "emiAmountDefault": 9500,
      "roiMin": 10,
      "roiMax": 30,
      "roiDefault": 10.99
    },
    "labels": {
      "headerTitle": "Personal Loan",
      "emiCalculatorHeaderTitle": "Personal loan EMI calculator",
      "loanAmountCalculatorHeaderTitle": "Personal loan amount calculator",
      "helperBannerText": "Use this calculator to plan your instalments better",
      "homeTitle": "Our Calculators",
      "homeSubtitle": "Select a calculator you would like to proceed with",
      "emiCalculatorOptionTitle": "EMI Calculator",
      "loanAmountCalculatorOptionTitle": "Loan Amount Calculator",
      "tenureLabel": "Tenure",
      "tenureSuffix": "in months",
      "loanAmountLabel": "Loan Amount",
      "emiAmountLabel": "EMI Amount",
      "roiLabel": "Rate of interest",
      "roiSuffix": "%*",
      "currencySymbol": "₹",
      "totalPayableLabel": "Total payable amount",
      "estimatedEmiLabel": "Your estimated EMI amount",
      "estimatedLoanAmountLabel": "Your estimated loan amount",
      "principalAmountLabel": "Principal Amount",
      "interestAmountLabel": "Interest Amount",
      "calculateButtonText": "Calculate",
      "applyNowButtonText": "Apply Now",
      "disclaimerText": "Disclaimer : The aforementioned values, calculations and results are for illustrative and informational purposes only, and may vary basis various parameters laid down by Aditya Birla Capital Limited.",
      "tenureValidationMessage": "Loan tenure needs to be in the range of {min} to {max} months",
      "loanAmountValidationMessage": "Loan amount needs to be in the range of {min} to {max}",
      "emiAmountValidationMessage": "EMI amount needs to be in the range of {min} to {max}",
      "roiValidationMessage": "ROI should be in the range of {min}-{max}%"
    },
    "icons": {
      "helperBannerIcon": "/assets/personal-loan/icons/helperbannericon.webp",
      "emiCalculatorIcon": "/assets/personal-loan/icons/plcalculator.webp",
      "loanAmountCalculatorIcon": "/assets/personal-loan/icons/plcoins.webp"
    }
  },
  "benefitBlock": {
    "items": [
      {
        "id": "instant-offer",
        "icon": "/assets/personal-loan/icons/pl-benefit-bolt.webp",
        "text": "Get\nInstant Offer"
      },
      {
        "id": "no-paperwork",
        "icon": "/assets/personal-loan/icons/pl-benefit-laptop-cloud.webp",
        "text": "No Paperwork\nRequired"
      },
      {
        "id": "lowest-interest",
        "icon": "/assets/personal-loan/icons/pl-benefit-three-steps.webp",
        "text": "Lowest\ninterest rate"
      }
    ],
    "footerText": "1 Lakh+ people got a personal loan in just a few clicks",
    "footerLeftIcon": "/assets/personal-loan/icons/pl-benefit-star.webp",
    "footerRightIcon": "/assets/personal-loan/icons/pl-benefit-star.webp"
  },
  "trustedPartners": {
    "title": "Our Trusted Lending Partners",
    "subtitle": "",
    "columns": [
      {
        "trustedPartnersId": "partner-1",
        "name": "ICICI Lombard",
        "logoUrl": "/assets/personal-loan/icons/icic.webp"
      },
      {
        "trustedPartnersId": "partner-2",
        "name": "ACKO",
        "logoUrl": "/assets/personal-loan/icons/acko.webp"
      },
      {
        "trustedPartnersId": "partner-3",
        "name": "Digit",
        "logoUrl": "/assets/personal-loan/icons/digit.webp"
      },
      {
        "trustedPartnersId": "partner-4",
        "name": "Tata AIG",
        "logoUrl": "/assets/personal-loan/icons/tata.webp"
      },
      {
        "trustedPartnersId": "partner-5",
        "name": "Bajaj Allianz General",
        "logoUrl": "/assets/personal-loan/icons/general.webp"
      }
    ]
  },
  "faq": {
    "tabs": [
      {
        "id": "why-digital-gold",
        "label": "Why Digital Gold?",
        "content": "Digital gold offers secure investment with instant buying and selling.",
        "icon": "/assets/sidebar-faq/why-digital-gold.webp"
      },
      {
        "id": "how-digital-gold-works",
        "label": "How Digital gold works?",
        "content": "Start investing in gold digitally with just a few clicks.",
        "icon": "/assets/sidebar-faq/how-it-works.webp"
      },
      {
        "id": "other-questions",
        "label": "Other questions?",
        "content": "Find answers to all your questions about digital gold.",
        "icon": "/assets/sidebar-faq/other-questions.webp",
        "isExternal": true,
        "externalUrl": "https://help.abcd.com/personal-loan"
      }
    ]
  },
  "footer": {
    "referenceDetails": {
      "heading": "Powered by",
      "name": "Aditya Birla Capital Digital Ltd",
      "logo": "/assets/personal-loan/icons/abcfooter.webp",
      "certification": "Aditya Birla Capital Digital Ltd"
    },
    "sideLogoDetails": {
      "image": "/assets/personal-loan/icons/goldbag.webp",
      "alt": "Decorative footer waves"
    },
    "features": [
      { "id": "instant-offer", "text": "Get Instant Offer" },
      { "id": "no-paperwork", "text": "No Paperwork" },
      { "id": "low-interest", "text": "Lowest interest rate" }
    ]
  },
  "exclusiveEmployeeBanner": {
    "imageSrc": "",
    "mobileImageSrc": "",
    "imageAlt": "Exclusive Employee Offer"
  },
  "exclusiveBanner": {
    "imageSrc": "",
    "mobileImageSrc": "",
    "imageAlt": "Exclusive Offer"
  }
}
  ]
}
```
-----

## Complete JSON Structure with Data Types

> **Note:** Keep this structure aligned with dashboard components and fallback content.

```json
{
  "data": {
    "id": "number",
    "documentId": "string",
    "subProduct": "string",
    "partner": "string",
    "createdAt": "ISO 8601 timestamp",
    "updatedAt": "ISO 8601 timestamp",
    "publishedAt": "ISO 8601 timestamp",

    "header": {
      "id": "number",
      "logo": {
        "id": "number",
        "alt": "string",
        "size": "number",
        "src": "media_object"
      }
    },

    "hero": {
    "ctaText": "string",
    "eligibilityCriteria":[
      {
      "label": "string",
      "value": "string",
      }
    ],
    "highlighterContent": {
      "newJourney": {
        "title": "string",
        "subtitle": "string",
        "ctaText": "string",
        "illustrationSrc": "string",
        "redirectUrl": "string",
      },
      "resumeJourney": {
        "title": "string",
        "subtitle": "string",
        "ctaText": "string",
        "illustrationSrc": "string",
        "redirectUrl": "string",
      },
      "preApprovedOffer":{
        "title": "string",
        "subtitle": "string",
        "ctaText": "string",
        "illustrationSrc": "string",
        "redirectUrl": "string",
      },
      "exclusiveOffer":{
        "title": "string",
        "subtitle": "string",
        "ctaText": "string",
        "illustrationSrc": "string",
        "redirectUrl": "string",
      },
      "progress":{
        "title": "string",
        "subtitle": "string",
        "ctaText": "string",
        "illustrationSrc": "string",
        "redirectUrl": "string",
      },
      "success":{
        "title": "string",
        "subtitle": "string",
        "ctaText": "string",
        "illustrationSrc": "string",
        "redirectUrl": "string",
      },
      "failed":{
        "title": "string",
        "subtitle": "string",
        "ctaText": "string",
        "illustrationSrc": "string",
        "redirectUrl": "string",
      },
      "rejected":{
        "title": "string",
        "subtitle": "string",
        "ctaText": "string",
        "illustrationSrc": "string",
        "redirectUrl": "string",
      },
    }
   },
    "calculator": {
      "id": "number",
      "sectionTitle": "string",
      "title": "string",
      "description": "string",
      "ctaText": "string",
      "ctaAriaLabel": "string",
      "illustrationIcon": "media_object | null"
    },

    "getStarted": {
      "id": "number",
      "headingPrefix": "string",
      "headingHighlight": "string",
      "headingSuffix": "string",
      "cardBackground": "string (CSS gradient)",
      "cardBorder": "string (CSS border)",
      "items": [
        {
          "id": "number",
          "title": "string",
          "description": "string",
          "imageAlt": "string",
          "image": "media_object | null"
        }
      ]
    },

    "benefitBlock": {
      "id": "number",
      "footerText": "string",
      "footerLeftIcon": "media_object | null",
      "footerRightIcon": "media_object | null",
      "items": [
        {
          "id": "number",
          "text": "string",
          "icon": "media_object | null"
        }
      ]
    },

    "lenderLogos": [
      {
        "id": "number",
        "lenderLogoId": "number",
        "name": "string",
        "logoPath": "media"
      }
    ],

    "ratesAndCharges": {
      "ratesAndChargesId": "number",
      "text": "string",
      "cardBackground": "string (CSS gradient)",
      "cardBorder": "string (CSS border)",
      "items": [
        {
          "id": "number",
          "title": "string",
          "description": "string",
          "imageAlt": "string",
          "image": "media_object | null"
        }
      ]
    },

    "trustedPartners": {
      "id": "number",
      "title": "string",
      "subtitle": "string",
      "columns": [
        {
          "trustedPartnersId": "number",
          "name": "string",
          "highlighted": "boolean",
          "logoUrl": "string | media_object | null"
        }
      ]
    },

    "referralBanner": {
      "id": "number",
      "title": "string",
      "subtitle": "string",
      "termsText": "string",
      "isVisible": "boolean | null",
      "assets": {
        "id": "number",
        "treasureChest": "media_object | null",
        "goldCoin": "media_object | null",
        "chevron": "media_object | null"
      }
    },

    "exclusiveBanner": {
      "id": "number",
      "imageAlt": "string",
      "imageSrc": "media_object | null",
      "mobileImageSrc": "media_object | null"
    },

    "exclusiveEmployeeBanner": {
      "id": "number",
      "imageAlt": "string",
      "imageSrc": "media_object | null",
      "mobileImageSrc": "media_object | null"
    },

    "inlineInfoBanner": {
      "id": "number",
      "isVisible": "boolean",
      "text": "string",
      "highlightedText": "string",
      "iconAlt": "string",
      "iconSrc": "media_object ",
      "chevronSrc": "media_object ",
      "chevronAlt": "string | null",
      "backgroundColor": "string (hex color) | null",
      "borderColor": "string (hex color) | null",
      "textColor": "string (hex color) | null",
      "highlightedTextColor": "string (hex color) | null"
    },

    "faq": {
      "id": "number",
      "tabs": [
        {
          "id": "number",
          "label": "string",
          "content": "string",
          "isExternal": "boolean",
          "externalUrl": "string (URL)",
          "icon": "media_object | null"
        }
      ]
    },

    "footer": {
      "id": "number",
      "features": [
        {
          "id": "number",
          "text": "string"
        }
      ],
      "sideLogoDetails": {
        "id": "number",
        "alt": "string",
        "image": "media_object | null"
      },
      "referenceDetails": {
        "id": "number",
        "heading": "string",
        "name": "string",
        "certification": "string",
        "logo": "media_object | null"
      }
    },

    "plCalculatorSidebar": {
      "id": "number",
      "icons": {
        "id": "number",
        "helperBannerIcon": "string (relative path)",
        "emiCalculatorIcon": "string (relative path)",
        "loanAmountCalculatorIcon": "string (relative path)"
      },
      "labels": {
        "id": "number",
        "headerTitle": "string",
        "emiCalculatorHeaderTitle": "string",
        "loanAmountCalculatorHeaderTitle": "string",
        "helperBannerText": "string",
        "homeTitle": "string",
        "homeSubtitle": "string",
        "emiCalculatorOptionTitle": "string",
        "loanAmountCalculatorOptionTitle": "string",
        "tenureLabel": "string",
        "tenureSuffix": "string",
        "loanAmountLabel": "string",
        "emiAmountLabel": "string",
        "roiLabel": "string",
        "roiSuffix": "string",
        "currencySymbol": "string",
        "totalPayableLabel": "string",
        "estimatedEmiLabel": "string",
        "estimatedLoanAmountLabel": "string",
        "principalAmountLabel": "string",
        "interestAmountLabel": "string",
        "calculateButtonText": "string",
        "applyNowButtonText": "string",
        "disclaimerText": "string",
        "tenureValidationMessage": "string (with {min}, {max} placeholders)",
        "loanAmountValidationMessage": "string (with {min}, {max} placeholders)",
        "emiAmountValidationMessage": "string (with {min}, {max} placeholders)",
        "roiValidationMessage": "string (with {min}, {max} placeholders)"
      },
      "ranges": {
        "id": "number",
        "tenureMin": "number",
        "tenureMax": "number",
        "tenureDefault": "number",
        "loanAmountMin": "number",
        "loanAmountMax": "number",
        "loanAmountDefault": "number",
        "emiAmountMin": "number",
        "emiAmountMax": "number",
        "emiAmountDefault": "number",
        "roiMin": "number",
        "roiMax": "number",
        "roiDefault": "number"
      }
    }
  }
}
```

---

## Components Detail

### 1. dashboard.header-logo

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `alt` | string | Yes | "ABCD Logo" |
| `size` | number | No | 40 |
| `src` | media | Yes | - |

---

### 2. dashboard.calculator-section

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `sectionTitle` | string | Yes | "Financial tools & calculators" |
| `title` | string | Yes | - |
| `description` | string | Yes | - |
| `ctaText` | string | Yes | "Calculate" |
| `ctaAriaLabel` | string | No | - |
| `illustrationIcon` | media | No | null |

---

### 3. dashboard.get-started-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `title` | string | Yes | - |
| `description` | string | Yes | - |
| `imageAlt` | string | Yes | - |
| `image` | media | No | null |

---

### 4. dashboard.benefit-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `text` | string | Yes | - |
| `icon` | media | No | null |

---

### 5. dashboard.lender-logo

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `lenderLogoId` | number | Yes | - |
| `name` | string | Yes | - |
| `logoPath` | string | Yes | - |

---

### 6. dashboard.rate-charge-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `title` | string | Yes | - |
| `description` | string | Yes | - |
| `imageAlt` | string | Yes | - |
| `image` | media | No | null |

---

### 7. dashboard.trusted-partner

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `name` | string | Yes | - |
| `highlighted` | boolean | No | `false` |
| `logoUrl` | media | No | null |

---

### 8. dashboard.referral-banner-assets

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `treasureChest` | media | No | null |
| `goldCoin` | media | No | null |
| `chevron` | media | No | null |

---

### 9. dashboard.info-banner

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `isVisible` | boolean | No | `true` |
| `text` | string | Yes | - |
| `highlightedText` | string | Yes | - |
| `iconAlt` | string | No | - |
| `iconSrc` | media | No | null |
| `chevronSrc` | media | No | null |
| `chevronAlt` | string | No | null |
| `backgroundColor` | string (hex) | No | null |
| `borderColor` | string (hex) | No | null |
| `textColor` | string (hex) | No | null |
| `highlightedTextColor` | string (hex) | No | null |

---

### 10. dashboard.faq-tab

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `label` | string | Yes | - |
| `content` | text | Yes | - |
| `isExternal` | boolean | No | `false` |
| `externalUrl` | string (URL) | No | "" |
| `icon` | media | No | null |

---

### 11. dashboard.footer-feature

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `text` | string | Yes | - |

---

### 12. dashboard.logo-details

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `alt` | string | Yes | - |
| `image` | media | No | null |

---

### 13. dashboard.reference-details

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `heading` | string | Yes | - |
| `name` | string | Yes | - |
| `certification` | string | Yes | - |
| `logo` | media | No | null |

---

### 14. dashboard.calculator-icons

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `helperBannerIcon` | string (path) | Yes | - |
| `emiCalculatorIcon` | string (path) | Yes | - |
| `loanAmountCalculatorIcon` | string (path) | Yes | - |

---

### 15. dashboard.calculator-labels

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `headerTitle` | string | Yes | - |
| `emiCalculatorHeaderTitle` | string | Yes | - |
| `loanAmountCalculatorHeaderTitle` | string | Yes | - |
| `helperBannerText` | string | Yes | - |
| `homeTitle` | string | Yes | - |
| `homeSubtitle` | string | Yes | - |
| `emiCalculatorOptionTitle` | string | Yes | - |
| `loanAmountCalculatorOptionTitle` | string | Yes | - |
| `tenureLabel` | string | Yes | - |
| `tenureSuffix` | string | Yes | - |
| `loanAmountLabel` | string | Yes | - |
| `emiAmountLabel` | string | Yes | - |
| `roiLabel` | string | Yes | - |
| `roiSuffix` | string | Yes | - |
| `currencySymbol` | string | Yes | - |
| `totalPayableLabel` | string | Yes | - |
| `estimatedEmiLabel` | string | Yes | - |
| `estimatedLoanAmountLabel` | string | Yes | - |
| `principalAmountLabel` | string | Yes | - |
| `interestAmountLabel` | string | Yes | - |
| `calculateButtonText` | string | Yes | - |
| `applyNowButtonText` | string | Yes | - |
| `disclaimerText` | string | Yes | - |
| `tenureValidationMessage` | string | Yes | - |
| `loanAmountValidationMessage` | string | Yes | - |
| `emiAmountValidationMessage` | string | Yes | - |
| `roiValidationMessage` | string | Yes | - |

---

### 16. dashboard.calculator-ranges

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `tenureMin` | number | Yes | - |
| `tenureMax` | number | Yes | - |
| `tenureDefault` | number | Yes | - |
| `loanAmountMin` | number | Yes | - |
| `loanAmountMax` | number | Yes | - |
| `loanAmountDefault` | number | Yes | - |
| `emiAmountMin` | number | Yes | - |
| `emiAmountMax` | number | Yes | - |
| `emiAmountDefault` | number | Yes | - |
| `roiMin` | number | Yes | - |
| `roiMax` | number | Yes | - |
| `roiDefault` | number | Yes | - |

---