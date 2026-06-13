# Cortex-Med-Web

**OSS-Distribution für Medizin-Tenants** — Schwester-Repo zu
[Cortex-Web](https://github.com/Sanexio/cortex-web), bündelt
Webseite + angedockte Praxis-Apps (Workforce-Time, später weitere) zu
einem reproduzierbaren Setup, das auf jedem Cortex-Knoten via
Bootstrap-Skript verfügbar gemacht wird.

> Status: **Skeleton** (2026-06-13). Apps und Public-Tenant werden in
> folgenden Wellen befüllt.

## Verhältnis zu Cortex-Web

```
Cortex-Web (OSS Framework)
    ↑
    │ konsumiert (Schemas, Adapter, Trunk-Generika)
    │
Cortex-Med-Web (OSS Medizin-Distribution)
    ├── apps/praxis-webseite/   ← Submodule auf Sanexio/praxiszentrum-theme
    ├── apps/workforce-time/    ← Symlink/Klon-Pointer auf Cortex-Web/sites/workforce-time/
    ├── examples/public-tenant/ ← Demo-Praxis "Dr. Mustermann"
    ├── deploy/                 ← Caddyfile, systemd, macOS-LaunchAgents
    └── bootstrap.sh            ← Mac-Knoten-Installation
```

`Cortex-Web` bleibt das generische Framework. `Cortex-Med-Web` ist die
**Medizin-Vertikale** — sie weiß, dass „Praxis", „MFA",
„Sprechstunde" existieren, und liefert UI/Apps für genau diese Domäne.

## Tenant-Modi

Der Code ist immer identisch. Die ENV `CORTEX_TENANT_DIR` entscheidet
über die Daten:

| Modus               | `CORTEX_TENANT_DIR`                                       | Anwendung                          |
|---------------------|-----------------------------------------------------------|------------------------------------|
| **Public-Demo**     | `Cortex-Med-Web/examples/public-tenant`                   | Showcase, README-Screenshots, Schulungen, GitHub-Demos. |
| **Praxis-privat**   | `~/Cortex/projects/Sanexio-Tenant` (oder anderer privater Tenant) | Echtbetrieb mit echten Mitarbeitenden und Patientendaten. |

Damit gibt es **eine Public-Tenant-Variante** für die Außendarstellung
und beliebig viele **Praxis-private** Konfigurationen, die nie das
Cortex-Med-Web-Repo betreten.

## Authoritative Quelle pro App

- **`apps/praxis-webseite/`** — wahrer Ursprung bleibt die Live-Domain
  (`westend-hausarzt.com` auf GoDaddy) bzw. die lokale Local-Flywheel
  Staging-Site auf `Cluster-Mini-02`. Das Submodule hier wird
  **nachgezogen**, nicht authoritativ gepflegt. Edits laufen im
  Theme-Working-Copy unter
  `~/Local Sites/gpmedicalcenterwestend-…/app/public/wp-content/themes/praxiszentrum/`
  und werden von dort gepusht; das Cortex-Med-Web-Submodule trackt den
  publizierten Stand.
- **`apps/workforce-time/`** — wahrer Ursprung bleibt
  `Cortex-Web/sites/workforce-time/`. Das Bootstrap-Skript stellt einen
  Symlink auf den lokal vorhandenen Cortex-Web-Klon her; bei
  Cortex-Web-Updates ist die App automatisch aktualisiert.

## Bootstrap auf Cortex-Knoten

```bash
git clone git@github.com:Sanexio/cortex-med-web.git ~/Cortex/projects/Cortex-Med-Web
cd ~/Cortex/projects/Cortex-Med-Web
git submodule update --init --recursive
./bootstrap.sh                       # legt Symlinks + launchd-Plists an
```

`bootstrap.sh` (Skeleton in Folgewelle) leistet:
- Symlink `apps/workforce-time/` → `~/Cortex/projects/Cortex-Web/sites/workforce-time/`
- macOS-LaunchAgents in `~/Library/LaunchAgents/` registrieren
- Default-Tenant auf Public, wenn kein privater Tenant gefunden wird
- `cortex-harness`-Layer-Registrierung, sodass das Dashboard den Status sieht

## Roadmap

1. **Welle Skeleton (heute)** — Repo, README, Public-Tenant-Stub,
   praxis-webseite-Submodule.
2. **Welle Bootstrap** — `bootstrap.sh` + launchd-Plist-Vorlagen.
3. **Welle Public-Tenant** — fiktive Praxis „Dr. Mustermann" mit
   5 Demo-Mitarbeitenden, neutrale Standortnamen, gerenderter
   Showcase-Screenshot.
4. **Welle Dashboard-Integration** — `cortex-harness`-Layer für
   Cortex-Med-Web-Status auf allen Knoten.

## Lizenz

MIT (analog Cortex-Web). Public-Tenant enthält keine echten Patient/MA-Daten.
