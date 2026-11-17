<!--
LICENSE

Copyright (C) 2026  sterling motuz <Sterling@dexabyte.ca>

for https://github.com/printer-buddy/printer-buddy

SPDX-License-Identifier: AGPL-3.0-only

Additional term (AGPL-3.0 section 7b, keep author credit): keep this header

Additional term (AGPL-3.0 section 7c, mark changed versions): if you make any changes, you must include a CHANGELOG with all changes and their dates
-->
# Elegoo Centauri Carbon

Printer Buddy's built-in bridge runs the **Centauri Carbon (CC1)** and **Centauri Carbon 2 (CC2)** over your own network, with the same pages as a Klipper printer.

## What you get

- **Live status**: state, file, progress, time left and temperatures.
- **Camera**: the printer's own camera.
- **Print control**: start, pause, resume and stop.
- **Files** on the printer: list, upload and delete.
- **History**, [AI failure detection](../using/ai.md), [notifications](../using/notifications.md), [timelapses](../using/timelapse.md) and [share links](../using/remote.md), like any other printer.

| | CC1 | CC2 |
|---|---|---|
| Talks over | SDCP (port 3030) | MQTT (port 1883) |
| Temperatures, fans, light and speed | Only with OpenCentauri patched firmware: tick **OpenCentauri patched firmware** when you add it | Yes |

## OpenCentauri

- **OpenCentauri COSMOS** (CC1 or CC2) is a full Klipper firmware with Moonraker. Add the printer as a **Klipper** printer instead, and it gets everything a [Klipper printer](klipper.md) gets.
- **OpenCentauri patched firmware** (CC1) still talks like Elegoo's own firmware. Add it as **Elegoo Centauri Carbon** and tick **OpenCentauri patched firmware**, so Printer Buddy can change temperatures, fans, light and speed. On Elegoo's own firmware those commands can crash the printer's software, so Printer Buddy doesn't send them.

## What it can't do

Klipper-only parts, such as macros, the bed mesh, config files and Klipper's system pages, don't apply.

[All features](../features.md)
