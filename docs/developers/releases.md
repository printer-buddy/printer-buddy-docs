# Releases

## Parts

Each part repo (UI, notify, streamer, timelapse) has a **release** workflow that publishes into the main repo. Run it from **Actions → release → Run workflow**, on the repo's default branch. The form asks:

| Box | What it does |
|---|---|
| **What to publish** | **stable** or **nightly** |
| **Version** | Stable only. Leave it blank for the next version, or type one like `1.2.5`. A version that already exists rolls `main` back to it |
| **When the version is blank, raise the last one by** | `x.x.0 -> x.x.1` (a fix), `x.0.0 -> x.1.0` (a new feature) or `0.0.0 -> 1.0.0` (a big change) |
| **Test run** | Does everything except publish, and shows the version and the notes in the run summary |

- **Nightly** &mdash; built every day at 06:00 UTC (only if the part has a new commit), as `<part>-nightly`. Choosing **nightly** by hand rebuilds it right away.
- **Stable** &mdash; checks the code, works out the next version from the last `v` tag, and asks GitHub Copilot to write the release notes from the commits. If Copilot fails it uses the plain list of commit messages. It then moves `main` to match the default branch, tags the repo `vX.Y.Z`, and publishes `<part>-vX.Y.Z` into the main repo and `vX.Y.Z` in the part's own repo.

The workflows publish into the main repo with the `MAIN_REPO_TOKEN` secret. The organization only accepts fine-grained tokens that last 366 days or less, so make a new one before it runs out.

### needs.txt

If a part needs a minimum version of another part, add `needs.txt` to its repo, one per line:

```
streamer v1.4
```

Updates are held back ("Waiting") until that's met.

## Core

Run **Actions → release → Run workflow** from `nightly`. It has the same version, raise-by and **Test run** boxes as the parts, but no **What to publish** box, because core has no nightly release: nightly installs follow the `nightly` branch itself.

It checks the code (compiles the Python and checks the shell scripts), moves `main` to match `nightly`, publishes the release `core-vX.Y.Z` with Copilot-written notes (the plain commit list is the fallback), and then rebuilds `updates.txt`. A version that already exists rolls `main` back to it instead. Stable installs follow `main`.

## AI models

`export.py --release` in the AI repo publishes `ai-<kind>-vX` and starts the **ai stats** workflow, which tests the models and adds a **Model check** section to the release notes.

## updates.txt

The **updates list** workflow rebuilds `updates.txt` from all releases whenever one is published, and uploads it to the `updates` release. Printer Buddy reads it to know what's newest.
