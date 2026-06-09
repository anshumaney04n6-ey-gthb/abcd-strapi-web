# Strapi Schema Requirements - Personal Loan Landing Page Widget Component

**Document Version:** 1.0  
**Date:** May 28, 2026  
**Content-Type:** `personal-loan-landing-pages`

---

## Overview

This document outlines the schema requirements for adding new fields to the **Widget Component** in the Personal Loan Landing Page. The widget handles OTP verification, consent management, and user input configurations.

---

## Content-Type Information

**Content-Type:** `personal-loan-landing-pages`  
**Component to Update:** `pl-landing.widget`  
**Category:** `pl-landing`

---

## Changes Summary

### New Fields to Add in Widget Component:
1. `mobileVerificationText` - Text field (direct field in widget component)

### New Sub-Components to Create:
1. `pl-landing.widget-consent-config` - Consent configuration with terms & privacy
2. `pl-landing.widget-input-config` - Reusable input field configuration

### Component References to Add:
1. `consentConfig` - Reference to widget-consent-config
2. `nameInputConfig` - Reference to widget-input-config  
3. `mobileInputConfig` - Reference to widget-input-config

---

## 1. Update Existing Widget Component

### Component: `pl-landing.widget`

**Add this new field to existing component:**

| Field Name | Type | Required | Max Length | Default | Description |
|-----------|------|----------|------------|---------|-------------|
| `mobileVerificationText` | Text (Short) | No | 255 | "OTP will be sent to your mobile number for verification" | Text shown during mobile verification |

**Add these component references to existing component:**

| Field Name | Type | Component Reference | Required | Description |
|-----------|------|---------------------|----------|-------------|
| `consentConfig` | Component (Single) | `pl-landing.widget-consent-config` | No | Consent text with terms & privacy policy |
| `nameInputConfig` | Component (Single) | `pl-landing.widget-input-config` | No | Name input field configuration |
| `mobileInputConfig` | Component (Single) | `pl-landing.widget-input-config` | No | Mobile input field configuration |

#### Field Configuration

**mobileVerificationText:**
```
Type: Text (Short text)
Max length: 255
Required: No
Default value: "OTP will be sent to your mobile number for verification"
Example: "OTP will be sent to your mobile number for verification"
```

---

## 2. New Sub-Component: widget-consent-config

### Component: `pl-landing.widget-consent-config`

**Purpose:** Manages consent text, terms & conditions, and privacy policy links with expandable read more/less functionality.

**Component Settings:**
- Display Name: `Widget Consent Config`
- Icon: `check-square`
- Category: `pl-landing`

| Field Name | Type | Required | Max Length | Default | Description |
|-----------|------|----------|------------|---------|-------------|
| `label` | Text (Long/HTML) | Yes | 500 | - | Consent label with HTML support |
| `termsText` | Text (Short) | Yes | 100 | - | Display text for Terms link |
| `termsUrl` | Text (Short/URL) | Yes | 500 | - | URL for Terms & Conditions |
| `privacyText` | Text (Short) | Yes | 100 | - | Display text for Privacy link |
| `privacyUrl` | Text (Short/URL) | Yes | 500 | - | URL for Privacy Policy |
| `previewText` | Text (Short) | No | 500 | "" | Truncated preview of consent |
| `fullText` | Text (Long) | No | 1000 | "" | Complete consent with legal text |
| `readMoreText` | Text (Short) | No | 50 | "Read more" | Expand action text |
| `readLessText` | Text (Short) | No | 50 | "Read less" | Collapse action text |

#### Field Configurations

**label:**
```
Type: Text (Long text) with HTML support
Max length: 500
Required: Yes
HTML Support: Yes (for <strong>, <b> tags)
Example: "By Clicking <strong>\"Apply now\"</strong> you consent to the"
```

