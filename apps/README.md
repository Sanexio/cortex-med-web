# `apps/` — Cortex-Med-Web Sub-Apps

Dieses Verzeichnis bündelt die Medizin-Apps. **Code wird hier nicht
authoritativ gepflegt.** Pro App gibt es einen Integrations-Pfad:

| App                  | Quelle                                                  | Integration         |
|----------------------|----------------------------------------------------------|---------------------|
| `praxis-webseite/`   | `git@github.com:Sanexio/praxiszentrum-theme.git`        | Git-Submodule       |
| `workforce-time/`    | `Cortex-Web/sites/workforce-time/` (lokal vorhanden)     | Symlink via Bootstrap |

## praxis-webseite

WordPress Child-Theme `praxiszentrum`, basiert auf Blocksy. Wahrer
Ursprung ist die Live-Domain `westend-hausarzt.com` (GoDaddy) bzw. die
lokale Local-Flywheel Staging-Site. Edits laufen im Theme-Working-Copy
unter
`~/Local Sites/gpmedicalcenterwestend-…/app/public/wp-content/themes/praxiszentrum/`.
Das Cortex-Med-Web-Submodule trackt den jeweils publizierten Stand —
es wird **nachgezogen**, nicht gepflegt.

```bash
# Submodule auf neuesten publizierten Stand ziehen:
cd ~/Cortex/projects/Cortex-Med-Web
git submodule update --remote --merge apps/praxis-webseite
git add apps/praxis-webseite
git commit -m "praxis-webseite: nachziehen auf <commit-sha>"
git push
```

## workforce-time

Vite/React/Node-Sqlite-App, generisches Trunk-Modul im OSS-Framework
`Cortex-Web`. Lebt dort unter `sites/workforce-time/`.

Cortex-Med-Web zieht die App nicht als Submodule (das würde eine
Repo-Extraktion aus Cortex-Web erfordern), sondern legt einen Symlink
an, sobald `bootstrap.sh` läuft:

```
Cortex-Med-Web/apps/workforce-time → ~/Cortex/projects/Cortex-Web/sites/workforce-time
```

Updates: `git -C ~/Cortex/projects/Cortex-Web pull` zieht App-Updates
automatisch in den Symlink-Pfad.

## Zukünftige Apps

Schicht-Konvention für neue Med-Apps:
1. App lebt im Cortex-Web-Trunk (OSS-Slot) **oder** als eigenes Repo
   (z.B. wenn die App medizin-spezifisch ist und nicht in OSS-Framework
   gehört).
2. Cortex-Med-Web integriert per Submodule (eigenes Repo) oder Symlink
   (Trunk-Slot).
3. Bootstrap-Skript pflegt Symlinks/Submodules ein.
4. `cortex-harness`-Dashboard zeigt den Status.
