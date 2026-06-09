# Highlights `genericURL` Schema Addendum

## What Needs To Be Added

`genericURL` is a new top-level prop inside the `highlights` component.

This is the new field to add in Strapi:

| Property | Value |
|----------|-------|
| Component | `investments-dashboard.highlights` |
| Field name | `genericURL` |
| Field type | `String` |
| Required | No |
| Default | `""` |
| Purpose | Generic deep-link URL used by the highlights section |

---

## Where It Lives

```
investments_dashboard_pages
  └── highlights                        ← investments-dashboard.highlights (component)
        ├── title
        ├── showNavigation
        ├── genericURL                  ← new field to add
        └── items[]                     ← highlights-item (sub-component)
              ├── id
              ├── title
              ├── ctaText
              └── ...
```

---

## Code Change Reference

```ts
export const HIGHLIGHTS_CONFIG = {
  title: "Special highlights",
  showNavigation: true,
  genericURL: "https://adityabirlaapp.blostem.com/purchase/80f5547d-9238-4006-8e67-4dee91f64642",
  items: [ ... ],
};
```

---

## Strapi Schema Update

Add this field under the `highlights` component:

```json
{
  "genericURL": {
    "type": "string"
  }
}
```

---

## Strapi Admin

1. Open **Content Manager** → **investments-dashboard-pages**
2. Select the entry (e.g. `subProduct: fixed-deposits`, `partner: default`)
3. Scroll to the **Highlights** component block
4. Fill in the **`genericURL`** field with the deep-link URL

---

## API Payload Addition

Only this new property needs to be added inside `highlights`:

```json
{
  "data": {
    "highlights": {
      "genericURL": "https://adityabirlaapp.blostem.com/purchase/80f5547d-9238-4006-8e67-4dee91f64642"
    }
  }
}
```

---

## Expected Response Addition

```json
{
  "data": [
    {
      "id": 1,
      "attributes": {
        "highlights": {
          "genericURL": "https://adityabirlaapp.blostem.com/purchase/80f5547d-9238-4006-8e67-4dee91f64642"
        }
      }
    }
  ]
}
```

---

## Source Files

| File | Purpose |
|------|---------|
| `abcd-investments-web/src/app/[subProduct]/customer/@dashboard/content/fallback.ts` | `HIGHLIGHTS_CONFIG` — default value for `genericURL` |
| `abcd-investments-web/src/app/[subProduct]/customer/@dashboard/content/index.ts` | Transformer that maps CMS `highlights.genericURL` to the dashboard |
| `Dashboard_Page.md` | Full dashboard page schema reference |
