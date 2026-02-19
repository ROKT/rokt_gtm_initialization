# rokt_gtm_initialization

## Project Overview

This is a **public** repository containing a Google Tag Manager (GTM) Community Template for initializing the mParticle by Rokt SDK and optionally logging page views. The template is published to Google's [Community Template Gallery](https://tagmanager.google.com/gallery/#/?page=1), allowing partners to configure Rokt SDK loading through Google Tag Manager instead of managing the Rokt script directly.

**Resident Expert:** Alex Sapountzis (alex.sapountzis@rokt.com)

## Architecture

The repo contains a single GTM tag template (`.tpl` file) that:

1. Configures an `mParticleConfig` object with user-provided settings (API key, log level, cookie preferences, development mode).
2. Sets global window variables (`mParticleConfig`, `apiKey`, `isLogPageView`).
3. Injects the Rokt wrapper script from `https://apps.rokt.com/store/js/gtm_wrapper_init.min.js`.
4. Pushes `mparticle_wrapper_loaded` or `mparticle_wrapper_failed` events to the `dataLayer`.

### Template Parameters

| Parameter | Type | Description |
|---|---|---|
| `apiKey` | Text | Rokt API Key |
| `isDevelopmentMode` | Checkbox | Enables development/sandbox mode |
| `isLogPageView` | Checkbox | Enables page view logging |
| `logLevel` | Select | `verbose`, `warning`, or `none` |
| `noFunctional` | Checkbox | Disallow functional cookies |
| `noTargeting` | Checkbox | Disallow targeting cookies |
| `useCookieStorage` | Checkbox | Use cookie storage |

### Web Permissions

The template requests the following GTM sandbox permissions:

- **Logging** — debug console logging
- **Access Globals** — read/write `dataLayer`, `mParticleConfig`, `apiKey`, `isLogPageView`; read `_roktStubInitialized`; execute `roktHandlePageView`
- **Inject Script** — load scripts from `https://*.rokt.com/*`

## Tech Stack

- **Google Tag Manager Sandboxed JavaScript** — the template uses GTM's sandboxed JS APIs (`logToConsole`, `injectScript`, `setInWindow`, `copyFromWindow`, `callInWindow`, `queryPermission`, `makeNumber`, `createQueue`)
- **License:** Apache 2.0

## Project Structure

```text
rokt_gtm_initialization/
├── template.tpl       # GTM tag template (template params, sandboxed JS, permissions, tests)
├── metadata.yaml      # Google template gallery metadata (homepage, docs link, version history)
├── LICENSE            # Apache 2.0 license
├── README.md          # Usage instructions and deployment process
└── .gitignore         # Ignores .DS_Store
```

## Development Guide

### Prerequisites

- Access to a [Google Tag Manager](https://tagmanager.google.com/) workspace
- A Rokt API key

### Making Changes

1. Edit `template.tpl` — this is the single source file containing the tag definition, template parameters, sandboxed JavaScript logic, web permissions, and test scenarios.
2. Update `metadata.yaml` with a new version entry (SHA + change notes) when publishing a new version to the gallery.

### Testing

Follow the [testing instructions](https://github.com/ROKT/gtm_wrapper/tree/master/docs/guides/how-to-test.md) in the `gtm_wrapper` repo to set up the Testing Playground and test template changes.

### Deployment

Follow [Google's guide for updating a Community Template Gallery template](https://developers.google.com/tag-platform/tag-manager/templates/gallery#update_your_template).

## Related Repositories

- [ROKT/gtm_wrapper](https://github.com/ROKT/gtm_wrapper) — contains the wrapper script loaded by this template and testing documentation

## Maintaining This Document

When making changes to this repository that affect the information documented here
(template parameters, permissions, deployment configuration, etc.),
please update this document to keep it accurate. This file is the primary reference
for AI coding assistants working in this codebase.
