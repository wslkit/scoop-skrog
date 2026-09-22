# scoop-skrog

The [Scoop](https://scoop.sh) bucket for **[Skrog](https://github.com/wslkit/skrog)** —
the upstream open source Docker Engine on Windows via WSL2. No licence fees, no
Electron.

```powershell
scoop bucket add skrog https://github.com/wslkit/scoop-skrog
scoop install skrog
```

That puts the `skrog` command on PATH and provisions nothing. Then:

```powershell
skrog install                  # the engine: a checksum-verified rootfs in its own WSL2 distro
skrog start                    # the bridge
docker run --rm hello-world
```

You also need a `docker` command, and Skrog does not install one by default —
Docker Desktop's works, or `skrog cli install` fetches the upstream tools.

## Status

**Skrog 0.5.1 is in the bucket.**

This page used to say the manifest was waiting on signed release binaries. That
was wrong, and it held the bucket empty for no reason: Scoop installs unsigned
archives as a matter of course — that is essentially what Scoop *is* — and it
asks for no elevation and no Authenticode signature. Nothing here ever depended
on the signing work.

What signing would change is SmartScreen warning on first run of `skrog.exe`.
That part is real and still open:
[wslkit/skrog#77](https://github.com/wslkit/skrog/issues/77).

Every release also carries SLSA build provenance and a cosign-signed
`SHA256SUMS`, which tie the artifact to a workflow run and a commit — two checks
an Authenticode signature does not give you. See
[verifying a download](https://wslkit.github.io/skrog/security/).

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
