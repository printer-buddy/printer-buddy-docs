# Printer page

Click a printer on the dashboard to open its page.

## Tabs and panels

The sidebar on the left holds the page's tabs. Each tab is made of panels (status, camera, temperatures, move, console, files, bed mesh, macros…).

- **Edit layout** (top bar) lets you add, move and remove panels and tabs, and drag tabs to reorder them.
- **Collapse** at the bottom of the sidebar shrinks it to icons.

## Top bar

| Button | What it does |
|---|---|
| **Save config** | Only shows when Klipper has unsaved changes &mdash; see below |
| Theme | Light or dark |
| Pause / Cancel | Pause or cancel the current print |
| Emergency stop | Stops the printer immediately |
| **☰** | The [printer drawer](drawers.md): restarts, host power, services |

## Console

Type G-code and press **Send**.

- **↑ / ↓** go through the commands you've sent.
- Start typing to get suggestions for every command and macro Klipper knows.
- **Filters** hides lines you don't care about (like temperature reports).
- Click a line you sent to put it back in the box.

## Klipper errors and warnings

When Klipper isn't ready, a **red banner** under the top bar says why &mdash; Klipper's own error (for example a config mistake and its line), or that Klipper isn't connected to Moonraker. It has **Restart**, **Firmware restart**, **Restart service** and a link to download `klippy.log`.

When Klipper is fine but there are **warnings** (deprecated config options, a Moonraker part that failed to start…), a **yellow banner** lists them. **Hide** hides it until the warnings change.

## Save config

After a calibration, bed mesh, offset or anything else Klipper hasn't saved yet, an orange **Save config** button appears. Click it to see exactly what will be written to `printer.cfg`, then **Save config & restart** (runs `SAVE_CONFIG`, which restarts Klipper). It's disabled while printing.
