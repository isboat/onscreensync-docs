# OnScreenSync platform overview

OnScreenSync is a digital signage platform for creating and managing what appears on TVs from a web dashboard. A shop can advertise offers, a restaurant can update its menu, and a venue can show announcements, media, or a clock. Staff can make changes centrally and assign different screens to different TVs.

## What you can display

| Content | How you control it |
| --- | --- |
| Pictures and videos | Upload files to the media library and reuse them in screen layouts or playlists. Use a media-only layout to give an image or looping video the whole screen. Some layouts and players also support external media, subject to the source and TV's playback support. |
| Announcements and information | Create reusable rich-text assets for notices, promotions, or instructions. Format the text and choose a layout for displaying it on its own or in a supported playlist. |
| Menus | Create menu items with names and prices, and use a menu layout to display them. Supported layouts can place the menu over an image or video. |
| Date and time | Choose the live date-and-time layout and configure the presentation so the TV shows a clock that updates during playback. |
| Rotating content | Arrange images, videos, and text in a playlist. Assign that playlist to a compatible screen layout to cycle through the items in order. |

## How to put content on a TV

1. **Pair the TV.** Open the OnScreenSync player on a supported TV. It shows an activation code that an authorised dashboard user approves.
2. **Create the screen.** Choose a layout in the dashboard and select the media, menu, text, playlist, or clock to display. A screen is a saved composition. A device is the physical TV running the player.
3. **Preview and publish.** Review the composition in the browser where the layout is supported. Publish it and assign it to the appropriate TV. Playback, external embeds, and layout support can differ by TV platform, so check the final result on the intended device.
4. **Update centrally.** Edit a screen or its assets and publish the updated content. The registered player retrieves its assigned content and responds to supported update messages.

The dashboard also lets authorised staff manage users, devices, and organisation settings. Partner and central administration portals support customer onboarding and service operations.

## Plans and supported players

The public site lists Free, Standard, and Premium plans. Its plan comparison covers user and TV limits, media uploads, screen creation, and AI image generation. Check the current offering before choosing a plan. [Public plans](https://www.onscreensync.com/service.html) · [Website repository](https://github.com/isboat/ss-solution-website)

The player repository covers native Android TV, Samsung Tizen, and LG webOS. Check the platform-specific installation, packaging, and device requirements before choosing hardware. [TV player repository](https://github.com/isboat/ss-display-androidtv)

Use the dashboard to explore the editing and publishing workflow. The preview repository documents the separate browser renderer and its supported layouts. [Dashboard](https://dashboard.onscreensync.com/) · [Dashboard UI repository](https://github.com/isboat/ss-management-dashboard-ui) · [Preview repository](https://github.com/isboat/ss-management-dashboard-preview)

For the system architecture, see the [technical overview](technical-overview.md).
