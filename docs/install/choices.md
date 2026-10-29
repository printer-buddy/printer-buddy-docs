# Install choices

The installer asks these when you install, and you can change them later with **2) Change setup**. They're saved in `printer-buddy.env` in the Printer Buddy folder.

| Choice | Options (first = default) |
|---|---|
| Interface | advanced (basic is coming soon) |
| AI detection | off, basic, heavy |
| Video | snapshots, live, timelapse |
| Notifications | basic, advanced |
| Remote access | off, on |
| Camera streamer | off, light, basic, advanced |
| Release channel | stable, nightly |

## Interface

- **advanced** &mdash; dashboard, Quick View, each printer's status page, plus Control, Console, Files, History, list view and printer groups.
- **basic** &mdash; coming soon. It shows greyed out in the menu and can't be picked yet.

## AI detection

- **off** &mdash; no failure detection.
- **basic** &mdash; light model that runs on a Pi.
- **heavy** &mdash; bigger, more accurate model; needs a strong PC or a GPU.

See [AI failure detection](../using/ai.md).

## Video

- **snapshots** &mdash; camera pictures, refreshed every few seconds.
- **live** &mdash; smooth live stream.
- **timelapse** &mdash; live stream plus a timelapse of every print (installs `ffmpeg`).

## Notifications

- **basic** &mdash; ntfy or Discord when prints start, pause, finish or fail.
- **advanced** &mdash; basic plus Telegram, Pushover and email, and progress updates.

## Remote access

- **off** &mdash; only reachable on your home network.
- **on** &mdash; share links that work from anywhere. See [Remote access](../using/remote.md).

## Camera streamer

In **2) Change setup** pick a level, then say where the camera is plugged in (this box or the printer):

- **off** &mdash; streamer not installed.
- **light** &mdash; USB cameras, MJPEG (mjpg-streamer).
- **basic** &mdash; USB cameras, MJPEG (ustreamer).
- **advanced** &mdash; everything above, plus Pi cameras, network cameras (RTSP / IP) and WebRTC (go2rtc); needs more CPU.

Any number of cameras at every level. For network cameras on this box, put each address as `device:` in `data/streamer.conf` after the install.

If the camera is on the printer, the installer shows how to install the streamer there. See [Camera streamer](../using/camera-streamer.md#on-the-printer).

## Release channel

- **stable** &mdash; tested releases.
- **nightly** &mdash; the newest builds, may have bugs.

You can also put single parts on nightly &mdash; see [Dev/beta builds](../updates/dev-builds.md).

## Setting them without the menu

Every choice has a command-line flag:

```bash
./install.sh --ui advanced --ai basic --video timelapse --stream basic
```
