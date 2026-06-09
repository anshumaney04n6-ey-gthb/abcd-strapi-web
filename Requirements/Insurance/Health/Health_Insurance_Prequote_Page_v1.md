# Health Insurance Prequote Page - Complete Requirement Documentation

## Content-Type: Health Journey Prequote (Apply)

**Collection Key:** `health-insurance-journey-pages`  
**Operation Key:** `apply`  
**Partner Variant:** `default`

## Scope

For health preQuote apply flow, CMS must provide only these two fields:

1. `collectMembers.whySeparatePlans`
2. `capturePincode.disclaimerContent`

---

## All CMS-Consumed Fields (Exact)

| Field Path | Type | Required | Default Source | Description |
|------------|------|----------|----------------|-------------|
| `apply.preQuote.collectMembers.whySeparatePlans` | object | No | fallback | Why separate plans modal/content block |
| `apply.preQuote.capturePincode.disclaimerContent` | string | No | fallback | Pincode disclaimer body text |

---

## API Endpoints & CMS Fetching

### Base URL

```
/api/health-insurance-journey-pages
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/health-insurance-journey-pages` | List journey entries |
| GET | `/api/health-insurance-journey-pages/:id` | Get single entry by ID |
| POST | `/api/health-insurance-journey-pages` | Create entry |
| PUT | `/api/health-insurance-journey-pages/:id` | Update entry |
| DELETE | `/api/health-insurance-journey-pages/:id` | Delete entry |

### Query Parameters

**Partner filter:**

```
?filters[partner][$eq]=default&populate=*
```

**Effective app fetch intent:**

```
GET /api/health-insurance-journey-pages?
  filters[partner][$eq]=default&
  populate=*
```

---

### Request Example

**URL:**

```
GET https://cms.abcd.io/api/health-insurance-journey-pages?
  filters[partner][$eq]=default&
  populate=*
```

---

### Response Payload Structure

**Success Response (200 OK):**

```json
{
  "data": [
    {
      "id": 1,
      "attributes": {
        "partner": "default",
        "apply": {
            "preQuote": {
                "collectMembers": {
                    "whySeparatePlans": {
                        "title": "Why separate plans",
                        "highlightText": "This way, your parents and family get the coverage that suits their needs best."
                    }
                },
                "capturePincode": {
                    "disclaimerContent": "Aditya Birla Capital Digital Ltd (ABCDL) ..."
                }
            }
        }
      }
    }
  ]
}
```

**Empty Response (No Match):**

```json
{
  "data": []
}
```

---

## Complete JSON Structure (CMS Requirement Only)

```json
{
  "data": {
    "partner": "default",
    "apply": {
        "preQuote": {
            "collectMembers": {
                "whySeparatePlans": {
                    "title": "Why separate plans",
                    "highlightText": "This way, your parents and family get the coverage that suits their needs best.",
                    "switchContext": {
                    "titleForParents": "Why parents are better covered separately",
                    "titleForFamily": "Why family is better covered separately",
                    "primaryCtaForParents": "Get a parents plan",
                    "primaryCtaForFamily": "Get a family plan",
                    "secondaryCtaForParents": "Continue with family plan",
                    "secondaryCtaForFamily": "Continue with parents plan"
                    },
                    "items": [
                    {
                        "itemId": "premium-depends-on-eldest-member",
                        "title": "Premium depends on eldest member",
                        "description": "When parents are included, the overall premium may increase for the family.",
                        "icon": "media" //media
                    }
                    ]
                }
            },
            "capturePincode": {
                "disclaimerContent": "Aditya Birla Capital Digital Ltd (ABCDL) ..."
            }
        }
    }
  }
}
```

---

## Components Detail

### 1) collectMembers.whySeparatePlans

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `title` | string | No | fallback |
| `highlightText` | string | No | fallback |
| `switchContext` | object | No | fallback |
| `items` | array | No | fallback |

**switchContext fields:**

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `titleForParents` | string | No | fallback |
| `titleForFamily` | string | No | fallback |
| `primaryCtaForParents` | string | No | fallback |
| `primaryCtaForFamily` | string | No | fallback |
| `secondaryCtaForParents` | string | No | fallback |
| `secondaryCtaForFamily` | string | No | fallback |

**items[] fields:**

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `id` | string | No | fallback |
| `title` | string | No | fallback |
| `description` | string | No | fallback |
| `icon` | string | No | fallback |

---

### 2) capturePincode.disclaimerContent

| Field | Type | Required | Default |
|-------|------|----------|---------|
| `disclaimerContent` | text/string | No | fallback |

---

## Restrictions Summary

| Area | CMS Accepted | Notes |
|------|--------------|------|
| collectMembers | `whySeparatePlans` only | All other collectMembers keys are fallback-only |
| capturePincode | `disclaimerContent` only | All other capturePincode keys are fallback-only |
| other preQuote pages | none | Fully fallback-driven |

---

## Populate Query

```
GET /api/health-insurance-journey-pages?
filters[partner][$eq]=default&
populate=*
```

---

## Field Usage Examples

### Example A: Only whySeparatePlans from CMS

```json
{
  "apply": {
    "preQuote": {
        "collectMembers": {
            "whySeparatePlans": {
                "title": "Why separate plans",
                "items": []
            }
        }
    }
  }
}
```

### Example B: Only disclaimerContent from CMS

```json
{
  "apply": {
    "preQuote": {
        "capturePincode": {
            "disclaimerContent": "Custom legal disclaimer from CMS"
        }
      }
    }
}
```
