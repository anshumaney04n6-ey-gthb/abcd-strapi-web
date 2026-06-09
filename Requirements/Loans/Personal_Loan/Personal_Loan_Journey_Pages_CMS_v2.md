# Strapi Schema Requirements - Personal Loan Journey Pages
## Soft Reject Screen & Basic Details Updates

**Document Version:** 1.0  
**Date:** May 28, 2026  
**Content-Type:** `personal-loan-journey-pages`

---

## Overview

This document outlines the complete schema requirements for:
1. **Soft Reject Screen** - Complete new component structure
2. **Basic Details** - Additional fields to existing component

---

## 1. Soft Reject Screen (Complete Component)

### Component: `journey.soft-reject-screen`

This is the screen shown when no loan offers are available for the user.

#### Main Component Fields

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `heroIcon` | Media (Single) | No | - | Main illustration/icon shown at top |
| `heroIconAlt` | Text (Short) | No | - | Alt text for hero icon |
| `title` | Text (Short) | Yes | - | Main heading (e.g., "No offers available!") |
| `description` | Text (Long) | No | - | Supporting description text |
| `sectionTitle` | Text (Short) | No | - | Section heading for cross-sell banners |
| `buttonText` | Text (Short) | No | - | Primary CTA button text |
| `footerText` | Text (Short) | No | - | Footer text (e.g., "Powered by...") |
| `crossSellBanners` | Component (Repeatable) | Yes | [] | Array of cross-sell banner items |
| `minBanners` | Number (Integer) | No | 1 | Minimum banners to show |
| `maxBanners` | Number (Integer) | No | 4 | Maximum banners to show |
| `hideCarousel` | Boolean | No | false | Whether to hide the carousel |
| `autoPlay` | Boolean | No | false | Enable auto-play for carousel |
| `autoPlayInterval` | Number (Integer) | No | 4000 | Auto-play interval in milliseconds |
| `showCarouselDots` | Boolean | No | true | Show navigation dots |

#### Field Configurations

**heroIcon:**
```
Type: Media (Single Image)
Allowed formats: WebP, PNG, SVG, JPEG
Max size: 2MB
Required: No
```

**heroIconAlt:**
```
Type: Text (Short text)
Max length: 100
Required: No
Example: "No offers available"
```

**title:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Example: "No offers available!"
```

**description:**
```
Type: Text (Long text)
Max length: 500
Required: No
Example: "Sorry, we are unable to provide you any loan offers currently..."
```

**sectionTitle:**
```
Type: Text (Short text)
Max length: 100
Required: No
Example: "Did you know?"
```

**buttonText:**
```
Type: Text (Short text)
Max length: 50
Required: No
Example: "Back to homepage"
```

**footerText:**
```
Type: Text (Short text)
Max length: 200
Required: No
Example: "Powered by Aditya Birla Capital Digital Ltd"
```

**minBanners:**
```
Type: Number (Integer)
Min: 0
Max: 10
Default: 1
```

**maxBanners:**
```
Type: Number (Integer)
Min: 1
Max: 10
Default: 4
```

**Carousel Settings:**
```
hideCarousel: Boolean, default: false
autoPlay: Boolean, default: false
autoPlayInterval: Integer (milliseconds), default: 4000
showCarouselDots: Boolean, default: true
```

---

### Sub-Component: `journey.cross-sell-banner`

**Component Name:** `journey.cross-sell-banner`  
**Type:** Repeatable component used inside `softRejectScreen.crossSellBanners`

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `id` | Text (Short) | Yes | - | Unique identifier for banner |
| `offerType` | Enumeration | Yes | - | Type of offer (see values below) |
| `title` | Text (Short) | Yes | - | Banner title/heading |
| `subtitle` | Text (Long) | No | - | Banner description/subtitle |
| `ctaText` | Text (Short) | Yes | - | Call-to-action button text |
| `redirectUrl` | Text (Short) | Yes | - | URL to redirect on click |
| `utmSource` | Text (Short) | No | - | UTM source parameter |
| `utmMedium` | Text (Short) | No | - | UTM medium parameter |
| `utmCampaign` | Text (Short) | No | - | UTM campaign parameter |
| `background` | Text (Long) | No | - | CSS gradient string for background |
| `backgroundImage` | Media (Single) | No | null | Background image/pattern |
| `image` | Component (Single) | No | - | Banner illustration/image |
| `martechEvent` | Text (Short) | No | - | Analytics event tracking name |
| `priority` | Number (Integer) | No | - | Display order priority |

#### Field Configurations for Cross-Sell Banner

**id:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Unique: No (but should be unique within the banner array)
Example: "gold-loan-banner"
```

