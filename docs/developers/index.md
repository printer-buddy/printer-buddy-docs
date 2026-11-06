# Developers

## Repos

| Repo | What's in it |
|---|---|
| [printer-buddy](https://github.com/printer-buddy/printer-buddy) | Core app, installer, AI runtime; all releases are published here |
| [print-buddy-ui](https://github.com/printer-buddy/print-buddy-ui) | The web interface |
| [print-buddy-notify](https://github.com/printer-buddy/print-buddy-notify) | Notifications |
| [print-buddy-timelapse](https://github.com/printer-buddy/print-buddy-timelapse) | Timelapses |
| [print-buddy-streamer](https://github.com/printer-buddy/print-buddy-streamer) | Camera streamer |
| [print-buddy-relay](https://github.com/printer-buddy/print-buddy-relay) | Cloudflare worker for remote access |
| [printer-buddy-docs](https://github.com/printer-buddy/printer-buddy-docs) | These docs |

The installer downloads the parts into the main checkout: `ui/`, `app/core/notify.py`, `app/media/timelapse.py` and `streamer/` (all gitignored).

## Branches

- **nightly** &mdash; the default branch in the core, UI, notify and streamer repos, where development happens.
- **main** &mdash; stable. The release workflow moves it forward when a version is released, so don't commit to it. The timelapse, relay and docs repos only have `main`.

## Running it locally

```bash
git clone https://github.com/printer-buddy/printer-buddy.git
cd printer-buddy
python3 app/core/updater.py parts      # download the parts
python3 -m venv .venv && .venv/bin/pip install -r requirements.txt
.venv/bin/uvicorn app.main:app --port 8080
```
