# Arbeitsplan Deutsch KK9 · Textproduktion HS26

Online-Fassung des Excel-Arbeitsplans (DL01–DL11). Lernende tragen ihren Stand ein, die Lehrperson kontrolliert und ändert Aufträge, der Beamer zeigt den Stand live.

**Adresse:** https://kingofwar1918.github.io/klassentracker/arbeitsplan/

| Ansicht | Für wen | Was |
|---|---|---|
| Mein Plan | Lernende | eigene Aufträge: offen → in Arbeit → fertig, «Das kann ich heute», FLK, Hausaufgaben |
| Klasse | alle, Beamer | Raster wie im Excel (Aufträge × Lernende), Fortschritt, Selbsteinschätzung |
| Übersicht | Lehrperson (Klasse nur, wenn freigegeben) | Fortschritt pro DL und XP (fertig = 1, kontrolliert = 2) |
| Archiv | alle | Aufträge, die fertig kontrolliert sind (von Hand verschoben); zählen weiter für XP und Fortschritt |
| Bearbeiten | nur Lehrperson (Login) | Aufträge, Datum/Thema/Ziel, FLK, Hausaufgaben, Lernende, Export |

**Für die Lehrperson im Raster:** Zelle antippen → Status setzen, auch **«zur Korrektur zurückweisen»** (rot umrandet mit Warnleuchte, bei den Lernenden zusätzlich als Warnung oben in «Mein Plan»; sie überarbeiten und setzen wieder «fertig»). Am Griff ⠿ ziehen: Auftrag **in eine andere DL** (mit dem Stand der Klasse), **ins Archiv** oder an eine andere Stelle; Antippen des Griffs öffnet dasselbe als Menü. «📦 n ins Archiv» verschiebt alle Aufträge, die bei allen kontrolliert sind.

Beamer direkt öffnen: `…/arbeitsplan/?beamer=1`

## Datenschutz

- In der Datenbank und in diesem Repository stehen **keine Namen**, nur Farbnamen (Gelb, Orange …).
- Echte Namen kommen nur über den Klassenlink aufs Gerät (Teil nach `#`, wird nie an GitHub oder Firebase gesendet). Klassenlink: Bearbeiten → Lernende → «Link kopieren».
- Datenbank in der EU (europe-west1). Am Ende der Einheit: CSV exportieren, dann «Alles löschen».

## Einrichtung (einmalig)

Solange in `index.html` oben bei `CONFIG` keine Datenbank steht, läuft die App im **Demo-Modus** (nur auf dem eigenen Gerät).

1. console.firebase.google.com → Projekt hinzufügen, z.B. `arbeitsplan-kk9` (Google Analytics aus).
2. Build → **Realtime Database** → Datenbank erstellen → Standort **Belgien (europe-west1)** → **gesperrter Modus**.
3. Build → **Authentication** → Jetzt starten → Anbieter **E-Mail/Passwort** aktivieren → Tab «Users» → Nutzer hinzufügen (deine E-Mail + Passwort) → **UID** kopieren.
4. Realtime Database → **Regeln**: Inhalt von `regeln.json` einfügen, `LEHRER_UID` durch deine UID ersetzen → Veröffentlichen.
5. Projekteinstellungen (Zahnrad) → Allgemein → Meine Apps → Web-App `</>` registrieren → `apiKey` und `databaseURL` in `index.html` bei `CONFIG` eintragen.
6. App öffnen → Lehrperson → anmelden → «Arbeitsplan aus Vorlage laden».

Fehlt Schritt 4, zeigt die App nach dem Login «Regeln kopieren» mit bereits eingesetzter UID.

## Was die Regeln erzwingen

- Lernende dürfen nur `offen`, `in Arbeit`, `fertig` setzen – nie `kontrolliert` oder `korrektur`, nichts löschen, nichts an Aufträgen ändern.
- Archivierte Aufträge können Lernende nicht mehr ändern.
- Einen kontrollierten Auftrag können Lernende nicht mehr zurücksetzen.
- Nur bestehende Aufträge, DL, FLK-Lernziele und Lernende sind beschreibbar.
- Alles andere (Plan, Zuteilung, Löschen) nur mit Lehrer-Login.

Getestet gegen den Firebase-Emulator (39 Regelfälle, 66 Ablaufschritte inkl. Offline-Puffer, Ziehen mit Maus und Finger).

Nach einem Update der Regeln (z.B. 23.10.2026: «zur Korrektur», Archiv) zeigt die App nach dem Login eine rote Karte «Regeln aktualisieren» mit Kopierknopf.
