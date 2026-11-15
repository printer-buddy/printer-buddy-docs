# Releases

## Parts

Each part repo (UI, notify, streamer, timelapse) has a **release** workflow that publishes into the main repo. Run it from **Actions → release → Run workflow**, on the repo's default branch. The form asks:

| Box | What it does |
|---|---|
| **What to publish** | **stable** or **nightly** |
| **Version** | Stable only. Leave it blank for the next version, or type one like `1.2.5`. A version that already exists rolls `main` back to it |
| **When the version is blank, raise the last one by** | `x.x.0 -> x.x.1` (a fix), `x.0.0 -> x.1.0` (a new feature) or `0.0.0 -> 1.0.0` (a big change) |
| **Test run** | Does everything except publish, and shows the version and the notes in the run summary |

- **Nightly** &mdash; built on every push to `nightly`, as `<part>-nightly`. A daily run at 06:00 UTC catches anything missed; it skips if that commit is already built. Choosing **nightly** by hand rebuilds it right away. (Pushing on every commit is set up in the UI repo so far.)
- **Stable** &mdash; checks the code, works out the next version, and asks GitHub Copilot to write the release notes from the commits since the last release. If Copilot fails it uses the plain list of commit messages. It then adds **one commit** to `main` with the default branch's files ("Squashed from nightly@&lt;sha&gt;"), tags that commit `vX.Y.Z`, and publishes `<part>-vX.Y.Z` into the main repo and `vX.Y.Z` in the part's own repo. `main`'s history is one commit per release.

The workflows publish into the main repo with the `MAIN_REPO_TOKEN` secret. The organization only accepts fine-grained tokens that last 366 days or less, so make a new one before it runs out.

Copilot writes the notes with the `COPILOT_TOKEN` secret: a fine-grained token from an account with Copilot, with the **Copilot Requests** permission. Without it the notes fall back to the commit list.

### needs.txt

If a part needs a minimum version of another part, add `needs.txt` to its repo, one per line:

```
streamer v1.4
```

Updates are held back ("Waiting") until that's met.

## Core

Run **Actions → release → Run workflow** from `nightly`. It has the same version, raise-by and **Test run** boxes as the parts, but no **What to publish** box, because core has no nightly release: nightly installs follow the `nightly` branch itself.

It checks the code (compiles the Python and checks the shell scripts), adds one commit to `main` with `nightly`'s files (the same squash as the parts) and publishes the release `core-vX.Y.Z` with Copilot-written notes (the plain commit list is the fallback). A version that already exists rolls `main` back to it instead. Stable installs follow `main`.

## AI models

`export.py --release` in the AI repo publishes `ai-<kind>-vX` and starts the **ai stats** workflow, which tests the models and adds a **Model check** section to the release notes.

## What's newest

Printer Buddy reads the main repo's release list from GitHub to know the newest stable and nightly of each part, and the `needs:` lines in their notes. Publishing a release is all it takes.
