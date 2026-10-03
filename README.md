# ss6connect-oneos

## Build requirements

The Cloudflare Pages workflow (`.github/workflows/deploy-oneos.yml`) uses Node.js 20, runs `npm ci` followed by `npm run build`, and deploys the generated `out/` directory. `wrangler.toml` identifies the Pages project as `ss6connect-oneos`.

This checkout does not include a `package.json` or `package-lock.json`, so the workflow's install and build steps cannot currently run. Add the application and its npm manifests before relying on this workflow to publish a build.

## Deployment

The Cloudflare Pages workflow runs when changes are pushed to `main` or when manually dispatched. Configure the repository's `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID` GitHub Actions secrets for deployment.

There is also an Azure workflow at `.github/workflows/azure-webapps-node.yml`. It runs on pushes to `main` and manual dispatch, but its `AZURE_WEBAPP_NAME` is still the placeholder `your-app-name` and it requires an `AZURE_WEBAPP_PUBLISH_PROFILE` secret. Configure or disable that workflow if Azure deployment is not intended.
