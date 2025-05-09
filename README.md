# Google Tag Template - Initialization

## Resident Experts

- Alex Sapountzis - alex.sapountzis@rokt.com

## Overview

Rokt integrates with Google Tag Manager, enabling partners to set attributes and launch placements through Google's tag management system. This template allows for the configuration and loading of the mParticle by Rokt SDK on your site, helping to pre-load and improve the performance of the SDK integration.

Partners can configure their tags on [Google's Console](https://tagmanager.google.com/gallery/#/?page=1) instead of managing the Rokt script directly.

### Steps to enable:
1. Select the Initialization Tag Template from the [Google Community Template Gallery](https://tagmanager.google.com/gallery/#/?page=1) or import this .tpl file into your GTM workspace.
2. Configure your tag with the proper API Key and desired settings. 
3. Configure the trigger to load the SDK as the page is loaded. 
4. Deploy the tag. 
5. Verify and QA, you should see window.mParticle loaded on your webpage.

This is a public repository containing the TPL file necessary for Google to support Rokt's application onto the Tag Manager Marketplace.

To use on an adhoc basis -- please download the .tpl file and upload this in your Google Tag Manager Template interface. You can read more about how to do that [here](https://developers.google.com/tag-platform/tag-manager/templates).

[For more info on developing a Google Tag](https://developers.google.com/tag-platform/tag-manager)

## Testing

[Follow these instructions](https://github.com/ROKT/gtm_wrapper/tree/master/docs/guides/how-to-test.md) to set up the Testing Playground and test your template changes.

## Deployment Process

[Follow these steps](https://developers.google.com/tag-platform/tag-manager/templates/gallery#update_your_template) to deploy the template.
