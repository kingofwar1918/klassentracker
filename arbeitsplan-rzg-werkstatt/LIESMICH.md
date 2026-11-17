# Arbeitsplan RZG KK9 · Werkstatt (1914-1945)

Eigener Online-Arbeitsplan für die **Werkstatt-Fassung** der RZG-Einheit «Vom Ersten zum Zweiten Weltkrieg 1914-1945» (DL01-DL18, Pflichtposten P, Wahlposten ★, Exit-Ticket, Lernkontrollen in DL 6, 11 und 18). Er ist eine Kopie von `../arbeitsplan-rzg` mit eigenem Datenbereich. **Der bisherige RZG-Tracker und der Deutsch-Tracker bleiben unverändert.**

**Adresse:** https://kingofwar1918.github.io/klassentracker/arbeitsplan-rzg-werkstatt/ · Beamer: `…/arbeitsplan-rzg-werkstatt/?beamer=1`

## Was getrennt ist
- **Datenbank:** eigener Bereich `/arbeitsplan-rzg-werkstatt` im selben Firebase-Projekt (`arbeitsplan-kk9`). Stand, Ziele, FLK und Interessen mischen sich nicht mit `/arbeitsplan` (Deutsch) und `/arbeitsplan-rzg` (RZG V2).
- **Gerätespeicher:** eigener Präfix `arbeitsplan_rzg_werkstatt_kk9.`; Namen und Farbe auf den iPads sind getrennt (eigener Klassenlink).
- **Exporte:** Dateinamen `arbeitsplan_rzg_werkstatt_kk9_…`.

## Inhalt der Vorlage
Pro DL: Input (Rückblick, Wissensbite, Kurzinput), Startauftrag, Pflichtposten P1…, Wahlposten W1… ★, Vertiefung ★, Abschluss mit Exit-Ticket und 💡 Frage wählen. In DL 6, 11 und 18 zusätzlich die Lernkontrolle (35'). Keine Daten: Datum und Abgabedaten der Hausaufgaben trägst du in «Bearbeiten» ein. Interessenfragen, Wissensbite und Vertiefungslinks wie im RZG-Tracker V2.

## Regeln (wichtig)
`regeln.json` enthält **alle drei Bereiche**: Deutsch und RZG wie in den beiden Trackern im Repository (Stand 12.11.2026), dazu der neue Bereich. Sie ersetzt in der Firebase-Konsole den ganzen Regelinhalt.
- Nach dem Einspielen funktionieren Deutsch- und RZG-Tracker wie vorher (ihre Regeln sind Wort für Wort gleich wie im Repository). Gelten in Firebase noch ältere Regeln, kommen mit dem Einspielen auch die neueren Deutsch-Regeln dazu (Sperre für archivierte DL und für den Stand «korrektur»).
- **Ab jetzt die Regeln nur noch aus dem Werkstatt-Tracker kopieren.** Der Knopf «Regeln kopieren» im Deutsch- oder RZG-Tracker kennt den Werkstatt-Bereich nicht; wer dort kopiert und veröffentlicht, schaltet den Werkstatt-Tracker wieder aus.

## Einrichtung (einmalig, ca. 5 Minuten)
1. Erledigt am 17.11.2026: Der Ordner `arbeitsplan-rzg-werkstatt` liegt im Repository `klassentracker`. GitHub Pages veröffentlicht Änderungen nach 1-2 Minuten.
2. Adresse öffnen → Tab «Lehrperson» → mit dem Lehrer-Konto anmelden (wie Deutsch und RZG).
3. Rote Karte «Regeln einspielen» → «Regeln kopieren» → Firebase-Konsole → Realtime Database → Regeln: ganzen Inhalt ersetzen → «Veröffentlichen» → in der App «Erneut prüfen».
4. «Arbeitsplan aus Vorlage laden» (DL01-DL18).
5. Bearbeiten → Lernende → echte Namen eintragen (nur auf diesem Gerät) → «Link kopieren» → neuen Klassenlink posten. Jedes iPad öffnet ihn einmal.
6. Kontrolle: Deutsch- und RZG-Tracker kurz öffnen; beide zeigen ihren Stand wie vorher.

## Datenschutz
Wie im RZG-Tracker: in Datenbank und Repository nur Farbnamen, keine Namen. Ende der Einheit: CSV «Daten» und «💡 Interessen» exportieren, dann «Alles löschen» (löscht nur den Werkstatt-Bereich).

Gebaut mit `bauen_werkstatt.py` aus `arbeitsplan-rzg/index.html` (Stand ffe7f92) und den Werkstatt-Heften DL 1-18 (12.11.2026). Geprüft: Regeln der bisherigen Bereiche identisch mit dem Deutsch- und dem RZG-Tracker im Repository; Demo-Modus im Browser (Mein Plan, Klasse, Lehrperson) ohne Fehler. Ein Test gegen die echte Datenbank war hier nicht möglich. Stand 17.11.2026: Regeln nochmals mit dem Repository verglichen (Deutsch- und RZG-Tracker, Stand 7884b91): gleich.
