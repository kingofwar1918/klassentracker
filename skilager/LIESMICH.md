# Skilager Gruppen – Einrichtung und Bedienung

Eine Seite, drei Ansichten:

| Link | Wer | Was |
|---|---|---|
| `…/skilager/?ansicht=lp#n=…` | Lagerleitung (Passwort) | einteilen, umteilen, Bourbaki, Zimmer, Ämtli, freigeben, Appell-Übersicht, Rückmeldungen |
| `…/skilager/?ansicht=leiter#n=…` | Leitende (Passwort) | eigene Gruppe mit Appell und Auf-/Abstufen, alle Gruppen, Bourbaki mit Grund, Zimmer, Ämtli, Kontakte |
| `…/skilager/#n=…` | Schüler/innen (ohne Passwort) | Namen wählen → Gruppe, Leitung, Treffpunkt, Kontakt (falls freigegeben), Gruppe, Zimmer, Ämtli |

Die Links kopierst du in der App unter **Einrichten → Online → Links**.

## Datenschutz: was wo liegt

- **Namen** stehen nie in Firebase und nie im Repository. Sie stecken im Link (Teil nach `#`, wird nicht an den Server geschickt) und werden auf dem Gerät gespeichert. In der Datenbank stehen nur zufällige Kennungen.
- **`/skilager/oeffentlich`** (alle lesen): Gruppennamen, Farben, Niveaus, Leitung, Treffpunkt, Kontakt nur bei Häkchen «für SuS», Zuteilung des freigegebenen Tages, Zimmer, Ämtli.
- **`/skilager/leitstand`** (nur Lagerleitung und Leitungskonten): ganzer Stand inkl. Bourbaki-Grund, Selbsteinschätzung, Kontakte, Appell, Rückmeldungen.
- **Nur auf dem Gerät der Lagerleitung:** Bemerkungen zu Schüler/innen, Klasse, Geschlecht, Backup.
- Ein Schüler-Link zeigt allen, wer in welcher Gruppe ist und wer im Bourbaki steht (ohne Grund). Wenn die Schule das anders will: vorher mit der Schulleitung klären.

## Firebase einrichten (einmal)

1. console.firebase.google.com → neues Projekt, z.B. `skilager-2027`. Analytics weglassen.
2. **Realtime Database** erstellen: Standort **europe-west1**, **gesperrter Modus** (nicht Testmodus).
3. **Authentication** → Anmeldeart «E-Mail/Passwort» einschalten.
4. Unter **Users** zwei Konten anlegen: eines für dich (Lagerleitung), eines für die Leitung. Die Leitung kann sich ein Konto teilen; wer will, bekommt ein eigenes.
5. **Authentication → Einstellungen → Benutzeraktionen:** «Registrierung (Erstellen)» ausschalten, damit niemand selbst Konten anlegt.
6. Projekteinstellungen → Allgemein → Web-App hinzufügen → `databaseURL` und `apiKey` kopieren.
7. In `index.html` oben bei `CONFIG` eintragen: `datenbank`, `apiKey`, `seite` (die GitHub-Pages-Adresse). Der apiKey ist kein Geheimnis.
8. Regeln: `regeln.json` öffnen, `LEHRER_UID` durch deine UID und `LEITUNG_UID` durch die UID des Leitungskontos ersetzen (UIDs stehen unter Authentication → Users) und unter Realtime Database → Rules einfügen und **veröffentlichen**. Einfacher: nach deiner ersten Anmeldung zeigt die App unter Einrichten → Online die fertigen Regeln mit deiner UID; dort die Leitungs-UIDs eintragen und «Regeln kopieren».
9. Mehrere Leitungskonten: in der App bei «Leitungskonten» alle UIDs mit Komma eintragen, Regeln neu kopieren und veröffentlichen.

Meldet sich ein Leitungskonto an, das noch nicht in den Regeln steht, zeigt die Leiteransicht seine UID an.

## GitHub Pages

`index.html` als Ordner `skilager/` ins Repository `klassentracker` legen (wie `arbeitsplan/`). `regeln.json` und `LIESMICH.md` dürfen mit, sie enthalten keine Namen. **Kein Backup und keine Namensliste ins Repository.** Pages hält alte Versionen bis 10 Minuten im Zwischenspeicher: Geräte danach einmal neu laden.

## Prüfen, bevor die Links rausgehen

- [ ] Regeln veröffentlicht (nicht nur eingetippt)
- [ ] Im privaten Browserfenster `…firebasedatabase.app/skilager/leitstand.json` öffnen → muss «Permission denied» zeigen
- [ ] Oder: `python3 scripts/pruefe_regeln.py regeln.json --live <databaseURL>` aus dem Skill firebase-github-pages
- [ ] Registrierung in Authentication ausgeschaltet
- [ ] Testlauf mit Laptop (Lagerleitung), einem Handy (Leitung) und einem Handy (Schüler/in)
- [ ] Gruppenlisten als Excel exportiert und ausgedruckt (Rückfall bei schlechtem Netz)

Geprüft vor der Übergabe: Regelprüfskript ohne Fehler; im Firebase-Emulator 22 Fälle (anonym, fremdes Konto, Leitung, Lagerleitung; Lesen, Schreiben, ungültige Rückmeldungen) wie erwartet; Ablauf Lagerleitung → Leitung (Appell, Aufstufen) → Lagerleitung sieht es → Schüler/in sieht Gruppe gegen den Emulator durchgespielt. Der Live-Test gegen die echte Datenbank steht noch aus.

## Bedienung im Lager

- **Einteilen:** Bei einer Gruppe «Ziel» antippen, dann alle Namen antippen, die dorthin gehören. Ohne Ziel öffnet ein Namen das Menü mit allen Gruppen, Bourbaki und dem Verlauf. Am Laptop geht auch Ziehen.
- **Niveaus:** Höhere Nummer = stärker. Unter Einrichten → Niveaus mit «+ Anfänger 3 (stärker)» oder «+ unten einfügen» ergänzen; Gruppen bleiben richtig zugeordnet, nur die Nummern rücken.
- **Neuer Tag:** «+ Tag» übernimmt Gruppen, Bourbaki und Ämtli. Erst «Für Schüler/innen freigeben» macht ihn für die Schüler/innen sichtbar (grüner Punkt). Die Leitung sieht alle Tage sofort.
- **Bourbaki:** Name antippen → Grund → «In Bourbaki». Zurück mit «Gesund – zurück zu …».
- **Appell:** Die Leitung hakt in ihrer Ansicht ab; im Reiter «Appell» siehst du alle Gruppen und wer fehlt.
- **Auf-/Abstufen:** Die Leitung tippt ↑ oder ↓ (mit Bemerkung). Bei dir erscheint die Rückmeldung mit Knopf «→ nächste Gruppe».
- **Ämtli:** «ganzes Zimmer zuteilen» oder einzeln; am nächsten Tag «Vom Vortag rotieren».
- Die Anmeldung der Leitung bleibt auf dem Gerät gespeichert, bis jemand «Abmelden» tippt. Fällt das Netz aus, zeigt die Leiteransicht den letzten Stand und liefert Appell-Häkchen nach.

## Nach dem Lager

Excel exportieren, Backup speichern, dann Einrichten → Online → «Online-Daten löschen». Die Datenbank ist kein Archiv.
