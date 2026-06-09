# Health Insurance Landing Page - Complete Schema Documentation

## Content-Type: Health Insurance Landing Page

**Collection Name:** `health-insurance-landing-pages`  
**Singular Name:** `health-insurance-landing-page`  
**Plural Name:** `health-insurance-landing-pages`  
**Draft & Publish:** Enabled

---

## All Content-Type Fields (Exact Strapi Field Names)

| Field Name | Type | Required | Default | Max | Description |
|------------|------|----------|---------|-----|-------------|
| `partner` | string | No | `default` | - | Optional partner-specific variant |
| `header` | component | No | fallback | - | Header logo and branding configuration |
| `newsTicker` | component | No | fallback | - | News ticker/announcements section configuration |
| `newsItems` | component | No | fallback | - | News ticker items source (`content[]`) |
| `promoBannerHealth` | component | No | fallback | - | Promotional banner with CTA |
| `hero` | component | No | fallback | - | Hero section with slides and carousel config |
| `heroSlides` | component[] | No | - | - | Optional flat hero slides array |
| `productHighlighters` | component[] | No | - | - | Optional flat product highlighters array |
| `smartFeaturesHealth` | component | No | fallback | - | Smart feature highlights |
| `smartFeaturesTitle` | string | No | fallback | - | Smart features section title |
| `motorCriticalProps` | component | No | fallback | - | Why buy online section with statistics |
| `howMotorWorksTabs` | component[] | No | fallback | - | Health coverage benefits tabs/accordion |
| `howMotorWorksTitle` | string | No | fallback | - | Benefits section title |
| `howMotorWorkAddOnsTabs` | component[] | No | fallback | - | Add-on riders and optional covers tabs |
| `howMotorWorkAddOnsTitle` | string | No | fallback | - | Add-ons section title |
| `whyDoYouNeedProps` | component | No | fallback | - | Why you need health insurance section content |
| `howToChooseProps` | component | No | fallback | - | How to choose the right plan section content |
| `widget` | component | No | fallback | - | OTP verification widget configuration |
| `widgetConsent` | component | No | - | - | Optional alternate consent source |
| `howItsWorkStepsProps` | component | No | fallback | - | 3-step process: Get Quote, Compare, Pay & Get Policy |
| `claimProcessProps` | component | No | fallback | - | Claim process section with cashless and reimbursement flows |
| `whatAffectYourProps` | component | No | fallback | - | Premium factors section |
| `planCoverHeading` | string | No | fallback | - | Plan coverage section heading |
| `planCoverSubheading` | string | No | fallback | - | Plan coverage section subheading |
| `planCoverComparisonColumns` | component[] | No | fallback | - | Plan coverage comparison table column definitions |
| `planCoverComparisonRows` | component[] | No | fallback | - | Plan coverage comparison table row data |
| `faq` | component | No | fallback | - | FAQ section with items and default opened IDs |
| `faqItems` | component[] | No | - | - | Optional flat FAQ array (legacy/alternate input) |
| `defaultOpenFaqIds` | json | No | `[]` | - | Optional FAQ default-open ids (legacy/alternate input) |
| `footer` | component | No | fallback | - | Footer details, features, and branding |
| `footerFeatures` | component[] | No | - | - | Optional alternate footer features input |
| `sectionsEnabled` | component | No | fallback | - | Boolean flags to enable/disable page sections |

---

## API Endpoints & CMS Content Fetching

### Base URL
```
/api/health-insurance-landing-pages
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/health-insurance-landing-pages` | List all health insurance landing pages |
| GET | `/api/health-insurance-landing-pages/:id` | Get single landing page by ID |
| POST | `/api/health-insurance-landing-pages` | Create new landing page |
| PUT | `/api/health-insurance-landing-pages/:id` | Update landing page content |
| DELETE | `/api/health-insurance-landing-pages/:id` | Delete landing page |

### Query Parameters

**Filtering by Partner:**
```
?filters[partner][$eq]=default
?populate=*
```

**Full Health Landing Page Query:**
```
GET /api/health-insurance-landing-pages?
  filters[partner][$eq]=default&
  populate=*
```

**Partner-Specific Content (e.g., HDFC bank partner):**
```
GET /api/health-insurance-landing-pages?
  filters[partner][$eq]=hdfc&
  populate=*
```

