# dotping-dist

Public download point for prebuilt `dotping` binaries. This repo holds **binaries and checksums only**: no source, no tokens, no credentials.
Source lives in the private `vizidrix/viz` repo under `tools/dotping`.

## Current release: tag `dotping-68eb8686`, contents from main `48b3a765`

The tag keeps its old name because the ping text inside dotping links to it. Its assets were replaced on 2026-10-09 at 03:55 PT with the exact binaries deployed from `vizidrix/viz` main at `48b3a76529672f9046fa22eef9970b398f1db5da` (#5945, with #5930, #5934, #5939, #5932, #5940), built with Zig 0.16.0 and `-Doptimize=ReleaseSafe`.

| Asset | Platform | sha256 |
|---|---|---|
| `dotping-linux-x86_64` (**recommended**, same bytes as `-baseline`) | Linux x86_64, any CPU (static, baseline CPU) | `1b640148fb741b4690c7a5f3a1d97d9c78883271d387ab6aeef858ac807e8c44` |
| `dotping-linux-x86_64-baseline` | Linux x86_64, any CPU | `1b640148fb741b4690c7a5f3a1d97d9c78883271d387ab6aeef858ac807e8c44` |
| `dotping-macos-arm64` | macOS Apple Silicon (ad-hoc signed) | `7a0a837bddb2243ea45b7748b20e5514b1a80b8a1a6ec7fcdba3612d7f50de4a` |

Each binary also has its own `<asset>.sha256` file. New in this build: `dotping <slug> gh` (GitHub token issuance). It stays inert until an issuer is pinned: until then it exits 75 and prints no token.

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

