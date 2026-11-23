# Änderungen

## 1.1.2 – 23.11.2026

- Thermik-Prüfung Achensee: Das TAWES-Archiv von GeoSphere reicht nur wenige Monate zurück (Achenkirch 2025 leer,
  2026 nur 39 Tage). Fehlt mehr als die Hälfte, holt die Prüfung jetzt den Klimadatensatz `klima-v2-10min`
  derselben Station (lange Historie)

## 1.1.1 – 23.11.2026

Korrektur der Thermik-Prüfung nach dem ersten echten Lauf.

- Übernahme nach **Heidke Skill Score** statt CSI-Gewinn: mindestens HSS 0,2 und +0,05 gegenüber der Faustregel.
  1.1 hatte Schwellen übernommen, die nicht besser waren als „immer ja“ (Walensee 0,15/0,35; Seewind ab 3 K)
- Vorschläge aus einer `thermik_pruefung.json` von 1.1 werden nicht angewandt; Messzahlen passen zu den geltenden
  Schwellen
- Diagnose in der Ausgabe: Seewind je Messstufe (gedreht / ≥ 5 / ≥ 8 / ≥ 12 kn) und je Temperaturunterschied;
  Thermik je Klasse mit Tagesgang-Kriterium und Windrose, Messabdeckung je Saison
- GeoSphere-Messung abschnittsweise (ein Fehler kostet 30 Tage statt der Saison), lückenhafte Ablagen werden neu
  geholt, Hinweise auf fehlende Messungen auf der normalen Ausgabe
- „kann stärker kommen“ / „eher ein paar kn mehr“ entfällt, wenn die Prüfung unter 1,5 kn Verstärkung misst;
  Thermik-Text „Gemessen …“ nennt den Vergleich mit „kaum“-Tagen
- Fußzeile mit dreistelliger Version übersetzt

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
