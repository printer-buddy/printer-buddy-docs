<!--
LICENSE

Copyright (C) 2026  sterling motuz <Sterling@dexabyte.ca>

for https://github.com/printer-buddy/printer-buddy

SPDX-License-Identifier: AGPL-3.0-only

Additional term (AGPL-3.0 section 7b, keep author credit): keep this header

Additional term (AGPL-3.0 section 7c, mark changed versions): if you make any changes, you must include a CHANGELOG with all changes and their dates
-->
# Third-party apps

Apps can send labelled printer photos to help train the Printer Buddy AI. Each app gets 50 box IDs to send them with.
App box IDs only send photos: they can't share a printer or be registered with `/register`.

## Get your box IDs

1. In the Printer Buddy Discord, in **#register**, run `/register-app name:yourapp`.
   The name is 2 to 40 letters, numbers, `-` or `_`. The reply says your request is waiting for an admin.
2. Once an admin approves it, run `/register-app name:yourapp` again. You get:
    - a file, `yourapp-ids.csv`, with one `id,key` line per box ID;
    - your **app key**.

Only you can see the replies, and only the person who asked for the app can get the file.

You can also get the same IDs and keys with the app key:

```bash
curl -s -X POST https://www.printerbuddy.stream/api/app/ids -H 'content-type: application/json' \
  -d '{"name": "yourapp", "key": "<app key>"}'
```

Answer: `{"ids": [{"id": "...", "key": "..."}, ...]}`, the same 50 every time.

**Keep the file and the app key private.** Anyone who has them can send photos as your app.

## Send a photo

`POST https://www.printerbuddy.stream/api/contribute` with a JSON body:

| Field | Required | Value |
|---|---|---|
| `id` | yes | one of your box IDs |
| `key` | yes | that box ID's key |
| `label` | yes | `ok`, `spaghetti`, `warping`, `first_layer`, `failure`, `stringing` or `blob` |
| `image` | yes | the photo as a base64 JPEG, 1 KB to 1 MB |
| `source` | no | `alert_yes`, `alert_no`, `print_ok`, `print_failed` or `user` (default `user`) |
| `verdict` | no | `right`, `false_alarm` or `missed` |
| `severity` | no | a whole number from 1 to 10 |
| `meta` | no | an object; `meta.model` (1 to 40 letters, numbers, `.`, `_` or `-`) and `meta.score` (a number) are used |

```bash
{ printf '{"id": "<box ID>", "key": "<box key>", "label": "ok", "image": "'; base64 -w0 photo.jpg; printf '"}'; } |
  curl -s -X POST https://www.printerbuddy.stream/api/contribute -H 'content-type: application/json' --data-binary @-
```

## Answers

| Status | Body | Meaning |
|---|---|---|
| 201 | `{"ok": true, "path": "incoming/<label>/..."}` | saved |
| 400 | `{"error": "label must be one of: ..."}`, `"Bad source"`, `"image must be base64"`, `"image must be 1 KB to 1 MB"`, `"image must be a JPEG"`, `"Bad Printer Buddy ID"`, `"Bad request"` | fix the request |
| 403 | `{"error": "This box ID and key don't match. ..."}` | wrong ID or key |
| 403 | `{"error": "The app this box ID came from has been turned off by Printer Buddy."}` | your app was blocked |
| 429 | `{"error": "Daily photo limit reached. The rest will be sent tomorrow."}` | try again tomorrow |
| 502 / 503 | `{"error": "..."}` | the server is busy or updating; try again later |

## Limits (same as a standard box)

- 50 photos per box ID per day.
- 200 photos per IP address per day.
