# Strapi Schema Requirements - Personal Loan Journey Pages
## Loader Screens, Milestones & Income/Thank-You Screen

**Document Version:** 1.0
**Date:** May 29, 2026
**Content-Type:** `personal-loan-journey-pages`

---

## Overview

This document outlines the complete schema requirements for:
1. **Review Details Loader** - Loader shown after PAN submit while BRE eligibility is being fetched
2. **Offer Loader (LRE)** - Loader shown after basic-details submit while LRE marketplace offers are being fetched
3. **Redirection Loader** - Visuals shown while redirecting to a lending partner
4. **Milestones** - Shared sidebar milestones panel used across screens
5. **Income & Thank-You Screen** - Combined income capture + thank-you confirmation screen

---

## 1. Review Details Loader (Complete Component)

### Component: `journey.loader-content`

JSON key on API response: **`reviewDetailsLoader`**

Loader shown after PAN submit while BRE eligibility is being fetched.

#### Main Component Fields

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `title` | Text (Short) | Yes | - | Main heading shown on loader |
| `subtitleLine1` | Text (Short) | Yes | - | First subtitle line |
| `subtitleLine2` | Text (Short) | Yes | - | Second subtitle line |
| `waitPrefixText` | Text (Short) | Yes | - | Text shown before the highlighted seconds value |
| `waitHighlightSeconds` | Number (Integer) | No | 45 | Highlighted seconds value in the wait line |
| `waitSuffixText` | Text (Short) | Yes | - | Text shown after the highlighted seconds value |
| `safeVisualPath` | Media (Single) | Yes | - | Primary visual (illustration / animation) |
| `waitIconPath` | Media (Single) | Yes | - | Inline spinner / wait icon shown beside the wait text |
| `sheetVisualPath` | Media (Single) | Yes | - | Secondary sheet visual / background image |

#### Field Configurations

**title:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Example: "We are reviewing your details"
```

**subtitleLine1:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Example: "Please wait while we review"
```

**subtitleLine2:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Example: "your details"
```

**waitPrefixText:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Example: "This process may take upto"
```

**waitHighlightSeconds:**
```
Type: Number (Integer)
Min: 1
Max: 600
Default: 45
Required: No
```

