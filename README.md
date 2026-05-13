# Brandon Quantz Blog

Personal static blog built with plain HTML and CSS for Azure Static Web Apps.

No build step is required.

Production Azure resource:

- Static Web App: `brandon-quantz-blog`
- Resource group: `rg-brandon-blog`
- Subscription: `Merit`
- Default hostname: `https://lively-mushroom-071ad5810.7.azurestaticapps.net`

## Azure Static Web Apps

Use these build settings:

- App location: `/`
- API location: empty
- Output location: empty

The included GitHub Actions workflow expects this repository secret:

- `AZURE_STATIC_WEB_APPS_API_TOKEN`
