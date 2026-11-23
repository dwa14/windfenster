# Änderungen

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
