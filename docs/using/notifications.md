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

Started, paused, resumed, finished, failed, cancelled, went offline and Klipper shutdown &mdash; plus AI alerts. With advanced notifications you can also get **progress updates** (for example at 25% and 50%).

## Setting them up

1. Open the home page's **Settings → Alerts**, or a printer's **Settings** tab under **Notifications**.
2. Add a service and fill in its details (ntfy topic, Discord webhook URL…).
3. Tick the events you want.
4. Send a test to check it works.
