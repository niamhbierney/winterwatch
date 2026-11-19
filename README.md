# Winter Watch

A single-file GitHub Pages teaching demonstration for the Week 10 Mock CA2 assignment.

## Publish with GitHub Pages

1. Open the repository **Settings → Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select branch **main** and folder **/(root)**, then Save.
4. Wait for GitHub Pages to publish. The coursework link is the website, not this repository:
   https://niamhbierney.github.io/winterwatch/

The page is the root `index.html`. No Worker, Cloudflare account, backend, build step or GitHub Actions secret is required.

## AI provider key

Open the Settings panel on the website, select a provider and model, paste your own API key, and press **Save settings**. The key is stored in that browser's `localStorage` and sent directly from the browser to the selected provider. It is not included in this repository. Use **Forget key** on shared computers. Whoever enters a key pays for the provider usage; set a low spending limit in the provider dashboard.

Supported providers: OpenAI, Anthropic, Google Gemini and Groq. The default is OpenAI with `gpt-4.1-mini`. Check the provider's current model name and token prices before use.

## Data and decision logic

For every question the page fetches the depot CSV, route CSV, Open-Meteo forecast, winter service plan and history CSV. It computes route decisions and a compact ten-route historical summary in the browser. The raw history file is not sent to the AI.

The tool is advisory only. A qualified Duty Engineer must review local conditions and approve or reject any treatment. The roads team, service plan and records are fictional teaching data; this public demo is not a secure or production council system. Do not enter confidential or operationally sensitive information.

Weather data: Open-Meteo, CC BY 4.0.
