# Bambu Lab printers

Printer Buddy runs Bambu Lab printers **fully locally**, over your own network. It doesn't use Bambu's cloud. Its built-in bridge talks to the printer directly and shows it with the same pages as a Klipper printer.

**Models:** X1 Carbon, X1, X1E, P1P, P1S, P2S, A1 mini, A1, A2L, X2D, H2C, H2D, H2D Pro and H2S.

## What you get

- **Live status**: state, file, progress, layer, time left, nozzle, bed and chamber temperatures, speed and fans.
- **Camera**: the printer's own camera, live. Printer Buddy only pulls it while someone is watching, and reconnects by itself if it stalls.
- **Print control**: pause, resume and stop.
- **Start prints** from the Jobs list: `.3mf` plates and G-code files. For a `.3mf`, it matches the file's filaments to your AMS slots by colour.
- **Files** on the printer's storage: list, upload, rename and delete.
- **AMS**: every slot with its colour and material, what's loaded, and load or unload from the MMU / AMS card.
- **Speed levels**: silent, standard, sport and ludicrous.
- **Chamber light** on and off, and **temperatures** for the nozzle (each nozzle on the H2D and other dual-nozzle models) and the bed.
- **Fans**: part cooling, auxiliary and chamber, where the model has them.
- **Console** for G-code.
- **Errors in plain words.** "The nozzle is clogged. (0300_4006)" instead of a number, and the printer's own notices (HMS), such as "The AMS filament ran out", as warnings on the page.
- **History**, [AI failure detection](../using/ai.md), [notifications](../using/notifications.md), [timelapses](../using/timelapse.md) and [share links](../using/remote.md), like any other printer.

## What it needs

- **LAN only mode** and **Developer mode** turned on in the printer's settings. Without them the printer refuses commands from anything but Bambu's own apps.
- The printer's **IP address**, **serial number** and **access code** (on the printer's screen).
- On X1 and H2 models, **LAN liveview** on, for the camera.
- Printer Buddy on a separate host on the same network (a Bambu printer can't run it).

## What it can't do

Klipper-only parts, such as macros, the bed mesh, config files and Klipper's system pages, don't apply to Bambu printers.

[All features](../features.md)
