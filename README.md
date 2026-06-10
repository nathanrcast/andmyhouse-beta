# andmyhouse-beta

Public **release host** for the And My House beta. This repo holds **no source** —
just the tester-facing artifacts, so beta testers don't need access to the private
app repo.

Three ways to test:

- **Android (APK)** — signed APK on GitHub Releases. No GitHub account needed.
  - Stable download: `https://github.com/nathanrcast/andmyhouse-beta/releases/latest/download/andmyhouse.apk`
- **Raspberry Pi (flashable image)** — SD-card image with the hub preinstalled
  (Pi Zero 2 W / 3 / 4 / 5). No GitHub account needed. Lives on the rolling
  [`pi-latest`](../../releases/tag/pi-latest) prerelease — prerelease on purpose,
  so `releases/latest` keeps resolving to the APK.
  - Stable download: `https://github.com/nathanrcast/andmyhouse-beta/releases/download/pi-latest/andmyhouse-pi.img.xz`
- **Docker (self-host the server)** — for technical testers. Compose + env + setup in
  [`docker/`](docker/). The image (`ghcr.io/nathanrcast/andmyhouse:beta`) is **private**
  during beta, so this path needs a GitHub account and a one-time access grant.

Tester-facing page for all three: **https://andmyhouse.app/beta**

The app itself lives in the private `andmyhouse` repo. Cutting a new beta is
documented there: `docs/beta-release.md` (Android), `docs/pi-beta.md` (Pi image),
and `docs/docker-beta.md` (Docker).
