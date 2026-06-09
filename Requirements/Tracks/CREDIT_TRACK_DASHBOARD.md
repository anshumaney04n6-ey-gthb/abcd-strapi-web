# Tracks Dashboard CMS Content Documentation

This document is intended for the Strapi team as a reference for the Tracks dashboard CMS payload used by the web app.

It follows the same documentation approach as the DigiMetal landing page API doc, but it is based on the dashboard fallback content and the current transformation logic in the application.

---

## Table of Contents

1. [Overview](#overview)
2. [Content Type Reference](#content-type-reference)
3. [Payload Structure](#payload-structure)
4. [Components](#components)
5. [API Endpoint](#api-endpoint)
6. [Sample API Request](#sample-api-request)
7. [Sample API Response](#sample-api-response)
8. [Fallback Reference Content](#fallback-reference-content)
9. [Implementation Notes](#implementation-notes)

---

## Overview

The Tracks dashboard content is fetched from the Strapi collection used by the credit dashboard page in `abcd-tracks-web`.

The UI reads the CMS response, transforms it into `DashboardCMSContent`, and falls back to static content when fields are missing or when the API is unavailable.

**Strapi Collection:** `tracks-dashboard-pages`

**Consumer Files:**

- `src/app/[subProduct]/customer/@dashboard/content/index.ts`
- `src/app/[subProduct]/customer/@dashboard/content/fallback.ts`

**Current fetch behavior:**

- Filters by `subProduct`
- Optionally filters by `partner`
- Uses `populate=*`
- Falls back field-by-field when values are missing

---

## Content Type Reference

This section documents the fields currently consumed by the frontend from Strapi.

### Component Collections

| Attribute | Component | Max Items | Description |
|-----------|-----------|-----------|-------------|
| `latestArticles.articles` | `tracks-dashboard.article-item` | 4 | Latest article cards shown on the dashboard |
| `sidebarFAQs` | `tracks-dashboard.sidebar-faq-item` | 3 | Sidebar FAQ/help cards |

### Single Components

| Attribute | Component | Description |
|-----------|-----------|-------------|
| `header` | `tracks-dashboard.header` | Header logo and branding assets |
| `predictCreditScore` | `tracks-dashboard.predict-credit-score` | Predict credit score CTA card |
| `referralCard` | `tracks-dashboard.referral-card` | Referral promotion card |
| `latestArticles` | `tracks-dashboard.latest-articles` | Latest articles section wrapper |
| `raiseDispute` | `tracks-dashboard.raise-dispute` | Raise dispute CTA configuration |
| `footerDisclaimer` | `tracks-dashboard.footer-disclaimer` | Footer disclaimer content |

### Root Fields

| Field | Type | Required by UI | Description |
|-------|------|----------------|-------------|
| `predictCreditScoreTitle` | string | No | Predict credit score card title |
| `simulatorLink` | string | No | Predict credit score action link |
| `referralCardSubtitle` | string | No | Referral card subtitle |
| `referralCardHeading` | string | No | Referral card heading |
| `referralCardRewardAmount` | string | No | Referral reward amount |
| `referralCardLink` | string | No | Referral card action link |
| `heroTitle` | string | No | Hero section main title |
| `heroDescription` | string | No | Hero section supporting description |
| `heroCtaText` | string | No | Hero CTA button label |
| `footerHeading` | string | No | Footer reference heading label |
| `footerName` | string | No | Footer partner or brand name |
| `footerCertification` | string | No | Footer certification or regulatory label |
| `raiseDisputeText` | string | No | Raise dispute CTA text |
| `raiseDisputeLink` | string | No | Raise dispute CTA link |
| `footerDisclaimerText` | string | No | Footer disclaimer text |
| `header` | component/object | No | Header logo and branding assets |
| `latestArticles` | component/object | No | Latest articles section |
| `sidebarFAQs` | component[] | No | Sidebar FAQ cards |

### Latest Articles Object

| Field | Type | Required by UI | Description |
|-------|------|----------------|-------------|
| `title` | string | No | Latest articles section title |
| `articles` | component[] | No | Article items |

### Article Item

| Field | Type | Required by UI | Description |
|-------|------|----------------|-------------|
| `id` | string/number | No | Fallback identifier |
| `text` | string | No | Article label/title |
| `image` | media | No | Article image |

### Sidebar FAQ Item

| Field | Type | Required by UI | Description |
|-------|------|----------------|-------------|
| `id` | string/number | No | Fallback identifier |
| `title` | string | No | FAQ card title |
| `icon` | media | No | FAQ icon media object |
| `content` | string | No | FAQ body content |

---

## Payload Structure

The frontend transforms the Strapi response into this structure:

```ts
interface DashboardCMSContent {
  header: {
    logo: { src: string; alt: string; size: number };
    mobileHeaderLogo: string;
  };
  hero: {
    title: string;
    description: string;
    ctaText: string;
  };
  footer: {
    referenceDetails: {
      heading: string;
      name: string;
      certification: string;
    };
  };
  predictCreditScore: {
    title: string;
    simulatorLink: string;
  };
  referralCard: {
    subtitle: string;
    heading: string;
    rewardAmount: string;
    referalLink: string;
  };
  latestArticles?: {
    title: string;
    articles: {
      id: string;
      text: string;
      image: string;
    }[];
  };
  sidebarFAQs: {
    id: string;
    title: string;
    icon: string;
    content: string;
    isExternal?: boolean;
    externalUrl?: string;
  }[];
  raiseDispute: {
    raiseDisputeText: string;
    raiseDisputeLink: string;
  };
  footerDisclaimer: {
    footerDisclaimerText: string;
  };
}
```

---

## Components

All components below are proposed using the same style as the Credit Tack documentation, based on the structure currently consumed by the frontend.

### Header

Header logo and branding assets.

**Proposed Component:** `tracks-dashboard.header`

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| `logo` | media | No | Logo image media object |
| `logoAlt` | string | No | Logo alt text |
| `logoSize` | number | No | Logo display size in px |
| `mobileHeaderLogo` | media | No | Mobile header logo media object |

```json
{
  "logoAlt": "ABCD Logo",
  "logoSize": 40,
  "logo": "/logos/lob/abcd.svg",
}
```

### Hero

Hero section content. These are stored as root-level fields (not a nested component) in the Strapi collection.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| `heroTitle` | string | No | Hero section main title |
| `heroDescription` | string | No | Hero section supporting description |
| `heroCtaText` | string | No | CTA button label |

```json
{
  "heroTitle": "Track Your Credit Score for Free",
  "heroDescription": "Multiple Trusted Lenders, 24 hours* Disbursal",
  "heroCtaText": "Apply Now"
}
```

### Footer

Footer reference and certification details. These are stored as root-level fields (not a nested component) in the Strapi collection.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| `footerHeading` | string | No | Label preceding the partner/brand name |
| `footerName` | string | No | Partner or brand name |
| `footerCertification` | string | No | Certification or regulatory label |

```json
{
  "footerHeading": "Powered by",
  "footerName": "ABCD",
  "footerCertification": "RBI Regulated Lenders"
}
```

### Predict Credit Score

Card content for the simulator CTA.

**Proposed Component:** `tracks-dashboard.predict-credit-score`

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| `title` | string | Yes | Card title |
| `simulatorLink` | string | No | CTA destination for the simulator flow |

```json
{
  "title": "Predict your credit score",
  "simulatorLink": "#"
}
```

### Referral Card

Referral module content.

**Proposed Component:** `tracks-dashboard.referral-card`

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| `subtitle` | string | Yes | Referral card subtitle |
| `heading` | string | Yes | Referral card heading |
| `rewardAmount` | string | Yes | Reward amount label |
| `referalLink` | string | No | Referral CTA link used by the frontend model |

```json
{
  "subtitle": "Refer & Earn",
  "heading": "Invite friends and earn",
  "rewardAmount": "₹500",
  "referalLink": "#"
}
```

### Latest Articles

List of quick article cards.

**Proposed Component:** `tracks-dashboard.latest-articles`

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| `title` | string | Yes | Section title |
| `articles` | component[] | No | List of latest article items |

**Nested Component:** `tracks-dashboard.article-item`

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| `articleId` | string | No | Preferred article identifier |
| `text` | string | Yes | Article title/label |
| `image` | media | No | Article image asset |
| `imagePath` | string | No | Asset path fallback for image |

```json
{
  "title": "Latest articles",
  "articles": [
    {
      "articleId": "article-1",
      "text": "Understanding Basics: Credit Score 101",
      "imagePath": "/icons/tick.png"
    }
  ]
}
```

### Sidebar FAQ Item

Sidebar FAQ/help card.

**Proposed Component:** `tracks-dashboard.sidebar-faq-item`

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | string | No | Preferred FAQ identifier |
| `title` | string | Yes | FAQ title |
| `icon` | media | No | FAQ icon media asset |
| `content` | text | No | FAQ content text |

```json
{
  "title": "What is a credit score?",
  "iconPath": "/assets/sidebar-faq/meter1.png",
  "content": "A credit score is a 3-digit number ranging from 300 to 900 that represents your creditworthiness."
}
```

### Raise Dispute

Raise dispute CTA content.

**Proposed Component:** `tracks-dashboard.raise-dispute`

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| `raiseDisputeText` | string | Yes | CTA label |
| `raiseDisputeLink` | string | No | CTA destination |

```json
{
  "raiseDisputeText": "Raise dispute",
  "raiseDisputeLink": "#"
}
```

### Footer Disclaimer

Disclaimer displayed in the dashboard footer.

**Proposed Component:** `tracks-dashboard.footer-disclaimer`

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| `footerDisclaimerText` | text | Yes | Footer disclaimer text |

```json
{
  "footerDisclaimerText": "ABCD is partnered with Equifax(bureau) to fetch your credit report. ABCD itself doesn't evaluate your credit score"
}
```

---

## API Endpoint

The dashboard content is fetched from Strapi using the existing collection endpoint.

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tracks-dashboard-pages` | Get dashboard CMS entries |
| GET | `/api/tracks-dashboard-pages?filters[subProduct][$eq]=credit` | Get dashboard entry for a sub-product |
| GET | `/api/tracks-dashboard-pages?filters[subProduct][$eq]=credit&filters[partner][$eq]=Vodafone` | Get partner-specific dashboard entry |

---

## Sample API Request

### Default dashboard

```http
GET /api/tracks-dashboard-pages?filters[subProduct][$eq]=credit&populate=*
```

### Partner-specific dashboard

```http
GET /api/tracks-dashboard-pages?filters[subProduct][$eq]=credit&filters[partner][$eq]=Vodafone&populate=*
```

---

## Sample API Response

This sample shows the shape expected by the frontend before transformation.

```json
{
  "data": [
    {
      "id": 1,
      "attributes": {
        "header": {
          "logoAlt": "ABCD Logo",
          "logoSize": 40,
          "logoPath": "/logos/lob/abcd.svg",
          "mobileHeaderLogo": "/logos/lob/abcd.svg"
        },
        "hero": {
          "heroTitle": "Track Your Credit Score for Free",
          "heroDescription": "Multiple Trusted Lenders, 24 hours* Disbursal",
          "heroCtaText": "Apply Now",
        },
        "footer":{
          "referenceDetails":{
            "footerHeading": "Powered by",
            "footerName": "ABCD",
            "footerCertification": "RBI Regulated Lenders",
          }
        },
        "predictCreditScore": {
          "title": "Predict your credit score",
          "simulatorLink": "#"
        },
        "referralCard": {
          "subtitle": "Refer & Earn",
          "heading": "Invite friends and earn",
          "rewardAmount": "₹500",
          "referalLink": "#"
        },
        "latestArticles": {
            "title": "Latest articles",
            "articles": [
            {
              "id": "article-1",
            "text": "Understanding Basics: Credit Score 101",
            "image": "/tracks/icons/tick.png"
          },
          {
            "id": "article-2",
            "text": "How to Improve Your Credit Score",
            "image": "/tracks/icons/tick.png"
          },
          {
            "id": "article-3",
            "text": "Credit Cards: Best Practices",
            "image": "/tracks/icons/tick.png"
          },
          {
            "id": "article-4",
            "text": "Managing Your Credit Utilization",
            "image": "/tracks/icons/tick.png"
          }
        ]
  },
  "sidebarFAQs": [
    {
      "id": "faq-what-is-credit-score",
      "title": "What is a credit score?",
      "icon": "/tracks/assets/sidebar-faq/meter1.png",
      "content": "A credit score is a 3-digit number ranging from 300 to 900 that represents your creditworthiness. Higher scores indicate better credit behavior and make it easier to get loans approved at better interest rates."
    },
    {
      "id": "faq-how-to-improve",
      "title": "How to improve credit score?",
      "icon": "/tracks/assets/sidebar-faq/search.png",
      "content": "Pay all bills on time, keep credit utilization below 30%, maintain old credit accounts, avoid too many credit inquiries, and maintain a healthy mix of credit types."
    },
    {
      "id": "faq-other-questions",
      "title": "Other questions?",
      "icon": "/tracks/assets/sidebar-faq/other-questions.png",
      "content": "If you have more questions about credit scores, feel free to reach out to our support team or check out our comprehensive FAQ section on our website."
    }
  ],
  "raiseDispute": {
    "raiseDisputeText": "Raise dispute",
    "raiseDisputeLink": "#"
  },
  "footerDisclaimer": {
    "footerDisclaimerText": "ABCD is partnered with Equifax(bureau) to fetch your credit report. ABCD itself doesn't evaluate your credit score"
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

## Fallback Reference Content

This is the current fallback content used by the frontend when CMS data is missing.

```json
{
  "header": {
    "logo": {
      "src": "/logos/lob/abcd.svg",
      "alt": "ABCD Logo",
      "size": 40
    },
    "mobileHeaderLogo": "/logos/lob/abcd.svg"
  },
  "hero": {
    "title": "Track Your Credit Score for Free",
    "description": "Multiple Trusted Lenders, 24 hours* Disbursal",
    "ctaText": "Apply Now"
  },
  "footer": {
    "referenceDetails": {
      "heading": "Powered by",
      "name": "ABCD",
      "certification": "RBI Regulated Lenders"
    }
  },
  "predictCreditScore": {
    "title": "Predict your credit score",
    "simulatorLink": "#"
  },
  "referralCard": {
    "subtitle": "Refer & Earn",
    "heading": "Invite friends and earn",
    "rewardAmount": "₹500",
    "referalLink": "#"
  },
  "latestArticles": {
    "title": "Latest articles",
    "articles": [
      {
        "id": "article-1",
        "text": "Understanding Basics: Credit Score 101",
        "image": "/tracks/icons/tick.png"
      },
      {
        "id": "article-2",
        "text": "How to Improve Your Credit Score",
        "image": "/tracks/icons/tick.png"
      },
      {
        "id": "article-3",
        "text": "Credit Cards: Best Practices",
        "image": "/tracks/icons/tick.png"
      },
      {
        "id": "article-4",
        "text": "Managing Your Credit Utilization",
        "image": "/tracks/icons/tick.png"
      }
    ]
  },
  "sidebarFAQs": [
    {
      "id": "faq-what-is-credit-score",
      "title": "What is a credit score?",
      "icon": "/tracks/assets/sidebar-faq/meter1.png",
      "content": "A credit score is a 3-digit number ranging from 300 to 900 that represents your creditworthiness. Higher scores indicate better credit behavior and make it easier to get loans approved at better interest rates."
    },
    {
      "id": "faq-how-to-improve",
      "title": "How to improve credit score?",
      "icon": "/tracks/assets/sidebar-faq/search.png",
      "content": "Pay all bills on time, keep credit utilization below 30%, maintain old credit accounts, avoid too many credit inquiries, and maintain a healthy mix of credit types."
    },
    {
      "id": "faq-other-questions",
      "title": "Other questions?",
      "icon": "/tracks/assets/sidebar-faq/other-questions.png",
      "content": "If you have more questions about credit scores, feel free to reach out to our support team or check out our comprehensive FAQ section on our website."
    }
  ],
  "raiseDispute": {
    "raiseDisputeText": "Raise dispute",
    "raiseDisputeLink": "#"
  },
  "footerDisclaimer": {
    "footerDisclaimerText": "ABCD is partnered with Equifax(bureau) to fetch your credit report. ABCD itself doesn't evaluate your credit score"
  }
}
```