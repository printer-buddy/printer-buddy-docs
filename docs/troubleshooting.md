<!--
LICENSE

Copyright (C) 2026  sterling motuz <Sterling@dexabyte.ca>

for https://github.com/printer-buddy/printer-buddy

SPDX-License-Identifier: AGPL-3.0-only

Additional term (AGPL-3.0 section 7b, keep author credit): keep this header

Additional term (AGPL-3.0 section 7c, mark changed versions): if you make any changes, you must include a CHANGELOG with all changes and their dates
-->
# Troubleshooting

## A printer shows offline

- Check the printer is on and its Moonraker is running (open Fluidd/Mainsail on it).
- Check Printer Buddy's host can reach it: same network, right IP and port (usually 7125).
- If Moonraker has login turned on, the printer needs its **API key** in Printer Buddy.

## Klipper errors

The **Klippy** card at the top of the printer page shows Klipper's error. Fix what it says (often a typo in `printer.cfg`), then press **Restart Klipper** (or **Firmware Restart** for an MCU error). If Klipper isn't connected at all, the card's **Restart Klipper** restarts the Klipper service; then look at `klippy.log` (download button on the card). The card only shows when Klipper has an error or a warning.

## An update failed

- The Updates list shows the error. Try again &mdash; a dropped connection is the usual cause.
- If it says to run `./update.sh`, do that once.
- Still stuck? Reset the code to the latest release and update again:

```bash
cd printer-buddy
git fetch origin
git reset --hard origin/$(git branch --show-current)
./update.sh
```

This only resets the code. Your printers and settings in `data/` and `printer-buddy.env` aren't touched.

## Port already in use

Something else took port 8080. Move Printer Buddy to a free one with `./scripts/port.sh <number>`.

## Logs

| Log | Where |
|---|---|
| Printer Buddy | `journalctl -u printer-buddy -f` on Printer Buddy's host |
| Klipper | `klippy.log` &mdash; **System → System Overview**, or the **Klippy** card when there's an error |
| Moonraker | `moonraker.log` &mdash; **System → System Overview**, or the **Klippy** card when there's an error |
