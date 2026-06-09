# Personal Loan Landing Page - Complete Schema Documentation

## Content-Type: Personal Loan Landing Page

**Collection Name:** `personal-loan-landing-pages`  
**Singular Name:** `personal-loan-landing-page`  
**Plural Name:** `personal-loan-landing-pages`  
**Draft & Publish:** Enabled

---

## All Content-Type Fields (Exact Strapi Field Names)

| Field Name | Type | Required | Default | Max | Description |
|------------|------|----------|---------|-----|-------------|
| `partner` | string | No | `default` | - | Optional partner-specific variant |
| `subProduct` | string | No | `personal` | - | Sub-product identifier (personal, business, etc.) |
| `header` | component | No | fallback | - | Header logo and branding configuration |
| `hero` | component | No | fallback | - | Hero section with call-to-action |
| `productHighlighters` | component[] | No | - | - | Flat array of product highlighters (key benefits) |
| `rates` | component | No | fallback | - | Rates & Charges section with loan details |
| `steps` | component | No | fallback | - | Process steps section (How to get loan) |
| `footer` | component | No | fallback | - | Footer details and features |
| `widget` | component | No | fallback | - | OTP verification widget configuration |
| `eligibility` | component | No | fallback | - | Eligibility criteria section |
| `simpleSection` | component | No | fallback | - | Simple benefits/features section with center image |
| `smartFeatures` | component | No | fallback | - | Smart feature highlights with auto-scroll |
| `appPromo` | component | No | fallback | - | App promotion section with QR and store links |
| `faq` | component | No | fallback | - | FAQ section with items and default opened IDs |
| `partners` | component | No | fallback | - | Trusted lending partners section |
| `mobileNavigation` | component | No | fallback | - | Mobile navigation configuration |

---

## API Endpoints & CMS Content Fetching

### Base URL
```
/api/personal-loan-landing-pages
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/personal-loan-landing-pages` | List all personal loan landing pages |
| GET | `/api/personal-loan-landing-pages/:id` | Get single landing page by ID |
| POST | `/api/personal-loan-landing-pages` | Create new landing page |
| PUT | `/api/personal-loan-landing-pages/:id` | Update landing page content |
| DELETE | `/api/personal-loan-landing-pages/:id` | Delete landing page |

### Query Parameters

**Filtering by Partner:**
```
?filters[partner][$eq]=default
?populate=*
```

**Full Personal Loan Landing Page Query:**
```
GET /api/personal-loan-landing-pages?
  filters[partner][$eq]=default&
  filters[subProduct][$eq]=personal&
  populate=*
```

**Partner-Specific Content:**
```
GET /api/personal-loan-landing-pages?
  filters[partner][$eq]=partner_name&
  filters[subProduct][$eq]=personal&
  populate=*
```

---

### Response Payload Structure

