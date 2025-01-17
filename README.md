# Exchain Analytics Adapter (Exchain IOID Module)

Welcome to the **Exchain Analytics Adapter** repository! This custom Prebid.js module provides a unique solution for enhancing tracking and analytics in programmatic advertising by appending a tamper-proof identifier to bid requests. It serves as both the **Exchain Impression Opportunity Identifier (IOID) Module** and the **Exchain Analytics Adapter**, offering a streamlined integration for publishers.

## Overview

- **Module Name:** Exchain Impression Opportunity Identifier Module (Exchain IOID Module) / Exchain Analytics Adapter
- **Module Type:** Analytics Adapter
- **Maintainer:** [admin@exchain.co ](mailto:admin@exchain.co )
- **Purpose:** To generate an anonymous, unique, and tamper-proof identifier (UUID) appended to RTB ad requests, addressing challenges in bidstream bloat, sustainability, and wasted ad spend while enabling enhanced tracking and analytics.

## Description

The Exchain IOID is an anonymous, unique, and tamper-proof identifier that is appended to RTB ad requests by publishers. This solution tackles programmatic ecosystem challenges by reducing bidstream bloat, improving sustainability, and minimizing wasted ad spend. The Exchain Analytics Adapter builds on this by automatically generating and appending a UUID to bid requests, leveraging secure cryptographic APIs for UUID generation, and integrating seamlessly with Prebid.js.

## Features

- Automatically generates and appends a UUID to bids before requests are sent.
- Seamlessly integrates with Prebid.js as part of the Real Time Data (RTD) and Analytics modules.
- Addresses programmatic advertising challenges like bidstream bloat and wasted ad spend.
- Utilizes secure crypto APIs for reliable UUID generation.
- Configurable via Prebid.js setConfig and enableAnalytics functions.

## Integration

### 1. Compile the Module

Compile the Exchain Prebid Module along with your bid adapter and other modules into your Prebid build. For example:

```bash
gulp build --modules="rtdModule,exchainPrebidAdapter,appnexusBidAdapter,..."  
```

Refer to [Prebid.js Getting Started Documentation](https://docs.prebid.org/dev-docs/getting-started.html) for more details on the build process.

### 2. Add Compiled Files

Add the compiled `prebid.js` and the `exchainAnalyticsAdapter.js` file (from `path/to/exchainAnalyticsAdapter.js`) to your website.

### 3. Configure Prebid.js

#### For Real Time Data Configuration:

Use `setConfig` to instruct Prebid.js to initialize the Exchain IOID module as part of the Real Time Data providers:

```javascript
pbjs.setConfig({
  realTimeData: {
    dataProviders: [
      {
        name: "exchainPrebidAdapter",
        // Additional provider-specific configuration can go here
      }
    ]
  }
});
```

#### For Analytics Integration:

Initialize the analytics adapter using `enableAnalytics`:

```html
<script>
  pbjs.que.push(function() {
    pbjs.enableAnalytics([{
      provider: 'ExchainAnalyticsAdapter',
      options: {
        // Additional options (if any) can be configured here.
      }
    }]);
  });
</script>
```

## Contact

For more information or support, please contact the maintainer at [admin@exchain.co](mailto:admin@exchain.co).
