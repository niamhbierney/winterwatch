# Winter Watch

Cloudflare Worker serving the static Winter Watch dashboard and a protected server-side AI briefing endpoint.

## Required GitHub Actions secrets

- `OPENAI_API_KEY`: OpenAI API key (uploaded to the Worker as a Cloudflare Worker secret during deployment).
- `CLOUDFLARE_API_TOKEN`: Cloudflare API token with Workers Scripts:Edit and account access for the target account.
- `CLOUDFLARE_ACCOUNT_ID`: Cloudflare account ID.

The OpenAI key is not embedded in the HTML or repository. GitHub Actions transfers it to Cloudflare as a Worker secret.

## Deploy

Push to `main` or manually run the **Deploy Winter Watch to Cloudflare** workflow.

## Mandatory access control before operational use

Configure a Cloudflare Zero Trust Access self-hosted application for the deployed Winter Watch hostname. Restrict it to authorised council staff (preferably managed identities and MFA). The Worker AI endpoint fails closed unless Cloudflare Access supplies its JWT assertion. Do not treat a public `workers.dev` URL as an internal council system.

## Limitations

The AI briefing is advisory only. It cannot approve treatment, dispatch vehicles or replace local road observations, the adopted winter service plan, or a duty engineer's judgement. The browser dashboard's decision log is session-local and is not an authoritative council audit record.
