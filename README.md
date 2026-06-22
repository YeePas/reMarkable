# reMarkable Templates

Een kleine collectie reMarkable-sjablonen in twee vormen:

- PNG templates voor echte reMarkable notebook templates.
- PDF notebooks/planners voor import via de reMarkable app, inclusief klikbare navigatie waar dat zinvol is.

De stijl is bewust rustig: zwart-witte headers, lichte schrijflijnen en veel ruimte voor eigen notities. De PNG-set is bedoeld als custom template pack; de PDF's zijn bedoeld als gewone documenten/notebooks.

## Inhoud

```text
outputs/
  remarkable_template_pngs_strak/        # aanbevolen PNG template set
  remarkable_template_pngs/              # oudere, zachtere eerste variant
  remarkable_transformatie_meetings.pdf  # klikbare meeting notebook
  remarkable_powerpoint_schets.pdf       # liggende PowerPoint schets PDF
```

## PNG Templates

Gebruik bij voorkeur:

[outputs/remarkable_template_pngs_strak](outputs/remarkable_template_pngs_strak)

Deze map bevat 21 templates:

| Template | Orientatie | Bestand |
| --- | --- | --- |
| 1:1 Meeting | Portrait | `one_on_one_meeting_portrait.png` |
| Decision Log | Landscape | `decision_log_landscape.png` |
| Project Dashboard | Portrait | `project_dashboard_portrait.png` |
| Weekly Leadership Review | Portrait | `weekly_leadership_review_portrait.png` |
| Workshop Canvas | Landscape | `workshop_canvas_landscape.png` |
| Daily Planner | Portrait | `daily_planner_portrait.png` |
| Weekly Planner | Landscape | `weekly_planner_landscape.png` |
| GTD Inbox | Portrait | `gtd_inbox_portrait.png` |
| Eisenhower Matrix | Portrait | `eisenhower_matrix_portrait.png` |
| Focus Sprint | Portrait | `focus_sprint_portrait.png` |
| OKR Template | Portrait | `okr_template_portrait.png` |
| One-page Strategy | Portrait | `one_page_strategy_portrait.png` |
| Problem Framing Canvas | Portrait | `problem_framing_canvas_portrait.png` |
| Pre-mortem | Portrait | `pre_mortem_portrait.png` |
| Hypothesis Tracker | Landscape | `hypothesis_tracker_landscape.png` |
| Slide Storyboard | Landscape | `slide_storyboard_landscape.png` |
| Executive Memo Outline | Portrait | `executive_memo_outline_portrait.png` |
| Before After Transformation Canvas | Landscape | `before_after_transformation_canvas_landscape.png` |
| Cornell Notes | Portrait | `cornell_notes_portrait.png` |
| Sketchnote | Portrait | `sketchnote_portrait.png` |
| Moodboard Concept Board | Landscape | `moodboard_concept_board_landscape.png` |

Resoluties:

- Portrait: `1404 x 1872`
- Landscape: `1872 x 1404`

Bijbehorende metadata:

- [manifest.json](outputs/remarkable_template_pngs_strak/manifest.json) beschrijft naam, bestand, orientatie en resolutie. Dit bestand is alleen inventaris/controle en wordt niet door de reMarkable gebruikt.
- [remarkable_templates_entries.json](outputs/remarkable_template_pngs_strak/remarkable_templates_entries.json) bevat kant-en-klare entries die je toevoegt aan je bestaande `templates.json`.

Let op: `remarkable_templates_entries.json` is geen volledige `templates.json`. Vervang je bestaande reMarkable `templates.json` hier dus niet mee.

## templates.json

reMarkable gebruikt `/usr/share/remarkable/templates/templates.json` om templates zichtbaar te maken in de template-kiezer. De PNG-bestanden zelf staan in dezelfde template-map.

Een custom entry ziet er bijvoorbeeld zo uit:

```json
{
  "name": "Daily Planner",
  "filename": "daily_planner_portrait",
  "iconCode": "\ue991",
  "categories": ["Joep", "Planners"]
}
```

Voor een liggende template:

```json
{
  "name": "Decision Log",
  "filename": "decision_log_landscape",
  "iconCode": "\ue9ab",
  "categories": ["Joep", "Planners"],
  "landscape": true
}
```

