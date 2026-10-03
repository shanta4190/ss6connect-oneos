# ss6connect-oneos

## Deployment readiness

The repository is not currently ready to build or deploy:

- Application source, `package.json`, and `package-lock.json` are missing, so the Cloudflare workflow's `npm ci` and `npm run build` steps cannot run. The build must produce the configured `out/` directory.
- The Cloudflare workflow uses `cloudflare/pages-action@v1`, an unresolved deployment blocker. Replace it with `cloudflare/wrangler-action@v3` before enabling deployment. Cloudflare deployment also requires the `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID` Actions secrets.
- The Azure workflow is unconfigured: `AZURE_WEBAPP_NAME` is still `your-app-name` and deployment requires `AZURE_WEBAPP_PUBLISH_PROFILE`. Disable or remove that workflow unless Azure is intentionally part of the deployment architecture.

The Cloudflare Pages project is `ss6connect-oneos`, with `out/` as its build output directory, as configured in `wrangler.toml`.