# Remote access

By default Printer Buddy only works on your home network. Remote access lets you check a printer from anywhere with a **share link**.

## Turning it on

Pick **Remote access = on** in **2) Change setup** and go back. The installer then installs a secure tunnel (`cloudflared`), registers it and starts it.

Turn it **off** again and the installer asks whether to remove the tunnel. Share links stop working from outside once it's removed.

## Share links

Share a printer's view with someone else. Links look like:

```
https://www.printerbuddy.stream/share/user/<your id>/...
```

To make one, open the menu on a printer's card on the dashboard and choose **Share**. It only shows when remote access is on. Pick how long the link works:

- **1 hour**, **1 day** or **7 days**
- **until the print ends** &mdash; only offered while a print is running. The link turns itself off when the print finishes, is cancelled or fails.
- **until I turn it off**

Then **Create link**, and **Copy** it. The list shows each link and when it stops working, and **Turn off** ends one straight away.

The people you send it to see the printer's camera, progress, time left, layer and temperatures. They can't control anything. On the page, the full screen button in the corner of the camera fills the screen (double-click does the same) and the same button leaves it.
## Who can see what

There's no login. Each share link has its own long, secret code, and **anyone with the link can see that printer**, so only send it to people you trust. Links can be set to expire, and you can delete a link any time to stop it working.
