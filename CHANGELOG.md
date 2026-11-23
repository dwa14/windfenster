# Änderungen

## 1.1 – 23.11.2026

Seewind und Thermik an Messungen prüfen.

- Neu: `--thermik-pruefen` (Zeitraum `--jahre`, Standard 2 Saisons, höchstens 4). Dieselbe Regel wie im Lauf, mit
  den damaligen Modellvorhersagen (Open-Meteo Historical Forecast) gegen gemessene Nachmittage:
  - Seewind-Index: Kiel-Holtenau, Schönhagen, Fehmarn, St. Peter-Ording (DWD), März–September. Raster über
    Temperaturunterschied Land−Wasser und Grundwind, Maß CSI; „wahrscheinlich“ ab dem Unterschied, ab dem mindestens
    jeder zweite Tag Seewind brachte
  - „Thermik verstärkt“: Messung minus Modell an solchen Tagen gegen andere auflandige Tage
  - Thermik-Score: Walensee (MeteoSwiss Quinten, Talwind West), Achensee (GeoSphere Achenkirch, Nordwind),
    April–September; Anteil der Tage mit ≥ 3 h ≥ 8 bzw. 12 kn aus der Thermikrichtung je Klasse, Schwellen per CSI
- Ergebnis in `thermik_pruefung.json`; übernommen wird nur, was mit genug Ereignissen klar besser ist
  (sonst bleibt die Faustregel, aber mit Messzahlen)
- Seiten: „An Messungen geprüft“ statt „Faustregel“ beim Thermik-Index, „Gemessen …: an solchen Tagen in X % …“
  im Tooltip und in der Tabelle, Seewind mit „geprüft: kam an X % solcher Tage“; Methodik-Seite angepasst
- Rohdaten in `thermik_cache/` – ein zweiter Lauf kostet keine Open-Meteo-Abrufe (der erste etwa 330)
- Englische Texte für Seewind und „Thermik verstärkt“ ergänzt (fehlten bisher, fielen im Demo-November nicht auf)
- Gardasee bleibt Faustregel (keine frei verfügbare Messhistorie)

## 1.0 – 23.11.2026

Erste versionierte Fassung. Öffentlich seit 08.11.2026 unter https://windfenster.org/.

- 72 Spots in 12 Revieren (Nord-/Ostsee, Alpenseen, Mittelmeer/Atlantik), Deutsch und Englisch
- Spotseite: Kurzsatz, Kennzahl-Kacheln, Nächste Tage als Liste, eine Zeitleiste „Stunde für Stunde“
  (Liste | Grafik), Tage im Detail
- Revierseite: Kurzsatz, Jetzt-Messungen, amtliche Warnungen (DWD), Nächste Tage als Liste, alle Spots im Vergleich
- Startseite: Meine Spots (Kurzsatz, Stundenstreifen, 7 Tage, Bearbeiten), beliebte Spots, Revier-Matrix
- Handy: untere Leiste Spots · Karte · Reviere, Wind-Karte bildschirmfüllend mit einer Zeitleiste über alle Tage
- Wahrscheinlichkeit nach gemessener Treffsicherheit der Modelle (`modell_guete.json`), Eichung ab 30 echten Tagen
- Modellfaktoren je Revier und Vorlauf aus der Validierung
- Föhn/Bise an Messungen geprüft, Thermik als Faustregel gekennzeichnet
- Richtung wird mitgeschrieben und automatisch geprüft; Toleranz am Rand schaltet sich nur ein, wenn die
  Messungen es belegen
- Auffindbarkeit: Titel und Beschreibung je Seite, Sitemap mit Sprachpaaren, robots.txt, App-Symbol (Manifest)
- Push-Thema (ntfy) aus dem Skript in `ntfy.json` verschoben
