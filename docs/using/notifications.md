<!--
LICENSE

Copyright (C) 2026  sterling motuz <Sterling@dexabyte.ca>

for https://github.com/printer-buddy/printer-buddy

SPDX-License-Identifier: AGPL-3.0-only

Additional term (AGPL-3.0 section 7b, keep author credit): keep this header

Additional term (AGPL-3.0 section 7c, mark changed versions): if you make any changes, you must include a CHANGELOG with all changes and their dates
-->
# Notifications

Printer Buddy can message you when something happens on a printer.

## Services

| Service | Needs |
|---|---|
| ntfy | basic |
| Discord | basic |
| Telegram | advanced |
| Pushover | advanced |
| Email | advanced |

The advanced ones need **Notifications = advanced** in the installer.

## Events

Started, paused, resumed, finished, failed, cancelled, went offline mid-print and Klipper shutdown &mdash; plus AI alerts. With advanced notifications you can also get **progress updates** (for example at 25% and 50%).

## Setting them up

1. Open the home page's **Settings → Alerts**, or a printer's **Settings** tab under **Notifications**.
2. Fill in the services you want to use (ntfy topic URL, Discord webhook URL, Telegram bot token and chat ID…). Tick **Attach a webcam snapshot** to get a picture with each message.
3. Tick the events you want.
4. **Save**, then **Send test** (or a service's own button, such as **Send test to Telegram**) to check it works.

To silence one printer, open the menu on its card and switch **Notifications** off.
