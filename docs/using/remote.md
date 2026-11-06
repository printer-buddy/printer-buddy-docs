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

Untick **Chat** if you want a link with no chat box at all. Then **Create link**, and **Copy** it. The list shows each link and when it stops working, and **Turn off** ends one straight away.

The people you send it to see the printer's camera, progress, time left, layer and temperatures. They can't control anything. On the page, the full screen button in the corner of the camera fills the screen (double-click does the same) and the same button leaves it.
## Chat

Everyone watching a printer through a share link can chat. The page has a **Chat** button next to the printer's name: click it to open the chat box, and click it again to close it. Each viewer types a name (it's remembered in their browser) and a message, and everyone watching that printer sees it, whichever of your links they used.

You see the same chat in the **Share** window in Printer Buddy and can write in it as **Owner**. **Clear chat** empties it for everyone. The **Allow chat** tickbox there switches chat on or off for that printer: it's on by default, and turning it off hides the **Chat** button on every share link for that printer and clears the chat.

- A link made with **Chat** unticked never shows the chat button, and the list marks it "no chat".
- Messages are plain text, up to 300 characters, one every 2 seconds per viewer.
- The last 100 messages are kept in memory. They're gone when Printer Buddy restarts.
- A link that's turned off or has expired loses the chat too.

!!! note "Nightly for now"
    Chat is on nightly and comes to stable with the next release. For viewers coming in through remote access, the relay also has to be updated, which happens when its repository is pushed.

## Who can see what

There's no login. Each share link has its own long, secret code, and **anyone with the link can see that printer**, so only send it to people you trust. Links can be set to expire, and you can delete a link any time to stop it working.
