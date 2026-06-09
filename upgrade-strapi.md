Upgrade the strapi instance.
Make note of current version and etc.
Be very aware we can rollback to current state if things don't work out.
Check my plugins and see if they also need to be upgraded for compatibility.
Create a proper plan to execute this.


Root Cause Analysis
1. Save taking 25+ seconds
Known Issues:
- Input lag on edit view (#24462) - partially fixed in 5.33.1
- Excessive re-renders when editing content
- Your content type has 44 components in digimetal-journey - very complex
2. Publish taking 25+ seconds
This is a CONFIRMED BUG in Strapi 5 - Issue #25568:
> "Publishing takes 4-6 seconds regardless of how many components the specific entry actually uses. The slowness scales with the number of component types declared in the dynamic zone, not with the actual content."
- Your digimetal-journey-page uses 44 components (I counted them)
- This explains the 25+ second publish time
- A content type with 2 components publishes in 100-200ms
3. Publish button doesn't enable on second change
This is a CONFIRMED BUG - Issue #25634:
> "When content includes a relational list of items, the number and order of the items returned is not the same in draft/publish version."
---
## Proposed Fix Plan
### Option 1: Wait for Strapi Fix (No Action Now)
- Issues #25568 and #25634 are open and being worked on

Links :

https://github.com/strapi/strapi/issues/24462
https://github.com/strapi/strapi/issues/25568



I have tried below solutions to fix this bug.

After upgrading Strapi from v5.1.0 to v5.42.0, the performance issues with Save (25+ seconds) and Publish (25+ seconds) buttons persist. This has been identified as known bugs within Strapi 5's core platform, not something we can resolve through code changes.

**Root Cause Analysis(RCA)**:

1. Publish Button (25+ sec): [Confirmed Strapi bug (#25568)](https://github.com/strapi/strapi/issues/25568) - Publishing time scales with total component types declared, not actual content used. For eg. Our digimetal-journey-page content type uses 44 components, causing 25+ second publish times.
2. Save Button (25+ sec): Known [issue (#24462)](https://github.com/strapi/strapi/issues/24462) - Input lag on edit view with excessive re-renders. Partially fixed in v5.33.1 but still problematic for complex content types.
3. Publish button not enabling: Confirmed [bug (#25634)](https://github.com/strapi/strapi/issues/25634) - Draft/Publish versions get out of sync, especially with relational data.

Strapi Version After Upgrade on my local testing: 5.42.0 (latest as of today)

**Why We Cannot Fix This**:
- These are core platform bugs in Strapi 5's Document Service and Content Manager
- Performance degradation is architectural in Strapi v5, not code-related
- The issues require fixes from Strapi's core team
- No workaround or configuration can resolve this

**Blocked Until**: 
Strapi releases fix for these performance issues OR we decide to restructure content types / downgrade to v4, which will again display API vulnerabilities.