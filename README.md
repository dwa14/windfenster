# Windfenster

Windvorhersage für Windsurfen, Kiten und Wingen: https://windfenster.org/

Ein einziges Python-Skript (`windsurf_spots.py`) holt Punktvorhersagen mehrerer Wettermodelle (Open-Meteo),
Ensembles, Kartenfelder (ECMWF, GFS, ICON-D2) und Messwerte (DWD, DMI, MeteoSwiss, KNMI, GeoSphere,
Meteotrentino, NOAA, Pegel), bewertet die Spots und erzeugt statische HTML-Seiten (DE/EN). Ein Raspberry Pi
rechnet per Cron und lädt die Seiten zu Uberspace hoch.

## Betrieb (Raspberry Pi)

```
# Hauptlauf (Cron: 17 0,6,9,12,15,18,21 * * *)
python3 windsurf_spots.py --kein-browser
# Messungen alle 10 Minuten (ohne Open-Meteo)
python3 windsurf_spots.py --nur-jetzt
# Version
python3 windsurf_spots.py --version
```

Weitere Auswertungen: `--validieren`, `--treffer`, `--richtung-pruefen`, `--druck-pruefen`,
`--stationen-suchen SPOT`, `--demo` (ohne Netz, zum Testen).

## Nicht im Repository (bleibt auf dem Pi)

Zugangsdaten und private Dateien: `upload.json`, `impressum.json`, `knmi_zugang.json`, `polar_zugang.json`,
`server_zugang.json`, `ntfy.json` (Push-Thema), `.htpasswd`, Logbuch und Sessions. Dazu alle Archive und
Zwischenspeicher (`*.jsonl`, `*_cache*`, `treffer.json`, `modell_guete.json` …) und die erzeugten Seiten.
Die `.gitignore` lässt nur Code und Doku zu.

## Versionen

Nummerierung: Korrekturen 1.0.1, neue Funktionen 1.1, große Umbauten 2.0.
Änderungen stehen in `CHANGELOG.md`, jede Version als Git-Tag (`v1.0`, …).