**waitSuffixText:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Example: "to complete, please stay on the screen"
```

**safeVisualPath:**
```
Type: Media (Single Image/Animation)
Allowed formats: GIF, WebP, PNG, SVG
Max size: 4MB
Required: Yes
Example: "/assets/personal-loan/gifs/scan.gif"
```

**waitIconPath:**
```
Type: Media (Single Image/Animation)
Allowed formats: GIF, SVG, PNG, WebP
Max size: 1MB
Required: Yes
Example: "/assets/personal-loan/icons/loader.gif"
```

**sheetVisualPath:**
```
Type: Media (Single Image)
Allowed formats: SVG, WebP, PNG
Max size: 2MB
Required: Yes
Example: "/assets/error-pages/brefile1.svg"
```

---

## 2. Offer Loader / LRE (Reuses `journey.loader-content`)

### Component: `journey.loader-content`

JSON key on API response: **`offerLoaderLRE`**

Loader shown after basic-details submit while LRE marketplace offers are being fetched. Reuses the same `journey.loader-content` component as the Review Details Loader — only content values differ.

#### Main Component Fields

Identical schema to **Review Details Loader** above. Reuse the same `journey.loader-content` component.

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `title` | Text (Short) | Yes | - | Main heading shown on loader |
| `subtitleLine1` | Text (Short) | Yes | - | First subtitle line |
| `subtitleLine2` | Text (Short) | Yes | - | Second subtitle line |
| `waitPrefixText` | Text (Short) | Yes | - | Text shown before the highlighted seconds value |
| `waitHighlightSeconds` | Number (Integer) | No | 45 | Highlighted seconds value in the wait line |
| `waitSuffixText` | Text (Short) | Yes | - | Text shown after the highlighted seconds value |
| `safeVisualPath` | Media (Single) | Yes | - | Primary visual (illustration / animation) |
| `waitIconPath` | Media (Single) | Yes | - | Inline spinner / wait icon shown beside the wait text |
| `sheetVisualPath` | Media (Single) | Yes | - | Secondary sheet visual / background image |

---

## 3. Redirection Loader (Complete Component)

### Component: `journey.redirection-loader`

JSON key on API response: **`redirectionLoader`**

Visuals shown while redirecting to a lending partner. Richer shape than the standard loader — includes left logo, middle slot animation with rotation, and a list of partner-experience highlights.

#### Main Component Fields

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `title` | Text (Short) | Yes | - | Main heading shown on loader |
| `subtitleLine1` | Text (Short) | Yes | - | First subtitle line |
| `subtitleLine2` | Text (Short) | No | "" | Second subtitle line (may be empty) |
| `waitPrefixText` | Text (Short) | Yes | - | Text shown before the highlighted seconds value |
| `waitHighlightSeconds` | Number (Integer) | Yes | 45 | Highlighted seconds value in the wait line |
| `waitSuffixText` | Text (Short) | Yes | - | Text shown after the highlighted seconds value |
| `waitIconPath` | Media (Single) | Yes | - | Inline spinner / wait icon shown beside the wait text |
| `leftLogoPath` | Media (Single) | Yes | - | Left-side logo (e.g., ABCD brand mark) |
| `leftLogoAlt` | Text (Short) | Yes | - | Alt text for left logo |
| `middleSlotPath` | Media (Single) | Yes | - | Middle slot animation/icon (e.g., redirecting arrow) |
| `middleSlotAlt` | Text (Short) | Yes | - | Alt text for middle slot |
| `middleSlotRotationDeg` | Number (Integer) | Yes | 0 | Rotation applied to middle slot in degrees |
| `highlights` | Component (Repeatable) | Yes | [] | List of partner-experience highlights |

#### Field Configurations

**title:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Example: "Setting things up for your loan disbursal"
```

**subtitleLine1:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Example: "Confirm your details with our trusted lending partner,"
```

**subtitleLine2:**
```
Type: Text (Short text)
Max length: 200
Required: No
Default: ""
```

**waitPrefixText:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Example: "This process will take just"
```

**waitHighlightSeconds:**
```
Type: Number (Integer)
Min: 1
Max: 600
Default: 45
Required: Yes
```

**waitSuffixText:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Example: "seconds, please stay on this screen."
```

**waitIconPath:**
```
Type: Media (Single Image/Animation)
Allowed formats: GIF, SVG, PNG, WebP
Max size: 1MB
Required: Yes
Example: "/assets/personal-loan/icons/loader.gif"
```

**leftLogoPath:**
```
Type: Media (Single Image)
Allowed formats: SVG, PNG, WebP
Max size: 500KB
Required: Yes
Example: "/assets/personal-loan/icons/abcd-logo.svg"
```

**leftLogoAlt:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Example: "ABCD"
```

**middleSlotPath:**
```
Type: Media (Single Image/Animation)
Allowed formats: GIF, SVG, PNG, WebP
Max size: 2MB
Required: Yes
Example: "/assets/personal-loan/icons/plarrow.gif"
```

