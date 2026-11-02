# Arbeitsplan RZG KK9 · Vom Ersten zum Zweiten Weltkrieg 1914-1945

Online-Arbeitsplan für die RZG-Einheit (DL01–DL18, 13.11.2026–09.04.2027). Er ist eine Kopie des Deutsch-Trackers (`../arbeitsplan`), mit eigenem Datenbereich und drei Erweiterungen: Interesse, Wissensbite und Vertiefung.

**Adresse:** https://kingofwar1918.github.io/klassentracker/arbeitsplan-rzg/ · Beamer: `…/arbeitsplan-rzg/?beamer=1`

| Ansicht | Für wen | Was |
|---|---|---|
| Mein Plan | Lernende | Aufträge pro DL (Einstieg, Input, Arbeitsphase, Abschluss); 💡 «Was willst du mehr wissen?»; 🔎 Vertiefung mit geprüften Links; Hausaufgaben |
| Klasse | alle, Beamer | Raster Aufträge × Lernende; oben «Wissensbite heute» (Gewinnerfrage der vorherigen DL); unten die Abstimmung als Balken (ohne Namen) |
| Übersicht, Archiv | wie im Deutsch-Tracker | |
| 💡 Interessen | nur Lehrperson | Stimmen pro DL mit Namen, eigene Fragen und Vertiefungen (privat), «KI-Prompt kopieren», CSV |
| Bearbeiten | nur Lehrperson | wie im Deutsch-Tracker, zusätzlich die 3 Interessenfragen und Links pro DL |

## Interesse · Wissensbite · Vertiefung
1. **Ende jeder DL (2'):** Die Lernenden wählen eine von 3 Interessenfragen. Das ist öffentlich, auf dem Beamer ohne Namen. Wer will, schreibt zusätzlich eine eigene Frage. Diese ist **privat**, nur die Lehrperson liest sie.
2. **Beginn der nächsten DL (5'):** Die Lehrperson stellt die meistgewählte Frage als Wissensbite vor. Die Folien liegen im Anhang der PPT, über den Knopf «Wissensbite ›» auf der Rückblick-Folie.
3. **Arbeitsphase:** Die übrigen Fragen sind ★ Vertiefung, mit geprüften Links. Die Lernenden schicken 3 Fakten und die Quelle privat an die Lehrperson. Wer will, meldet sich für einen Schüler-Bite.
4. **KI nur für die Lehrperson:** Im Tab «💡 Interessen» kopiert «KI-Prompt kopieren» eine Vorlage, die keine Namen enthält. Die App enthält keinen KI-Schlüssel.

## Daten und Regeln
- **Projekt:** Firebase-Projekt wie beim Deutsch-Tracker (`arbeitsplan-kk9`). Der RZG-Tracker hat einen eigenen Bereich `/arbeitsplan-rzg`, der Deutsch-Tracker `/arbeitsplan`.
- **Bereiche:**
  - `oeffentlich`: Plan, Stand, Ziel, FLK, `interesse` (Wahl f1–f4) und `biteAngebot`. Alle können lesen.
  - `privat`: eigene Fragen (`fragen`, höchstens 300 Zeichen) und Vertiefungen (`vertiefung`, höchstens 1200 Zeichen). Die Lernenden können hier nur schreiben, lesen kann nur die Lehrperson.
- **Regeln:** `regeln.json` enthält **beide** Bereiche, Deutsch und RZG. Sie ersetzt in der Firebase-Konsole den ganzen Regelinhalt. Dieselbe Datei liegt auch in `../arbeitsplan/regeln.json`. Damit löscht der Knopf «Regeln kopieren» im einen Tracker die Regeln des anderen nicht.
- **Was die Regeln erzwingen (zusätzlich zum Deutsch-Tracker):**
  - Lernende wählen nur eine bestehende Frage einer bestehenden DL.
  - Sie können ihre Wahl wechseln, aber nicht löschen.
  - Bei eigener Frage und Vertiefung gilt: nur Text, nicht leer, Längenbegrenzung, nur für bestehende DL und Lernende. Löschen und Lesen kann nur die Lehrperson.
- **Geprüft:**
  - 51 Regelfälle mit einem Auswerter der Regelausdrücke (`tracker/regeltest.js` im Arbeitsordner). Ein Emulator-Test war in dieser Umgebung nicht möglich.
  - Die Abläufe habe ich im Demo-Modus mit Playwright geprüft: wählen, eigene Frage, Vertiefung, Schüler-Bite, Banner, LP-Ansicht, Bearbeiten.

## Einrichtung (einmalig)
1. Firebase-Konsole → Realtime Database → Regeln: den ganzen Inhalt durch `regeln.json` ersetzen und `LEHRER_UID` durch die eigene UID ersetzen. Einfacher geht es so: in der App anmelden, dann Bearbeiten → «Regeln kopieren». Danach «Veröffentlichen».
2. App öffnen → Lehrperson → anmelden → «Arbeitsplan aus Vorlage laden». Das lädt DL01–DL18 mit den Interessenfragen.
3. Bearbeiten → Lernende → echte Namen eintragen (nur auf diesem Gerät) → «Link kopieren». Diesen Klassenlink gibst du den Lernenden.

## Datenschutz
- In der Datenbank und im Repository stehen **keine Namen**, nur Farbnamen.
- **Ende der Einheit:** beide CSV exportieren, «Daten» und «💡 Interessen». Danach Bearbeiten → «Alles löschen». Das löscht auch die privaten Fragen.

Gebaut mit `tracker/bauen.py` aus dem Deutsch-Tracker (Stand abe73a8) und `tracker/vorlage_rzg.json` + `wissensbite/DLxx.json`.
