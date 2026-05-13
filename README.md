# Brandon Quantz Blog

Personal static blog built with plain HTML and CSS for Azure Static Web Apps.

No build step is required.

Production Azure resource:

- Static Web App: `brandon-quantz-blog`
- Resource group: `rg-brandon-blog`
- Subscription: `Merit`
- Default hostname: `https://lively-mushroom-071ad5810.7.azurestaticapps.net`
- Target custom domain: `https://theinfrastructureshift.com`

## DNS setup

Current DNS for `theinfrastructureshift.com` points at Squarespace. To move the
site to Azure Static Web Apps, update DNS at the domain's DNS provider.

Azure Static Web Apps default hostname:

```text
lively-mushroom-071ad5810.7.azurestaticapps.net
```

Required records for the same A-record pattern used by the other Static Web App:

```text
Type: TXT
Host/Name: _dnsauth
Value: _iirzp2661edr5r0q8tinfvqjs0m5n3v
```

```text
Type: TXT
Host/Name: _dnsauth.www
Value: _1jej2e6eyjt1ypmbxl48v6j8855cas0
```

```text
Type: A
Host/Name: @
Value/Target: 64.236.125.137
```

```text
Type: CNAME
Host/Name: www
Value/Target: lively-mushroom-071ad5810.7.azurestaticapps.net
```

After the records propagate, run:

```powershell
az staticwebapp hostname set --name brandon-quantz-blog --resource-group rg-brandon-blog --hostname www.theinfrastructureshift.com --validation-method cname-delegation
```

After the apex records propagate, check status with:

```powershell
az staticwebapp hostname list --name brandon-quantz-blog --resource-group rg-brandon-blog -o table
```

## Azure Static Web Apps

Use these build settings:

- App location: `/`
- API location: empty
- Output location: empty

The included GitHub Actions workflow expects this repository secret:

- `AZURE_STATIC_WEB_APPS_API_TOKEN`
