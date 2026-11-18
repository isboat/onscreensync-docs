# OnScreenSync technical overview

OnScreenSync separates public discovery, browser-based content management, and TV playback. The dashboard API handles operator actions. The display API handles requests from registered TVs. Administration portals manage customer and device records, and messaging helps connected clients respond to changes.

For the customer workflow and offerings, see the [platform overview](platform-overview.md).

## Repository map

| Repository | Role in the platform |
| --- | --- |
| [Public website](https://github.com/isboat/ss-solution-website) | Hosts the product pages, plans, dashboard links, Android TV download, and the bootstrap configuration that players use to discover display endpoints. |
| [Management Dashboard UI](https://github.com/isboat/ss-management-dashboard-ui) | Angular workspace where operators sign in, manage assets and screens, pair devices, and publish content. It calls the dashboard API and opens the separate preview app. |
| [Management Dashboard API](https://github.com/isboat/ss-management-dashboard-api) | ASP.NET Core API for user authentication and tenant-scoped screens, templates, media, menus, text, playlists, devices, and publishing. It also serves the preview payload. |
| [Management Dashboard Preview](https://github.com/isboat/ss-management-dashboard-preview) | Angular renderer that requests a selected screen's preview data from the dashboard API and renders a supported layout in the browser. |
| [Display API](https://github.com/isboat/ss-display-api) | ASP.NET Core API for device-code pairing, device tokens and refresh, device identity, assigned content, and SignalR connection setup. |
| [TV players](https://github.com/isboat/ss-display-androidtv) | Native Android TV app and separate Samsung Tizen and LG webOS apps. They discover endpoints, pair, retrieve content, and render it full-screen. |
| [Tenant management service](https://github.com/isboat/ss-tenant-managment-service) | Server-rendered portal for central operators to manage tenants, partners, users, registrations, and TV support actions. |
| [Partner management service](https://github.com/isboat/ss-partners-management-service) | Server-rendered portal for partners to onboard and support customer tenants associated with their partner account. |
| [Dashboard change listener](https://github.com/isboat/ss-management-dashboard-changelistener) | Azure Functions worker that forwards messages from a configured Service Bus queue to a dashboard SignalR hub. It also provides a negotiation endpoint for compatible clients. |
| [Platform documentation](https://github.com/isboat/onscreensync-docs) | This repository. It documents the product and how the repositories work together. Component-specific guidance lives with each project. |

## How content reaches a TV

1. **Bootstrap and pairing.** A player reads the endpoint configuration from the public website, then requests an activation code from the display API. An operator approves the code in the dashboard through the dashboard API. The TV can then obtain device credentials and retrieve its identity.
2. **Editing and preview.** The browser dashboard sends screen and asset changes to the dashboard API. Screen records describe the layout and which assets to display. The separate preview app requests that screen's preview payload using the operator's session and renders the supported template.
3. **Publishing and assignment.** The dashboard API handles publish and assignment operations. The display API uses the registered device's identity to resolve the assigned content. The player renders the returned layout and loads the referenced media.
4. **Live updates.** Players negotiate and register for SignalR messages. A supported publish notification tells the player to retrieve updated content through the display API. Administrative portals can also send supported operator messages and remote actions.
5. **Dashboard notifications.** The change listener is a separate messaging path. It consumes a configured Service Bus queue and broadcasts to the dashboard hub. The dashboard API's display notification code publishes via Azure SignalR directly.

## Shared services and boundaries

- **MongoDB** holds operational records such as tenants, users, registrations, device assignments, and screen and asset metadata. APIs and administration portals access the records needed for their role.
- **Amazon S3** stores uploaded media for the dashboard API. Preview and player apps load media from the URLs in their content payloads.
- **Azure SignalR Service** delivers notifications to connected clients. **Azure Service Bus** supplies the input queue for the dashboard change listener, and **Azure Storage** supports its Functions host. Application Insights provides worker telemetry.
- **Stability AI** supports optional image generation in the dashboard API. **SMTP** supports invitations and other email workflows in the management services.
- **Operator and device access** use distinct flows. Dashboard sessions govern tenant-scoped operator work, device credentials identify an activated player, and administrative portals have their own sign-in.
