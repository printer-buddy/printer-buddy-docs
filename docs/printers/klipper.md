# Klipper printers

Any printer running **Klipper and Moonraker** gets everything Printer Buddy does: Voron, Creality K1 and K1C, Sovol, FlashForge with Klipper and the rest. Printer Buddy talks to Moonraker, the same way Fluidd and Mainsail do.

## Everything on the printer page

- **Status**: progress ring, file and its picture, layer, speed, flow, filament, slicer and file estimates, finish time. Pause, cancel and **re-print** the last files.
- **Camera**: every webcam Moonraker knows, full screen and zoom up to 8 times.
- **Tool**: jog and home, absolute or relative position fields, extrude and retract with a filament and flow readout, live **Z offset** with save, speed, flow, **pressure advance** and smooth time. **FORCE_MOVE** when your config allows it.
- **Thermals**: every heater, sensor and temperature fan, with presets and a chart.
- **Outputs**: fans with their speed and RPM, pins, LEDs, LED effects and Moonraker power devices.
- **Limits**: velocity, acceleration, square corner velocity and minimum cruise ratio, live.
- **Macros** in groups, with value boxes, hiding and locking during prints.
- **Console** with every command and macro suggested, Tab completion, search and filters.
- **Jobs** and the **job queue**, with totals.
- **G-code preview** in 2D or 3D, following the print, with **object skipping** (`[exclude_object]`).
- **Bed mesh** in 3D, mesh profiles, **end stops**, **runout sensors**, **Beacon** and **manual probe**, bed screws and screws tilt adjust.
- **History** with statistics, notes, CSV and reprint.
- **Config files** with an editor, and **Save config** that shows the changes first.
- **System**: host details, disks, SD card, Moonraker database backups, load charts and every MCU.
- **Diagnostics**: live charts of any Klipper value, Moonraker sensors and an object viewer.
- **Klipper errors and warnings** with restart buttons and logs.
- **Restarts, host power and services** in the ☰ drawer.

## Extras for some printers

| Printer or add-on | What you get |
|---|---|
| **Happy Hare MMU** | The MMU card: every gate with its colour and material, what's loaded, load and unload |
| **AFC** (Box Turtle, Night Owl…) | The lanes and what's loaded |
| **Toolchangers** | Each tool and which one is active |
| **Creality K2** | [CFS units and slots](creality-k2.md) |
| **Snapmaker U1** | [Toolheads, per-nozzle filament and the top cover](snapmaker-u1.md) |

## Also on Klipper

- [AI failure detection](../using/ai.md), [notifications](../using/notifications.md), [timelapses](../using/timelapse.md), [share links and chat](../using/remote.md).
- Printer Buddy can be installed **on the printer's own Klipper host**, so no extra computer is needed. See [Install](../install/index.md).

[All features](../features.md)