---

### Response Payload Structure

**Success Response (200 OK):**
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "abc123xyz",
      "attributes": {
        "partner": "default",
        "header": {
          "logo": {
            "src": "https://cdn.abcd.io/logo.webp",
            "alt": "ABCD Logo"
          }
        },
        "newsTicker": {
          "badge": {
            "text": "NEWS",
            "backgroundColor": "#9F1B22",
            "textColor": "#FFFFFF"
          },
          "backgroundColor": "#F9FAFB",
          "textColor": "#414042",
          "ariaLabel": "Health insurance announcements"
        },
        "newsItems": {
          "enabled": true,
          "content": [
            {
              "id": 738,
              "text": "Check out the latest App Exclusive plan and other health plans.",
              "order": 1
            }
          ]
        },
        "smartFeaturesTitle": "Smart Features. Real Impact.",
        "howMotorWorksTitle": "Key Benefits You Get",
        "howMotorWorkAddOnsTitle": "Enhance Your Protection with Add-Ons",
        "planCoverHeading": "What Our Plans Cover",
        "planCoverSubheading": "Different types of Motor Insurance plans have different features and benefits. Have a look at their comparative analysis."
      }
    }
  ]
}
```

---


## Complete JSON Structure with enabled/order fields

> **Note:** Keep this structure aligned with LandingClient.jsx and fallback content.  
> **Note:** For repeatable arrays, use `order` in each item when ordering matters.

```json
{
  "data": {
    "partner": "default",

    "header": {
      "logo": {
        "src": "media_or_url",
        "alt": "ABCD Logo",
        "size": "default"
      },
      "mobileHeaderLogo": {
        "src": "media_or_url",
        "alt": "ABCD Logo"
      }
    },

    "newsTicker": {
      "badge": {
        "text": "NEWS",
        "backgroundColor": "#9F1B22",
        "textColor": "#FFFFFF"
      },
      "backgroundColor": "#F9FAFB",
      "textColor": "#414042",
      "ariaLabel": "Health insurance announcements"
    },

    "newsItems": {
      "enabled": true,
      "content": [
        {
          "id": "health-1",
          "text": "Check out the latest App Exclusive plan and other health plans.",
          "order": 1
        }
      ]
    },

    "promoBannerHealth": {
      "imageSrc": "media_or_url",
      "imageAlt": "Health insurance shield",
      "title": "Introducing ActivOne MAX Economy!",
      "subtitle": "Check out the latest App Exclusive plan and other health plans.",
      "subtitleColor": "#FFFFFF",
      "ctaLabel": "Insure now",
      "background": "linear-gradient(90deg, #7C2279 14.822%, #FCCA67 72.785%)"
    },

    "hero": {
      "slides": [
        {
          "id": "1",
          "title": "Get Affordable Health Insurance for Every Family's Needs",
          "subtitle": "Protect your health, safeguard your savings, and enjoy complete peace of mind. Health insurance plans starting at around Rs 450/month.",
          "background": "media_or_url",
          "order": 1
        }
      ],
      "productHighlighters": [
        {
          "id": "1",
          "text": "2.5 Crore+ lives insured",
          "showIcon": true,
          "order": 1
        }
      ]
    },

    "smartFeaturesHealth": {
      "items": [
        {
          "id": "hi-smart-feature-1",
          "number": "01",
          "title": "Upto 100% HealthReturns",
          "description": "Get 100% premium back as HealthReturns for healthcare spends. Use it for medicines, tests, consults & wellness.",
          "ctaText": "Insure now",
          "backgroundColor": "#f9fafb",
          "backgroundImage": "media_or_url",
          "order": 1
        }
      ]
    },
    "smartFeaturesTitle": "Smart Features. Real Impact.",

    "motorCriticalProps": {
      "title": "Why Buy Online?",
      "subtitle": "Buying health insurance online is secure, quick, and convenient.",
      "leftSection": {
        "iconUrl": "media_or_url",
        "iconAlt": "Why buy online illustration",
        "title": "Why Buy Online?",
        "description": "Purchasing health insurance online is not only secure, quick, and convenient, but it also offers a wide range of options tailored to your needs."
      },
      "statistics": [
        {
          "id": "realtime-premium-quotes",
          "value": "Real-time premium quotes",
          "description": "Get instant premium estimates based on your age, location, and coverage preferences.",
          "iconUrl": "media_or_url",
          "iconAlt": "Real-time premium quotes icon",
          "order": 1
        }
      ]
    },

    "howMotorWorksTabs": [
      {
        "tabsId": "cashless-treatment-across-india",
        "label": "Cashless Treatment Across India",
        "steps": [
          {
            "number": 1,
            "text": "Get treatment without paying upfront with access to network hospitals."
          }
        ],
        "image": "media_or_url",
        "order": 1
      }
    ],
    "howMotorWorksTitle": "Key Benefits You Get",

    "howMotorWorkAddOnsTabs": [
      {
        "tabsId": "opd-coverage",
        "label": "OPD Coverage",
        "steps": [
          {
            "number": 1,
            "text": "Covers outpatient expenses such as consultations, diagnostics, and medicines."
          }
        ],
        "image": "media_or_url",
        "order": 1
      }
    ],
    "howMotorWorkAddOnsTitle": "Enhance Your Protection with Add-Ons",

    "whyDoYouNeedProps": {
      "headingPrefix": "Why Do You Need Health",
      "headingHighlight": "Insurance?",
      "introText": "Protect your health, safeguard your savings, and enjoy complete peace of mind.",
      "detailText": "In today's world of rising medical costs and lifestyle-related conditions, even a routine procedure can strain your finances.",
      "benefits": [
        {
          "id": "benefit-1",
          "text": "Protects your savings from unexpected medical expenses"
        }
      ],
      "heroImageSrc": "media_or_url",
      "heroImageAlt": "Health insurance illustration",
      "bulletIconSrc": "media_or_url",
      "bulletIconAlt": "Benefit bullet"
    },

    "howToChooseProps": {
      "heading": "How to Choose the Right Plan?",
      "subheading": "Picking the right plan is necessary to protect your lifestyle and needs.",
      "note": "A slightly higher premium often offers significantly more protection.",
      "items": [
        {
          "id": "coverage-needs",
          "title": "Coverage needs",
          "description": "Is it for yourself, family, or senior parents?",
          "iconSrc": "media_or_url"
        }
      ],
      "iconBadgeAlt": "Icon badge",
      "backgroundPatternAlt": "Section background pattern"
    },

    "howItsWorkStepsProps": {
      "eyebrow": "Insurance, simplified",
      "title": "How It Works - 3 Simple Steps",
      "steps": [
        {
          "id": "step-get-quote",
          "title": "Get Quote",
          "description": "Enter ages and coverage details to receive instant premium options.",
          "iconSrc": "media_or_url",
          "iconAlt": "Get quote icon",
          "order": 1
        }
      ]
    },

    "claimProcessProps": {
      "title": "Claim Process",
      "subtitle": "Medical emergencies are hard, claims should not be.",
      "items": [
        {
          "id": "cashless-claim",
          "title": "Cashless Claim",
          "description": "Visit a network hospital and complete pre-authorization.",
          "imageSrc": "media_or_url",
          "imageAlt": "Cashless claim illustration",
          "imageBackground": "#FFF0E9",
          "overlayIconSrc": "media_or_url",
          "overlayIconAlt": "Claim approved icon",
          "order": 1
        }
      ]
    },

    "whatAffectYourProps": {
      "title": "What Affects Your Premium?",
      "subtitle": "Buying health insurance online is secure, quick, and convenient.",
      "items": [
        {
          "id": "age-and-medical-history",
          "title": "Age and medical history",
          "description": "Age and pre-existing health risks influence premium pricing.",
          "iconSrc": "media_or_url",
          "iconAlt": "Age and medical history icon"
        }
      ]
    },

    "planCoverHeading": "What Our Plans Cover",
    "planCoverSubheading": "Different types of Motor Insurance plans have different features and benefits. Have a look at their comparative analysis.",

    "planCoverComparisonColumns": [
      {
        "id": "description",
        "title": "Description",
        "isHighlighted": true,
        "headerBackground": "#FFD56C",
        "borderColor": "#FFD56C"
      }
    ],

    "planCoverComparisonRows": [
      {
        "id": "eligibility",
        "label": "Eligibility",
        "values": [
          {
            "text": "Indian residents aged 18-65 years; children aged 91 days+ can be covered with an adult.",
            "color": "#2e2e2e",
            "weight": "regular"
          }
        ]
      }
    ],

    "widget": {
      "headerTitle": "<strong>Health insurance</strong> made <strong>simple, fast &amp; transparent</strong>",
      "title": "Take the first step to better health",
      "maxResendAttempts": 3,
      "maxResendMessage": "Maximum resend attempts reached. Please try again later.",
      "insuranceOptions": [
        {
          "optionId": "buy-new-health-plan",
          "label": "Buy a new health plan",
          "value": "Buy a new health plan"
        }
      ],
      "consentConfig": {
        "label": "I agree with",
        "termsText": "Terms and Conditions",
        "termsUrl": "/terms",
        "privacyText": "Privacy Policy",
        "privacyUrl": "/privacy"
      },
      "ctaConfig": {
        "buttonText": "Get Insured Now",
        "otpButtonText": "Verify OTP",
        "trustText": "Join families trusting ABCD for health coverage."
      }
    },

    "faq": {
      "title": "Frequently Asked Questions",
      "defaultOpenIds": ["1"],
      "items": [
        {
          "itemsId": "1",
          "question": "What is health insurance and why is it important?",
          "answer": "Health insurance helps cover medical expenses and reduces financial burden.",
          "order": 1
        }
      ]
    },

    "footer": {
      "referenceDetails": {
        "heading": "Powered by",
        "name": "ABCD",
        "logo": "media_or_url"
      },
      "sideLogoDetails": {
        "image": "media_or_url",
        "alt": "Health icon"
      },
      "features": [
        {
          "featuresId": "1",
          "text": "2.5 Crore+ lives insured"
        }
      ]
    },

    "sectionsEnabled": {
      "newsItems": true,
      "promoBannerHealth": true,
      "heroSlides": true,
      "productHighlighters": true,
      "smartFeaturesHealth": true,
      "howMotorWorksTabs": true,
      "whyDoYouNeed": true,
      "howToChoose": true,
      "motorCritical": true,
      "howMotorWorkAddOnsTabs": true,
      "whatAffectYour": true,
      "planCoverComparison": true,
      "howItsWorkSteps": true,
      "claimProcess": true,
      "faq": true,
      "footer": true
    }
  }
}
```

---

## Components Detail

### 1. health-landing.header-logo

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `src` | media/string | Yes | - |
| `alt` | string | Yes | "ABCD Logo" |
| `size` | enum | No | "default" |

**Enum values:** `small`, `default`, `large`

---

### 2. health-landing.news-ticker-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `text` | string | Yes | - |
| `order` | number | No | - |

---

### 3. health-landing.hero-slide

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `title` | string | Yes | - |
| `subtitle` | string | No | "" |
| `background` | media/string | No | - |
| `order` | number | No | - |

---

### 4. health-landing.product-highlighter

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `text` | string | Yes | - |
| `showIcon` | boolean | No | `true` |
| `order` | number | No | - |

---

### 5. health-landing.smart-feature

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `number` | string | No | "" |
| `title` | string | Yes | - |
| `description` | string | No | "" |
| `ctaText` | string | No | "Insure now" |
| `backgroundColor` | string | No | "#f9fafb" |
| `backgroundImage` | media/string | No | - |
| `order` | number | No | - |

**Note:** The `variant` field is mapped to `common` in the transformer and is not CMS-configurable.

---

### 6. health-landing.statistic-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `value` | string | Yes | - |
| `description` | string | No | "" |
| `iconUrl` | media/string | No | - |
| `iconAlt` | string | No | "" |
| `order` | number | No | - |

---

### 7. health-landing.how-it-works-tab

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `tabsId` | string | Yes | - |
| `label` | string | Yes | - |
| `steps` | component[] | Yes | - |
| `image` | media/string | No | - |
| `order` | number | No | - |

---

### 8. health-landing.step-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `number` | number | Yes | - |
| `text` | string | Yes | - |

---

### 9. health-landing.claim-process-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `title` | string | Yes | - |
| `description` | text | Yes | - |
| `imageSrc` | media/string | No | - |
| `imageAlt` | string | No | "" |
| `imageBackground` | string | No | - |
| `overlayIconSrc` | media/string | No | - |
| `overlayIconAlt` | string | No | "" |
| `order` | number | No | - |

---

### 10. health-landing.premium-factor

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `title` | string | Yes | - |
| `description` | string | No | "" |
| `iconSrc` | media/string | No | - |
| `iconAlt` | string | No | "" |

---

### 11. health-landing.coverage-column

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `title` | string | Yes | - |
| `isHighlighted` | boolean | No | `false` |
| `headerBackground` | string | No | - |
| `borderColor` | string | No | - |

---

### 12. health-landing.coverage-row

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `label` | string | Yes | - |
| `values` | component[] | Yes | - |

---

### 13. health-landing.coverage-value

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `text` | string | Yes | - |
| `color` | string | No | "#2e2e2e" |
| `weight` | enum | No | "regular" |

**Enum values (weight):** `light`, `regular`, `semibold`, `bold`

---

### 14. health-landing.insurance-option

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `optionId` | string | Yes | - |
| `label` | string | Yes | - |
| `value` | string | Yes | - |

---

### 15. health-landing.consent-config

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `label` | string | No | "I agree with" |
| `termsText` | string | No | "Terms and Conditions" |
| `termsUrl` | string | No | "/terms" |
| `privacyText` | string | No | "Privacy Policy" |
| `privacyUrl` | string | No | "/privacy" |

---

### 16. health-landing.cta-config

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `buttonText` | string | No | "Get Insured Now" |
| `otpButtonText` | string | No | "Verify OTP" |
| `trustText` | string | No | "Join families trusting ABCD for health coverage." |

---

### 17. health-landing.faq-item

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `itemsId` | string | Yes | - |
| `question` | string | Yes | - |
| `answer` | text | Yes | - |
| `order` | number | No | - |

---

### 18. health-landing.footer-feature

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `featuresId` | string | Yes | - |
| `text` | string | Yes | - |

---

## Restrictions Summary Table

| Section | Component | Max Items |
|---------|-----------|-----------|
| News Ticker Items | news-ticker-item | - |
| Hero Slides | hero-slide | 10 |
| Product Highlighters | product-highlighter | 6 |
| Smart Features | smart-feature | 5 |
| Statistics | statistic-item | 8 |
| How It Works Tabs | how-it-works-tab | 7 |
| Add-On Tabs | how-it-works-tab | 7 |
| Insurance Options | insurance-option | 5 |
| FAQ Items | faq-item | 20 |
| Footer Features | footer-feature | 5 |
| Coverage Rows | coverage-row | 10 |

---

## Populate Query for Full Response

```
GET /api/health-insurance-landing-pages?
filters[partner][$eq]=default&
populate=deep
```

---

### Hero Slides Configuration
```json
{
  "slides": [
    {
      "id": "1",
      "title": "Get Affordable Health Insurance",
      "subtitle": "Starting from Rs 450/month",
      "background": "image_url",
      "order": 1
    }
  ]
}
```

**Note:** Carousel behavior (autoPlay, interval, arrows, indicators) is hardcoded in the design system and not configurable via Strapi.

### Widget Configuration with OTP Options
```json
{
  "widget": {
    "headerTitle": "<strong>Health insurance</strong> made <strong>simple, fast &amp; transparent</strong>",
    "title": "Take the first step to better health",
    "insuranceOptions": [
      {
        "optionId": "buy-new",
        "label": "Buy a new health plan",
        "value": "Buy a new health plan"
      },
      {
        "optionId": "topup",
        "label": "Top Up existing cover",
        "value": "Top Up existing cover"
      }
    ],
    "consentConfig": {
      "label": "I agree with",
      "termsText": "Terms and Conditions",
      "termsUrl": "/terms"
    }
  }
}
```

### Sections Enabled/Disabled Control
```json
{
  "sectionsEnabled": {
    "newsItems": true,
    "promoBannerHealth": true,
    "heroSlides": true,
    "smartFeaturesHealth": true,
    "howMotorWorksTabs": true,
    "faq": true,
    "footer": true,
    "claimProcess": true
  }
}
```

---

