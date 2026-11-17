<!--
LICENSE

Copyright (C) 2026  sterling motuz <Sterling@dexabyte.ca>

for https://github.com/printer-buddy/printer-buddy

SPDX-License-Identifier: AGPL-3.0-only

Additional term (AGPL-3.0 section 7b, keep author credit): keep this header

Additional term (AGPL-3.0 section 7c, mark changed versions): if you make any changes, you must include a CHANGELOG with all changes and their dates
-->
# Timelapse

## Turning it on

Pick **Video = timelapse** in the installer. It installs `ffmpeg`, which makes the videos.

## How it records

| Setting | Choices | Default |
|---|---|---|
| Take a picture | every layer, or every few seconds | every layer |
| every (every few seconds) | 5, 10 or 30 seconds between pictures | 10 s |
| Video speed | 15, 25 or 30 frames per second | 25 fps |
| Keep the last | 5, 10, 20, 50 or 100 timelapses per printer | 20 |

A timelapse starts with the print and the video is made when it ends. Prints with fewer than two frames don't make a video.

**Every layer** uses the layer number your slicer puts in the file. If the file doesn't have one, Printer Buddy works the layer out from the nozzle height, and a quick Z-hop doesn't count as a new layer.

If Printer Buddy restarts during a print, that print's timelapse is lost.

## Finding your videos

Open the printer's **Timelapse** tab. It has three panels:

- **Timelapses** &mdash; your videos, to watch, download or delete. They're stored in Printer Buddy's `data/` folder.
- **Timelapse Status** &mdash; whether a timelapse is recording now, and how many pictures it has so far.
- **Timelapse Settings** &mdash; when to take a picture, the video speed and how many to keep, from the table above. Changes apply to all printers from the next print.
