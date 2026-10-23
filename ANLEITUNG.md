# Meine Beat-Werkstatt als installierbare App (PWA)

Der ursprüngliche Code ist unverändert als `beat_werkstatt_original.html` enthalten. In `index.html` wurden **nur** Links zum Manifest, Apple-Metadaten und die Service-Worker-Registrierung ergänzt. Alle bisherigen Funktionen, das Schlagzeugbild und die Sounds bleiben erhalten.

## Einfach veröffentlichen (z. B. Netlify Drop)

1. Entpacke das ZIP-Paket.
2. Öffne https://app.netlify.com/drop im Browser und lade den **Ordner `Beat-Werkstatt-PWA`** hoch (alternativ dessen Inhalte als ZIP, falls der Dienst das unterstützt).
3. Netlify stellt eine HTTPS-URL bereit. Öffne diese URL auf dem gewünschten Gerät.
4. Android / Chrome: Browsermenü → **App installieren** oder **Zum Startbildschirm hinzufügen**.
5. iPhone / iPad / Safari: Teilen-Menü → **Zum Home-Bildschirm** → ggf. **Als Web-App öffnen** aktivieren → **Hinzufügen**.
6. Desktop / Chrome oder Edge: Symbol **Installieren** in der Adressleiste bzw. Browsermenü.

## Wichtige Hinweise

- `index.html` per Doppelklick (`file://`) zu öffnen genügt **nicht** für eine installierbare PWA. Der Service Worker benötigt HTTPS (lokal funktioniert auch `localhost`).
- Nach dem ersten vollständigen Laden über HTTPS kann die App dank Service Worker offline geöffnet werden; das gilt für unterstützende Browser.
- Zum lokalen Testen im entpackten Ordner: `python -m http.server 8000` und auf **demselben Computer** `http://localhost:8000` aufrufen.
- Alle Dateien im Ordner gemeinsam auf den Webserver laden. **Nicht** nur `index.html` hochladen.
- Das App-Icon ist eine neue, einfache Trommelillustration. Das originale Drumset-Bild bleibt unverändert in der App.
- Die Beats werden derzeit nicht dauerhaft gespeichert, weil diese Funktion auch in der Originalversion noch nicht vorhanden war.
- Wird die App später geändert, muss ggf. der Cache-Name in `service-worker.js` aktualisiert werden.
- HTTPS-Hosting kann die Webadresse öffentlich zugänglich machen: Link nur mit gewünschten Personen teilen und ggf. Zugriffsschutz konfigurieren.

## Was wurde technisch ergänzt?

- `manifest.webmanifest`: Name, Icons, Farben, Startadresse, App-Fenstermodus
- `service-worker.js`: Offline-Cache
- `icons/icon-180.png`, `icon-192.png`, `icon-512.png`: Homescreen- und App-Icons
- `index.html`: unveränderte Anwendung mit minimalen Installations-Einbindungen
