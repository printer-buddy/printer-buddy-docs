# Updater and root helper

## updater.py

`app/core/updater.py` does every update. The installer, `update.sh` and the Updates list all call it.

```bash
python3 app/core/updater.py update     # core, then everything below
python3 app/core/updater.py parts      # download the parts
python3 app/core/updater.py ai         # AI libraries and model
python3 app/core/updater.py streamer   # download and set up the camera streamer
python3 app/core/updater.py packages   # system packages the chosen features need
```

It only uses Python's standard library, so it works before the virtual environment exists.

## Root helper

`tools/root.sh` is installed as `/usr/local/lib/printer-buddy/root.sh`, with a sudo rule that lets the Printer Buddy user run **only that script** without a password. Its jobs:

| Job | What it does |
|---|---|
| `pkg <name>` | Install an apt package, only from a fixed list (ffmpeg, v4l-utils, ustreamer, python3-venv) |
| `deps`, `unit`, `enable`, `restart`, `disable` | Set up and control the camera streamer service |
| `reboot`, `shutdown` | Reboot or power off Printer Buddy's host |

The installer updates the helper; the app can't change it.

## Channels

| Setting | Meaning |
|---|---|
| `PB_CHANNEL` | `stable` or `nightly` for everything |
| `PB_NIGHTLY` | Parts on dev/beta builds, e.g. `ui,streamer` |

Core follows the `main` branch on stable and `nightly` on nightly.
