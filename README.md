# Winter Watch

Cloudflare Worker serving the static Winter Watch dashboard and a protected server-side AI briefing endpoint.

## GitHub Actions secrets

- `OPENAI_API_KEY`: a newly generated OpenAI API key. The workflow uploads it to Cloudflare as a Worker secret; it is not bundled into the site.
- `CLOUDFLARE_API_TOKEN`: Cloudflare API token with permission to edit Workers Scripts for the target account.
- `CLOUDFLARE_ACCOUNT_ID`: Cloudflare account ID.

## Configure Cloudflare Access before use

1. In Cloudflare Zero Trust, create a self-hosted Access application for the custom hostname you will use for Winter Watch.
2. Add an allow policy for authorised council staff only, preferably using managed identities and MFA.
3. Copy the Access team domain (for example, `team-name.cloudflareaccess.com`) and the application's AUD tag.
4. Replace the two placeholder values `ACCESS_TEAM_DOMAIN` and `ACCESS_AUD` in `wrangler.toml` with those exact values, then commit.
5. Attach a custom domain to this Worker in Cloudflare and ensure the Access application covers that hostname.

The Worker validates the Cloudflare Access JWT signature, issuer, audience and expiry on every request. The `workers.dev` address is also denied unless a valid token for this Access application is supplied.

## AI behaviour and limitations

The AI briefing is advisory only. It cannot approve treatment, dispatch vehicles or replace local road observations, the adopted winter service plan, or a duty engineer's judgement. The browser dashboard's decision log is session-local and is not an authoritative council audit record.
