# Tracks Landing Page - Widget Configuration Schemas

This document provides schema documentation for the Tracks Landing Page widget components.

---

## Table of Contents

1. [Overview](#overview)
2. [Components](#components)
   - [Hero Section](#hero-section)
   - [Widget Config](#widget-config)
     - [New User Form](#new-user-form)
     - [Existing User Form](#existing-user-form)
     - [OTP Verification](#otp-verification)
3. [API Endpoints](#api-endpoints)
4. [Sample API Response](#sample-api-response)

---

## Overview

The Tracks Landing Page widget schemas define the content structure for the credit score tracking landing page and form flows. These components are part of the Tracks Landing Pages collection type.

**API Identifier:** `api::tracks-landing-pages.tracks-landing-pages`

**Location:** `/src/app/[subProduct]/landing/`

---

## Components

All components are configured through the `tracks-landing-pages` collection.

### Hero Section

**Component:** Hero configuration for landing page headline and trust bar.

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `heroTitle` | text | Yes | `Check Your Credit Score for Free in seconds` | Main hero headline |
| `heroSubtitle` | text | No | `Stay on top of your credit health with easy tracking, personalized insights, and improvement tips` | Hero subtitle text |
| `heroDescription` | text | No | - | Additional hero description |
| `heroImage` | media | No | - | Hero section background image |
| `heroImageAlt` | string | No | `Credit Track Hero` | Hero image alt text |
| `showHeroSeparator` | boolean | No | `true` | Show decorative separator below hero |
| `productHighlighters` | component | No | - | Trust bar items (array) |

**Product Highlighters Schema:**

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `id` | string | Yes | - | Unique identifier |
| `text` | string | Yes | - | Highlighter display text |
| `showIcon` | boolean | No | `true` | Show decorative star icon (✦) after item |
| `order` | number | No | - | Display order (ascending) |

**Default Product Highlighters:**
```json
[
  { "id": "highlighter-1", "text": "No Negative Impact on Score", "showIcon": true, "order": 1 },
  { "id": "highlighter-2", "text": "Get Instant Credit Score", "showIcon": true, "order": 2 },
  { "id": "highlighter-3", "text": "Safe & Secure", "showIcon": false, "order": 3 }
]
```

---

### Widget Config

**Component:** `widget-config.json`

Form widget configuration for new user registration, existing user login, and OTP verification flows.

---

#### New User Form

Configuration for new user credit score registration form.

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `headerTitle` | text | Yes | `Join 10L+ users tracking their Credit Score with ABCD` | Top banner text |
| `title` | string | Yes | `Take the first step to better credit` | Form card title |
| `fullNamePlaceholder` | string | Yes | `Full Name` | Full name input placeholder |
| `mobileInputPlaceholder` | string | Yes | `Mobile Number` | Mobile number input placeholder |
| `mobileHelperText` | text | No | `OTP will be sent to verify your number` | Helper text below mobile input |
| `panPlaceholder` | string | Yes | `PAN` | PAN input placeholder |
| `panHelperText` | text | No | `Increases the accuracy of your score` | Helper text below PAN input |
| `consentSeparatorText` | string | No | ` and ` | Text separator between T&C links |
| `consentConfig` | component | Yes | - | Consent checkbox configuration |
| `ctaConfig` | component | Yes | - | Primary CTA configuration |
| `alreadyUserConfig` | component | Yes | - | Existing user link configuration |
| `securityFooterConfig` | component | Yes | - | Security footer badge configuration |

**Consent Config Schema:**

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `label` | string | Yes | `I agree with` | Consent checkbox label prefix |
| `termsText` | string | Yes | `Terms and Conditions` | Terms link text |
| `termsUrl` | string | Yes | `/terms` | Terms link URL (opens in new tab) |
| `privacyText` | string | Yes | `Privacy Policy` | Privacy policy link text |
| `privacyUrl` | string | Yes | `/privacy` | Privacy policy link URL (opens in new tab) |

**CTA Config Schema:**

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `buttonText` | string | Yes | `Get my Free Credit Score` | Primary CTA button text |
| `secondaryLinkText` | string | No | `Already tracked?` | Secondary link text |
| `secondaryLinkHref` | string | No | `/credit/customer` | Secondary link URL |

**Already User Config Schema:**

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `text` | string | Yes | `Already a Credit Track user?` | Prompt text |
| `linkText` | string | Yes | `View Report` | Link text (switches to existing user state) |
| `linkHref` | string | No | `/credit/customer` | Link URL |

**Security Footer Config Schema:**

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `text` | string | Yes | `YOUR INFORMATION IS SECURE WITH US` | Trust badge text |
| `partnerLogoUrl` | string | No | `/icons/Experian-logo.svg` | Partner logo image URL |
| `partnerLogoAlt` | string | No | `Experian` | Partner logo alt text |
| `partnerLogoHeight` | number | No | `24` | Partner logo height in pixels |

**Schema:**
```json
{
  "collectionName": "components_landing_pages_widget_configs",
  "info": {
    "displayName": "Widget Config",
    "description": "Landing page form widget configuration"
  },
  "options": {},
  "attributes": {
    "headerTitle": {
      "type": "text",
      "required": true,
      "default": "Join 10L+ users tracking their Credit Score with ABCD"
    },
    "title": {
      "type": "string",
      "required": true,
      "default": "Take the first step to better credit"
    },
    "fullNamePlaceholder": {
      "type": "string",
      "required": true,
      "default": "Full Name"
    },
    "mobileInputPlaceholder": {
      "type": "string",
      "required": true,
      "default": "Mobile Number"
    },
    "mobileHelperText": {
      "type": "text",
      "default": "OTP will be sent to verify your number"
    },
    "panPlaceholder": {
      "type": "string",
      "required": true,
      "default": "PAN"
    },
    "panHelperText": {
      "type": "text",
      "default": "Increases the accuracy of your score"
    },
    "consentSeparatorText": {
      "type": "string",
      "default": " and "
    },
    "consentConfig": {
      "type": "component",
      "repeatable": false,
      "component": "consent.config"
    },
    "ctaConfig": {
      "type": "component",
      "repeatable": false,
      "component": "cta.config"
    },
    "alreadyUserConfig": {
      "type": "component",
      "repeatable": false,
      "component": "user.config"
    },
    "securityFooterConfig": {
      "type": "component",
      "repeatable": false,
      "component": "security.footer"
    }
  }
}
```

**Example:**
```json
{
  "headerTitle": "Join 10L+ users tracking their Credit Score with ABCD",
  "title": "Take the first step to better credit",
  "fullNamePlaceholder": "Full Name",
  "mobileInputPlaceholder": "Mobile Number",
  "mobileHelperText": "OTP will be sent to verify your number",
  "panPlaceholder": "PAN",
  "panHelperText": "Increases the accuracy of your score",
  "consentSeparatorText": " and ",
  "consentConfig": {
    "label": "I agree with",
    "termsText": "Terms and Conditions",
    "termsUrl": "/terms",
    "privacyText": "Privacy Policy",
    "privacyUrl": "/privacy"
  },
  "ctaConfig": {
    "buttonText": "Get my Free Credit Score",
    "secondaryLinkText": "Already tracked?",
    "secondaryLinkHref": "/credit/customer"
  },
  "alreadyUserConfig": {
    "text": "Already a Credit Track user?",
    "linkText": "View Report",
    "linkHref": "/credit/customer"
  },
  "securityFooterConfig": {
    "text": "YOUR INFORMATION IS SECURE WITH US",
    "partnerLogoUrl": "/icons/Experian-logo.svg",
    "partnerLogoAlt": "Experian",
    "partnerLogoHeight": 24
  }
}
```

---

#### Existing User Form

Configuration for existing user "View Report" flow.

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `headerTitle` | text | Yes | _(same as new user)_ | Top banner text (reused) |
| `viewReportTitle` | string | Yes | `View report` | Desktop view report title |
| `viewReportMobileTitle` | string | Yes | `View your credit report` | Mobile view report title |
| `mobileInputPlaceholder` | string | Yes | `Registered Mobile Number` | Mobile input placeholder |
| `mobileHelperText` | text | Yes | _(same as new user)_ | Helper text (reused) |
| `continueButtonText` | string | Yes | `Continue` | Continue CTA button text |
| `newUserPromptText` | string | Yes | `New to credit Track? ` | New user prompt text |
| `newUserLinkText` | string | Yes | `Get your credit score` | New user link text (switches to new user state) |
| `securityFooterConfig` | component | Yes | _(same as new user)_ | Security footer (reused) |

**Schema:**
```json
{
  "attributes": {
    "viewReportTitle": {
      "type": "string",
      "required": true,
      "default": "View report"
    },
    "viewReportMobileTitle": {
      "type": "string",
      "required": true,
      "default": "View your credit report"
    },
    "continueButtonText": {
      "type": "string",
      "required": true,
      "default": "Continue"
    },
    "newUserPromptText": {
      "type": "string",
      "required": true,
      "default": "New to credit Track? "
    },
    "newUserLinkText": {
      "type": "string",
      "required": true,
      "default": "Get your credit score"
    }
  }
}
```

**Example:**
```json
{
  "headerTitle": "Join 10L+ users tracking their Credit Score with ABCD",
  "viewReportTitle": "View report",
  "viewReportMobileTitle": "View your credit report",
  "mobileInputPlaceholder": "Registered Mobile Number",
  "mobileHelperText": "OTP will be sent to verify your number",
  "continueButtonText": "Continue",
  "newUserPromptText": "New to credit Track? ",
  "newUserLinkText": "Get your credit score",
  "securityFooterConfig": {
    "text": "YOUR INFORMATION IS SECURE WITH US",
    "partnerLogoUrl": "/icons/Experian-logo.svg",
    "partnerLogoAlt": "Experian",
    "partnerLogoHeight": 24
  }
}
```

---

#### OTP Verification

Configuration for OTP verification screen.

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `otpConfig` | component | Yes | - | OTP verification configuration |

**OTP Config Schema:**

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `title` | string | Yes | `OTP Verification` | OTP screen title |
| `subtitle` | string | Yes | `Enter the 6 digit code sent to ` | Subtitle prefix (mobile number appended dynamically) |
| `imageAlt` | string | No | `OTP Verification` | OTP illustration alt text |
| `errorMessage` | string | Yes | `OTP incorrect. Please try again.` | Error message for incorrect OTP |
| `actionButtonText` | string | Yes | `Verify` | Verify button text (disabled until 6 digits entered) |

**Schema:**
```json
{
  "collectionName": "components_otp_configs",
  "info": {
    "displayName": "OTP Config",
    "description": "OTP verification screen configuration"
  },
  "options": {},
  "attributes": {
    "title": {
      "type": "string",
      "required": true,
      "default": "OTP Verification"
    },
    "subtitle": {
      "type": "string",
      "required": true,
      "default": "Enter the 6 digit code sent to "
    },
    "imageAlt": {
      "type": "string",
      "default": "OTP Verification"
    },
    "errorMessage": {
      "type": "string",
      "required": true,
      "default": "OTP incorrect. Please try again."
    },
    "actionButtonText": {
      "type": "string",
      "required": true,
      "default": "Verify"
    }
  }
}
```

**Example:**
```json
{
  "otpConfig": {
    "title": "OTP Verification",
    "subtitle": "Enter the 6 digit code sent to ",
    "imageAlt": "OTP Verification",
    "errorMessage": "OTP incorrect. Please try again.",
    "actionButtonText": "Verify"
  }
}
```

---

## API Endpoints

The Tracks Landing Pages use Strapi's default REST API routes.

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tracks-landing-pages` | Get all landing pages |
| GET | `/api/tracks-landing-pages/:id` | Get landing page by ID |
| GET | `/api/tracks-landing-pages?filters[subProduct][$eq]=credit&populate=*` | Get credit landing page with all components |
| GET | `/api/tracks-landing-pages?filters[subProduct][$eq]=credit&populate[widgetConfig]=*&populate[productHighlighters]=*` | Get credit landing page with widget config and trust bar |

---

## Sample API Response

**GET** `/api/tracks-landing-pages?filters[subProduct][$eq]=credit&populate[widgetConfig][populate]=*&populate[productHighlighters]=*`

```json
{
  "data": [
    {
      "id": 1,
      "attributes": {
        "subProduct": "credit",
        "createdAt": "2026-01-15T10:00:00.000Z",
        "updatedAt": "2026-04-27T18:30:00.000Z",
        "publishedAt": "2026-01-15T12:00:00.000Z",
        
        "heroTitle": "Check Your Credit Score for Free in seconds",
        "heroSubtitle": "Stay on top of your credit health with easy tracking, personalized insights, and improvement tips",
        "heroDescription": null,
        "heroImage": {
          "data": {
            "id": 5,
            "attributes": {
              "url": "/uploads/hero_credit_track.webp",
              "alternativeText": "Credit Track Hero"
            }
          }
        },
        "heroImageAlt": "Credit Track Hero",
        "showHeroSeparator": true,
        
        "productHighlighters": [
          {
            "id": 1,
            "text": "No Negative Impact on Score",
            "showIcon": true,
            "order": 1
          },
          {
            "id": 2,
            "text": "Get Instant Credit Score",
            "showIcon": true,
            "order": 2
          },
          {
            "id": 3,
            "text": "Safe & Secure",
            "showIcon": false,
            "order": 3
          }
        ],
        
        "widgetConfig": {
          "id": 1,
          "headerTitle": "Join 10L+ users tracking their Credit Score with ABCD",
          "title": "Take the first step to better credit",
          "fullNamePlaceholder": "Full Name",
          "mobileInputPlaceholder": "Mobile Number",
          "mobileHelperText": "OTP will be sent to verify your number",
          "panPlaceholder": "PAN",
          "panHelperText": "Increases the accuracy of your score",
          "consentSeparatorText": " and ",
          "viewReportTitle": "View report",
          "viewReportMobileTitle": "View your credit report",
          "continueButtonText": "Continue",
          "newUserPromptText": "New to credit Track? ",
          "newUserLinkText": "Get your credit score",
          
          "consentConfig": {
            "id": 1,
            "label": "I agree with",
            "termsText": "Terms and Conditions",
            "termsUrl": "/terms",
            "privacyText": "Privacy Policy",
            "privacyUrl": "/privacy"
          },
          
          "ctaConfig": {
            "id": 1,
            "buttonText": "Get my Free Credit Score",
            "secondaryLinkText": "Already tracked?",
            "secondaryLinkHref": "/credit/customer"
          },
          
          "alreadyUserConfig": {
            "id": 1,
            "text": "Already a Credit Track user?",
            "linkText": "View Report",
            "linkHref": "/credit/customer"
          },
          
          "securityFooterConfig": {
            "id": 1,
            "text": "YOUR INFORMATION IS SECURE WITH US",
            "partnerLogoUrl": "/icons/Experian-logo.svg",
            "partnerLogoAlt": "Experian",
            "partnerLogoHeight": 24
          },
          
          "otpConfig": {
            "id": 1,
            "title": "OTP Verification",
            "subtitle": "Enter the 6 digit code sent to ",
            "imageAlt": "OTP Verification",
            "errorMessage": "OTP incorrect. Please try again.",
            "actionButtonText": "Verify"
          }
        }
      }
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

## Implementation Notes

### Code Locations

- **CMS Client:** `abcd-tracks-web/src/config/cms/index.ts`
- **Content Transformer:** `abcd-tracks-web/src/app/[subProduct]/landing/content/index.ts`
- **Fallback Content:** `abcd-tracks-web/src/app/[subProduct]/landing/content/fallback.ts`
- **Landing Client:** `abcd-tracks-web/src/app/[subProduct]/landing/LandingClient.tsx`

### CMS Integration

```typescript
// Fetch from Strapi
const response = await fetchCmsContent("tracks-landing-pages", {
  filters: { subProduct: "credit" },
  populate: "*"
});

// Deep merge with fallbacks
const widgetConfig = deepMergeWithFallback(
  data.widgetConfig,
  FALLBACK_LANDING_CONTENT.widgetConfig
);
```

### Fallback Behavior

- All fields have defined fallback values in `fallback.ts`
- If Strapi is unavailable or returns empty data, fallbacks are used
- Deep merge ensures partial Strapi data works correctly
- Environment variable `USE_FALLBACK_CONTENT=true` forces fallback usage

### Debug Logging

Console logs are available for troubleshooting:
- `[CMS:Landing] productHighlighters raw from Strapi`
- `[CMS:Landing] widgetConfig raw from Strapi`
- `[LandingClient] ProductHighlighters from CMS`

### Business Logic

- **Form Validation:** Handled in component layer
- **OTP Flow:** sendOtp → verifyOtp → PAN verification → /userconsent → Dashboard
- **Existing User Flow:** /userconsent (CAP-002) → OTP if consent found
- **Button States:** Auto-managed by components (disabled/enabled states)
- **Mobile Masking:** Automatically masked for display (e.g., +91 98765*****)

---

**End of Documentation**