**Success Response (200 OK):**
```json
{
  "data": [
    {
      "id": 206,
      "documentId": "el6gfzd0wbmdncdmw55eczcm",
        "partner": "default",
        "subProduct": "personal",
        "header": {
    "logo": { "src": "${LOGOS_BASE}/abcd.svg", "alt": "ABCD Logo", "size": 40 },
    "mobileHeaderLogo": "${LOGOS_BASE}/abcd.svg"
  },
  "hero": {
    "slides": [
      {
        "id": "slide-1",
        "title": "Apply for a Instant Personal Loan Up to ₹15 Lakh, in Minutes!",
        "subtitle": "Access a wide variety of loan offers across multiple lenders.",
        "background": "/assets/landing/pl-herosection-bag.webp",
        "order": 1
      },
      {
        "id": "slide-2",
        "title": "Apply for a Personal Loan with Flexible Terms",
        "subtitle": "Choose from a variety of loan options tailored to your needs.",
        "background": "/assets/landing/pl-herosection-bag.webp",
        "order": 2
      },
      {
        "id": "slide-3",
        "title": "Join 2.5 Lakh+ borrowers",
        "subtitle": "Trusted by thousands for personal loans",
        "background": "/assets/landing/pl-herosection-bag.webp",
        "order": 3
      }
    ],
    "carouselConfig": {
      "autoPlay": true,
      "autoPlayInterval": 5000,
      "showArrows": true,
      "showIndicators": true,
      "indicatorStyle": "bars"
    },
    "backgroundVariant": "default",
    "productHighlighters": [
      { "id": "highlighter-1", "text": "Get Instant Offer", "showIcon": true, "order": 1 },
      { "id": "highlighter-2", "text": "No Paperwork", "showIcon": true, "order": 2 },
      { "id": "highlighter-3", "text": "Low interest rates", "showIcon": true, "order": 3 }
    ],
    "showSeparator": true
  },
  "widget": {
    "headerTitle": "Verified partners. <strong>100% transparent</strong>. Fully secure.",
    "headerBackgroundColor": "#7c2279",
    "title": "Enter your mobile number to get started",
    "mobileInputPlaceholder": "Enter 10-digit mobile number",
    "helperText": "OTP will be sent to your mobile number",
    "consentConfig": {
      "label": "I agree with",
      "termsText": "Terms & Conditions",
      "termsUrl": "https://www.adityabirlacapital.com/abc-digital/terms-conditions",
      "privacyText": "Privacy Policy",
      "privacyUrl": "https://www.adityabirlacapital.com/abcd/privacy-policy"
    },
    "ctaConfig": {
      "buttonText": "Apply now",
      "trustText": "Join 1L+ investors trusting ABCD for Personal Loans",
      "loadingText": "Processing..."
    }
  },
  "smartFeatures": {
    "title": "Smart Features. Real Impact.",
    "autoScroll": true,
    "autoScrollInterval": 5000,
    "items": [
      {
        "id": "pl-instant-offer",
        "variant": "gifting",
        "number": "01",
        "title": "Get Instant Offer",
        "subtitle": "Personalized loan assessment",
        "description": "Unlock your personalized loan offer in seconds with our smart AI assessment",
        "ctaText": "Apply Now",
        "backgroundColor": "#FFF8E7",
        "backgroundImage": "/assets/landing/pl-instant-offer-bg.webp",
        "order": 1,
        "notificationContent": {
          "icon": "bell",
          "headerText": "Your A/C can be credited with ₹30,000/-",
          "title": "",
          "bodyLines": []
        }
      },
      {
        "id": "pl-no-paperwork",
        "variant": "gifting",
        "number": "02",
        "title": "100% Digital Process",
        "subtitle": "Completely paperless",
        "description": "Complete your loan application entirely online without any physical documentation",
        "ctaText": "Start Application",
        "backgroundColor": "#E8F5E9",
        "backgroundImage": "/assets/landing/pl-instant-offer-bg.webp",
        "order": 2
      },
      {
        "id": "pl-quick-disbursal",
        "variant": "gifting",
        "number": "03",
        "title": "Quick Disbursal",
        "subtitle": "Fast fund transfer",
        "description": "Get funds credited directly to your account within 24 hours of approval",
        "ctaText": "Learn More",
        "backgroundColor": "#E3F2FD",
        "backgroundImage": "/assets/landing/pl-instant-offer-bg.webp",
        "order": 3
      }
    ]
  },
  "steps": {
    "tagline": "Personal Loan",
    "heading": "Get Your Loan in 3 Easy Steps",
    "items": [
      {
        "id": "step-1",
        "number": "1",
        "title": "Provide Basic Details",
        "description": "Share a few quick details to help us personalise your loan offer",
        "icon": "/assets/landing/document-11.webp",
        "iconurl": "/assets/landing/document-11.webp",
        "iconAlt": "Document icon"
      },
      {
        "id": "step-2",
        "number": "2",
        "title": "Choose & Apply Loan Offers",
        "description": "Pick the offer that best fits your needs and repayment plan.",
        "icon": "/assets/landing/filter-1.webp",
        "iconurl": "/assets/landing/filter-1.webp",
        "iconAlt": "Filter icon"
      },
      {
        "id": "step-3",
        "number": "3",
        "title": "Get instant Cash in Bank",
        "description": "Once approved, your loan is transferred directly to your bank account in minutes.",
        "icon": "/assets/landing/money-4.webp",
        "iconurl": "/assets/landing/money-4.webp",
        "iconAlt": "Money icon"
      }
    ]
  },
  "eligibility": {
    "title": "Personal Loan Eligibility",
    "items": [
      {
        "id": "age-limit",
        "label": "Age Limit",
        "value": "19 to 60 years",
        "alternateValueBackground": true
      },
      {
        "id": "income",
        "label": "Income",
        "value": "Min. ₹10,000/m",
        "alternateValueBackground": false
      },
      {
        "id": "residency",
        "label": "Residency",
        "value": "Resident of India",
        "alternateValueBackground": true
      }
    ]
  },
  "rates": {
    "title": "Rates & Charges",
    "items": [
      {
        "id": "rate-1",
        "icon": "/assets/landing/rate-pl-loan.webp",
        "title": "Loan Amount",
        "value": "Min. ₹25,000 and Max. 5 Lakhs",
        "description": "Min. ₹25,000 and Max. 5 Lakhs",
        "badge": "Best Rate"
      },
      {
        "id": "rate-2",
        "icon": "/assets/landing/rate-pl-repayment.webp",
        "title": "Repayment Tenure",
        "value": "12 months to 36 months",
        "description": "12 months to 36 months"
      },
      {
        "id": "rate-3",
        "icon": "/assets/landing/rate-pl-interest.webp",
        "title": "Rate of Interest",
        "value": "10.99% to 30% per annum",
        "description": "10.99% to 30% per annum",
        "badge": "Zero Charges"
      },
      {
        "id": "rate-4",
        "icon": "/assets/landing/rate-pl-delivery.webp",
        "title": "Free Insurance on Delivery",
        "value": "1.18% - 4.13% of Loan amount incl. GST.",
        "description": "1.18% - 4.13% of Loan amount incl. GST."
      }
    ]
  },
  "simpleSection": {
    "heading": "Personal Loans Made Simple, Fast & Transparent",
    "highlightWord": "Simple",
    "centerImageUrl": "/assets/personal-loan/icons/money_simple_lending.webp",
    "centerImageAlt": "Hands holding money bag with rupee symbol",
    "circleBackgroundUrl": "",
    "patternIconUrl": "/assets/personal-loan/icons/patternIconLending.webp",
    "backgroundColor": "#FFFFFF",
    "benefits": [
      {
        "benefitId": "benefit-1",
        "icon": "speed",
        "title": "Instant Approval",
        "description": "Get loan approval in minutes with our AI-powered assessment engine"
      },
      {
        "benefitId": "benefit-2",
        "icon": "security",
        "title": "Secure Process",
        "description": "Your data is encrypted and protected with bank-grade security"
      },
      {
        "benefitId": "benefit-3",
        "icon": "compare",
        "title": "Compare Offers",
        "description": "Access multiple lender offers in one place and choose the best"
      },
      {
        "benefitId": "benefit-4",
        "icon": "support",
        "title": "24/7 Support",
        "description": "Our customer support team is always available to help you"
      }
    ]
  },
  "partners": {
    "title": "Our Trusted Lending Partners",
    "subtitle": "We are associated with India's popular lenders",
    "items": [
      {
        "partnerId": "partner-1",
        "alt": "ICICI Lombard",
        "src": "/assets/personal-loan/icons/icic.webp"
      },
      {
        "partnerId": "partner-2",
        "alt": "ACKO",
        "src": "/assets/personal-loan/icons/acko.webp"
      },
      {
        "partnerId": "partner-3",
        "alt": "Digit",
        "src": "/assets/personal-loan/icons/digit.webp"
      },
      {
        "partnerId": "partner-4",
        "alt": "Tata AIG",
        "src": "/assets/personal-loan/icons/tata.webp"
      },
      {
        "partnerId": "partner-5",
        "alt": "Bajaj Allianz General",
        "src": "/assets/personal-loan/icons/general.webp"
      }
    ],
    "fallbackLogoSrc": ""
  },
  "faq": {
    "title": "Frequently Asked Questions",
    "defaultOpenIds": ["pl-faq-1"],
    "items": [
      {
        "id": "pl-faq-1",
        "question": "What is the maximum loan amount I can get?",
        "answer": "You can get a personal loan up to ₹15 Lakh, depending on your eligibility, income, and credit profile. The final amount will be determined by the lender based on their assessment."
      },
      {
        "id": "pl-faq-2",
        "question": "How quickly can I get the loan disbursed?",
        "answer": "Once your application is approved and all documents are verified, the loan amount is typically disbursed within 24 hours directly to your bank account."
      },
      {
        "id": "pl-faq-3",
        "question": "What documents are required for a personal loan?",
        "answer": "You need basic KYC documents: Aadhaar card, PAN card, bank statements for the last 3-6 months, and income proof (salary slips or ITR). Additional documents may be required based on the lender's policy."
      },
      {
        "id": "pl-faq-4",
        "question": "Can I prepay my personal loan without penalty?",
        "answer": "Yes, most lenders allow prepayment without any penalty charges. However, it's recommended to check the specific terms with your chosen lender before proceeding."
      },
      {
        "id": "pl-faq-5",
        "question": "What is the minimum credit score required?",
        "answer": "While requirements vary by lender, a credit score of 650 or above generally improves your chances of approval with better interest rates. Some lenders may approve loans with lower scores based on other factors."
      },
      {
        "id": "pl-faq-6",
        "question": "How is my loan eligibility calculated?",
        "answer": "Loan eligibility is calculated based on multiple factors including your monthly income, existing obligations, credit score, employment stability, and repayment capacity. Our AI-powered engine instantly assesses these factors to determine your eligibility."
      },
      {
        "id": "pl-faq-7",
        "question": "Can self-employed individuals apply for a personal loan?",
        "answer": "Yes, both salaried and self-employed individuals can apply. Self-employed applicants need to provide business proof, ITR for the last 2-3 years, and bank statements showing regular income."
      },
      {
        "id": "pl-faq-8",
        "question": "What happens if I miss an EMI payment?",
        "answer": "Missing an EMI can result in late payment charges and may negatively impact your credit score. It's important to contact your lender immediately if you're facing difficulty in making payments to discuss possible solutions."
      }
    ]
  },
  "appPromo": {
    "appLabel": "The ABCD app",
    "title": "Everything Finance\nas simple as\nABCD",
    "mobileTitle": "Everything Finance as simple as ABCD",
    "subtitle": "Download the ABCD app and start doing more with your money everyday",
    "mobileSubtitle": "Download the ABCD app today",
    "fromLabel": "From the house of",
    "houseLogoSrc": "/assets/vehicle-insurance/abcd-logo.webp",
    "houseLogoAlt": "ABCD Logo",
    "qrSrc": "/assets/vehicle-insurance/qr-code.webp",
    "qrAlt": "QR Code to download ABCD app",
    "phoneImageSrc": "/assets/gold-loan/gl-finanace.webp",
    "phoneImageAlt": "ABCD app showing personal loans",
    "ctaButtons": [
      {
        "label": "App Store",
        "link": "https://apps.apple.com/",
        "iconSrc": "/assets/mobile-nav/apple.webp",
        "iconAlt": "Apple App Store"
      },
      {
        "label": "Google Play",
        "link": "https://play.google.com/store",
        "iconSrc": "/assets/mobile-nav/google.webp",
        "iconAlt": "Google Play Store"
      }
    ],
    "ctaVisibility": "all",
    "companyInfoLayout": "column"
  },
  "footer": {
    "referenceDetails": {
      "heading": "Powered by",
      "name": "ABCD",
      "logo": "/assets/landing/Grouping.webp",
      "certification": "A Aditya Birla Capital Company - ISO 27001:2013 certified."
    },
    "sideLogoDetails": {
      "image": "/assets/landing/pl-footer-money.webp",
      "alt": "Money bag with coins"
    },
    "features": [
      { "id": "footer-feature-1", "text": "Get Instant Offer" },
      { "id": "footer-feature-2", "text": "No Paperwork" },
      { "id": "footer-feature-3", "text": "Lowest interest rate" }
    ]
  },
  "mobileNavigation": {
    "tabs": [],
    "footerBanner": {
      "text": "Download the app",
      "appStoreButton": { "icon": "apple", "label": "App Store", "url": "https://apps.apple.com" },
      "playStoreButton": { "icon": "google", "label": "Play Store", "url": "https://play.google.com" }
    }
  }
      
    }
  ]
}
```

