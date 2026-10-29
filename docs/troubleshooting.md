# Troubleshooting

## A printer shows offline

- Check the printer is on and its Moonraker is running (open Fluidd/Mainsail on it).
- Check Printer Buddy's host can reach it: same network, right IP and port (usually 7125).
- If Moonraker has login turned on, the printer needs its **API key** in Printer Buddy.

## Klipper errors

The red banner on the printer page shows Klipper's error. Fix what it says (often a typo in `printer.cfg`), then press **Restart**. If Klipper isn't connected at all, try **Restart service**, then look at `klippy.log` (link in the banner).

## An update failed

- The Updates list shows the error. Try again &mdash; a dropped connection is the usual cause.
- If it says to run the installer's Update, do that once: `./install.sh` → **3) Update**.
- Still stuck? Reset the code to the latest release and update again:

```bash
cd printer-buddy
git fetch origin
git reset --hard origin/$(git branch --show-current)
./update.sh
```

This only resets the code. Your printers and settings in `data/` and `printer-buddy.env` aren't touched.

## Port already in use

Something else took port 8080. Run `./install.sh`, pick **P) Change port** and choose a free one.

## Logs

| Log | Where |
|---|---|
| Printer Buddy | `journalctl -u printer-buddy -f` on Printer Buddy's host, or **5) Show logs** in the installer |
| Klipper | `klippy.log` &mdash; link in the error banner |
| Moonraker | `moonraker.log` &mdash; link in the warnings banner |
