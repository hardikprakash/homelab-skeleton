# Homelab Skeleton

A complete Docker Compose-based homelab stack with reverse proxy, media management, file sharing, and monitoring. Powered by Caddy, Jellyfin, *arrs, Immich, Syncthing, Samba, Scrutiny, and more.

---

## Features
- **Caddy**: Automatic HTTPS, reverse proxy, Cloudflare DNS challenge
- **Jellyfin**: Media server
- **Stirling PDF**: PDF tools
- **Radarr/Sonarr/Prowlarr/Overseerr**: Movie, TV, indexer, and request management
- **qBittorrent**: Torrent client
- **Immich**: Photo management with hardware acceleration
- **Syncthing**: File sync
- **Samba**: Windows-compatible file sharing
- **Scrutiny**: Disk health monitoring

---

## Quick Start

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd homelab-skeleton
   ```

2. **Configure environment variables**
   - Copy `.env.example` to `.env` and fill in your values:
     ```bash
     cp .env.example .env
     # Edit .env with your secrets and paths
     ```

3. **Review and customize `docker-compose.yaml`**
   - Adjust volumes, device paths, and service options as needed.

4. **Set up Caddy reverse proxy**
   - Edit `config/caddy/Caddyfile` for your domain and subdomains.
   - Ensure your Cloudflare API token and email are set in `.env`.

5. **Start the stack**
   ```bash
   docker compose up -d
   ```

---

## Accessing Services

| Service         | URL                                 |
|-----------------|-------------------------------------|
| Jellyfin        | https://jellyfin.<your-domain>      |
| Stirling PDF    | https://pdf.<your-domain>           |
| Radarr          | https://radarr.<your-domain>        |
| Sonarr          | https://sonarr.<your-domain>        |
| Prowlarr        | https://prowlarr.<your-domain>      |
| Overseerr       | https://overseerr.<your-domain>     |
| qBittorrent     | https://torrent.<your-domain>       |
| Immich          | https://photos.<your-domain>        |
| Syncthing       | https://sync.<your-domain>          |
| Scrutiny        | https://scrutiny.<your-domain>      |
| Samba           | Windows network share (\\<your-server-ip>\Data) |

---

## Volumes & Data
- Media, file, and config paths are mapped via Docker volumes.
- Change paths in `.env` and `docker-compose.yaml` to suit your storage layout.

---

## Security Notes
- Use strong passwords and secrets in `.env`.
- Restrict access to your homelab from the public internet.
- Keep your system and containers up to date.

---

## Troubleshooting
- Check logs with `docker compose logs <service>`
- Ensure all required environment variables are set
- Verify your DNS records point to your server
- For Caddy/Cloudflare issues, see [Caddy docs](https://caddyserver.com/docs/) and [Cloudflare API docs](https://developers.cloudflare.com/api/)
