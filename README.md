Now Playing Dashboard for Nest Hub

A Home Assistant dashboard card designed to display currently playing media in a clean and modern style on Google Nest Hub devices. Supports casting the dashboard automatically when media starts playing.

Features

Now Playing Card: Displays album art, track title, artist, and playback progress.

Clean, Minimal Design: Modern UI optimized for smart displays.

Automatic Casting: Casts the dashboard to your Nest Hub when media starts playing.

Responsive Layout: Works well on Google Nest Hub and other Cast-enabled devices.

Customizable: Adjust colors, fonts, and layout to match your Home Assistant theme.

Requirements

Home Assistant
 (Core 2025.x or later recommended)

Google Nest Hub or other Cast-enabled smart display

Media players integrated in Home Assistant (Sonos, Spotify, etc.)

Required Lovelace cards / plugins (install via HACS or manually):

card-mod
 – for styling and theming the card

layout-card
 – for arranging the card layout (if used)

Any other helper cards used in your configuration (e.g., progress bar, button cards)

⚠️ Make sure these dependencies are installed before adding the Now Playing dashboard card.

Manual Installation

Clone or download this repository to your Home Assistant /config/www/ directory:

git clone https://github.com/yourusername/now-playing-dashboard.git

Add the card to your Lovelace resources:

resources:
  - url: /local/now-playing-dashboard/now-playing-card.js
    type: module

Add the Lovelace view:

title: Now Playing
path: now-playing
panel: true
cards:
  - type: custom:now-playing-card
    entity: media_player.living_room
Optional Automation

Cast the dashboard automatically when media starts playing:

alias: Cast Now Playing
trigger:
  - platform: state
    entity_id: media_player.living_room
    to: 'playing'
action:
  - service: cast.show_lovelace_view
    data:
      entity_id: media_player.nest_hub
      dashboard_path: lovelace
      view_path: now-playing
Customization

Colors & Fonts: Adjust CSS variables in now-playing-card.js to match your theme.

Progress Bar Style: Modify the card’s progress bar design in the card’s CSS.

Album Art Size: Change the dimensions in the card configuration.

Screenshots

Contributing

Contributions, improvements, and feature requests are welcome! Please submit a pull request or open an issue.

License

This project is licensed under the MIT License – see the LICENSE
 file for details.
