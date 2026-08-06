# Release Notes

## Version 26 — 06 March 2026

### What's new

- **SMS support** — introduced support for SMS to broaden communication channels and improve user accessibility. *(Subject to license.)*
- **Email column in multi-match contact list** — when an inbound call or chat matches more than one HubSpot contact, the picker now shows each contact's email address alongside their name.
- **Call attributes support** — configured Connect attributes can now be captured per call and shown in the HubSpot call description, for better decision-making based on call flow data.

### Bug fixes and improvements

- Resolved identified security vulnerabilities in the container image used to build and run the connector.
- Fixed an issue with call recording storage that could cause inconsistent uploads.
- Connector settings, agent sessions, and license data now persist in DynamoDB in production, for reliability across restarts and multiple instances.
- Improved API security with additional authorization checks on connector endpoints.

---

> Earlier version history is not yet published here. Contact [sales@octavebytes.com](mailto:sales@octavebytes.com) if you need details on a prior release.
