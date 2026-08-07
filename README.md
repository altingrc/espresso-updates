# Espresso updates

The update manifest and public downloads for [Espresso](https://github.com/altingrc/espresso),
a macOS menu bar utility that keeps a Mac working through long jobs.

Espresso's source lives in a private repository. This one exists so the app can
reach its own updates: a private repo's release assets are not publicly
downloadable, so an app fetching one would get a 404 and fall back to opening a
browser — which is the manual reinstall the in-app updater exists to avoid.

## latest.json

Served at <https://altingrc.github.io/espresso-updates/latest.json>, which is
the address compiled into the app. Running copies poll it and offer to update
themselves when it names a version newer than their own.

```json
{
  "version": "1.17.2",
  "url": "https://.../Espresso-v1.17.2.dmg",
  "sha256": "..."
}
```

- `version` — without the `v` prefix
- `url` — a direct, public download for the DMG
- `sha256` — checksum of that DMG, verified before anything is installed. The
  update replaces the running application, so this is the only thing standing
  between a bad download and a broken install. Always set it.

## Releasing

Covered by `RELEASING.md` in the main repository. In short: the DMG is attached
to a release here, then `latest.json` is pointed at it.
