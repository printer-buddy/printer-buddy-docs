<!--
LICENSE

Copyright (C) 2026  sterling motuz <Sterling@dexabyte.ca>

for https://github.com/printer-buddy/printer-buddy

SPDX-License-Identifier: AGPL-3.0-only

Additional term (AGPL-3.0 section 7b, keep author credit): keep this header

Additional term (AGPL-3.0 section 7c, mark changed versions): if you make any changes, you must include a CHANGELOG with all changes and their dates
-->
# Features

## Why Printer Buddy

- **One page for all your printers.** Klipper, Bambu Lab and Elegoo printers side by side, live, on one self-hosted page.
- **Yours, on your network.** It runs on a Pi, the printer's own host or any Linux box. No cloud, no account, no subscription.
- **Feels like Fluidd.** The printer page uses Fluidd's layout, so it's familiar from the first click.
- **Its own AI.** Failure detection that watches the camera and can pause a print before it turns into spaghetti, running right on a Pi.
- **Share your prints.** Send a link to a printer's live camera and progress, and chat with the people watching.

## Your printers

Everything below works on every printer. What each kind of printer adds or can't do:

| Printer | Highlights | All features |
|---|---|---|
| **Klipper** | Full control, like Fluidd: macros, bed mesh, console, config editor, G-code preview, object skipping | [Klipper printers](printers/klipper.md) |
| **Bambu Lab** | Fully local over LAN: live status, camera, AMS, start prints, errors in plain words | [Bambu Lab](printers/bambu.md) |
| **Snapmaker U1** | Its four toolheads, the filament on each nozzle, and the top cover purifier | [Snapmaker U1](printers/snapmaker-u1.md) |
| **Creality K2** | CFS units and their slots, with colours and humidity | [Creality K2](printers/creality-k2.md) |
| **Elegoo Centauri Carbon** | CC1 and CC2: status, camera and print control | [Elegoo](printers/elegoo.md) |

AFC and Happy Hare filament changers and toolchangers on Klipper show up too.

## Watch every printer at once

- **Printer cards** with the live camera, state, file, progress, time left and temperatures. Sort them, search them, put them in your own order or in groups, or switch to a compact list.
- **Fleet** tells you how many printers are printing, idle, offline or in error, and which one finishes next.
- **Fleet Stats** adds up every printer's history: prints, success rate, print time and filament, with a table per printer. It also shows **where prints fail**: the files that fail most, and the hours of the day they fail. Download it all as CSV.
- **Quick View** opens any printer in a pop-up, and the **camera wall** shows every camera at once.
- **Edit layout** puts the panels you want where you want them.

[More about the home page](using/home.md)

## Run each printer like you're standing next to it

- **Camera** in full screen, with zoom up to 8 times. Scroll, pinch and drag to get a close look at the first layer.
- **Start, pause, cancel and re-print**, with the print's picture, progress ring, layer, speed, flow, filament and finish time.
- **Tool**: move and home, extrude and retract, fine-tune the Z offset live, and change speed, flow and pressure advance mid-print.
- **Temperatures** with presets (PLA, PETG, ABS or your own) and a history chart.
- **Macros** as buttons, in groups you choose. Macros that take values get a box to fill in. Lock risky ones while printing.
- **Console** with suggestions for every command and macro, Tab completion, search and filters.
- **Jobs**: every file on the printer, sortable like Fluidd, with print, queue, preview, download, rename and remove.
- **Job queue**: line up prints, set copies, and see the total filament, time and finish time.
- **G-code preview** in 2D or 3D, following the print layer by layer.
- **Skip a failed object.** Click it on the G-code preview and the rest of the plate keeps printing.
- **Plate check.** Before a print starts, Printer Buddy compares the camera with a picture of the empty bed and warns you if the last print is still on it.

[More about the printer page](using/printer-page.md)

## Tune and look after it

- **Bed mesh** in 3D with your saved profiles, **end stops**, **runout sensors**, **Beacon** and **manual probe**.
- **Config files** with an editor, and a **Save config** button that shows exactly what will change before it's written.
- **Errors you can act on**: Klipper's error with restart buttons and logs right there, and Bambu errors in plain words.
- **System**: the printer's computer, disk space, SD card, database backups, load charts and every MCU.
- **Diagnostics**: live charts of any Klipper value, and a viewer for every Klipper object.
- **History** of every print, with statistics, notes, CSV export and one-click reprint.

## AI failure detection

- Watches the camera during prints and spots **spaghetti, warping, first-layer problems, stringing, blobs and cracks**.
- **Alert only, or alert and pause** the print, per printer. A box on the camera shows where the problem is.
- Three models: **lite** for the smallest hosts, **basic** for a Pi, and **heavy** for a PC or GPU. Every model release is scored on the same 1,000 photos.
- Tune how sensitive it is, set a detection area to ignore clutter, and see the score history of every print.
- Your answers to "was it really a failure?" can help train it.

[More about AI](using/ai.md)

## Hear about it wherever you are

- **ntfy, Discord, Telegram, Pushover and email.**
- Started, paused, resumed, finished, failed, cancelled, offline, Klipper shutdown and AI alerts, with a camera snapshot.
- **Progress updates**, for example at 25%, 50% and 75%.

[More about notifications](using/notifications.md)

## Share it

- **Share links** to a printer's live camera and progress, for an hour, a day, a week, until the print ends, or until you turn them off. Viewers need no account.
- Works from anywhere through Printer Buddy's relay, **without opening ports** on your router.
- **Live chat** with viewers, with flags, blocked words and alerts so you stay in control.

[More about remote access](using/remote.md)

## Timelapses

- One frame per layer or every few seconds, turned into a video when the print ends. Watch, download or delete them from the printer's page.

[More about timelapses](using/timelapse.md)

## Easy to set up and keep up to date

- A **guided installer**: on the printer's own host or on a separate one, with a simple or a full interface.
- Its own **camera streamer** can replace Crowsnest.
- **Updates from the page.** Each part updates on its own, and you choose stable or nightly for each.
- For tinkerers, `/metrics` for Prometheus and Grafana, and `/api/stats` for print history.

[Install](install/index.md) · [Updates](updates/index.md) · [Developers](developers/index.md)
