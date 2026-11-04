# Camera streamer

Printer Buddy's camera streamer is a replacement for crowsnest and camera-streamer. It streams your USB, Pi and network cameras and is set up, updated and controlled from Printer Buddy like every other part.

## Tiers

| Tier | What it does |
|---|---|
| **off** | Streamer not installed |
| **light** | USB cameras, MJPEG (mjpg-streamer) |
| **basic** | USB cameras, MJPEG (ustreamer) |
| **advanced** | Everything above, plus Pi cameras, network cameras (RTSP / IP) and WebRTC (go2rtc); needs more CPU |

Any number of cameras at every level.

Pick it with **Camera streamer** in the installer's **2) Change setup** (a level, then where the camera is plugged in, see [Install choices](../install/choices.md#camera-streamer)), or switch tiers in the **Updates** list (home page ☰). It runs as its own service, `printer-buddy-streamer`, which you can restart or stop from the home page ☰ drawer.

## Cameras

Each printer's cameras come from Moonraker. On a printer page, the camera's settings let you add or edit Moonraker cameras, flip or rotate them and pick the **main camera** &mdash; the one the AI and timelapses use.

## On the printer

If the camera is plugged into the printer itself, run the streamer there. In **Change setup** pick **Camera streamer**, a level, then **The printer**. The installer offers two ways to install it:

- **Copy and paste** &mdash; it shows one command to run over SSH on the printer, for example `curl -fsSL https://raw.githubusercontent.com/printer-buddy/print-buddy-streamer/main/install-printer.sh | bash -s -- basic`.
- **Guided SSH** &mdash; it asks for the printer's IP and login user (default `pi`) and runs the same command over SSH. SSH asks for the printer's password; nothing is saved.

For **advanced** it also asks for network camera addresses and adds them to the command.

On the printer, the command installs what the level needs, downloads the streamer to `~/print-buddy-streamer`, starts it as the `printer-buddy-streamer` service and adds the cameras to the printer's Moonraker. It's also added to Moonraker's update manager, so you can update and restart it from Fluidd or Mainsail. Its settings are in `printer_data/config/print-buddy-streamer.conf`.

Printer Buddy then sees the cameras through Moonraker like any other camera.

!!! note
    The printer needs Debian-based Linux with `apt` and Python 3.9 or newer. A printer without `apt` can't run it; use the printer's own camera service there.

!!! warning "New"
    The printer install and the **light** level are new and have not been tested on a real printer yet.

Cameras start at port 8081 so they don't clash with Printer Buddy on 8080.
