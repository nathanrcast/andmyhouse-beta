# And My House — Docker beta (self-host)

Run the And My House **server** yourself with Docker, for technical testers who'd
rather self-host than use the Android app. Everything runs locally — one container,
one SQLite database on a volume, no external services.

The beta image is **private** while in beta, so you need a GitHub account and a
one-time access grant. The walkthrough also lives at
**https://andmyhouse.app/beta**.

## Requirements

- Docker + Docker Compose (Docker Desktop, or `docker` + the compose plugin)
- A GitHub account
- amd64 (x86) or arm64 (Raspberry Pi 4/5, ARM NAS) — the image is multi-arch

## 1. Request access

Email your **GitHub username** to **beta@andmyhouse.app** (or the contact link on
the `/beta` page). You'll be granted read access to the private image.

## 2. Log in to the registry

Create a GitHub **classic** Personal Access Token with the **`read:packages`** scope
(Settings → Developer settings → Tokens (classic)), then:

```bash
echo YOUR_TOKEN | docker login ghcr.io -u YOUR_GITHUB_USERNAME --password-stdin
```

## 3. Configure and run

```bash
# in an empty folder, alongside this docker-compose.yml:
cp .env.example .env

# generate a secret and put it in .env as ANDMYHOUSE_SECRET_KEY:
python -c "import secrets; print(secrets.token_urlsafe(48))"

docker compose up -d
```

Open **http://localhost:8500** and walk the first-run setup wizard (household name,
members, auth mode). The first launch takes a few seconds.

## Updating

```bash
docker compose pull
docker compose up -d
```

Your data lives in the `andmyhouse_data` Docker volume and survives updates.

## Notes

- `ANDMYHOUSE_SECRET_KEY` is **permanent** — it encrypts stored Google tokens.
  Changing it after setup forces connected Google accounts to reconnect. Set it once.
- Behind a reverse proxy, set `ANDMYHOUSE_BASE_URL` to your public URL.
- Health check: `curl -fsS http://localhost:8500/api/health`.
- Found a bug? Use the **feedback form** on https://andmyhouse.app/beta.