Belangrijk:

- `filename` is zonder `.png`.
- De PNG zelf heeft wel `.png` in de bestandsnaam.
- Gebruik `landscape: true` alleen voor liggende templates.
- Velden zoals `orientation` en `size` horen niet in reMarkable's `templates.json`; die staan alleen in het manifest voor onszelf.
- De categorie `Joep` werkt als eigen categorie. De tweede categorie, zoals `Planners`, `Creative` of `Lines`, zorgt dat de template ook in een standaardgroep vindbaar blijft.
- Voeg custom entries toe aan de bestaande `"templates": [...]` array. Vervang de standaardtemplates niet.

Voorbeeld van het principe:

```json
{
  "templates": [
    {
      "name": "Blank",
      "filename": "Blank",
      "iconCode": "\ue9fe",
      "categories": ["Creative", "Lines", "Grids", "Planners"]
    },
    {
      "name": "Daily Planner",
      "filename": "daily_planner_portrait",
      "iconCode": "\ue991",
      "categories": ["Joep", "Planners"]
    }
  ]
}
```

## Installatie Op reMarkable

De veiligste route is met een template-manager zoals RCU of ReManager. Handmatig via SSH kan ook.

Handmatig concept:

1. Maak een backup van je bestaande `templates.json`.
2. Kopieer de PNG's uit `outputs/remarkable_template_pngs_strak/` naar:

```text
/usr/share/remarkable/templates/
```

3. Voeg de entries uit `remarkable_templates_entries.json` toe aan de bestaande `"templates": [...]` array in:

```text
/usr/share/remarkable/templates/templates.json
```

4. Vervang dus niet het hele bestand; plak alleen de objecten uit `remarkable_templates_entries.json` als extra items in de array.
5. Herstart de reMarkable UI of reboot de tablet.

Voor USB/SSH is het device meestal bereikbaar via:

```bash
ssh root@10.11.99.1
```

Je SSH password staat op de reMarkable onder:

```text
Settings > Help > Copyrights and licenses > General information
```

## PDF Templates

PDF's kun je gewoon importeren via de reMarkable desktop/mobile app. Ze gedragen zich als documenten/notebooks, niet als echte template-achtergronden.

Aanwezige PDF's:

- [remarkable_transformatie_meetings.pdf](outputs/remarkable_transformatie_meetings.pdf)
  - Klikbaar Transformatie-notitieboek.
  - Homepagina met secties.
  - Secties: ART Sync, Kernteam, PTO, Agile Community, Transformatie Board.
  - 15 pagina's per sectie.
  - Home-icoon en klikbare meeting-tabs.

- [remarkable_powerpoint_schets.pdf](outputs/remarkable_powerpoint_schets.pdf)
  - Liggende schets-PDF voor presentatie-denken.
  - 25 pagina's.
  - Links notitieruimte, rechts een lege 16:9 slide-rand.

Ook bedoeld als onderdeel van deze collectie:

- `klikbare_todo.pdf`
  - Klikbare todo/planner PDF.
  - Voeg dit bestand toe aan `outputs/` wanneer je hem in deze repo publiceert.

- `remarkable-paper-pure-gelijnd-tabs-v5.pdf`
  - Gelijnde paper-template met tabs.
  - Voeg dit bestand toe aan `outputs/` wanneer je hem in deze repo publiceert.

## Genereren

De generatoren staan in `work/`:

- [work/make_remarkable_template_pngs.py](work/make_remarkable_template_pngs.py)
- [work/make_remarkable_templates.py](work/make_remarkable_templates.py)

PNG's opnieuw genereren:

```bash
python3 work/make_remarkable_template_pngs.py
```

PDF's opnieuw genereren:

```bash
python3 work/make_remarkable_templates.py
```

## Opmerkingen

- Custom templates kunnen na een reMarkable software-update verdwijnen. Bewaar daarom altijd deze repo of een lokale backup.
- Als templates niet zichtbaar lijken, check eerst de filter/visibility-knoppen in de template-kiezer. Niet elk zichtbaarheidsprobleem is een kapotte JSON.
- Maak altijd een backup van `templates.json` voordat je handmatig wijzigt.
