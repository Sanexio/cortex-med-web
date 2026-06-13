# Public-Tenant — Demo-Praxis „Dr. Mustermann"

Fiktiver Tenant für Showcase-, Schulungs- und README-Zwecke.

- **Enthält keine echten Patient/MA-Daten.** Mitarbeitende, Standorte
  und Wochen-Soll sind synthetisch.
- Wird per `CORTEX_TENANT_DIR=Cortex-Med-Web/examples/public-tenant`
  von den Med-Apps geladen.
- Ist die **Default-Tenant-Variante** für jeden Cortex-Knoten, der
  Cortex-Med-Web installiert hat, ohne einen privaten Tenant
  (`Sanexio-Tenant` o.ä.) konfiguriert zu haben.

## Status (2026-06-13, befüllt)

- **6 fiktive Mitarbeitende**: Dr. Markus Mustermann (Arzt), Anna
  Beispiel, Bert Demo, Carla Mock, Daniel Probe, Eva Test.
- **3 Standorte**: Praxis Demo Nord, Praxis Demo Süd, Homeoffice.
- **5 Arbeitsbereiche**: Sprechstunde, Anmeldung, Labor, Funktion,
  Backoffice.
- **Shift-Schema** mit 5 Shift-Templates für die Standort-Kategorie
  „Praxis Demo Dr. Mustermann".
- **120 synthetische Schichten + 120 Time-Entries** für 4 Wochen
  (2026-05-18 bis 2026-06-12), 5-Tage-Woche.
- **2 Abwesenheiten** (1 Fortbildung, 1 Urlaubsantrag).
- **Aggregations-Gruppen** „Patientenkontakt" + „Verwaltung" für
  Auswertungen.
- **Wochen-Soll** variabel je Mitarbeitende (25 h Eva / 30 h Carla /
  35 h Anna / 40 h Standard).

## Nutzung

```bash
cd ~/Cortex/projects/Cortex-Web/sites/workforce-time
CORTEX_TENANT_DIR=~/Cortex/projects/Cortex-Med-Web/examples/public-tenant \
  npm run dev:web
```
