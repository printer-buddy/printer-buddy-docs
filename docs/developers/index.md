<!--
LICENSE

Copyright (C) 2026  sterling motuz <Sterling@dexabyte.ca>

for https://github.com/printer-buddy/printer-buddy

SPDX-License-Identifier: AGPL-3.0-only

Additional term (AGPL-3.0 section 7b, keep author credit): keep this header

Additional term (AGPL-3.0 section 7c, mark changed versions): if you make any changes, you must include a CHANGELOG with all changes and their dates
-->
# Developers

## Repos

| Repo | What's in it |
|---|---|
| [printer-buddy](https://github.com/printer-buddy/printer-buddy) | Core app, installer, AI runtime; every part's releases are published here too |
| [print-buddy-ui](https://github.com/printer-buddy/print-buddy-ui) | The web interface |
| [print-buddy-notify](https://github.com/printer-buddy/print-buddy-notify) | Notifications |
| [print-buddy-timelapse](https://github.com/printer-buddy/print-buddy-timelapse) | Timelapses |
| [print-buddy-streamer](https://github.com/printer-buddy/print-buddy-streamer) | Camera streamer |
| [print-buddy-relay](https://github.com/printer-buddy/print-buddy-relay) | Cloudflare worker for remote access |
| [solo-print-buddy-ai](https://github.com/printer-buddy/solo-print-buddy-ai) | The stand-alone AI that runs on a Klipper printer by itself, without the rest of Printer Buddy |
| [printer-buddy-docs](https://github.com/printer-buddy/printer-buddy-docs) | These docs |

The installer downloads the parts into the main checkout: `ui/`, `app/core/notify.py`, `app/media/timelapse.py` and `streamer/` (all gitignored).

## Branches

- **nightly** &mdash; where development happens, in the core, UI, notify, streamer, timelapse and solo AI repos. It's the default branch in all of them except solo AI.
- **main** &mdash; stable. The release workflow moves it forward when a version is released, so don't commit to it. The relay and docs repos only have `main`.

## Endpoints for other tools

| Address | What it gives |
|---|---|
| `/metrics` | Prometheus text: each printer's connection, ready, printing and paused state, progress, print time, time left, and every heater and sensor temperature and target |
| `/api/stats?days=30` | Every printer's print jobs since that many days ago (`0` = all), as JSON |

Like the rest of the app, they have no login.

## Licence

Printer Buddy is licensed under the GNU Affero General Public License v3.0 only (AGPL-3.0-only), with two extra terms under the licence's section 7. Each repo has the licence in `LICENSE` and the terms in `NOTICE`:

- **Keep the header.** Every file starts with a licence header that credits Printer Buddy. Keep it.
- **Keep a CHANGELOG.** If you change anything, include a CHANGELOG with all your changes and their dates.

`NOTICE` also explains how we read these terms (credit for files that have changed a lot, credit for the AI models, and how contributors can ask for their work to be removed) and that the Printer Buddy name and logo aren't covered by the licence. Bundled code from other projects keeps its own licence; each `NOTICE` lists it.

## Running it locally

```bash
git clone https://github.com/printer-buddy/printer-buddy.git
cd printer-buddy
python3 app/core/updater.py parts      # download the parts
python3 -m venv .venv && .venv/bin/pip install -r requirements/core.txt
.venv/bin/uvicorn app.main:app --port 8080
```
