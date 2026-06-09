# bannerFD - Complete Schema Documentation

## Content-Type: investments-dashboard.banner-fd

**Parent Collection Name:** `investments_dashboard_pages`  
**Parent Singular Name:** `investments-dashboard-page`  
**Parent Plural Name:** `investments-dashboard-pages`  
**Parent Field Name:** `bannerFD`  
**Draft & Publish:** Inherited from parent content-type

---

## All Component Fields (Exact Strapi Field Names)

| Field Name | Type | Required | Default | Max | Description |
|------------|------|----------|---------|-----|-------------|
| `id` | string | No | `suryoday` | - | Banner identity key |
| `amount` | string | No | `8.05` | - | Interest value shown on hero banner |
| `unit` | string | No | `p.a` | - | Unit for interest value |
| `prefix` | string | No | `Earn up to ` | - | Prefix text before amount |
| `heading` | string | No | `Suryoday Small Finance Bank` | - | Hero title |
| `badge` | string | No | `Popular Choice` | - | Badge label |
| `buttonLabel` | string | No | `Book now` | - | CTA text |
| `logoImagePath` | media/string | No | fallback asset | - | Logo image |
| `bannerImagePath` | media/string | No | fallback asset | - | Main banner image |
| `backgroundImagePath` | media/string | No | fallback asset | - | Background image |
| `badgeIconPath` | media/string | No | fallback asset | - | Badge icon |
| `chevronIconPath` | media/string | No | fallback asset | - | Chevron icon |
| `decorativeIconPath` | media/string | No | fallback asset | - | Decorative icon |
| `gradientColor1` | string | No | `rgba(115, 0, 48, 1)` | - | Primary gradient color |
| `gradientColor2` | string | No | `rgba(138, 11, 28, 0)` | - | Secondary gradient color |
| `items` | component[] | No | fallback | 3 | Feature points shown in hero |
| `cards` | component[] | No | fallback | 3 | Trust cards shown in hero |
| `banners` | component[] | No | fallback | 3 | Carousel slides |

---

## API Endpoints

### Base URL
```text
/api/investments-dashboard-pages
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/investments-dashboard-pages` | List pages with bannerFD component |
| GET | `/api/investments-dashboard-pages/:id` | Get one page with bannerFD component |
| POST | `/api/investments-dashboard-pages` | Create page containing bannerFD |
| PUT | `/api/investments-dashboard-pages/:id` | Update page bannerFD |
| DELETE | `/api/investments-dashboard-pages/:id` | Delete page |

### Query Parameters (Banner-Focused)
```text
?populate[bannerFD][populate]=*
?filters[subProduct][$eq]=fixed-deposits
?filters[partner][$eq]=default
```

---

## Complete JSON Structure with enabled/order fields

> **Note:** Keep this structure aligned with `transformDashboardCMSResponse` and fallback content.  
> **Note:** Use `order` inside repeatable items when order is managed in CMS.

```json
{
  "data": {
    "bannerFD": {
      "id": "suryoday",
      "amount": "8.05",
      "unit": "p.a",
      "prefix": "Earn up to ",
      "heading": "Suryoday Small Finance Bank",
      "badge": "Popular Choice",
      "buttonLabel": "Book now",
      "logoImagePath": "media_or_url",
      "bannerImagePath": "media_or_url",
      "backgroundImagePath": "media_or_url",
      "badgeIconPath": "media_or_url",
      "chevronIconPath": "media_or_url",
      "decorativeIconPath": "media_or_url",
      "gradientColor1": "rgba(115, 0, 48, 1)",
      "gradientColor2": "rgba(138, 11, 28, 0)",
      "items": [
        {
          "order": 1,
          "id": "item-1",
          "iconPath": "media_or_url",
          "label": "Instant withdrawal",
          "description": "available"
        }
      ],
      "cards": [
        {
          "order": 1,
          "id": "card-1",
          "iconPath": "media_or_url",
          "title": "RBI",
          "subtitle": "Regulated"
        }
      ],
      "banners": [
        {
          "order": 1,
          "id": "shivalik",
          "amount": "8.75",
          "unit": "p.a",
          "prefix": "Earn up to ",
          "heading": "Shivalik Small Finance Bank",
          "badge": "Highest Interest Rate",
          "buttonLabel": "Book now",
          "logoImagePath": "media_or_url",
          "bannerImagePath": "media_or_url",
          "backgroundImagePath": "media_or_url",
          "badgeIconPath": "media_or_url",
          "chevronIconPath": "media_or_url",
          "decorativeIconPath": "media_or_url",
          "gradientColor1": "rgba(79, 70, 122, 1)",
          "gradientColor2": "rgba(100, 85, 150, 0)",
          "items": [
            {
              "order": 1,
              "id": "item-1",
              "iconPath": "media_or_url",
              "label": "Instant withdrawal",
              "description": "available"
            }
          ],
          "cards": [
            {
              "order": 1,
              "id": "card-1",
              "iconPath": "media_or_url",
              "title": "RBI",
              "subtitle": "Regulated"
            }
          ]
        }
      ]
    }
  }
}
```

---

## Components Detail

