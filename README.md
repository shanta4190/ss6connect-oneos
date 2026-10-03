# ss6connect-oneos

## Build and deploy

The Cloudflare Pages workflow in `.github/workflows/deploy-oneos.yml` runs on
pushes to `main` and can also be started manually. It uses Node.js 20, runs
`npm ci` and `npm run build`, then publishes the `out/` directory to the
Cloudflare Pages project `ss6connect-oneos`. The workflow requires the
repository secrets `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID`.

The repository currently has no `package.json` or lockfile, so the build
workflow cannot run successfully from this checkout as-is. Before using it,
provide the root npm project and ensure its build command produces `out/`.
`wrangler.toml` also declares the Pages output directory and the production
variables `ENVIRONMENT`, `PORTAL_MODE`, and `STUDENT_RATE_USD`.

`.github/workflows/azure-webapps-node.yml` is a separate Azure deployment
workflow, not the Cloudflare Pages workflow. It also runs on pushes to `main`
or manual dispatch, and still has the placeholder app name `your-app-name`;
using it requires configuring that name and the `AZURE_WEBAPP_PUBLISH_PROFILE`
repository secret as described in the workflow.