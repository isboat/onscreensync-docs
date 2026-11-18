# OnScreenSync product growth opportunities

Focus first on small multi-location retailers and hospitality teams. They can already publish pictures, videos, menus, text, clocks, and playlists. The strongest reason to sign up is the ability to get one screen live quickly and keep several screens current without visiting each site. Treat that segment and the priorities below as hypotheses to test.

The [platform overview](platform-overview.md) describes the current customer workflow. The [technical overview](technical-overview.md) maps the dashboard, APIs, players, and external services that would deliver these improvements.

## Build first

| Feature | Why a prospect would sign up | What to ship and how to measure it |
| --- | --- | --- |
| Guided first screen | A shop manager can see a menu or promotion on a TV during the trial. | Offer an interactive demo with sample content before sign-up. After sign-up, guide the user through choosing a template, pairing a TV, publishing, and confirming playback. Measure the share of sign-ups with a confirmed first playback within 24 hours and the median time to that playback. |
| Scheduling and screen groups | A restaurant can rotate breakfast and lunch menus automatically. A retailer can publish one campaign to several branches and keep local exceptions. | Start with named screen groups, local time zones, recurring time windows, expiry dates, and a default layout. Show what will play next, resolve overlaps predictably, and test daylight-saving changes. Measure the share of activated customers who schedule a second publish and use a screen group. |
| Reliable offline playback and publish feedback | A customer can trust the TV to keep showing a known screen during a connection drop and see when a new version actually arrived. | Download and verify the next content version before switching to it. Keep the last successful version and a fallback for content that requires a live connection. Show connection status separately from downloaded and playing status. Measure successful switches, time to playback, and recovery after a simulated outage on each supported platform. |
| Reusable branded templates | A customer can produce a credible-looking menu, offer, or welcome screen with their own assets in minutes. | Start with a few editable layouts, brand colours and logos, portrait and landscape previews, and device-specific compatibility checks. Include readable defaults for viewing at a distance. Track template-to-publish completion and the share of new users who publish with their own content. |

Scheduling is a useful competitive benchmark. Xibo documents recurring schedules, dayparts, and priority, while the Screenly CLI documents labels for grouping screens and playlists. Anthias provides another public example of a signage scheduler and asset library. Those sources establish that customers can encounter these workflows elsewhere. They do not establish what OnScreenSync users will pay for. [Xibo manual index](https://github.com/xibosignage/xibo-manual/blob/master/help-links.yaml) · [Screenly CLI](https://github.com/Screenly/CLI) · [Anthias](https://github.com/Screenly/Anthias)

## Expand once publishing is dependable

- **Live content blocks.** Start with an iCalendar feed for venues or a read-only CSV menu feed for hospitality. Display the latest usable data with a last-updated time and a clear fallback. Add weather only after confirming which customers need it and how the data provider can be licensed. Use published formats so customers can switch source systems. Measure weekly active feeds and feed-related support requests. [iCal.NET and RFC 5545](https://github.com/ical-org/ical.net) · [Xibo remote data documentation index](https://github.com/xibosignage/xibo-manual/blob/master/help-links.yaml)
- **Fleet management for growing customers.** Add location-scoped roles, draft approval, version history and rollback, and alerts when a screen is stale or offline. Offer downloadable playback events to customers who need evidence that a campaign ran, with clear retention. Measure conversion among accounts with multiple sites and how often alerts lead to an issue being resolved.
- **Workflow integrations.** Start with a versioned API and outbound webhooks for publish completion and device status. Add one connector once several prospects request the same system. Prioritise approved read-only imports or narrow permissions so an integration failure cannot replace a live display unexpectedly. [OpenAPI Specification](https://github.com/OAI/OpenAPI-Specification)
- **AI that helps users publish.** The platform already offers image generation. Test practical additions such as fitting existing artwork to a screen, proposing concise menu copy, or adapting an approved template into another language. Make outputs editable, show a preview, and require approval before publishing. Measure time saved and the share of suggestions that make it into a published screen.

Across these features, define a common content version and playback status that each player can report. Qualify storage, video, and recovery behaviour on real Android TV, Tizen, and webOS devices. Browser service workers illustrate one offline approach, but support and storage limits must be checked on each TV platform. [MDN Service Worker API](https://github.com/mdn/content/blob/main/files/en-us/web/api/service_worker_api/index.md)

## Validate before expanding the roadmap

Recruit a small cohort of retailers and hospitality operators with at least two screens or a recurring content change. Ask each to pair a screen, publish a real menu or offer, schedule a change, and recover from a brief outage. Compare first playback, repeat publishing, and paid conversion with the current onboarding flow. Interview users who abandon the trial to find out where they stopped and what they used instead.

Research reviewed on 18 November 2026. The linked public documentation provides implementation and competitive examples. Direct access to several commercial feature pages was blocked in the research environment. No OnScreenSync product analytics or customer interviews were available for this review.
