# Alban Schledt – Karriereseite

Recruiting-Landingpage & Ad-Funnel für die **Alban Schledt GmbH & Co. KG**
(Feinmechanik / Schnittwerkzeugbau, Industriestraße 38, 64807 Dieburg).

Gesucht werden **2–3 Kolleg:innen fürs CNC-Drehen** – Präzisionsteile für die
Luft- und Raumfahrt aus hochfesten Werkstoffen (u. a. Aluminiumlegierungen und
amerikanische Werkstoffe). Aufbau und Funnel-Logik sind 1:1 an der ALWA-Seite
orientiert, umgesetzt im eigenen Corporate Design (Luft-/Raumfahrt-Blau).

## Inhalt

- `index.html` – die komplette Seite (self-contained, keine Build-Schritte nötig)
- `creatives/` – 6 fertige Meta-Ad-Motive (3 Stellen × 4:5 und 9:16 Story)
- `supabase-bewerbungen.sql` – legt den Storage-Bucket für den optionalen Lebenslauf-Upload an
- `bilder/` – Logo (`schledt-logo*.png`) und Hero-Fotos (`hero.jpg`, `cnc-dreher.jpg`, `zerspanungsmechaniker.jpg`, `cnc-einrichter.jpg`)
- `social/` – Facebook Profil- (1000×1000) und Titelbild (1640×624), aufeinander abgestimmt
- `.nojekyll` – sorgt dafür, dass GitHub Pages die Dateien 1:1 ausliefert

## Offene Stellen

| Stelle | Deeplink für die Ad |
| --- | --- |
| CNC-Dreher – Luft- & Raumfahrt (m/w/d) | `…/?stelle=cnc-dreher` |
| Zerspanungsmechaniker – Drehtechnik (m/w/d) | `…/?stelle=zerspanungsmechaniker` |
| CNC-Einrichter Drehen (m/w/d) | `…/?stelle=cnc-einrichter` |

Der Deeplink wählt die Stelle vor und startet direkt bei der Erfahrungs-Frage.

## Formular & Vorfilterung

Mehrstufiges, mobil- und conversionoptimiertes Formular (~60–90 Sek.):

1. **Stelle wählen**
2. **Qualifikation** – Ausbildung / Erfahrung in der Metallbearbeitung
3. **Erfahrung an CNC-Maschinen** – Jahre an der Dreh-/Zerspanungsmaschine
4. **Zeichnungen & Messen** – Zeichnungen lesen und mit Messmitteln prüfen
5. **Kontaktdaten** (+ optionaler Lebenslauf-Upload)

Die drei Qualifikationsfragen (2–4) sind mit einem Punkte-Vorfilter hinterlegt:
Jede Antwort trägt Punkte (`data-score` im HTML). Wer die Mindestpunktzahl
(`MIN_SCORE`, Standard 2 von max. 6) **nicht** erreicht **oder** ein
K.o.-Kriterium (`data-dq`, aktuell „weder Ausbildung noch Erfahrung in der
Metallbearbeitung") wählt, wird nach der letzten Frage freundlich abgelehnt –
es geht **kein Lead an Leadtable**. Wer „alles maximal schlecht" ausfüllt,
kommt also nicht durch. Schwellwert und Punkte lassen sich oben im `<script>`
von `index.html` anpassen. Screening & Erfolg gelten nur für den aktuellen
Besuch – ein Seiten-Neuladen startet frisch.

## Bewerbungen (Leadtable)

Jede abgeschlossene Bewerbung wird per Webhook an Leadtable gesendet
(Felder u. a. `vorname`, `nachname`, `email`, `telefon`, `stelle`, `erfahrung`,
`lebenslauf`, `quelle`, `seite`). Der Webhook ist in `index.html` in der Variable
`WEBHOOK_URL` hinterlegt und verweist auf die vorgegebene Leadtable-Kachel.

## Lebenslauf-Upload (optional)

Der optionale Datei-Upload nutzt Supabase Storage (Bucket `bewerbungen`).
Er ist **standardmäßig deaktiviert** – die Bewerbung wird auch ohne Upload
gesendet, der Lebenslauf kann dann per E-Mail nachgereicht werden.

Zum Aktivieren:
1. Ein Supabase-Projekt anlegen und `supabase-bewerbungen.sql` einmalig im
   SQL-Editor ausführen.
2. In `index.html` die Variablen `SUPABASE_URL` und `SUPABASE_KEY`
   (anon/publishable Key) eintragen.

Danach landet im Leadtable-Feld `lebenslauf` ein direkt öffenbarer Link.

## Corporate Design

Farbschema als CSS-Variablen ganz oben in `index.html` (`:root { --brand … }`).
Das Blau (`--brand:#1c3fce`) ist am Firmenlogo ausgerichtet. Das Original-Logo
liegt in `bilder/` (`schledt-logo.png` für helle, `schledt-logo-weiss.png` für
dunkle Flächen) und wird automatisch in Header, Hero und Footer eingesetzt.
Farben lassen sich jederzeit über die `--brand*`-Werte anpassen.

## Meta-Ad-Creatives

In `creatives/` liegen sechs einsatzfertige Motive im Alban-Schledt-CI:

- `creative-cnc-dreher-4x5.png` / `-story.png`
- `creative-zerspanungsmechaniker-4x5.png` / `-story.png`
- `creative-cnc-einrichter-4x5.png` / `-story.png`

Format `4x5` (1080×1350) für Feed, `story` (1080×1920) für Stories/Reels.
Jedes Motiv sollte auf den passenden Stellen-Deeplink verlinkt werden.

## Live schalten (GitHub Pages)

1. Repo-Settings → **Pages** → Source: **Deploy from a branch**, Branch: `main` / `/ (root)`.
2. Nach ein paar Minuten ist die Seite unter
   `https://saviold.github.io/schledt-gmbh/` erreichbar.
3. Optional eine Custom-Domain (z. B. `alban-schledt.de/karriere`) über die
   Pages-Einstellungen bzw. einen Redirect anbinden. Danach ggf. `canonical`
   und die `og:url` in `index.html` auf die finale Domain anpassen.

---

Karriereseite von [Ländle Digital](https://www.laendle-digital.com).
