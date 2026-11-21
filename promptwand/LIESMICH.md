# Prompt-Wand (KI-Workshop V2, Deutsch KK9)

Live-Wand für den KI-Workshop: Die Lernenden schreiben auf dem iPad ihren Prompt 1 und später ihren Prompt 2 (aus 3 Teilen: ICH, AUFTRAG, SO). Am Beamer erscheinen alle Prompts sofort.

- **Lernende:** https://kingofwar1918.github.io/klassentracker/promptwand/ (QR-Code in der Präsentation)
- **Beamer:** https://kingofwar1918.github.io/klassentracker/promptwand/?ansicht=wand
- **Lehrperson:** auf der Beamer-Ansicht unten «Lehrperson» → gleiches Konto wie im Arbeitsplan. Dann: «Prompt 2 freigeben», einzelne Zettel löschen (×), «Wand als Text herunterladen», «Wand leeren». Bei jedem Prompt kopiert «Kopieren» den Text für den KI-Chat.

## Einmalig vor dem ersten Einsatz: Regeln aktualisieren

Die Wand nutzt dieselbe Datenbank wie der Arbeitsplan KK9 (Pfad `arbeitsplan/oeffentlich/promptwand`). Damit Lernende dort schreiben dürfen, braucht die Datenbank die Regeln vom 21.11.2026: Arbeitsplan öffnen → als Lehrperson anmelden → rote Karte «Regeln aktualisieren» → «Regeln kopieren» → in Firebase (Realtime Database → Regeln) einfügen → Veröffentlichen. Fehlen die Regeln, zeigt die Wand nach dem Login einen roten Hinweis, und die Lernenden sehen «Die Wand ist noch nicht freigeschaltet».

## Was die Regeln erzwingen

- Lernende schreiben nur Zettel mit Tiername, Aufgabe, Prompt 1 (höchstens 400 Zeichen), Prompt 2 (höchstens 600 Zeichen) und Zeit; keine weiteren Felder.
- Lernende können keinen Zettel löschen, keinen Prompt löschen und kein fremdes Tier übernehmen. Die Phase (Prompt 2 offen) setzt nur die Lehrperson.
- Getestet im Firebase-Emulator (23 Fälle, 21.11.2026).

## Datenschutz

Die Lernenden erscheinen nur als zufälliger Tiername (gespeichert nur auf ihrem Gerät), nie mit Namen oder Kürzel. Die Prompts sind für alle mit dem Link lesbar: Hinweis «Keine Namen und keine Adressen» steht im Eingabefeld. Nach dem Workshop: «Wand als Text herunterladen», dann «Wand leeren».

Demo ohne Datenbank (nur im eigenen Browser): `?demo=1` bzw. `?demo=1&ansicht=wand`.