**offerType:**
```
Type: Enumeration
Required: Yes
Values:
  - GOLD_LOAN
  - CREDIT_TRACK
  - CREDIT_CARD
  - CREDIT_LINK
```

**title:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Example: "Unlock Instant Cash Using Your Gold"
```

**subtitle:**
```
Type: Text (Long text)
Max length: 500
Required: No
Example: "Get quick funds at attractive rates — without selling your gold"
```

**ctaText:**
```
Type: Text (Short text)
Max length: 50
Required: Yes
Example: "Get Gold Loan"
```

**redirectUrl:**
```
Type: Text (Short text)
Max length: 500
Required: Yes
Format: Valid URL
Example: "https://www.adityabirlacapital.com/abcd/gold-loan"
```

**UTM Parameters:**
```
utmSource: Text (Short), max: 100, optional
utmMedium: Text (Short), max: 100, optional
utmCampaign: Text (Short), max: 100, optional
```

**background:**
```
Type: Text (Long text)
Max length: 500
Required: No
Format: CSS gradient string
Example: "radial-gradient(120% 180% at 100% 50%, #ffe7a8 0%, #fff6dd 45%, #ffffff 80%)"
```

**backgroundImage:**
```
Type: Media (Single Image)
Allowed formats: SVG, PNG, WebP
Max size: 1MB
Required: No
```

**martechEvent:**
```
Type: Text (Short text)
Max length: 100
Required: No
Format: snake_case
Example: "pl_soft_reject_gold_loan_banner_click"
```

**priority:**
```
Type: Number (Integer)
Min: 1
Max: 100
Required: No
Description: Lower number = higher priority
```

---

### Sub-Component: `journey.banner-image`

**Component Name:** `journey.banner-image`  
**Type:** Single component used inside `cross-sell-banner.image`

| Field Name | Type | Required | Description |
|------------|------|----------|-------------|
| `src` | Media (Single) | No | Image file |
| `alt` | Text (Short) | No | Alt text for image |

**src:**
```
Type: Media (Single Image)
Allowed formats: WebP, PNG, SVG
Max size: 2MB
Required: No
```

**alt:**
```
Type: Text (Short text)
Max length: 100
Required: No
Example: "Gold bars"
```

---

## 2. Basic Details Component Updates

### Component: `journey.basic-details`

**Add these fields to the existing component:**

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `panLabel` | Text (Short) | Yes | - | Label for PAN input field |
| `panPlaceholder` | Text (Short) | No | - | Placeholder text for PAN input |
| `nameLabel` | Text (Short) | Yes | - | Label for name input field |
| `namePlaceholder` | Text (Short) | No | - | Placeholder text for name input |
| `invalidPanError` | Text (Short) | Yes | - | Error message for invalid PAN |
| `invalidNameError` | Text (Short) | Yes | - | Error message for invalid name |
| `editIconPath` | Media (Single) | No | - | Icon for edit functionality |

#### Field Configurations for Basic Details

**panLabel:**
```
Type: Text (Short text)
Max length: 50
Required: Yes
Default value: "PAN"
Example: "PAN"
```

**panPlaceholder:**
```
Type: Text (Short text)
Max length: 100
Required: No
Default value: "Enter PAN"
Example: "Enter PAN"
```

**nameLabel:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Default value: "Full name as per PAN"
Example: "Full name as per PAN"
```

**namePlaceholder:**
```
Type: Text (Short text)
Max length: 100
Required: No
Default value: "Enter your full name"
Example: "Enter your full name"
```