---

## Complete JSON Structure with Data Types

> **Note:** Keep this structure aligned with landing page components and fallback content.

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
      "logo": {
        "id": "number",
        "alt": "string",
        "size": "number",
        "src": "Media"
      },
      "mobileHeaderLogo": "Media"
    },

    "hero": {
      "slides": [
        {
          "id": "string",
          "title": "string",
          "subtitle": "string",
          "background": "media",
          "order": "number"
        }
      ],
      "carouselConfig": {
        "autoPlay": "boolean",
        "autoPlayInterval": "number (milliseconds)",
        "showArrows": "boolean",
        "showIndicators": "boolean",
        "indicatorStyle": "string (enum: 'dots' | 'bars')"
      },
      "backgroundVariant": "string (enum: 'default' | 'light')",
      "productHighlighters": [
        {
          "id": "string",
          "text": "string",
          "showIcon": "boolean",
          "order": "number"
        }
      ],
      "showSeparator": "boolean"
    },

    "rates": {
      "id": "number",
      "title": "string",
      "items": [
        {
          "id": "number",
          "title": "string",
          "value": "string",
          "description": "string",
          "badge": "string",
          "rateId": "string",
          "icon": "media_object | null"
        }
      ]
    },

    "steps": {
      "id": "number",
      "tagline": "string",
      "heading": "string",
      "items": [
        {
          "id": "number",
          "number": "string",
          "title": "string",
          "description": "string",
          "iconAlt": "string",
          "icon": "media_object | null",
          "iconUrl": "media_object | null"
        }
      ]
    },

    "footer": {
      "id": "number",
      "referenceHeading": "string | null",
      "referenceName": "string | null",
      "referenceCertification": "string | null",
      "sideImageAlt": "string | null",
      "features": [
        {
          "id": "number",
          "text": "string"
        }
      ],
      "sideImage": "media_object | null",
      "referenceLogo": "media_object | null"
    },

  "widget": {
    "headerTitle": "string",
    "headerBackgroundColor": "string",
    "title": "string",
    "mobileInputPlaceholder": "string",
    "helperText": "string",
    "consentConfig": {
      "label": "string",
      "termsText": "string",
      "termsUrl": "string",
      "privacyText": "string",
      "privacyUrl": "string"
    },
    "ctaConfig": {
      "buttonText": "string",
      "trustText": "string",
      "loadingText": "string"
    }
  },

    "eligibility": {
      "id": "number",
      "title": "string",
      "items": [
        {
          "id": "number",
          "label": "string",
          "value": "string",
          "alternateValueBackground": "boolean"
        }
      ]
    },

    "simpleSection": {
      "id": "number",
      "heading": "string",
      "highlightWord": "string",
      "centerImageAlt": "string",
      "circleBackgroundUrl": "string",
      "backgroundColor": "string (hex color)",
      "benefits": [
        {
          "benefitId": "number",
          "icon": "string",
          "title": "string",
          "description": "string"
        }
      ],
      "centerImageUrl": "media_object | null",
      "patternIconUrl": "media_object | null"
    },

    "smartFeatures": {
      "id": "number",
      "title": "string",
      "autoScroll": "boolean",
      "autoScrollInterval": "number (milliseconds)",
      "items": [
        {
          "order": "number",
          "id": "number",
          "variant": "string",
          "number": "string",
          "title": "string",
          "subtitle": "string",
          "description": "string (multiline)",
          "ctaText": "string",
          "backgroundColor": "string (hex color)",
          "backgroundImage": "media_object",
          "notificationContent": {
            "id": "number",
            "icon": "string",
            "headerText": "string",
            "title": "string",
            "bodyLines": ["string"]
          } | null
        }
      ]
    },

    "appPromo": {
      "id": "number",
      "appLabel": "string",
      "title": "string (multiline)",
      "mobileTitle": "string",
      "subtitle": "string",
      "mobileSubtitle": "string",
      "fromLabel": "string",
      "houseLogoAlt": "string",
      "qrAlt": "string",
      "phoneImageAlt": "string",
      "ctaVisibility": "string (enum: all, authenticated, unauthenticated)",
      "companyInfoLayout": "string (enum: row, column)",
      "qrSrc": "media_object | null",
      "ctaButtons": [
        {
          "id": "number",
          "label": "string",
          "link": "string (URL)",
          "iconAlt": "string",
          "iconSrc": "media_object | null"
        }
      ],
      "houseLogoSrc": "media_object | null",
      "phoneImageSrc": "media_object | null"
    },

    "faq": {
      "id": "number",
      "title": "string",
      "defaultOpenIds": ["string"],
      "viewMoreButtonText": "string | null",
      "disclaimerLabel": "string | null",
      "disclaimerText": "string | null",
      "viewLessButtonText": "string | null",
      "tabs": [],
      "items": [
        {
          "id": "number",
          "question": "string",
          "answer": "string (multiline)"
        }
      ]
    },

    "partners": {
      "id": "number",
      "title": "string",
      "subtitle": "string",
      "items": [
        {
          "partnerId": "number",
          "name": "string",
          "highlighted": "boolean",
          "logoUrl": "string | media_object | null"
        }
      ]
    },
    
    "securityFeatures": "object | null",
    "sectionLabels": "object | null",

    "mobileNavigation": {
      "id": "number",
      "tabs": ["string"],
      "footerBannerText": "string | null",
      "appStoreButton": {
        "icon": "mediaObject",
        "label": "string",
        "url": "string"
      },
      "playStoreButton": {
        "icon": "mediaObject",
        "label": "string",
        "url": "string"
      }
    }
  }
}
```

---

## Components Detail

### 1. pl-landing.header-logo

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `alt` | string | Yes | "ABCD Logo" |
| `size` | number | No | 40 |
| `src` | media/string | Yes | - |

---

### 2. pl-landing.product-highlighter

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `order` | number | No | - |
| `id` | string | Yes | - |
| `text` | string | Yes | - |
| `showIcon` | boolean | No | `true` |

---

### 2a. pl-landing.hero-slide

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `title` | string | Yes | - |
| `subtitle` | string | Yes | - |
| `background` | media | Yes | - |
| `order` | number | Yes | - |

---

### 2b. pl-landing.carousel-config

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `autoPlay` | boolean | No | `true` |
| `autoPlayInterval` | number | No | `5000` |
| `showArrows` | boolean | No | `true` |
| `showIndicators` | boolean | No | `true` |
| `indicatorStyle` | enum | No | `dots` |

**Enum values (indicatorStyle):** `dots`, `bars`

---

### 2c. pl-landing.hero

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `slides` | component[] | Yes | - |
| `carouselConfig` | component | Yes | - |
| `backgroundVariant` | enum | No | `default` |
| `productHighlighters` | component[] | No | [] |
| `showSeparator` | boolean | No | `true` |

**Enum values (backgroundVariant):** `default`, `light`

---

### 4. pl-landing.rate-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `title` | string | Yes | - |
| `value` | string | Yes | - |
| `description` | string | No | "" |
| `badge` | string | No | "" |
| `rateId` | string | Yes | - |
| `icon` | media/string | No | null |

---

### 5. pl-landing.step-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `number` | string | Yes | - |
| `title` | string | Yes | - |
| `description` | string | Yes | - |
| `iconAlt` | string | No | "" |
| `icon` | media/string | No | null |
| `iconUrl` | media/string | No | null |

---

### 6. pl-landing.footer-feature

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `text` | string | Yes | - |

---

### 7. pl-landing.widget

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `headerTitle` | string (HTML) | No | "" |
| `headerBackgroundColor` | string (hex) | No | "#7c2279" |
| `title` | string | Yes | - |
| `mobileInputPlaceholder` | string | No | "Enter 10-digit mobile number" |
| `helperText` | string | No | "OTP will be sent to your mobile number" |
| `consentConfig` | component | No | null |
| `ctaConfig` | component | No | null |


---

### 8. pl-landing.eligibility-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `label` | string | Yes | - |
| `value` | string | Yes | - |
| `alternateValueBackground` | boolean | No | `false` |

---

### 9. pl-landing.benefit

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `benefitId` | number | Yes | - |
| `icon` | string | Yes | - |
| `title` | string | Yes | - |
| `description` | string | Yes | - |

---

### 10. pl-landing.smart-feature-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `order` | number | No | - |
| `id` | number | Yes | - |
| `variant` | string | No | "" |
| `number` | string | Yes | - |
| `title` | string | Yes | - |
| `subtitle` | string | No | "" |
| `description` | string | Yes | - |
| `ctaText` | string | Yes | - |
| `backgroundColor` | string (hex) | No | "#FFF4CE" |
| `backgroundImage` | media_object | No | null |
| `notificationContent` | component | No | null |

---

### 11. pl-landing.notification-content

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `icon` | string | Yes | - |
| `headerText` | string | Yes | - |
| `title` | string | No | "" |
| `bodyLines` | string[] | Yes | - |

---

### 12. pl-landing.cta-button

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `label` | string | Yes | - |
| `link` | string (URL) | Yes | - |
| `iconAlt` | string | No | "" |
| `iconSrc` | media/string | No | null |

---

### 13. pl-landing.faq-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `question` | string | Yes | - |
| `answer` | text | Yes | - |

---

### 14. pl-landing.app-promo

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | number | Yes | - |
| `appLabel` | string | Yes | - |
| `title` | string (multiline) | Yes | - |
| `mobileTitle` | string | Yes | - |
| `subtitle` | string | No | "" |
| `mobileSubtitle` | string | No | "" |
| `fromLabel` | string | No | "" |
| `houseLogoAlt` | string | No | "" |
| `qrAlt` | string | No | "" |
| `phoneImageAlt` | string | No | "" |
| `ctaVisibility` | enum | No | "all" |
| `companyInfoLayout` | enum | No | "column" |
| `qrSrc` | media/string | No | null |
| `houseLogoSrc` | media/string | No | null |
| `phoneImageSrc` | media/string | No | null |
| `ctaButtons` | component[] | No | [] |


------

## Content Fields Usage Examples

### Hero Section Configuration
```json
{
  "hero": {
    "slides": [
      {
        "id": "slide-1",
        "title": "Apply for a Instant Personal Loan Up to ₹15 Lakh, in Minutes!",
        "subtitle": "Access a wide variety of loan offers across multiple lenders.",
        "background": "https://cdn.abcd.io/assets/landing/pl-herosection-bag.webp",
        "order": 1
      },
      {
        "id": "slide-2",
        "title": "Apply for a Personal Loan with Flexible Terms",
        "subtitle": "Choose from a variety of loan options tailored to your needs.",
        "background": "https://cdn.abcd.io/assets/landing/pl-herosection-bag.webp",
        "order": 2
      },
      {
        "id": "slide-3",
        "title": "Join 2.5 Lakh+ borrowers",
        "subtitle": "Trusted by thousands for personal loans",
        "background": "https://cdn.abcd.io/assets/landing/pl-herosection-bag.webp",
        "order": 3
      }
    ],
    "carouselConfig": {
      "autoPlay": true,
      "autoPlayInterval": 5000,
      "showArrows": true,
      "showIndicators": true,
      "indicatorStyle": "bars"
    },
    "backgroundVariant": "default",
    "productHighlighters": [
      {
        "id": "highlighter-1",
        "text": "Get Instant Offer",
        "showIcon": true,
        "order": 1
      },
      {
        "id": "highlighter-2",
        "text": "No Paperwork",
        "showIcon": true,
        "order": 2
      },
      {
        "id": "highlighter-3",
        "text": "Low interest rates",
        "showIcon": true,
        "order": 3
      }
    ],
    "showSeparator": true
  }
}
```

### Rates & Charges Configuration
```json
{
  "rates": {
    "id": 95,
    "title": "Rates & Charges",
    "items": [
      {
        "id": 362,
        "title": "Loan Amount",
        "value": "Min. ₹25,000 and Max. 5 Lakhs",
        "description": "Min. ₹25,000 and Max.\n5 Lakhs",
        "rateId": "1",
        "icon": null
      }
    ]
  }
}
```

### Smart Features with Auto-Scroll
```json
{
  "smartFeatures": {
    "id": 95,
    "title": "Smart Features. Real Impact.",
    "autoScroll": true,
    "autoScrollInterval": 5000,
    "items": [
      {
        "order": 1,
        "id": 353,
        "variant": "gifting",
        "number": "01",
        "title": "Get Instant Offer",
        "subtitle": "Personalized loan assessment",
        "description": "Unlock your personalized loan offer in seconds",
        "ctaText": "Apply Now",
        "backgroundColor": "#FFF4CE",
        "backgroundImage": "media_object",
        "notificationContent": {
          "id": 54,
          "icon": "bell",
          "headerText": "Your A/C can be credited with ₹30,000/-",
          "bodyLines": [
            "Funds will be credited within 24 hours",
            "Loan disbursal subject to verification"
          ]
        }
      }
    ]
  }
}
```

### Widget Configuration
```json
{
  "widget": {
    "headerTitle": "Verified partners. <strong>100% transparent</strong>. Fully secure.",
    "headerBackgroundColor": "#7c2279",
    "title": "Enter your mobile number to get started",
    "mobileInputPlaceholder": "Enter 10-digit mobile number",
    "helperText": "OTP will be sent to your mobile number",
    "consentConfig": {
      "label": "I agree with",
      "termsText": "Terms & Conditions",
      "termsUrl": "https://www.adityabirlacapital.com/abc-digital/terms-conditions",
      "privacyText": "Privacy Policy",
      "privacyUrl": "https://www.adityabirlacapital.com/abcd/privacy-policy",
    },
    "ctaConfig": {
      "buttonText": "Apply now",
      "trustText": "Join 1L+ investors trusting ABCD for Personal Loans",
      "loadingText": "Processing...",
    },
  },
}
```

### App Promotion Configuration
```json
{
  "appPromo": {
    "id": 84,
    "appLabel": "The ABCD app",
    "title": "Choose from 100+ \nCredit Cards tailored \nfor your needs",
    "mobileTitle": "Choose from 100+ credit Cards tailored for your needs",
    "subtitle": "From the list of recommended cards for you",
    "fromLabel": "From the house of",
    "ctaVisibility": "all",
    "companyInfoLayout": "column",
    "ctaButtons": [
      {
        "id": 167,
        "label": "App Store",
        "link": "https://apps.apple.com/",
        "iconAlt": "Apple App Store"
      },
      {
        "id": 168,
        "label": "Play Store",
        "link": "https://play.google.com/store/apps?hl=en_IN",
        "iconAlt": "Google Play Store"
      }
    ]
  }
}
```

### FAQ Configuration
```json
{
  "faq": {
    "id": 108,
    "title": "Frequently Asked Questions",
    "defaultOpenIds": ["pl-faq-1"],
    "viewMoreButtonText": null,
    "disclaimerLabel": null,
    "tabs": [],
    "items": [
      {
        "id": 702,
        "question": "Who can participate in the program?",
        "answer": "The program is open to eligible individuals meeting our criteria."
      }
    ]
  }
}
```
---
