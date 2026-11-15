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
| Temperatures, fans, light and speed | Only with OpenCentauri firmware (`"extra_commands": true` for the printer) | Yes |

## What it can't do

Klipper-only parts, such as macros, the bed mesh, config files and Klipper's system pages, don't apply.

[All features](../features.md)
