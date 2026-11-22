# QEXPRESS API documentation

Public documentation: https://restructure-tech-jo.github.io/qexpress-api-docs/

This standalone export uses the MIT-licensed Scalar API reference renderer (pinned to 1.82.1), with static hosting on GitHub Pages. No subscription or build step is required. The browser downloads the renderer from jsDelivr.

## Files

- `site/index.html`: branded reference page.
- `site/openapi.json`: customer API schemas, examples, and guides.
- `.github/workflows/pages.yml`: deploys only `site/` on pushes to `main`.

## Update documentation

Edit `site/openapi.json` in the dedicated `restructure-tech-jo/qexpress-api-docs` repository and push to `main`. GitHub Actions republishes automatically. Mirror approved updates to this local folder.

To refresh from the Odoo module, copy the canonical `re_logistics_equipment/docs/api/qexpress-delivery-api-1.0.2.openapi.json` into `site/openapi.json`, convert literal backslash-n sequences in description properties to actual newlines, and keep only the assigned public API server in `servers`. Review examples before publishing. The documented source version does not guarantee that every change has been deployed to production; optional website endpoints are explicitly labeled.

Publish only this folder to the dedicated public repository. The parent clients repository contains unrelated client code and must not be published as part of this site.

## Local preview

Run `python3 -m http.server 8080 --directory site` from this folder, then open http://localhost:8080. Do not open index.html directly via file:// because fetching the schema requires HTTP.

## API request testing

Readers can browse without credentials. API calls require their own raw key in the Authorization header. Credentials are not embedded in the files and authentication persistence is disabled. Requests go directly to the API; no third-party request proxy is configured. Browser testing requires the API to allow the documentation origin through CORS; otherwise use the generated curl examples or Postman. Production calls may create or change real shipments.

## Initial hosting setup

Repository Settings > Pages > Build and deployment > Source: GitHub Actions. Run the Publish API documentation workflow if needed.