**invalidPanError:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Default value: "Please enter a valid PAN in uppercase (e.g., ABCDE1234F)"
```

**invalidNameError:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Default value: "Characters should be minimum 3 letters"
```

**editIconPath:**
```
Type: Media (Single Image)
Allowed formats: SVG, PNG
Max size: 500KB
Required: No
Example file: "edit_pencil.svg"
```

---

## API Response Examples

### Soft Reject Screen Response

```json
{
  "softRejectScreen": {
    "heroIcon": {
      "id": 789,
      "name": "no-offers-icon.webp",
      "url": "https://cdn.abcd.io/assets/personal-loan/soft-reject/no-offers-icon.webp",
      "mime": "image/webp",
      "width": 200,
      "height": 200
    },
    "heroIconAlt": "No offers available",
    "title": "No offers available!",
    "description": "Sorry, we are unable to provide you any loan offers currently. Try again after a few months.",
    "sectionTitle": "Did you know?",
    "buttonText": "Back to homepage",
    "footerText": "Powered by Aditya Birla Capital Digital Ltd",
    "crossSellBanners": [
      {
        "id": "gold-loan-banner",
        "offerType": "GOLD_LOAN",
        "title": "Unlock Instant Cash Using Your Gold",
        "subtitle": "Get quick funds at attractive rates — without selling your gold",
        "ctaText": "Get Gold Loan",
        "redirectUrl": "https://www.adityabirlacapital.com/abcd/gold-loan",
        "background": "radial-gradient(120% 180% at 100% 50%, #ffe7a8 0%, #fff6dd 45%, #ffffff 80%)",
        "backgroundImage": {
          "id": 101,
          "url": "https://cdn.abcd.io/assets/personal-loan/icons/rejection-card-bg.svg"
        },
        "image": {
          "src": {
            "id": 102,
            "url": "https://cdn.abcd.io/assets/physical-gold/gold-stack.webp"
          },
          "alt": "Gold bars"
        },
        "martechEvent": "pl_soft_reject_gold_loan_banner_click",
        "priority": 1
      },
      {
        "id": "credit-track-banner",
        "offerType": "CREDIT_TRACK",
        "title": "Check, Track & Improve Your Credit Score",
        "subtitle": "View your free credit score and detailed credit report instantly",
        "ctaText": "Check My Credit Score",
        "redirectUrl": "https://www.adityabirlacapital.com/abcd/check-free-credit-score",
        "background": "radial-gradient(120% 180% at 100% 50%, #c9ecd6 0%, #e6f7ec 45%, #ffffff 80%)",
        "backgroundImage": null,
        "image": {
          "src": {
            "id": 103,
            "url": "https://cdn.abcd.io/assets/personal-loan/icons/speedometer.svg"
          },
          "alt": "Credit score meter"
        },
        "martechEvent": "pl_soft_reject_credit_score_banner_click",
        "priority": 2
      }
    ],
    "minBanners": 1,
    "maxBanners": 4,
    "hideCarousel": false,
    "autoPlay": false,
    "autoPlayInterval": 4000,
    "showCarouselDots": true
  }
}
```

### Basic Details Response (with new fields)

```json
{
  "basicDetails": {
    "title": "Personal loan",
    "stepLabel": "Basic details",
    "stepNumber": "Step 1/5",
    "panLabel": "PAN",
    "panPlaceholder": "Enter PAN",
    "nameLabel": "Full name as per PAN",
    "namePlaceholder": "Enter your full name",
    "emailLabel": "Email (Required)",
    "emailPlaceholder": "Enter email address",
    "invalidPanError": "Please enter a valid PAN in uppercase (e.g., ABCDE1234F)",
    "invalidNameError": "Characters should be minimum 3 letters",
    "invalidEmailError": "Please enter a valid Email Address",
    "editIconPath": {
      "id": 456,
      "name": "edit_pencil.svg",
      "url": "https://cdn.abcd.io/assets/personal-loan/icons/edit_pencil.svg",
      "mime": "image/svg+xml"
    },
    "ctaText": "Verify details",
    ...
  }
}
```

---

## Default Content Values

### For Soft Reject Screen (partner="default")

