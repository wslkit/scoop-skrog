# scoop-skrog

The [Scoop](https://scoop.sh) bucket for **[Skrog](https://github.com/wslkit/skrog)** —
the upstream open source Docker Engine on Windows via WSL2. No licence fees, no
Electron.

```powershell
scoop bucket add skrog https://github.com/wslkit/scoop-skrog
scoop install skrog
```

## Status

**No manifest yet.** This bucket exists so the name is claimed under the
`wslkit` org; the manifest lands when Skrog has signed release binaries.

Until then, install Skrog from the
[release zip](https://github.com/wslkit/skrog/releases) and verify it against
the published `SHA256SUMS`. Binaries are not yet signed, so SmartScreen will
warn — that is what the signing work is for, and why this bucket is empty rather
than pointing at an unsigned build.

Watch [wslkit/skrog#77](https://github.com/wslkit/skrog/issues/77) for progress
on signing and distribution.

## What goes here

One manifest per app, in `bucket/`, as Scoop expects:

```
bucket/skrog.json
```

Every manifest pins an exact version and its SHA256. Skrog pins every upstream
byte it ships; its own distribution is held to the same rule, so nothing here
will ever resolve "latest" at install time.

## Issues

Bugs in Skrog itself belong in
[wslkit/skrog](https://github.com/wslkit/skrog/issues). Open an issue here only
for packaging problems — a bad manifest, a checksum mismatch, a broken
`scoop update`.
