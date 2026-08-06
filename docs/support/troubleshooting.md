# Troubleshooting & FAQ

Common issues, grouped by area. For deployment-specific issues (stack creation, DNS, SSL), see the [Deployment Guide's troubleshooting section](../deployment/deployment-guide.md#81-troubleshooting-quick-reference) — this page focuses on day-to-day agent and admin issues.

## Extension & connection issues

| Symptom | Likely cause / next step |
|---|---|
| Extension icon does nothing, or connector window never opens | Confirm the connector URL is set correctly in the extension options and ends in `/connector.html` (see [Agent Setup Guide](../deployment/agent-setup.md#step-2-configure-your-connector-url)) |
| Calling window doesn't open at all | Pop-ups are likely still blocked for the connector URL — see [Agent Setup Guide, Step 3](../deployment/agent-setup.md#step-3-allow-pop-ups) |
| Dial/message buttons don't appear on HubSpot phone fields | Reload the HubSpot tab; confirm the extension is enabled in `chrome://extensions`; confirm you're on a `*.hubspot.com` page |
| Extension seems to load, but nothing syncs with HubSpot | Confirm you're logged into HubSpot in the same browser profile as the extension |

## Login & licensing

| Symptom | Likely cause / next step |
|---|---|
| Can't log in to the softphone | Confirm your AWS Connect agent credentials are correct and your account is active in Connect |
| "Seat limit reached" or similar login error | Your license has a fixed number of concurrent agent seats — ask your admin to check **Logged-in Agents** in the admin portal and remove any stale sessions, or request a seat increase |
| "License expired" or similar login error | Your admin needs to update the license key under **License Details** in the admin portal |
| Login works but agent status/queues look wrong | Confirm your AWS Connect user profile has the expected routing profile and permissions assigned in Connect |

## Screenpop & contact matching

| Symptom | Likely cause / next step |
|---|---|
| Screenpop doesn't happen at all | Check your admin's **Screen Pop Configuration** — confirm Contact or Deal is selected as expected; confirm the call actually connected (screenpop fires on `onConnecting`) |
| A known contact isn't matched — a new contact is created instead | Confirm the phone number in HubSpot matches the caller's number format (country code, formatting); the connector normalizes numbers but mismatched country codes can still cause a miss |
| Screenpop lands on the wrong object type | Your admin controls whether screenpop opens a Contact or a Deal — see [Admin Configuration Guide](../admin/configuration-guide.md#screenpop-configuration) |
| Multi-match picker shows contacts that don't seem related | The picker shows every HubSpot contact matching the caller's phone number — this usually means duplicate contacts exist in HubSpot for that number |

## WhatsApp

| Symptom | Likely cause / next step |
|---|---|
| Message button doesn't appear | WhatsApp may not be enabled on your license — check with your admin |
| Free-text message fails to send | WhatsApp only allows free-text replies inside an active conversation window; outside that window, send an approved template instead |
| Template list is empty | Templates are managed with your WhatsApp provider, not in the connector — confirm templates are approved and active with your provider |

## Recordings & transcripts

| Symptom | Likely cause / next step |
|---|---|
| No recording URL on the HubSpot call | Confirm call recording is enabled on your AWS Connect instance, and that the connector's `ConnectRecordingBucket` parameter (set at deployment) points to the correct S3 bucket |
| No transcript on the HubSpot call | Confirm **Transcription** is toggled on in the admin portal, and that Contact Lens is enabled on your Connect instance |
| Transcript appears late, well after the call ends | Transcripts are processed asynchronously and can take longer than the call activity itself to appear — this is expected for busy queues |

## Wrap-up & dispositions

| Symptom | Likely cause / next step |
|---|---|
| No wrap-up form appears after a call | **Wrap-Up Notes** is likely toggled off in the admin portal — see [Admin Configuration Guide](../admin/configuration-guide.md#toggle-settings) |
| Disposition list is empty or missing options | Your admin needs to add dispositions under **Disposition Configuration** in the admin portal |

## Still stuck?

Contact the Octave Bytes support team with your AWS Account ID, HubSpot Portal ID, and a description of the issue on hand so we can assist you quickly.
