# `deploy/` — Hosting-Vorlagen

Skeleton. Wird in Folgewelle „Bootstrap" befüllt:

- `caddy/Caddyfile.example` — Reverse-Proxy für `med.example.com`
- `systemd/*.service` — Linux-Server-Targets
- `launchd/*.plist` — macOS-User-LaunchAgents für Praxis-Hosts
  (Mac-Studio, Cluster-Mini-XX)
- `mkcert-setup.sh` — lokale CA für LAN-TLS (Praxisnetz-Szenario)

Die meisten Vorlagen existieren in vorgereifter Form bereits in
`Cortex-Web/sites/workforce-time/deploy/` und werden hier
zusammengefasst + um die anderen Apps erweitert.
