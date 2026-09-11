# scoop-hawser

The [Scoop](https://scoop.sh) bucket for **[Hawser](https://github.com/hawserhq/hawser)** —
the upstream open source Docker Engine on Windows via WSL2. No licence fees, no
Electron.

```powershell
scoop bucket add hawser https://github.com/hawserhq/scoop-hawser
scoop install hawser
```

## Status

**No manifest yet.** This bucket exists so the name is claimed under the
`hawserhq` org; the manifest lands when Hawser has signed release binaries.

Until then, install Hawser from the
[release zip](https://github.com/hawserhq/hawser/releases) and verify it against
the published `SHA256SUMS`. Binaries are not yet signed, so SmartScreen will
warn — that is what the signing work is for, and why this bucket is empty rather
than pointing at an unsigned build.

Watch [hawserhq/hawser#77](https://github.com/hawserhq/hawser/issues/77) for
progress on signing and distribution.

## What goes here

One manifest per app, in `bucket/`, as Scoop expects:

```
bucket/hawser.json
```

Every manifest pins an exact version and its SHA256. Hawser pins every upstream
byte it ships; its own distribution is held to the same rule, so nothing here
will ever resolve "latest" at install time.

## Issues

Bugs in Hawser itself belong in
[hawserhq/hawser](https://github.com/hawserhq/hawser/issues). Open an issue here
only for packaging problems — a bad manifest, a checksum mismatch, a broken
`scoop update`.
