# Tracks Landing Page - Hero Slides API Documentation v5

This document provides documentation for the Hero Slides carousel feature in the Tracks Landing Page.

---

## Table of Contents

2. [Hero Section Schema](#hero-section-schema)
3. [Hero Slide Component](#hero-slide-component)
4. [API Endpoints](#api-endpoints)
5. [Sample API Request & Response](#sample-api-request--response)
6. [Implementation Notes](#implementation-notes)

---
## Hero Section Schema

### Main Attributes

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `heroSlides` | component[] | No | - | Array of hero slides (max 5) |
| `heroTitle` | string | No | - | Fallback title if no slides |
| `heroSubtitle` | string | No | - | Fallback subtitle if no slides |
| `heroImage` | media | No | - | Fallback background if no slides |
| `heroImageAlt` | string | No | - | Fallback image alt text |
| `showHeroSeparator` | boolean | No | `true` | Show decorative separator |
| `heroBackgroundColor` | string | No | - | Custom background color |
| `heroBackgroundGradient` | string | No | - | Custom gradient |

### Carousel Configuration

| Attribute | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `carouselAutoScroll` | boolean | No | `true` | Enable auto scroll |
| `carouselInterval` | integer | No | `5000` | Auto scroll interval (milliseconds) |
| `carouselPauseOnHover` | boolean | No | `true` | Pause on hover |

---

## Hero Slide Component

**File:** `src/components/tracks-landing/hero-slide.json`

Each hero slide contains:

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| `title` | string | Yes | Slide title |
| `subtitle` | string | Yes | Slide subtitle/description |
| `background` | media | Yes | Background image |
| `order` | integer | No | Display order (1, 2, 3...) |

### Example Slide

```json
{
  "id": 1,
  "title": "Check Your Credit Score for Free in seconds",
  "subtitle": "Get instant access to your credit score with competitive rates",
  "background": {
    "data": {
      "id": 123,
      "attributes": {
        "name": "hero-slide-1.png",
        "url": "/uploads/hero_slide_1.png",
        "width": 1920,
        "height": 800,
        "formats": {
          "large": {
            "url": "/uploads/large_hero_slide_1.png",
            "width": 1000,
            "height": 417
          },
          "medium": {
            "url": "/uploads/medium_hero_slide_1.png",
            "width": 750,
            "height": 313
          },
          "small": {
            "url": "/uploads/small_hero_slide_1.png",
            "width": 500,
            "height": 208
          }
        }
      }
    }
  },
  "order": 1
}
```

---

## API Endpoints

### Get Hero Slides

**GET** `/api/tracks-landing-pages?filters[subProduct][$eq]=credit&populate[heroSlides][populate]=background`

### Query Parameters

| Parameter | Description | Example |
|-----------|-------------|---------|
| `filters[subProduct][$eq]` | Filter by product type | `credit` |
| `filters[partner][$eq]` | Filter by partner | `default`, `icici`, `hdfc` |
| `populate[heroSlides][populate]` | Populate hero slides with background images | `background` |

### Full Population Example

```
GET /api/tracks-landing-pages?filters[subProduct][$eq]=credit&filters[partner][$eq]=default&populate[0]=heroSlides&populate[1]=heroSlides.background
```

---

## Sample API Request & Response

### Request

```bash
GET /api/tracks-landing-pages?filters[subProduct][$eq]=credit&filters[partner][$eq]=default&populate[heroSlides][populate]=background
```

### Response

```json
{
  "data": [
    {
      "id": 1,
      "attributes": {
        "subProduct": "credit",
        "partner": "default",
        "createdAt": "2026-05-15T10:00:00.000Z",
        "updatedAt": "2026-05-19T15:30:00.000Z",
        "publishedAt": "2026-05-15T12:00:00.000Z",
        
        "carouselAutoScroll": true,
        "carouselInterval": 5000,
        "carouselPauseOnHover": true,
        
        "heroTitle": "Check Your Credit Score for Free in seconds",
        "heroSubtitle": "Get instant access to your credit score with competitive rates",
        "heroImageAlt": "Credit Score Dashboard",
        "showHeroSeparator": true,
        
        "heroSlides": [
          {
            "id": 1,
            "title": "Check Your Credit Score for Free in seconds",
            "subtitle": "Get instant access to your credit score with competitive rates",
            "order": 1,
            "background": {
              "data": {
                "id": 101,
                "attributes": {
                  "name": "hero-slide-1.png",
                  "url": "/uploads/hero_slide_1_abc123.png",
                  "width": 1920,
                  "height": 800,
                  "size": 245.67,
                  "ext": ".png",
                  "mime": "image/png",
                  "formats": {
                    "large": {
                      "url": "/uploads/large_hero_slide_1_abc123.png",
                      "width": 1000,
                      "height": 417
                    },
                    "medium": {
                      "url": "/uploads/medium_hero_slide_1_abc123.png",
                      "width": 750,
                      "height": 313
                    },
                    "small": {
                      "url": "/uploads/small_hero_slide_1_abc123.png",
                      "width": 500,
                      "height": 208
                    },
                    "thumbnail": {
                      "url": "/uploads/thumbnail_hero_slide_1_abc123.png",
                      "width": 245,
                      "height": 102
                    }
                  }
                }
              }
            }
          },
          {
            "id": 2,
            "title": "Track Your Credit Journey",
            "subtitle": "Monitor changes and understand what impacts your score",
            "order": 2,
            "background": {
              "data": {
                "id": 102,
                "attributes": {
                  "name": "hero-slide-2.png",
                  "url": "/uploads/hero_slide_2_def456.png",
                  "width": 1920,
                  "height": 800,
                  "size": 258.34,
                  "ext": ".png",
                  "mime": "image/png",
                  "formats": {
                    "large": {
                      "url": "/uploads/large_hero_slide_2_def456.png",
                      "width": 1000,
                      "height": 417
                    },
                    "medium": {
                      "url": "/uploads/medium_hero_slide_2_def456.png",
                      "width": 750,
                      "height": 313
                    },
                    "small": {
                      "url": "/uploads/small_hero_slide_2_def456.png",
                      "width": 500,
                      "height": 208
                    },
                    "thumbnail": {
                      "url": "/uploads/thumbnail_hero_slide_2_def456.png",
                      "width": 245,
                      "height": 102
                    }
                  }
                }
              }
            }
          },
          {
            "id": 3,
            "title": "Improve Your Financial Health",
            "subtitle": "Get personalized insights and tips to boost your credit score",
            "order": 3,
            "background": {
              "data": {
                "id": 103,
                "attributes": {
                  "name": "hero-slide-3.png",
                  "url": "/uploads/hero_slide_3_ghi789.png",
                  "width": 1920,
                  "height": 800,
                  "size": 267.89,
                  "ext": ".png",
                  "mime": "image/png",
                  "formats": {
                    "large": {
                      "url": "/uploads/large_hero_slide_3_ghi789.png",
                      "width": 1000,
                      "height": 417
                    },
                    "medium": {
                      "url": "/uploads/medium_hero_slide_3_ghi789.png",
                      "width": 750,
                      "height": 313
                    },
                    "small": {
                      "url": "/uploads/small_hero_slide_3_ghi789.png",
                      "width": 500,
                      "height": 208
                    },
                    "thumbnail": {
                      "url": "/uploads/thumbnail_hero_slide_3_ghi789.png",
                      "width": 245,
                      "height": 102
                    }
                  }
                }
              }
            }
          }
        ]
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

### Frontend Implementation

**File:** `abcd-tracks-web/src/app/[subProduct]/landing/LandingClient.tsx`

```tsx
<HeroSection
  slides={(cms.hero?.slides || [{
    id: "ct-hero-slide-1",
    title: cms.hero?.title,
    subtitle: cms.hero?.subtitle || cms.hero?.description || "",
    background: cms.hero?.image || "",
  }]) as any}
  carouselConfig={{
    autoPlay: true,
    autoPlayInterval: 5000,
    showArrows: true,
    showIndicators: true,
    indicatorStyle: "bars",
  }}
  widgetPosition={{ top: "44px", right: "40px" }}
  rightWidget={heroWidget}
  backgroundColor="#f7f7f7"
  backgroundVariant="light"
  customOverlays={mobileOverlay}
/>
```

### CMS Content Transformation

**File:** `abcd-tracks-web/src/app/[subProduct]/landing/content/index.ts`

```typescript
const heroSlidesContent = getSectionContent(
  data.heroSlides as Record<string, unknown>, 
  [], 
  "heroSlides"
);

// Transform heroSlides from CMS
type HeroSlide = { 
  id?: string; 
  title: string; 
  subtitle: string; 
  background: object; 
  order: number 
};

const heroSlides = (heroSlidesContent as HeroSlide[]).map((slide, idx) => ({
  id: `slide-${slide.id || idx}`,
  title: slide.title,
  subtitle: slide.subtitle,
  background: getCmsMediaUrl(slide.background) || 
              FALLBACK_LANDING_CONTENT.hero.slides?.[0]?.background || "",
  order: slide.order,
}));

// In result object
hero: {
  slides: heroSlides.length > 0 ? heroSlides : FALLBACK_LANDING_CONTENT.hero.slides,
  // ... other hero fields
}
```



### Carousel Settings

| Setting | Recommended | Description |
|---------|-------------|-------------|
| `carouselAutoScroll` | `true` | Enable for better engagement |
| `carouselInterval` | `5000` | 5 seconds per slide |
| `carouselPauseOnHover` | `true` | Better UX for reading |