**termsText:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Example: "Terms & Conditions"
```

**termsUrl:**
```
Type: Text (Short text)
Max length: 500
Required: Yes
Format: Valid URL (must start with http:// or https://)
Example: "https://www.adityabirlacapital.com/abc-digital/terms-conditions"
```

**privacyText:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Example: "Privacy Policy"
```

**privacyUrl:**
```
Type: Text (Short text)
Max length: 500
Required: Yes
Format: Valid URL (must start with http:// or https://)
Example: "https://www.adityabirlacapital.com/abcd/privacy-policy"
```

**previewText:**
```
Type: Text (Short text)
Max length: 500
Required: No
Usage: Shown initially before user expands
Example: "of Aditya Birla Capital Digital (ABCD) platform..."
```

**fullText:**
```
Type: Text (Long text)
Max length: 1000
Required: No
Usage: Complete legal text shown after "Read more"
Example: "of Aditya Birla Capital Digital (ABCD) platform. ABCDL is a Corporate Agent (IRDAI Reg No. CA0871) and does not underwrite the risk or act as an insurer. All products are subject to the terms and conditions of the relevant policy. For more details on risk factors, terms and conditions please read the policy documents carefully before concluding a sale."
```

**readMoreText:**
```
Type: Text (Short text)
Max length: 50
Required: No
Default value: "Read more"
Example: "Read more"
```

**readLessText:**
```
Type: Text (Short text)
Max length: 50
Required: No
Default value: "Read less"
Example: "Read less"
```

---

## 3. New Sub-Component: widget-input-config

### Component: `pl-landing.widget-input-config`

**Purpose:** Reusable component for input field configurations (used for both name and mobile inputs).

**Component Settings:**
- Display Name: `Widget Input Config`
- Icon: `pencil`
- Category: `pl-landing`

| Field Name | Type | Required | Max Length | Description |
|-----------|------|----------|------------|-------------|
| `label` | Text (Short) | Yes | 100 | Input field label |
| `placeholder` | Text (Short) | Yes | 150 | Input placeholder text |

#### Field Configurations

**label:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Example: "Name", "Mobile number"
```

**placeholder:**
```
Type: Text (Short text)
Max length: 150
Required: Yes
Example: "Enter your name", "Enter your mobile number"
```

---

## Default Content Values

### Widget Field
```json
{
  "mobileVerificationText": "OTP will be sent to your mobile number for verification"
}
```

### Consent Config
```json
{
  "label": "By Clicking <strong>\"Apply now\"</strong> you consent to the",
  "termsText": "Terms & Conditions",
  "termsUrl": "https://www.adityabirlacapital.com/abc-digital/terms-conditions",
  "privacyText": "Privacy Policy",
  "privacyUrl": "https://www.adityabirlacapital.com/abcd/privacy-policy",
  "previewText": "of Aditya Birla Capital Digital (ABCD) platform...",
  "fullText": "of Aditya Birla Capital Digital (ABCD) platform. ABCDL is a Corporate Agent (IRDAI Reg No. CA0871) and does not underwrite the risk or act as an insurer. All products are subject to the terms and conditions of the relevant policy. For more details on risk factors, terms and conditions please read the policy documents carefully before concluding a sale.",
  "readMoreText": "Read more",
  "readLessText": "Read less"
}
```

### Name Input Config
```json
{
  "label": "Name",
  "placeholder": "Enter your name"
}
```

### Mobile Input Config
```json
{
  "label": "Mobile number",
  "placeholder": "Enter your mobile number"
}
```

---

## Complete API Response Example

```json
{
  "data": {
    "id": 206,
    "documentId": "el6gfzd0wbmdncdmw55eczcm",
    "partner": "default",
    "subProduct": "personal",
    "widget": {
      "id": 95,
      "headerTitle": "Verified partners. <strong>100% transparent</strong>. Fully secure.",
      "headerBackgroundColor": "#7c2279",
      "title": "Enter your mobile number to get started",
      "mobileInputPlaceholder": "Enter 10-digit mobile number",
      "helperText": "OTP will be sent to your mobile number",
      "mobileVerificationText": "OTP will be sent to your mobile number for verification",
      "consentConfig": {
        "id": 42,
        "label": "By Clicking <strong>\"Apply now\"</strong> you consent to the",
        "termsText": "Terms & Conditions",
        "termsUrl": "https://www.adityabirlacapital.com/abc-digital/terms-conditions",
        "privacyText": "Privacy Policy",
        "privacyUrl": "https://www.adityabirlacapital.com/abcd/privacy-policy",
        "previewText": "of Aditya Birla Capital Digital (ABCD) platform...",
        "fullText": "of Aditya Birla Capital Digital (ABCD) platform. ABCDL is a Corporate Agent (IRDAI Reg No. CA0871) and does not underwrite the risk or act as an insurer. All products are subject to the terms and conditions of the relevant policy. For more details on risk factors, terms and conditions please read the policy documents carefully before concluding a sale.",
        "readMoreText": "Read more",
        "readLessText": "Read less"
      },
      "ctaConfig": {
        "id": 43,
        "buttonText": "Apply now",
        "trustText": "Join 1L+ investors trusting ABCD for Personal Loans",
        "loadingText": "Processing..."
      },
      "nameInputConfig": {
        "id": 44,
        "label": "Name",
        "placeholder": "Enter your name"
      },
      "mobileInputConfig": {
        "id": 45,
        "label": "Mobile number",
        "placeholder": "Enter your mobile number"
      }
    }
  }
}
```

---

## Implementation Checklist

### Phase 1: Create Sub-Components (20 mins)

- [ ] **Create `widget-consent-config` component**
  - Navigate to Content-Type Builder → Components → Create new component
  - Category: `pl-landing`
  - Display Name: `Widget Consent Config`
  - Icon: `check-square`
  - Add 9 fields:
    - [ ] `label` (Text, Long, Required, Max 500, HTML enabled)
    - [ ] `termsText` (Text, Short, Required, Max 100)
    - [ ] `termsUrl` (Text, Short, Required, Max 500)
    - [ ] `privacyText` (Text, Short, Required, Max 100)
    - [ ] `privacyUrl` (Text, Short, Required, Max 500)
    - [ ] `previewText` (Text, Short, Optional, Max 500)
    - [ ] `fullText` (Text, Long, Optional, Max 1000)
    - [ ] `readMoreText` (Text, Short, Optional, Max 50, Default: "Read more")
    - [ ] `readLessText` (Text, Short, Optional, Max 50, Default: "Read less")
  - [ ] Save component

- [ ] **Create `widget-input-config` component**
  - Navigate to Content-Type Builder → Components → Create new component
  - Category: `pl-landing`
  - Display Name: `Widget Input Config`
  - Icon: `pencil`
  - Add 2 fields:
    - [ ] `label` (Text, Short, Required, Max 100)
    - [ ] `placeholder` (Text, Short, Required, Max 150)
  - [ ] Save component

### Phase 2: Update Widget Component (15 mins)

- [ ] **Open `pl-landing.widget` component**
  - Navigate to Content-Type Builder → Components → pl-landing → widget

- [ ] **Add new text field**
  - [ ] Add `mobileVerificationText` (Text, Short, Optional, Max 255)
  - [ ] Set default value: "OTP will be sent to your mobile number for verification"
  - [ ] Position it after `helperText` field

- [ ] **Add component references**
  - [ ] Add `consentConfig` field
    - Type: Component (Single)
    - Component: `pl-landing.widget-consent-config`
    - Required: No
  - [ ] Add `nameInputConfig` field
    - Type: Component (Single)
    - Component: `pl-landing.widget-input-config`
    - Required: No
  - [ ] Add `mobileInputConfig` field
    - Type: Component (Single)
    - Component: `pl-landing.widget-input-config`
    - Required: No

- [ ] **Save all changes**

### Phase 3: Populate Default Content (25 mins)

- [ ] **Open Content Manager**
  - Navigate to Content Manager → `personal-loan-landing-pages`
  - Filter by partner="default" or open existing entry

- [ ] **Update widget section**
  - Scroll to widget component

- [ ] **Set mobileVerificationText**
  - [ ] Enter: "OTP will be sent to your mobile number for verification"

- [ ] **Configure consentConfig**
  - [ ] Click "Add component" for consentConfig
  - [ ] Fill all fields:
    - label: `By Clicking <strong>"Apply now"</strong> you consent to the`
    - termsText: `Terms & Conditions`
    - termsUrl: `https://www.adityabirlacapital.com/abc-digital/terms-conditions`
    - privacyText: `Privacy Policy`
    - privacyUrl: `https://www.adityabirlacapital.com/abcd/privacy-policy`
    - previewText: `of Aditya Birla Capital Digital (ABCD) platform...`
    - fullText: `of Aditya Birla Capital Digital (ABCD) platform. ABCDL is a Corporate Agent (IRDAI Reg No. CA0871) and does not underwrite the risk or act as an insurer. All products are subject to the terms and conditions of the relevant policy. For more details on risk factors, terms and conditions please read the policy documents carefully before concluding a sale.`
    - readMoreText: `Read more`
    - readLessText: `Read less`

- [ ] **Configure nameInputConfig**
  - [ ] Click "Add component" for nameInputConfig
  - [ ] Fill fields:
    - label: `Name`
    - placeholder: `Enter your name`

- [ ] **Configure mobileInputConfig**
  - [ ] Click "Add component" for mobileInputConfig
  - [ ] Fill fields:
    - label: `Mobile number`
    - placeholder: `Enter your mobile number`

- [ ] **Save and Publish**

### Phase 4: API Testing (15 mins)

- [ ] **Test API endpoint**
  ```bash
  curl "http://localhost:1337/api/personal-loan-landing-pages?filters[partner][$eq]=default&populate=*"
  ```

- [ ] **Verify response structure**
  - [ ] Check widget component returned
  - [ ] Verify `mobileVerificationText` field present
  - [ ] Verify `consentConfig` populated with all 9 fields
  - [ ] Verify `nameInputConfig` populated with label and placeholder
  - [ ] Verify `mobileInputConfig` populated with label and placeholder
  - [ ] Confirm HTML tags preserved in `consentConfig.label`
  - [ ] Confirm URLs formatted correctly

- [ ] **Test with different partners**
  - [ ] Test with partner-specific content if applicable
  - [ ] Verify fallback behavior


## Component Hierarchy

```
pl-landing.widget (existing component)
├── mobileVerificationText (NEW - direct field)
├── consentConfig (NEW - component reference)
│   └── pl-landing.widget-consent-config (NEW component)
│       ├── label
│       ├── termsText
│       ├── termsUrl
│       ├── privacyText
│       ├── privacyUrl
│       ├── previewText
│       ├── fullText
│       ├── readMoreText
│       └── readLessText
├── ctaConfig (existing)
├── nameInputConfig (NEW - component reference)
│   └── pl-landing.widget-input-config (NEW component)
│       ├── label
│       └── placeholder
└── mobileInputConfig (NEW - component reference)
    └── pl-landing.widget-input-config (reused component)
        ├── label
        └── placeholder
```