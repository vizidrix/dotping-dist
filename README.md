# dotping-dist

Public download point for prebuilt `dotping` binaries. This repo holds **binaries and checksums only**: no source, no tokens, no credentials.
Source lives in the private `vizidrix/viz` repo under `tools/dotping`.

## Current release: `dotping-68eb8686`

Built from `vizidrix/viz` main at `68eb8686ad7350539dac6759e21f605df06b628e` (#5899), Zig 0.16.0, `-Doptimize=ReleaseSafe`.

| Asset | Platform | sha256 |
|---|---|---|
| `dotping-linux-x86_64` | Linux x86_64 | `2cada44c2a4696498e1ce0f9f1ca9c83464cec45262d2f63fd727ca5e14bda27` |
| `dotping-macos-arm64` | macOS Apple Silicon (ad-hoc signed) | `b51643cf51797372a9aa0229e5f57200ea1c7d96b017408e0c227ef2ea910395` |

## Anonymous download (no GitHub sign-in needed)

Linux x86_64:

```sh
B=https://github.com/vizidrix/dotping-dist/releases/download/dotping-68eb8686
curl -fL -o dotping-linux-x86_64 "$B/dotping-linux-x86_64"
curl -fL -o SHA256SUMS "$B/SHA256SUMS"
sha256sum -c --ignore-missing SHA256SUMS
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

Note: the ping/roll-call text inside this build still says "build dotping ... from main at 20efb129". That pin is stale: build from current `main`.
