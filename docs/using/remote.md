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

## Who can see what

There's no login. Each share link has its own long, secret code, and **anyone with the link can see that printer**, so only send it to people you trust. Links can be set to expire, and you can delete a link any time to stop it working.
