<!--
LICENSE

Copyright (C) 2026  sterling motuz <Sterling@dexabyte.ca>

for https://github.com/printer-buddy/printer-buddy

SPDX-License-Identifier: AGPL-3.0-only

Additional term (AGPL-3.0 section 7b, keep author credit): keep this header

Additional term (AGPL-3.0 section 7c, mark changed versions): if you make any changes, you must include a CHANGELOG with all changes and their dates
-->
# ☰ drawers

The **☰** button at the right of the top bar opens a drawer from the right. Click outside it, press **Esc** or **×** to close it. Restarts, stopping a service, reboot, shut down and turning a power device off ask first, and on a printer page they also warn you if that printer is printing. Starting a service or turning a power device on happens straight away (on a printer page, starting a service asks first if it's printing).

## On a printer page

For **that printer**:

- **Restart** &mdash; Klipper, Firmware (MCU reset), Moonraker.
- **Host** &mdash; Reboot or Shut down the printer's host.
- **Power** &mdash; Moonraker power devices (only if the printer has any set up).
- **Services** &mdash; every service Moonraker lists (Klipper, Moonraker…) with its state, **Restart** and **Start/Stop**.

## On the home page

For **Printer Buddy's host** (a printer or a dedicated host):

- **Restart** &mdash; Printer Buddy. Prints keep going on the printers; the page reloads when it's back.
- **Host** &mdash; Reboot or Shut down Printer Buddy's host.
- **Services** &mdash; `printer-buddy` (**Restart** only), and `printer-buddy-streamer` if the camera streamer is on.
- **Updates** &mdash; see [Updates](../updates/index.md).
