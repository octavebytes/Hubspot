# Product Overview

## What is the HubSpot CTI Connector?

The **HubSpot CTI Connector** connects **AWS Connect** (your contact center platform) with **HubSpot CRM**, so agents can handle calls, chat, and WhatsApp without leaving their CRM workflow. It's made up of two parts:

- A **Chrome extension** that runs inside HubSpot and injects dial/message controls, and bridges HubSpot to the connector.
- A **connector application** deployed inside *your own AWS account*, which embeds the AWS Connect softphone (CCP), talks to the HubSpot API, and logs activity back to HubSpot.

Every customer runs their own dedicated, single-tenant deployment — your connector, your AWS account, your data.

## Who it's for

| Role | What they use |
|---|---|
| **Agents** | The Chrome extension + embedded Connect softphone, day to day, for every call/chat/WhatsApp conversation |
| **Admins** | The connector's admin portal, to configure HubSpot OAuth, dispositions, screenpop behavior, and licensing |
| **IT / DevOps** | The AWS CloudFormation deployment, once, to stand up the connector infrastructure |

## Core capabilities

- **Voice** — inbound and outbound calls through an embedded AWS Connect softphone (CCP), without leaving the browser.
- **Chat & WhatsApp** — inbound chat and WhatsApp via the Connect chat channel; outbound WhatsApp messaging (templates or free text) from HubSpot.
- **Screenpop** — when a contact calls or messages in, the connector automatically searches HubSpot and opens the matching contact or deal record. If there's more than one match, the agent picks from a short list; if there's no match, a new HubSpot contact is created automatically.
- **Click-to-dial / click-to-message** — dial and WhatsApp buttons appear directly on phone number fields throughout HubSpot.
- **Activity logging** — calls, chats, and WhatsApp messages are logged back to HubSpot automatically as calls or communications, with the recording URL, transcript (if enabled), and any associations to deals, tickets, or companies.
- **Wrap-up** — agents can select a call disposition and add a note after each call, which gets appended to the HubSpot call record.

## How it fits together

```text
┌─────────────────────┐   extension bridge    ┌──────────────────────┐
│  Agent's HubSpot tab │ ◄────────────────────►│   Chrome Extension    │
└─────────────────────┘                        └───────────┬──────────┘
                                                             │ popup window
                                                             ▼
                                                 ┌──────────────────────┐
                                                 │  Connector           │
                                                 │  (your AWS account)  │
                                                 └───────────┬──────────┘
                                        ┌────────────────────┼────────────────────┐
                                        ▼                    ▼                    ▼
                              ┌──────────────────┐ ┌──────────────────┐ ┌──────────────────┐
                              │   AWS Connect     │ │   HubSpot CRM    │ │    WhatsApp      │
                              │  softphone / CCP  │ │   (OAuth API)    │ │  partner API      │
                              └──────────────────┘ └──────────────────┘ └──────────────────┘
```

The Chrome extension lives in the agent's browser and never talks to the internet directly — every API call goes through the connector running in your AWS account. See [Solution Security](../security/index.md) for more on the tenancy and data model.

## Where to go next

- Deploying the connector for the first time? Start with the [Deployment Guide](../deployment/deployment-guide.md).
- Setting up an individual agent? See the [Agent Setup Guide](../deployment/agent-setup.md).
- Already deployed and want to configure it? See the [Admin Configuration Guide](../admin/configuration-guide.md).
- Agents looking for day-to-day usage help? See the [Agent User Guide](../user-guides/agent-guide.md).
