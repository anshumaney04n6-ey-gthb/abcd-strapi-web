# Strapi Schema Requirements - Personal Loan Journey Pages
## Powered By Footer

**Document Version:** 1.0
**Date:** June 2, 2026
**Content-Type:** `personal-loan-journey-pages`

---

## Overview

This document outlines the schema requirements for the 
1. **Powered By Footer** — the shared "Powered by …" footer copy + secure-data assets rendered in the Sidebar's action footer (via `ActionConfig.footerBottomChildren`) for personal apply screens.

---

## 1. Powered By Footer (Complete Component)

### Component: `journey.powered-by-footer`

JSON key on API response: **`poweredByFooter`**

Shared "Powered by …" footer copy + secure-data assets, rendered in the Sidebar's action footer for personal apply screens. Variant (single/double) is decided per-screen at the OrchestratorPage call site.

#### Main Component Fields

| Field Name | Type | Required | Default | Description |
|------------|------|----------|---------|-------------|
| `poweredByText` | Text (Short) | Yes | - | "Powered by …" copy shown in the footer |
| `secureWithUsText` | Text (Short) | Yes | - | Reassurance copy shown alongside the secure icon |
| `secureIconPath` | Media (Single) | Yes | - | Shield/secure icon asset |
| `secureIconAlt` | Text (Short) | Yes | - | Alt text for the secure icon |

#### Field Configurations

**poweredByText:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Example: "Powered by Aditya Birla Capital Digital Ltd"
```

**secureWithUsText:**
```
Type: Text (Short text)
Max length: 200
Required: Yes
Example: "Your data is secure with us"
```

**secureIconPath:**
```
Type: Media (Single Image)
Allowed formats: SVG, PNG, WebP
Max size: 500KB
Required: Yes
Example: "/assets/personal-loan/icons/shieldCheck.svg"
```

**secureIconAlt:**
```
Type: Text (Short text)
Max length: 100
Required: Yes
Example: "Secure"
```

---

## API Response Example

### Powered By Footer Response

```json
{
  "poweredByFooter": {
    "poweredByText": "Powered by Aditya Birla Capital Digital Ltd",
    "secureWithUsText": "Your data is secure with us",
    "secureIconPath": {
      "id": 601,
      "name": "shieldCheck.svg",
      "url": "https://cdn.abcd.io/assets/personal-loan/icons/shieldCheck.svg",
      "mime": "image/svg+xml"
    },
    "secureIconAlt": "Secure"
  }
}
```

---

## Default Content Values

### For Powered By Footer (partner="default")

```
poweredByText: "Powered by Aditya Birla Capital Digital Ltd"
secureWithUsText: "Your data is secure with us"
secureIconPath: "/assets/personal-loan/icons/shieldCheck.svg"
secureIconAlt: "Secure"
```

---

## Implementation Checklist

### Phase 1: Powered By Footer Component
- [ ] Create `journey.powered-by-footer` component
- [ ] Add `poweredByText` text field
- [ ] Add `secureWithUsText` text field
- [ ] Add `secureIconPath` media field
- [ ] Add `secureIconAlt` text field
- [ ] Wire the component into the `poweredByFooter` slot on `personal-loan-journey-pages`

### Phase 2: Content Population
- [ ] Create default content entry with partner="default"
- [ ] Populate `poweredByFooter` defaults
- [ ] Upload `secureIconPath` media asset
- [ ] Verify the footer renders correctly across personal apply screens

---

## Important Notes

1. **Shared Component:** `poweredByFooter` is rendered on multiple personal apply screens via the Sidebar's `ActionConfig.footerBottomChildren` slot. Updating it changes the footer everywhere it appears.

2. **Media Field:** `secureIconPath` should return the full media object with `id`, `name`, `url`, `mime` properties.

3. **Backward Compatibility:** This is a new component. Existing content should not break.
