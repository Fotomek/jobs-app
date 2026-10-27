# Jobs-App – Aufträge & Zeiten

Eine einzige, selbstständige Datei: `index.html` (inline CSS/JS, keine externen Abhängigkeiten, läuft offline).

## Öffnen
- Lokal: `index.html` per Doppelklick im Browser öffnen (funktioniert über `file://`).
- Auf dem Handy: Datei dorthin kopieren und im Browser öffnen, oder per GitHub Pages ausliefern (nur diese Datei nötig).
- Die Daten liegen im `localStorage` des jeweiligen Browsers/Geräts (Schlüssel `jobsapp.v1`) – pro Gerät/Browser getrennt.

## Erster Start
Leerzustand mit „Zeit erfassen“, „JSON importieren“ und „Beispieldaten laden“. Beispieldaten sind mit „Beispiel –“ markiert und unter Einstellungen bzw. über das gelbe Banner wieder entfernbar (echte Daten bleiben erhalten).

## Daten importieren / exportieren (Einstellungen → Daten)
- **Import**: JSON-Datei wählen oder JSON einfügen. Akzeptiert
  - die reine Liste aus `arbeitszeit.py` (`arbeitszeiten.json`):
    `[{"datum":"2026-10-27","start":"12:00","ende":"18:00","projekt":"…","text":"…"}]`
  - oder das komplette Format: `{"zeiten":[…],"projekte":{"Name":{"status":"In Arbeit"}},"stundensatz":95}`
  - Bei vorhandenen Daten: Zusammenführen (Duplikate werden übersprungen) oder Ersetzen. Ungültige Einträge werden übersprungen und gezählt.
- **Export Liste**: reine Liste, 1:1 kompatibel mit `arbeitszeit.py` (`ARBEITSZEIT_DATEI=…` bzw. `arbeitszeiten.json`).
- **Export komplett**: inkl. Projekt-Status und Stundensatz (dieses Format liest `arbeitszeit.py` *nicht*; dafür den Listen-Export nutzen).
- Ende vor Start = über Mitternacht (wie im Python-Programm). Status: Anfrage, In Arbeit, Wartet auf Kunde, Abgeschlossen.
- Die App verändert `arbeitszeiten.json` nie selbst – sie liest nur beim Import und schreibt nur Downloads.

## Hinweise
- Stundensatz (Standard 95 EUR) unter Einstellungen änderbar; Beträge = Minuten × Satz / 60, deutsch formatiert (1.234,50 EUR), Stunden als H:MM.
- Wochen laufen Montag–Sonntag (ISO-Kalenderwoche).
- Regelmäßig exportieren: Browserdaten löschen entfernt auch die App-Daten.