```
heroIconAlt: "No offers available"
title: "No offers available!"
description: "Sorry, we are unable to provide you any loan offers currently. Try again after a few months."
sectionTitle: "Did you know?"
buttonText: "Back to homepage"
footerText: "Powered by Aditya Birla Capital Digital Ltd"
minBanners: 1
maxBanners: 4
hideCarousel: false
autoPlay: false
autoPlayInterval: 4000
showCarouselDots: true
```

### Default Cross-Sell Banners

**Banner 1: Gold Loan**
```
id: "gold-loan-banner"
offerType: GOLD_LOAN
title: "Unlock Instant Cash Using Your Gold"
subtitle: "Get quick funds at attractive rates — without selling your gold"
ctaText: "Get Gold Loan"
redirectUrl: "https://www.adityabirlacapital.com/abcd/gold-loan"
martechEvent: "pl_soft_reject_gold_loan_banner_click"
priority: 1
```

**Banner 2: Credit Score**
```
id: "credit-track-banner"
offerType: CREDIT_TRACK
title: "Check, Track & Improve Your Credit Score"
subtitle: "View your free credit score and detailed credit report instantly"
ctaText: "Check My Credit Score"
redirectUrl: "https://www.adityabirlacapital.com/abcd/check-free-credit-score"
martechEvent: "pl_soft_reject_credit_score_banner_click"
priority: 2
```

**Banner 3: Credit Card**
```
id: "credit-card-banner"
offerType: CREDIT_CARD
title: "Find a Credit Card That Suits You"
subtitle: "Compare cards, apply easily, and enjoy rewards on every spend"
ctaText: "Explore Credit Cards"
redirectUrl: "https://www.adityabirlacapital.com/abcd/credit-card"
martechEvent: "pl_soft_reject_credit_card_banner_click"
priority: 3
```

**Banner 4: Credit Link**
```
id: "credit-links-banner"
offerType: CREDIT_LINK
title: "More lenders, more offers, better odds."
subtitle: "Explore additional credit options available just for you"
ctaText: "Explore More Offers"
redirectUrl: "https://www.adityabirlacapital.com/abcd"
martechEvent: "pl_soft_reject_credit_link_banner_click"
priority: 4
```

### For Basic Details Updates (partner="default")

```
panLabel: "PAN"
panPlaceholder: "Enter PAN"
nameLabel: "Full name as per PAN"
namePlaceholder: "Enter your full name"
invalidPanError: "Please enter a valid PAN in uppercase (e.g., ABCDE1234F)"
invalidNameError: "Characters should be minimum 3 letters"
```

---

## Implementation Checklist

### Phase 1: Soft Reject Screen
- [ ] Create `journey.soft-reject-screen` component
- [ ] Add all main fields to soft-reject-screen
- [ ] Create `journey.cross-sell-banner` repeatable component
- [ ] Add all fields to cross-sell-banner component
- [ ] Create `journey.banner-image` component for banner images
- [ ] Set up offerType enumeration with 4 values
- [ ] Configure media fields for heroIcon, backgroundImage, banner image
- [ ] Add carousel configuration fields (boolean and integer types)

### Phase 2: Basic Details Updates
- [ ] Add `panLabel` field to journey.basic-details
- [ ] Add `panPlaceholder` field
- [ ] Add `nameLabel` field
- [ ] Add `namePlaceholder` field
- [ ] Add `invalidPanError` field
- [ ] Add `invalidNameError` field
- [ ] Add `editIconPath` media field

### Phase 3: Content Population
- [ ] Create default content entry with partner="default"
- [ ] Add hero icon for soft reject screen
- [ ] Add 4 default cross-sell banners with all fields
- [ ] Upload banner images and background images
- [ ] Add edit icon for basic details
- [ ] Test all media uploads



---

## Important Notes

1. **Component Nesting Structure:**
   ```
   softRejectScreen (main component)
   ├── crossSellBanners (repeatable)
   │   └── image (single)
   │       └── src (media)
   ```

2. **Media Fields:** All media fields should return the full media object with `id`, `name`, `url`, `mime` properties.

3. **Backward Compatibility:** These are new fields/component. Existing content should not break.