### 1. investments-dashboard.banner-fd-item
**Max Items:** 3

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `iconPath` | media/string | No | - |
| `label` | string | No | `""` |
| `description` | string | No | `""` |
| `order` | number | No | - |

---

### 2. investments-dashboard.banner-fd-card
**Max Items:** 3

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `iconPath` | media/string | No | - |
| `title` | string | Yes | - |
| `subtitle` | string | No | `""` |
| `order` | number | No | - |

---

### 3. investments-dashboard.banner-fd-slide
**Max Items:** 3

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | Yes | - |
| `amount` | string | No | inherited |
| `unit` | string | No | `p.a` |
| `prefix` | string | No | `Earn up to ` |
| `heading` | string | No | inherited |
| `badge` | string | No | inherited |
| `buttonLabel` | string | No | `Book now` |
| `logoImagePath` | media/string | No | inherited |
| `bannerImagePath` | media/string | No | inherited |
| `backgroundImagePath` | media/string | No | inherited |
| `badgeIconPath` | media/string | No | inherited |
| `chevronIconPath` | media/string | No | inherited |
| `decorativeIconPath` | media/string | No | inherited |
| `gradientColor1` | string | No | inherited |
| `gradientColor2` | string | No | inherited |
| `items` | component[] | No | inherited |
| `cards` | component[] | No | inherited |
| `order` | number | No | - |

---

## Restrictions Summary Table

| Section | Component | Max Items |
|---------|-----------|-----------|
| Banner Items | banner-fd-item | 3 |
| Banner Cards | banner-fd-card | 3 |
| Banner Carousel Slides | banner-fd-slide | 3 |

---

## Transform Compatibility Notes

This schema is designed to work with the dashboard transformer in `content/index.ts`:

1. Media fields can be plain string URLs or Strapi media objects.
2. `bannerImagePath` should use preferred format resolution (`medium > large > small > thumbnail > url`).
3. Numeric-keyed object arrays are normalized to arrays.
4. `items[].iconPath` and `cards[].iconPath` are normalized for top-level and nested `banners[]`.
5. CMS may return numeric `id` values for repeatable components; transformer should safely handle them.

---

## Populate Query for Full bannerFD Response

```text
/api/investments-dashboard-pages?
filters[subProduct][$eq]=fixed-deposits&
filters[partner][$eq]=default&
populate[bannerFD][populate][items][populate]=*&
populate[bannerFD][populate][cards][populate]=*&
populate[bannerFD][populate][banners][populate][items][populate]=*&
populate[bannerFD][populate][banners][populate][cards][populate]=*&
populate[bannerFD][populate][logoImagePath]=*&
populate[bannerFD][populate][bannerImagePath]=*&
populate[bannerFD][populate][backgroundImagePath]=*&
populate[bannerFD][populate][badgeIconPath]=*&
populate[bannerFD][populate][chevronIconPath]=*&
populate[bannerFD][populate][decorativeIconPath]=*
```

---

## Fallback Content Mapping

> `fallback.ts` path -> BannerFD field mapping

| Fallback Constant/Path | BannerFD Field |
|------------------------|----------------|
| `BANNER_FD_CONFIG.id` | `bannerFD.id` |
| `BANNER_FD_CONFIG.amount` | `bannerFD.amount` |
| `BANNER_FD_CONFIG.unit` | `bannerFD.unit` |
| `BANNER_FD_CONFIG.prefix` | `bannerFD.prefix` |
| `BANNER_FD_CONFIG.heading` | `bannerFD.heading` |
| `BANNER_FD_CONFIG.badge` | `bannerFD.badge` |
| `BANNER_FD_CONFIG.buttonLabel` | `bannerFD.buttonLabel` |
| `BANNER_FD_CONFIG.logoImagePath` | `bannerFD.logoImagePath` |
| `BANNER_FD_CONFIG.bannerImagePath` | `bannerFD.bannerImagePath` |
| `BANNER_FD_CONFIG.backgroundImagePath` | `bannerFD.backgroundImagePath` |
| `BANNER_FD_CONFIG.badgeIconPath` | `bannerFD.badgeIconPath` |
| `BANNER_FD_CONFIG.chevronIconPath` | `bannerFD.chevronIconPath` |
| `BANNER_FD_CONFIG.decorativeIconPath` | `bannerFD.decorativeIconPath` |
| `BANNER_FD_CONFIG.gradientColor1` | `bannerFD.gradientColor1` |
| `BANNER_FD_CONFIG.gradientColor2` | `bannerFD.gradientColor2` |
| `BANNER_ITEMS` | `bannerFD.items` |
| `BANNER_CARDS` | `bannerFD.cards` |
| `BANNER_FD_CONFIG.banners` | `bannerFD.banners` |

---

## Source Files

| File | Purpose |
|------|---------|
| `abcd-investments-web/src/app/[subProduct]/customer/@dashboard/content/fallback.ts` | Fallback values (`BANNER_FD_CONFIG`, `BANNER_ITEMS`, `BANNER_CARDS`) |
| `abcd-investments-web/src/app/[subProduct]/customer/@dashboard/content/index.ts` | CMS transformer + bannerFD normalizers |
| `abcd-investments-web/src/app/[subProduct]/customer/@dashboard/DashboardClient.tsx` | BannerFD rendering in dashboard client |