**middleSlotAlt:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Example: "Redirecting"
```

**middleSlotRotationDeg:**
```
Type: Number (Integer)
Min: -360
Max: 360
Default: 0
Required: Yes
Example: 90
```

---

### Sub-Component: `journey.redirection-loader-highlight`

**Component Name:** `journey.redirection-loader-highlight`
**Type:** Repeatable component used inside `redirectionLoader.highlights`

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `iconPath` | Media (Single) | Yes | - | Highlight icon |
| `iconAlt` | Text (Short) | No | - | Alt text for icon |
| `label` | Text (Long) | Yes | - | Highlight label (supports `\n` for line breaks) |

#### Field Configurations for Redirection Loader Highlight

**iconPath:**
```
Type: Media (Single Image)
Allowed formats: SVG, PNG, WebP
Max size: 500KB
Required: Yes
Example: "/assets/personal-loan/icons/flash.svg"
```

**iconAlt:**
```
Type: Text (Short text)
Max length: 100
Required: No
Example: "Instant offer"
```

**label:**
```
Type: Text (Long text)
Max length: 200
Required: Yes
Notes: Use "\n" to insert a line break in the rendered label
Example: "Get\nInstant Offer"
```

---

## 4. Milestones (Complete Component)

### Component: `journey.milestones`

JSON key on API response: **`milestones`**

Shared milestones content used by step-header drilldowns across screens. Renders a panel with title, optional description, optional header illustration, an ordered list of steps, and a CTA in the footer.

#### Main Component Fields

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `title` | Text (Short) | Yes | - | Main heading inside the milestones panel |
| `description` | Text (Short) | No | - | Supporting description below the title |
| `headerIconPath` | Media (Single) | No | - | Header illustration (relative to product basePath) |
| `headerIconAlt` | Text (Short) | No | - | Alt text for the header illustration |
| `ctaText` | Text (Short) | Yes | "Got it" | CTA label shown in the sidebar footer |
| `steps` | Component (Repeatable) | Yes | [] | Ordered list of milestone steps |

#### Field Configurations

**title:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Example: "Complete your personal loan application"
```

**description:**
```
Type: Text (Short text)
Max length: 300
Required: No
Example: "Here's what to expect on your way to disbursal."
```

**headerIconPath:**
```
Type: Media (Single Image)
Allowed formats: SVG, PNG, WebP
Max size: 500KB
Required: No
Example: "/assets/personal-loan/icons/CoinRupee.svg"
```

**headerIconAlt:**
```
Type: Text (Short text)
Max length: 100
Required: No
Example: "Personal loan"
```

**ctaText:**
```
Type: Text (Short text)
Max length: 50
Required: Yes
Default value: "Got it"
```

---

### Sub-Component: `journey.milestone-step`

**Component Name:** `journey.milestone-step`
**Type:** Repeatable component used inside `milestones.steps`

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `id` | Text (Short) | Yes | - | Stable id for React keys |
| `title` | Text (Short) | Yes | - | Step title shown to the user |
| `description` | Text (Long) | No | - | Optional supporting copy |
| `tag` | Component (Single) | No | - | Optional tag rendered under the step (see `journey.milestone-step-tag`) |

#### Field Configurations for Milestone Step

**id:**
```
Type: Text (Short text)
Max length: 50
Required: Yes
Unique: No (but should be unique within the steps array)
Example: "step-1"
```

**title:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Example: "Check your eligibility"
```

**description:**
```
Type: Text (Long text)
Max length: 500
Required: No
Example: "Share basic details so we can check loan options for you."
```

---

### Sub-Component: `journey.milestone-step-tag`

**Component Name:** `journey.milestone-step-tag`
**Type:** Single component used inside `milestone-step.tag`

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `text` | Text (Short) | Yes | - | Tag label |
| `variant` | Enumeration | No | duration | Visual treatment (see values below) |
| `iconPath` | Media (Single) | No | - | Optional leading icon (relative to product basePath) |

#### Field Configurations for Milestone Step Tag

**text:**
```
Type: Text (Short text)
Max length: 50
Required: Yes
Example: "About 3 mins"
```

**variant:**
```
Type: Enumeration
Required: No
Default: duration
Values:
  - in-progress
  - duration
  - neutral
