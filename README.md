# Skipper — Codemagic trigger repo

Small helper repo used **only as a build trigger** on Codemagic, so we can test Skipper on a
real Apple Silicon Mac (M2/M4) over VNC. Nothing is compiled here — the build is downloaded
prebuilt and just launched.

## Phase 0 — verify Codemagic + VNC
`codemagic.yaml` currently defines the `vnc-smoke-test` workflow, which just boots the Mac and
keeps it alive so we can connect via VNC and confirm the whole path works.

## Phase 1 — Skipper import/export (added later)
- download the Apple Silicon Skipper build (`curl` from our server),
- unpack and launch it,
- over VNC, import a test model and export the output,
- exported files are collected as `artifacts:` for download.

## Connecting to Codemagic (manual URL / "Other")
1. Codemagic -> Add application -> **Other** (connect via URL).
2. Enter the repository URL: `https://github.com/Atlantic18/SkipperArmTest.git` (public, no key needed).
3. Start a build manually and connect over VNC.
