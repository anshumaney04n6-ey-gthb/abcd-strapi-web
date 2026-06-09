# Tracks Referral Media Strapi Reference

**Date:** 2026-05-22
**Purpose:** Small Strapi reference for referral card gift image field in `abcd-tracks-web`

---

## Field In Scope

Only this field is in scope:

- `referralCard.referalMedia` (Media)

Keep the existing spelling `referalMedia` to match app contracts.

---

## Sample Value

```json
{
  "referralCard": {
    "referralMedia": "/uploads/referral_gift.webp"
  }
}
```

---

## App Usage

- `referalMedia` is read from CMS and used as referral gift image URL.
- If missing or invalid, app fallback image is used.
