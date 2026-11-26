<!--
LICENSE

Copyright (C) 2026  sterling motuz <Sterling@dexabyte.ca>

for https://github.com/printer-buddy/printer-buddy

SPDX-License-Identifier: AGPL-3.0-only

Additional term (AGPL-3.0 section 7b, keep author credit): keep this header

Additional term (AGPL-3.0 section 7c, mark changed versions): if you make any changes, you must include a CHANGELOG with all changes and their dates
-->
# Making a theme

Themes live in [printer-buddy-themes](https://github.com/printer-buddy/printer-buddy-themes). Every theme there shows up in Printer Buddy under **Settings → Theme**, and picking one applies it to the whole box, on every device.

## 1. Fork the repo

Fork [printer-buddy-themes](https://github.com/printer-buddy/printer-buddy-themes) on GitHub and clone your fork.

## 2. Start from Printer Buddy's own look

Copy the `printer-buddy` folder and give the copy your theme's id, for example `my-theme`. The id is 1 to 40 lowercase letters, numbers or `-`, starting with a letter or number.

`printer-buddy/theme.json` has every colour Printer Buddy uses, for dark and light mode, so you only change what you want.

## 3. Edit theme.json

```json
{
  "mode": "dark",
  "colors": { "dark": { "bg": "#0B0B0D", "orange": "#FF8A1F" }, "light": { "bg": "#f4f4f6" } },
  "fonts": { "text": { "family": "My Font", "file": "my-font.woff2" } },
  "images": { "background": "background.jpg", "logo": "logo.svg", "sidebar": "sidebar.png" },
  "css": "theme.css"
}
```

Every part is optional:

| Part | |
|---|---|
| `mode` | `dark` or `light`: picking the theme switches the device to it |
| `colors` | separate `dark` and `light` sets; each colour is `#rgb`, `#rrggbb`, `#rrggbbaa`, `rgb(...)` or `rgba(...)` |
| `fonts` | `text` for everything, `mono` for the dashboard's monospace text; `file` is optional (`.woff2`, `.woff`, `.ttf`, `.otf`), without it the font must be on the device |
| `images` | `background` behind the whole page, `logo` next to the printer name, `sidebar` on the dashboard's side bar (`.png`, `.jpg`, `.jpeg`, `.gif`, `.svg`) |
| `css` | a stylesheet for anything the parts above don't cover |

Colour names:

| Name | |
|---|---|
| `bg` | page background |
| `text` | text |
| `orange` | the accent colour |
| `purple`, `lilac` | used for finished prints |
| `red`, `red-text` | errors |
| `card`, `card2`, `line`, `track`, `muted` | cards, lines and quieter text |
| `bd-panel`, `bd-head`, `bd-line`, `bd-hover`, `bd-deep` | the dashboard's panels, panel headers, lines and hover |

Put the pictures and fonts you use in your theme's folder.

## 4. theme.css (optional)

Every `url(...)` in it must point at a picture or font in your theme's folder, relative to `theme.css`. A theme whose `theme.css` loads anything from elsewhere, or uses `@import`, `image-set()`, `expression()`, `javascript:`, bindings or backslashes, can't be picked.

Each file can be up to 15 MB (`theme.json` and `theme.css` up to 200 KB), and a theme can have up to 20 files.

## 5. Add a preview

Take a screenshot of Printer Buddy with your theme on and save it in your theme's folder as `preview.png`. It's the picture on your theme's card in Settings.

## 6. Add it to themes.json

Add one line for your theme to `themes.json` in the repo's root:

```json
{ "id": "my-theme", "name": "My Theme", "author": "your name", "preview": "preview.png" }
```

`name` and `author` are shown on the card, up to 60 characters each.

## 7. Try it on your box

Push your theme to your fork. On your Printer Buddy box, add this line to `printer-buddy.env` in the Printer Buddy folder and restart Printer Buddy:

```
PB_THEMES_URL=https://raw.githubusercontent.com/<your name>/printer-buddy-themes/<your branch>
```

**Settings → Theme** now lists the themes from your fork. Remove the line and restart to go back to the normal list.

## 8. Open a pull request

Open a pull request on [printer-buddy-themes](https://github.com/printer-buddy/printer-buddy-themes) with your theme's folder and its line in `themes.json`.

Porting a Fluidd or Mainsail theme is welcome: its colour, logo, background and custom.css fit `colors`, `images` and `theme.css`.
