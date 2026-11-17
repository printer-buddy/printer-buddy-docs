<!--
LICENSE

Copyright (C) 2026  sterling motuz <Sterling@dexabyte.ca>

for https://github.com/printer-buddy/printer-buddy

SPDX-License-Identifier: AGPL-3.0-only

Additional term (AGPL-3.0 section 7b, keep author credit): keep this header

Additional term (AGPL-3.0 section 7c, mark changed versions): if you make any changes, you must include a CHANGELOG with all changes and their dates
-->
# Reinstall, back up and uninstall

Everything here is in the installer menu: run `./install.sh` in the Printer Buddy folder.

## Reinstall

**1) Reinstall** runs the whole install again with your current setup. Your printers and settings are kept: the installer never touches `data/`, and in `printer-buddy.env` it only writes your setup choices and the port.

Use it if something got broken or after changing a lot by hand.

## Back up and restore

**4) Backup / restore data**

- **Back up** copies `data/` (your printers, layouts, timelapses, AI photos…) and `printer-buddy.env` into `backups/<date-time>/`.
- **Restore** lists your backups, stops Printer Buddy, puts the chosen one back and starts it again. It replaces your current printers and settings, so it asks first.

!!! tip
    Make a backup before big changes, and copy the `backups/` folder somewhere else now and then.

## Uninstall

**6) Uninstall** first asks **Stop and remove the Printer Buddy service?**, then:

- removes the service and its entry in Moonraker's service list
- asks whether to also remove the **camera streamer**, if it's installed (cameras it serves will stop)
- removes the **share-link tunnel**, if one is set up (it asks first)
- removes Printer Buddy's root helper and its sudo rule
- asks, one at a time, whether to also delete the Python environment (`.venv`) and your printers and settings (`data/`). Make a backup first if you're unsure.

System packages it may have installed (ffmpeg, cloudflared, ustreamer, go2rtc) are kept, since other programs can use them. The Printer Buddy folder itself stays; delete it by hand if you want it gone completely.
