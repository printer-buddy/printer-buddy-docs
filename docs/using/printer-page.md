# Printer page

Click a printer on the dashboard to open its page.

## Tabs and panels

The sidebar on the left holds the page's tabs. Each tab is made of panels (status, camera, temperatures, move, console, files, bed mesh, macros…).

- **Edit layout** (top bar) lets you add, move and remove panels and tabs, and drag tabs to reorder them.
- **Collapse** at the bottom of the sidebar shrinks it to icons.

## Camera

The camera panel shows the printer's main camera. Use the buttons in its top-right corner:

- **Full screen** &mdash; fills the screen. Press the same button, or Esc, to leave.
- **+ and &minus;** &mdash; zoom in and out, up to 8 times. You can also scroll the mouse wheel over the picture to zoom towards the cursor, or double-click to zoom to 2.5 times and double-click again to go back.
- **Moving around** &mdash; when you're zoomed in, drag the picture. On a touch screen, drag with one finger and pinch with two.
- **The zoom button** (for example **2.5&times;**) appears while you're zoomed in. Click it to go back to normal. Switching camera or printer also resets the zoom.

It's a digital zoom: the page enlarges the picture the camera sends, so you don't get more detail than the camera gives you.

!!! note "Nightly for now"
    Zoom, moving around and leaving full screen with the same button are on nightly and come to stable with the next release. Full screen itself works on stable too, and Esc always leaves it.

## Macros

The macros panel shows each of your printer's macros as a button.

- **Click a macro** to run it. A macro that takes values has a small arrow next to it: click the arrow to open a box with a field for each value, then **Send**. The name button runs it without values.
- **Hide some&hellip;** shows an &times; on each button so you can hide the ones you never use. **Show hidden** brings them back.
- **Organize&hellip;** puts macros in groups you name, such as Calibration or Camera. Pick a group for each macro in the list. Click a group's heading to fold it.
- **Suggest groups** (in **Organize**) sorts macros that aren't in a group yet, by their names, into Print, Calibration, Motion, Filament, Temperature, Camera, Lights and System. Macros that share a first word, such as `MMU_LOAD` and `MMU_UNLOAD`, go in a group named after it. Macros you've already grouped stay where they are.
- **Lock** (in **Organize**) greys a macro out while a print is running or paused. An unlocked macro still asks you to confirm when you run it during a print.

Groups, locks and hidden macros are saved in your browser, for each printer.

!!! note "Nightly for now"
    Groups, locks and the arrow for values are on nightly and come to stable with the next release.

## Job queue

The queue panel lines up prints to run one after another. Add files with **+ Queue** in the Files panel. For each file you can set how many copies to print (**&minus;** and **+**), move it to the front with **&uarr; Next**, or remove it. **Start queue** and **Pause queue** control when the next job starts.

Under the list it adds up the queue: **Filament** (metres and grams), **Print time** and **ETA**, the time the whole queue should finish. If a print is running, the ETA includes what's left of it. If some files have no estimate in them, a note says how many.

!!! note "Nightly for now"
    The filament, print time and ETA totals are on nightly and come to stable with the next release.

## Database backup

The **Database backup** panel (add it with **Add a panel**) backs up Moonraker's database, which holds your print history, spools and saved settings.

- **Create backup** saves one, named with the date and time.
- The restore button puts a backup back. It replaces everything in the database with that backup, so it asks first, and it's off while a print is running.
- **Compact database** shrinks the database file.

!!! note "Nightly for now"
    This panel is on nightly and comes to stable with the next release.

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