```

**iconPath:**
```
Type: Media (Single Image)
Allowed formats: SVG, PNG, WebP
Max size: 500KB
Required: No
```

---

## 5. Income & Thank-You Screen (Complete Component)

### Component: `journey.income-thanku-screen`

JSON key on API response: **`incomeThankuScreen`**

Combined income-capture and thank-you confirmation screen. The same component drives both the input view (where the user enters monthly income) and the confirmation view (shown after submit).

#### Main Component Fields

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `pageTitle` | Text (Short) | Yes | - | Page header title shown in the sidebar header (income view) |
| `illustrationSrc` | Media (Single) | Yes | - | Illustration shown above the form |
| `illustrationAlt` | Text (Short) | Yes | - | Alt text for the illustration |
| `title` | Text (Short) | Yes | - | Main heading (income form view) |
| `subtitle` | Text (Long) | No | - | Supporting copy below the title |
| `inputLabel` | Text (Short) | Yes | - | Floating label on the income input |
| `inputPlaceholder` | Text (Short) | No | - | Placeholder shown when the income input is empty |
| `ctaText` | Text (Short) | Yes | - | Sidebar primary CTA text |
| `thankuPrimaryCtaText` | Text (Short) | Yes | "Go to homepage" | Primary CTA on the thank-you confirmation view |
| `thankuSecondaryCtaText` | Text (Short) | Yes | "Continue journey" | Secondary CTA on the thank-you confirmation view |
| `thankuPageTitle` | Text (Short) | Yes | - | Page title shown while on the thank-you confirmation view |
| `incomeMin` | Number (Integer) | Yes | 10000 | Minimum allowed monthly income (inclusive) |
| `incomeMax` | Number (Integer) | Yes | 100000 | Maximum allowed monthly income (inclusive) |
| `rangeErrorMessage` | Text (Short) | Yes | - | Range error message template — supports `{min}` and `{max}` placeholders |
| `thankuIconSrc` | Media (Single) | Yes | - | Done icon shown on the thank-you confirmation view |
| `thankuIconAlt` | Text (Short) | Yes | - | Alt text for the done icon |
| `thankuMessage` | Text (Long) | Yes | - | Message shown below the done icon on the thank-you view |

#### Field Configurations

**pageTitle:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Example: "Personal loan"
```

**illustrationSrc:**
```
Type: Media (Single Image)
Allowed formats: SVG, PNG, WebP
Max size: 1MB
Required: Yes
Example: "/assets/personal-loan/icons/incomeMoney.svg"
```

**illustrationAlt:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Example: "Monthly income"
```

**title:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Example: "Please enter your details"
```

**subtitle:**
```
Type: Text (Long text)
Max length: 500
Required: No
Example: "Updating your PAN number may lead to a revision of your current offer."
```

**inputLabel:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Example: "Enter monthly income"
```

**inputPlaceholder:**
```
Type: Text (Short text)
Max length: 100
Required: No
Example: "Enter amount"
```

**ctaText:**
```
Type: Text (Short text)
Max length: 50
Required: Yes
Example: "Submit"
```

**thankuPrimaryCtaText:**
```
Type: Text (Short text)
Max length: 50
Required: Yes
Default value: "Go to homepage"
```

**thankuSecondaryCtaText:**
```
Type: Text (Short text)
Max length: 50
Required: Yes
Default value: "Continue journey"
Example: "Continue with Digital journey"
```

**thankuPageTitle:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Example: "Personal loan"
```

**incomeMin:**
```
Type: Number (Integer)
Min: 0
Required: Yes
Default: 10000
```

**incomeMax:**
```
Type: Number (Integer)
Min: 0
Required: Yes
Default: 100000
```

**rangeErrorMessage:**
```
Type: Text (Short text)
Max length: 300
Required: Yes
Notes: Supports `{min}` and `{max}` placeholders, both formatted as ₹ values (Indian formatting).
Example: "Monthly income must be between {min} and {max}"
```

**thankuIconSrc:**
```
Type: Media (Single Image/Animation)
Allowed formats: GIF, SVG, PNG, WebP
Max size: 1MB
Required: Yes
Example: "/assets/personal-loan/icons/done.gif"
```

