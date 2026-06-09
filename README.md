# andmyhouse-beta

Public **release host** for the And My House beta. This repo holds **no source** —
just the tester-facing artifacts, so beta testers don't need access to the private
app repo.

Two ways to test:

- **Android (APK)** — signed APK on GitHub Releases. No GitHub account needed.
  - Stable download: `https://github.com/nathanrcast/andmyhouse-beta/releases/latest/download/andmyhouse.apk`
- **Docker (self-host the server)** — for technical testers. Compose + env + setup in
  [`docker/`](docker/). The image (`ghcr.io/nathanrcast/andmyhouse:beta`) is **private**
  during beta, so this path needs a GitHub account and a one-time access grant.

Tester-facing page for both: **https://andmyhouse.app/beta**

The app itself lives in the private `andmyhouse` repo. Cutting a new beta is
documented there: `docs/beta-release.md` (Android) and `docs/docker-beta.md` (Docker).
