# dotping-dist

Public download point for prebuilt `dotping` binaries. This repo holds **binaries and checksums only**: no source, no tokens, no credentials.
Source lives in the private `vizidrix/viz` repo under `tools/dotping`.

## Current release: tag `dotping-68eb8686`, contents from main `981647dc`

The tag keeps its old name because the ping text inside dotping links to it. Its assets were replaced on 2026-10-09 at 02:40 PT with the exact binaries deployed from `vizidrix/viz` main at `981647dc7b3a6a32fa0c238bf4ec236dd6f8221b` (#5921, #5925, #5928), built with Zig 0.16.0 and `-Doptimize=ReleaseSafe`.

| Asset | Platform | sha256 |
|---|---|---|
| `dotping-linux-x86_64` (**recommended**, same bytes as `-baseline`) | Linux x86_64, any CPU (static, baseline CPU) | `0f0fc1967889eec5fe3136e7b0c282988184d7e188bd6b9278c874e2ba97e262` |
| `dotping-linux-x86_64-baseline` | Linux x86_64, any CPU | `0f0fc1967889eec5fe3136e7b0c282988184d7e188bd6b9278c874e2ba97e262` |
| `dotping-macos-arm64` | macOS Apple Silicon (ad-hoc signed) | `9ce0dd4b48fc52b572b9042b39dedebac554a7dbfa391b77346c551c1330b739` |

Each binary also has its own `<asset>.sha256` file. The old AVX-512 `dotping-linux-x86_64-native` asset was removed. If you downloaded before 02:40 PT Oct 9, download again: the new build fixes `status` dying with `registry.json: no apps`.

## Anonymous download (no GitHub sign-in needed)

Linux x86_64:

```sh
B=https://github.com/vizidrix/dotping-dist/releases/download/dotping-68eb8686
curl -fL -o dotping-linux-x86_64 "$B/dotping-linux-x86_64"
curl -fL -o SHA256SUMS "$B/SHA256SUMS"
sha256sum -c --ignore-missing SHA256SUMS      # must print: dotping-linux-x86_64: OK
chmod +x dotping-linux-x86_64
```

macOS arm64:

```sh
B=https://github.com/vizidrix/dotping-dist/releases/download/dotping-68eb8686
curl -fL -o dotping-macos-arm64 "$B/dotping-macos-arm64"
curl -fL -o SHA256SUMS "$B/SHA256SUMS"
shasum -a 256 -c --ignore-missing SHA256SUMS   # or: sha256sum -c --ignore-missing SHA256SUMS
chmod +x dotping-macos-arm64
```

Only run the binary if the checksum line prints `OK`. Use your own sealed handoff (DOTKEY / KEYOK / DOTSEAL) for credentials; nothing secret ships here.

