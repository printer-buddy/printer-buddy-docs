# Reinstall, back up and uninstall

Everything here is in the installer menu: run `./install.sh` in the Printer Buddy folder.

## Reinstall

**1) Reinstall** runs the whole install again with your current setup. Your printers and settings are kept &mdash; they live in `data/` and `printer-buddy.env`, which the installer never overwrites.

Use it if something got broken or after changing a lot by hand.

## Back up and restore

**4) Backup / restore data**

- **Back up** copies `data/` (your printers, layouts, timelapses, AI photos…) and `printer-buddy.env` into `backups/<date-time>/`.
- **Restore** lists your backups, stops Printer Buddy, puts the chosen one back and starts it again. It replaces your current printers and settings, so it asks first.

!!! tip
    Make a backup before big changes, and copy the `backups/` folder somewhere else now and then.

## Uninstall

**6) Uninstall** stops and removes the Printer Buddy service. It then asks, one at a time, whether to also delete:

- the Python environment (`.venv`)
- your printers and settings (`data/`) &mdash; make a backup first if you're unsure

The Printer Buddy folder itself stays; delete it by hand if you want it gone completely.