**thankuIconAlt:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Example: "Submitted"
```

**thankuMessage:**
```
Type: Text (Long text)
Max length: 300
Required: Yes
Example: "Thank you our representative will call you shortly"
```

---

## API Response Examples

### Review Details Loader Response

```json
{
  "reviewDetailsLoader": {
    "title": "We are reviewing your details",
    "subtitleLine1": "Please wait while we review",
    "subtitleLine2": "your details",
    "waitPrefixText": "This process may take upto",
    "waitHighlightSeconds": 45,
    "waitSuffixText": "to complete, please stay on the screen",
    "safeVisualPath": {
      "id": 201,
      "name": "scan.gif",
      "url": "https://cdn.abcd.io/assets/personal-loan/gifs/scan.gif",
      "mime": "image/gif"
    },
    "waitIconPath": {
      "id": 202,
      "name": "loader.gif",
      "url": "https://cdn.abcd.io/assets/personal-loan/icons/loader.gif",
      "mime": "image/gif"
    },
    "sheetVisualPath": {
      "id": 203,
      "name": "brefile1.svg",
      "url": "https://cdn.abcd.io/assets/error-pages/brefile1.svg",
      "mime": "image/svg+xml"
    }
  }
}
```

### Offer Loader (LRE) Response

```json
{
  "offerLoaderLRE": {
    "title": "Fetching loan offers",
    "subtitleLine1": "Please wait while we look for the best loan",
    "subtitleLine2": "offers for you",
    "waitPrefixText": "This process may take upto",
    "waitHighlightSeconds": 45,
    "waitSuffixText": "to complete, please stay on the screen",
    "safeVisualPath": {
      "id": 211,
      "name": "offerLoader.svg",
      "url": "https://cdn.abcd.io/assets/personal-loan/icons/offerLoader.svg",
      "mime": "image/svg+xml"
    },
    "waitIconPath": {
      "id": 212,
      "name": "loader.gif",
      "url": "https://cdn.abcd.io/assets/personal-loan/icons/loader.gif",
      "mime": "image/gif"
    },
    "sheetVisualPath": {
      "id": 213,
      "name": "brefile1.svg",
      "url": "https://cdn.abcd.io/assets/error-pages/brefile1.svg",
      "mime": "image/svg+xml"
    }
  }
}
```

### Redirection Loader Response

```json
{
  "redirectionLoader": {
    "title": "Setting things up for your loan disbursal",
    "subtitleLine1": "Confirm your details with our trusted lending partner,",
    "subtitleLine2": "",
    "waitPrefixText": "This process will take just",
    "waitHighlightSeconds": 45,
    "waitSuffixText": "seconds, please stay on this screen.",
    "waitIconPath": {
      "id": 301,
      "name": "loader.gif",
      "url": "https://cdn.abcd.io/assets/personal-loan/icons/loader.gif",
      "mime": "image/gif"
    },
    "leftLogoPath": {
      "id": 302,
      "name": "abcd-logo.svg",
      "url": "https://cdn.abcd.io/assets/personal-loan/icons/abcd-logo.svg",
      "mime": "image/svg+xml"
    },
    "leftLogoAlt": "ABCD",
    "middleSlotPath": {
      "id": 303,
      "name": "plarrow.gif",
      "url": "https://cdn.abcd.io/assets/personal-loan/icons/plarrow.gif",
      "mime": "image/gif"
    },
    "middleSlotAlt": "Redirecting",
    "middleSlotRotationDeg": 90,
    "highlights": [
      {
        "iconPath": {
          "id": 311,
          "url": "https://cdn.abcd.io/assets/personal-loan/icons/flash.svg"
        },
        "iconAlt": "Instant offer",
        "label": "Get\nInstant Offer"
      },
      {
        "iconPath": {
          "id": 312,
          "url": "https://cdn.abcd.io/assets/personal-loan/icons/computer.svg"
        },
        "iconAlt": "No paperwork",
        "label": "No Paperwork\nRequired"
      },
      {
        "iconPath": {
          "id": 313,
          "url": "https://cdn.abcd.io/assets/personal-loan/icons/percent.svg"
        },
        "iconAlt": "Lowest interest rate",
        "label": "Lowest\ninterest rate"
      }
    ]
  }
}
```

### Milestones Response

```json
{
  "milestones": {
    "title": "Complete your personal loan application",
    "description": "Here's what to expect on your way to disbursal.",
    "headerIconPath": {
      "id": 401,
      "name": "CoinRupee.svg",
      "url": "https://cdn.abcd.io/assets/personal-loan/icons/CoinRupee.svg",
      "mime": "image/svg+xml"
    },
    "headerIconAlt": "Personal loan",
    "ctaText": "Got it",
    "steps": [
      {
        "id": "step-1",
        "title": "Check your eligibility",
        "description": "Share basic details so we can check loan options for you.",
        "tag": { "text": "About 3 mins", "variant": "duration" }
      },
      {
        "id": "step-2",
        "title": "Build your application",
        "description": "Add a few more details to complete your loan application.",
        "tag": { "text": "About 3 mins", "variant": "duration" }
      },
      {
        "id": "step-3",
        "title": "Lender assessment",
        "description": "Lenders review your profile to confirm the final offer.",
        "tag": { "text": "About 3 mins", "variant": "duration" }
      },
      {
        "id": "step-4",
        "title": "Lender offer generated",
        "description": "Pick the lender offer that works best for you.",
        "tag": { "text": "About 3 mins", "variant": "duration" }
      },
      {
        "id": "step-5",
        "title": "Agreement and disbursal",
        "description": "Sign the agreement and get the amount in your bank account.",
        "tag": { "text": "About 3 mins", "variant": "duration" }
      }
    ]
  }
}
```

### Income & Thank-You Screen Response

```json
{
  "incomeThankuScreen": {
    "pageTitle": "Personal loan",
    "illustrationSrc": {
      "id": 501,
      "name": "incomeMoney.svg",
      "url": "https://cdn.abcd.io/assets/personal-loan/icons/incomeMoney.svg",
      "mime": "image/svg+xml"
    },
    "illustrationAlt": "Monthly income",
    "title": "Please enter your details",
    "subtitle": "Updating your PAN number may lead to a revision of your current offer.",
    "inputLabel": "Enter monthly income",
    "inputPlaceholder": "Enter amount",
    "ctaText": "Submit",
    "thankuPrimaryCtaText": "Go to homepage",
    "thankuSecondaryCtaText": "Continue with Digital journey",
    "thankuPageTitle": "Personal loan",
    "incomeMin": 10000,
    "incomeMax": 100000,
    "rangeErrorMessage": "Monthly income must be between {min} and {max}",
    "thankuIconSrc": {
      "id": 502,
      "name": "done.gif",
      "url": "https://cdn.abcd.io/assets/personal-loan/icons/done.gif",
      "mime": "image/gif"
    },
    "thankuIconAlt": "Submitted",
    "thankuMessage": "Thank you our representative will call you shortly"
  }
}
```

---

## Default Content Values

### For Review Details Loader (partner="default")

```
title: "We are reviewing your details"
subtitleLine1: "Please wait while we review"
subtitleLine2: "your details"
waitPrefixText: "This process may take upto"
waitHighlightSeconds: 45
waitSuffixText: "to complete, please stay on the screen"
safeVisualPath: "/assets/personal-loan/gifs/scan.gif"
waitIconPath: "/assets/personal-loan/icons/loader.gif"
sheetVisualPath: "/assets/error-pages/brefile1.svg"
```

### For Offer Loader / LRE (partner="default")

```
title: "Fetching loan offers"
subtitleLine1: "Please wait while we look for the best loan"
subtitleLine2: "offers for you"
waitPrefixText: "This process may take upto"
waitHighlightSeconds: 45
waitSuffixText: "to complete, please stay on the screen"
safeVisualPath: "/assets/personal-loan/icons/offerLoader.svg"
waitIconPath: "/assets/personal-loan/icons/loader.gif"
sheetVisualPath: "/assets/error-pages/brefile1.svg"
```

### For Redirection Loader (partner="default")

```
title: "Setting things up for your loan disbursal"
subtitleLine1: "Confirm your details with our trusted lending partner,"
subtitleLine2: ""
waitPrefixText: "This process will take just"
waitHighlightSeconds: 45
waitSuffixText: "seconds, please stay on this screen."
waitIconPath: "/assets/personal-loan/icons/loader.gif"
leftLogoPath: "/assets/personal-loan/icons/abcd-logo.svg"
leftLogoAlt: "ABCD"
middleSlotPath: "/assets/personal-loan/icons/plarrow.gif"
middleSlotAlt: "Redirecting"
middleSlotRotationDeg: 90
```

### Default Redirection Loader Highlights

**Highlight 1: Instant Offer**
```
iconPath: "/assets/personal-loan/icons/flash.svg"
iconAlt: "Instant offer"
label: "Get\nInstant Offer"
```

**Highlight 2: No Paperwork**
```
iconPath: "/assets/personal-loan/icons/computer.svg"
iconAlt: "No paperwork"
label: "No Paperwork\nRequired"
```

**Highlight 3: Lowest Interest Rate**
```
iconPath: "/assets/personal-loan/icons/percent.svg"
iconAlt: "Lowest interest rate"
label: "Lowest\ninterest rate"
```

### For Milestones (partner="default")

```
title: "Complete your personal loan application"
description: "Here's what to expect on your way to disbursal."
headerIconPath: "/assets/personal-loan/icons/CoinRupee.svg"
headerIconAlt: "Personal loan"
ctaText: "Got it"
```

### Default Milestone Steps

**Step 1: Eligibility**
```
id: "step-1"
title: "Check your eligibility"
description: "Share basic details so we can check loan options for you."
tag.text: "About 3 mins"
tag.variant: "duration"
```

**Step 2: Build Application**
```
id: "step-2"
title: "Build your application"
description: "Add a few more details to complete your loan application."
tag.text: "About 3 mins"
tag.variant: "duration"
```

**Step 3: Lender Assessment**
```
id: "step-3"
title: "Lender assessment"
description: "Lenders review your profile to confirm the final offer."
tag.text: "About 3 mins"
tag.variant: "duration"
```

**Step 4: Lender Offer Generated**
```
id: "step-4"
title: "Lender offer generated"
description: "Pick the lender offer that works best for you."
tag.text: "About 3 mins"
tag.variant: "duration"
```

**Step 5: Agreement and Disbursal**
```
id: "step-5"
title: "Agreement and disbursal"
description: "Sign the agreement and get the amount in your bank account."
tag.text: "About 3 mins"
tag.variant: "duration"
```

### For Income & Thank-You Screen (partner="default")

```
pageTitle: "Personal loan"
illustrationSrc: "/assets/personal-loan/icons/incomeMoney.svg"
illustrationAlt: "Monthly income"
title: "Please enter your details"
subtitle: "Updating your PAN number may lead to a revision of your current offer."
inputLabel: "Enter monthly income"
inputPlaceholder: "Enter amount"
ctaText: "Submit"
thankuPrimaryCtaText: "Go to homepage"
thankuSecondaryCtaText: "Continue with Digital journey"
thankuPageTitle: "Personal loan"
incomeMin: 10000
incomeMax: 100000
rangeErrorMessage: "Monthly income must be between {min} and {max}"
thankuIconSrc: "/assets/personal-loan/icons/done.gif"
thankuIconAlt: "Submitted"
thankuMessage: "Thank you our representative will call you shortly"
```

---

## Implementation Checklist

### Phase 1: Loader Content Component (Shared)
- [ ] Create `journey.loader-content` component
- [ ] Add `title`, `subtitleLine1`, `subtitleLine2` text fields
- [ ] Add `waitPrefixText`, `waitHighlightSeconds`, `waitSuffixText` fields
- [ ] Add `safeVisualPath`, `waitIconPath`, `sheetVisualPath` media fields
- [ ] Wire the component into both `reviewDetailsLoader` and `offerLoaderLRE` slots

### Phase 2: Redirection Loader
- [ ] Create `journey.redirection-loader` component
- [ ] Add all base text fields (`title`, `subtitleLine1`, `subtitleLine2`, wait* fields)
- [ ] Add `waitIconPath` media field
- [ ] Add `leftLogoPath` + `leftLogoAlt`
- [ ] Add `middleSlotPath` + `middleSlotAlt` + `middleSlotRotationDeg`
- [ ] Create `journey.redirection-loader-highlight` repeatable component
- [ ] Add `iconPath`, `iconAlt`, `label` fields to the highlight component
- [ ] Wire `highlights` into `redirectionLoader`

### Phase 3: Milestones
- [ ] Create `journey.milestones` component
- [ ] Add `title`, `description`, `ctaText` text fields
- [ ] Add `headerIconPath` + `headerIconAlt` (optional)
- [ ] Create `journey.milestone-step` repeatable component
- [ ] Add `id`, `title`, `description` fields to the step component
- [ ] Create `journey.milestone-step-tag` single component
- [ ] Add `text`, `variant` (enum), `iconPath` fields to the tag component
- [ ] Wire `tag` into `journey.milestone-step`
- [ ] Wire `steps` into `journey.milestones`

### Phase 4: Income & Thank-You Screen
- [ ] Create `journey.income-thanku-screen` component
- [ ] Add header fields (`pageTitle`, `illustrationSrc`, `illustrationAlt`)
- [ ] Add income form fields (`title`, `subtitle`, `inputLabel`, `inputPlaceholder`, `ctaText`)
- [ ] Add range validation fields (`incomeMin`, `incomeMax`, `rangeErrorMessage`)
- [ ] Add thank-you view fields (`thankuPageTitle`, `thankuPrimaryCtaText`, `thankuSecondaryCtaText`, `thankuIconSrc`, `thankuIconAlt`, `thankuMessage`)

### Phase 5: Content Population
- [ ] Create default content entry with partner="default"
- [ ] Populate `reviewDetailsLoader` defaults and upload media
- [ ] Populate `offerLoaderLRE` defaults and upload media
- [ ] Populate `redirectionLoader` defaults
- [ ] Upload `leftLogoPath` and `middleSlotPath` media
- [ ] Add the 3 default redirection highlights with icons and labels
- [ ] Populate `milestones` defaults and upload `headerIconPath`
- [ ] Add the 5 default milestone steps with tags
- [ ] Populate `incomeThankuScreen` defaults and upload `illustrationSrc` + `thankuIconSrc`
- [ ] Test all media uploads

---

## Important Notes

1. **Shared Component:** `reviewDetailsLoader` and `offerLoaderLRE` reuse the same `journey.loader-content` schema. Only content values differ — do not duplicate the component definition.

2. **Component Nesting Structure:**
   ```
   redirectionLoader (main component)
   ├── highlights (repeatable: journey.redirection-loader-highlight)
   │   └── iconPath (media)

   milestones (main component)
   ├── steps (repeatable: journey.milestone-step)
   │   └── tag (single: journey.milestone-step-tag)
   │       └── iconPath (media)

   incomeThankuScreen (main component)
   ├── illustrationSrc (media)
   └── thankuIconSrc (media)
   ```

3. **Media Fields:** All media fields should return the full media object with `id`, `name`, `url`, `mime` properties.

4. **Line Breaks in Labels:** `redirectionLoader.highlights[].label` supports `\n` to control the rendered line break (e.g., `"Get\nInstant Offer"` renders on two lines).

5. **Income Range Placeholders:** `incomeThankuScreen.rangeErrorMessage` supports `{min}` and `{max}` placeholders. Both are substituted with Indian-formatted ₹ values at render time (e.g., `"Monthly income must be between ₹10,000 and ₹1,00,000"`).

6. **Shared Milestones:** The `milestones` component is shared across multiple screens via step-header drilldowns. Updating it changes the milestones panel everywhere it appears.

7. **Backward Compatibility:** These are new fields/components. Existing content should not break.
