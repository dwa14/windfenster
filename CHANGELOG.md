# Änderungen

## 1.3.3 – 25.11.2026

- Saison aus Messungen erst ab 3 brauchbaren Jahren. Tarifa (nur 2021 vollständig) und Viana do Castelo (2021–2022
  mit 76 % der Stunden, aber überall 0 Gleittage – die Altdaten taugen offenbar nicht) fallen damit heraus

## 1.3.2 – 25.11.2026

Nach dem ersten echten `--klima-messung`-Lauf:
- Ein Messjahr zählt nur mit mindestens der Hälfte der Stunden. Viana do Castelo zeigte überall 0 Gleittage –
  offenbar keine lückenlosen Stundenwerte, sodass nie genug Stunden am Stück zusammenkamen. Die Ausgabe nennt jetzt
  den Anteil der Stunden je Station und ausgelassene Jahre; ausgelassene Stationen verschwinden auch aus der Datei
- „Talwind“-Zeilen heißen „Nachmittags W/N ab 8/5 kn“: Die Messung trennt thermischen Wind nicht von Wetterlagen
  (im Winter sind das Westwind- bzw. Nordwindlagen)

## 1.3.1 – 25.11.2026

- Sandbank-Hinweis quantitativ: statt „Sandbank logohoch“ (ausgelöst allein durch ≥ 22 kn Wind im Fenster) jetzt
  „Sandbank: Welle 1,2 m / 5 s“ aus der Modell-Wellenhöhe (Mittel im Fenster) und -periode, ab 1,0 m, an Spots mit
  Sandbank (derzeit Heidkate); ersetzt dort den allgemeinen Chip „Welle … m“. Ohne Wellendaten kein Sandbank-Hinweis

## 1.3 – 23.11.2026

Zwei neue Abschnitte, beide aus Messungen.

- **Spotseite: „Wie gut lag die Vorhersage hier?“** Die Vorhersage vom Vortag für die nächste Messstation des Reviers
  (bis 40 km, ohne nicht repräsentative Stationen) gegen die Messung dort: Streifen der letzten 30 Tage (angesagt und
  gekommen / angesagt, kam nicht / kam unangesagt / richtig ruhig), Satz mit den Zahlen, dazu die Quote für 2–3 Tage
  vorher. `treffer.json` enthält dafür je Station und Gleitgrenze die Tage (`je_station`); eine ältere Datei wird
  beim nächsten Lauf neu gerechnet
- **Revierseite, Saison: „Gemessen an den Stationen“** – neu `--klima-messung`: Ø Gleitwindtage je Monat an jeder
  Station über volle Kalenderjahre (Standard 5, `--jahre N`), DWD/Bright Sky, MeteoSwiss, DMI, KNMI (mit Schlüssel),
  GeoSphere-Klimadatensatz; an Walensee/Achensee zusätzlich Talwind ab 5/8 kn (12–18 Uhr, ≥ 3 h aus der
  Thermikrichtung). An der Küste Seewind ab 5 kn je Monat aus `--thermik-pruefen` (jetzt mit Monatswerten je
  Station). Thermikseen zeigen damit erstmals eine Saison. Ergebnis `klima_messung.json`, Rohdaten
  `klima_messung_cache/`, keine Open-Meteo-Abrufe. Meteotrentino bleibt außen vor (Lizenz der Historie ungeklärt)
- `--jahre` ohne Angabe: 2 Jahre wie bisher, bei `--klima-messung` 5

## 1.2.1 – 23.11.2026

- Thermik-Index wird nach der Treffsicherheit bei ≥ 8 / ≥ 12 kn ein- oder ausgeblendet, nicht mehr nach der besten
  aller Stufen. Schwacher Talwind (≥ 5 kn, Tagesgang) kommt an Walensee und Achensee in der Saison fast täglich,
  unabhängig vom Score. Damit ist neben dem Walensee auch der Achensee ausgeblendet (≥ 8 kn: HSS 0,09); Gardasee bleibt
  Faustregel

## 1.2 – 23.11.2026

Seewind und Thermik nach der Prüfung an Messungen umgebaut.

- **Seewind:** nur noch „Seewind möglich, meist schwach“ – bei Sonne, Grundwind ≤ 10 kn (nicht ablandig über 8 kn,
  nicht schon auflandig ab 6 kn) und 2–8 K Unterschied Land−Wasser. Grund: An vier Küstenstationen (2 Saisons) traf
  die alte Regel nur schwachen Seewind (≥ 5 kn an Regel-Tagen 33 % statt 17 %, ≥ 12 kn praktisch nie); ein
  Unterschied über ~3 K brachte nichts, ab 8 K wurde Seewind seltener. „Wahrscheinlich“ entfällt
- **„Thermik verstärkt“ entfällt** (gemessen +0,5 kn gegenüber anderen auflandigen Tagen)
- `--thermik-pruefen` prüft die neue Regel gegen Seewind ≥ 5 kn (≥ 8 kn mitgezählt), Raster 0–5 K × Obergrenze
  6/8/10 K/offen × Grundwind; Seite zeigt „geprüft: ≥ 5 kn an X % solcher Tage, ≥ 8 kn an Y %“
- **Thermik-Index ohne Treffsicherheit wird ausgeblendet** (HSS < 0,1 in jeder Messstufe bei ≥ 60 Tagen) – derzeit
  Walensee (Quinten: nachmittags Westwind an rund der Hälfte der Tage, unabhängig vom Score). Methodik nennt es
- GeoSphere-Klimadatensatz: findet über die Metadaten die nächste Klimastation (≤ 15 km) und die dortigen
  Parameternamen, falls die TAWES-ID dort nichts liefert
- Saison-Abschnitt: „Ora und Pelèr“ nur noch am Gardasee, sonst allgemein „Thermikwind“

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
