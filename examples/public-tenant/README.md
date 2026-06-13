# Public-Tenant — Demo-Praxis „Dr. Mustermann"

Fiktiver Tenant für Showcase-, Schulungs- und README-Zwecke.

- **Enthält keine echten Patient/MA-Daten.** Mitarbeitende, Standorte
  und Wochen-Soll sind synthetisch.
- Wird per `CORTEX_TENANT_DIR=Cortex-Med-Web/examples/public-tenant`
  von den Med-Apps geladen.
- Ist die **Default-Tenant-Variante** für jeden Cortex-Knoten, der
  Cortex-Med-Web installiert hat, ohne einen privaten Tenant
  (`Sanexio-Tenant` o.ä.) konfiguriert zu haben.

## Status (2026-06-13)

Skeleton — `tenant.config.json` ist noch ein Stub. Wird in Folgewelle
„Public-Tenant" befüllt:

- 5 fiktive MFAs (`Anna Beispiel`, `Bert Demo`, …)
- 3 Standorte (`Praxis Demo Süd`, `Praxis Demo Nord`, `Homeoffice`)
- Shift-Schema analog zur echten Praxis, aber mit Demo-Namen
- Synthetische Time-Entries für die letzten 4 Wochen (Stempelzeiten)
- Synthetische Schichten + Absences

## Nutzung

```bash
cd ~/Cortex/projects/Cortex-Web/sites/workforce-time
CORTEX_TENANT_DIR=~/Cortex/projects/Cortex-Med-Web/examples/public-tenant \
  npm run dev:web
```
