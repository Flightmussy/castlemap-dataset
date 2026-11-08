# Castles of the World — 9,040 castles, fortresses & palaces

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21322359.svg)](https://doi.org/10.5281/zenodo.21322359)

A curated, hand-checked dataset of the world's **9,040 great castles, fortresses, palaces and ruins across 155 countries** — every landmark verified to have exact coordinates, a real Wikimedia Commons photo and a Wikipedia article (English where it exists, else the native edition).

This is the exact dataset behind **[Castlemap](https://thecastlemap.com)**, a free interactive night-map of all 9,040 landmarks.

- 🗺️ Interactive map: https://thecastlemap.com
- 📄 Dataset page & downloads: https://thecastlemap.com/data/
- 🏆 Fame ranking (methodology): https://thecastlemap.com/castles/ranked/
- 🤖 Live MCP server for AI agents: `https://thecastlemap.com/mcp` (Model Context Protocol, streamable HTTP, no key — tools: `search_castles`, `get_castle`, `castles_near`, `top_castles`, `list_countries`, `get_statistics`, `random_castle`)

## Files

| File | Format | Contents |
|---|---|---|
| `castles.geojson` | GeoJSON FeatureCollection | 9,040 Point features with all properties |
| `castles.csv` | CSV (UTF-8, header row) | Same records, flat |

## Fields

| Field | Description |
|---|---|
| `qid` | Wikidata item ID (e.g. `Q2946`) — join key to the whole linked-data web |
| `name` | English name |
| `category` | `castle` \| `fortress` \| `palace` \| `ruin` |
| `country`, `iso` | Country name and ISO 3166-1 alpha-2 code. England, Scotland, Wales and Northern Ireland are counted as countries and carry ISO 3166-2 codes (`GB-ENG`, `GB-SCT`, `GB-WLS`, `GB-NIR`); one record, HM Fort Roughs under Sealand, has no code |
| `lat`, `lon` | WGS84 coordinates (verified) |
| `year`, `century` | Founding year (negative = BC) and century, where documented (7,411 of 9,040 carry a year) |
| `year_approx` | Whether that year is an approximation rather than a documented date — `1`/`0` in the CSV, `true`/`false` in the GeoJSON. True for 3,157 records |
| `wikipedia` | Wikipedia article URL (English where it exists, else the native edition) |
| `image` | Wikimedia Commons photo URL |
| `image_by` | Photographer, as credited on Commons — most of these licences require you to name them if you reuse the picture |
| `image_licence` | The photo's licence (e.g. `CC BY-SA 4.0`, `Public domain`). Applies to the photograph only, never to this dataset |
| `sitelinks` | Number of Wikipedia language editions covering the landmark |
| `pageviews` | Wikipedia pageviews over the trailing 60 days, summed across every language edition that covers the landmark |
| `fame_rank` | Global fame rank 1…9040 — a blend of Wikipedia language coverage (`sitelinks`) and readership (`pageviews`). Rank 1 = the Great Wall of China. [Methodology](https://thecastlemap.com/castles/ranked/) |
| `url` | The landmark's page on thecastlemap.com |

`image_by` and `image_licence` were added on 2026-08-08 and, since v2.2.0, are present for every record (6,993 of 7,738 in v2.1.0). CSV columns are appended, never reordered: the column order is a contract with everyone who has already cited the file.

## Provenance & method

Curated from **[Wikidata](https://www.wikidata.org)** (CC0). Candidates are filtered to significant, well-documented sites: exact coordinates required, a real Commons photo required, an English Wikipedia article required; categories normalized; countries normalized; duplicates and phantom entries removed by hand. The dataset refreshes from Wikidata — spot an error or a missing castle? Improve its Wikidata entry and it flows into the next release.

## Mirrors & citation

- GitHub: https://github.com/Flightmussy/castlemap-dataset
- Hugging Face: https://huggingface.co/datasets/Flightmussy/castles-of-the-world
- Kaggle: https://www.kaggle.com/datasets/flightmussy/castles-of-the-world
- **Citable DOI (Zenodo): [10.5281/zenodo.21322359](https://doi.org/10.5281/zenodo.21322359)**

## Releases

- **v2.3.0** (2026-11-08) — **8,131 → 9,040 landmarks, 149 → 155 countries** (1,048 added, 139 removed, 7,992 kept); no schema change, the same 18 columns in the same order as v2.0.0. Everything here happened on the live atlas between September and October and is written up entry by entry in its [changelog](https://thecastlemap.com/changelog/); this is the first dataset release since. **Growth:** 630 landmarks looked at one by one and four countries reached on 20 September; 410 more landmarks in 31 countries on 27 September, each admitted only with at least three Wikipedia editions and a photograph that shows the landmark well; five moated castles of Westphalia a reader asked for on 25 October. Six countries are new: Honduras, New Caledonia (Fort Teremba, filed under France until now), Saint Vincent and the Grenadines, Senegal, Togo, and Sealand, whose one record, HM Fort Roughs, is the only row without an ISO code. **Checks:** on 23 September all 8,764 photographs were looked at on contact sheets and 645 replaced by a photograph of the landmark itself (a map, plan, drawing, print, postcard, model, interior or night shot had stood in for it); on 19 October every landmark was checked against its Wikipedia article, its Wikidata item and its photograph: 44 left the map (duplicates of a landmark already on it, group listings whose members are mapped one by one, buildings that were never castles or palaces), 291 were filed as ruins, among them 211 sites where nothing stands any more, such as the Bastille and the Tuileries Palace, and 28 that survive as earthworks, and 189 other categories, 113 founding years and 23 names were corrected, with 143 pins moved onto the landmark itself. Against v2.2.0 that reads as 536 category changes (232 castle → ruin, 111 castle → palace, 95 fortress → ruin, 52 castle → fortress), 1,326 founding years that differ, 137 coordinates moved, 44 names changed and 1,018 `image` links that differ. Category counts: 3,057 castles · 1,611 fortresses · 1,970 palaces · 2,402 ruins. 7,411 records carry a founding year, 3,157 of them flagged approximate. England, Scotland, Wales and Northern Ireland count as countries, as they always have in this dataset, and carry ISO 3166-2 codes in `iso` (`GB-ENG`, `GB-SCT`, `GB-WLS`, `GB-NIR`); the field description above now says so. ⚠ The doubled `image_by` strings reported under v2.2.0 are down from 111 to 55 (51 of them `Unknown authorUnknown author`), not yet gone; read those as *no credit*, the licence column is right.

- **v2.2.0** (2026-09-07) — **7,738 → 8,131 landmarks, 141 → 149 countries** (406 added, 13 removed); no schema change, the same 18 columns in the same order as v2.0.0. **Most of the growth is landmarks the queries could not see.** Above twelve Wikipedia editions the castle, fort, château, palace and citadel classes turned out to be complete, so the remaining gap was single wrong-class items: probes of the classes Wikidata files them under (dzong, kasbah, ksar, hillfort, castrum, city walls, and World Heritage Sites typed as settlements) plus a walk of 22,220 English Wikipedia category pages found 353 — Sigiriya, Mycenae, Knossos, the dzongs of Bhutan, the walls of Tallinn and Seoul — and seven countries the dataset had never had: Antigua and Barbuda, Kuwait, Mongolia, Nigeria, Saint Kitts and Nevis, Timor-Leste and Venezuela. Two French readers added 51 more around Lyon and along the Loire. **Puerto Rico** is the 149th country: its three San Juan fortifications had been filed under the United States. **412 records changed category**, 287 of them to *ruin*: 161 landmarks that Wikidata marks demolished or ruined were settled one by one from each article's infobox condition, its categories and its home-language lead (133 are ruins, 25 stand and are pinned), and a further pass over Iran, the Middle East and everything outside Western Europe re-filed 195 as palaces, ruins or fortresses. **101 founding years moved**: Wikidata's SPARQL export counts BC years with a year 0, so every BC date had been off by one (the Ishtar Gate is 575 BC, Erebuni 782 BC); an "earliest statement wins" rule had kept renovation dates for a few (Kernavė 1989 → 1279, the Ca' d'Oro 1927 → 1424, Chantilly 1882 → 1386); millennium-precision dates no longer yield a year at all. **Readership sums were incomplete**: a failed language batch had been written as a final total (the Great Wall of China carried 12,116 pageviews against 467,136 real), so `fame_rank` now puts the Great Wall first, Machu Picchu second and Versailles third — a correction of the counts, not a change of method. Every photograph was re-checked on Commons (one had vanished and was replaced), and every record now carries `image_by` and `image_licence`. Of the 13 removals two were duplicates and eleven were never castles at all — a weapon, a wine estate, a market hall, a garden, a Roman theatre, a lighthouse, a castle trail, a theme park. Category counts: 3,125 castles · 1,558 fortresses · 1,556 palaces · 1,892 ruins. 6,025 records carry a founding year, 2,334 of them flagged approximate. ⚠ Known defect (55 remain in v2.3.0): 111 `image_by` values read as a doubled string (`Unknown authorUnknown author` on 106 of them), an artefact of flattening Commons' Artist field; read those as *no credit* — the licence column is still right.

- **v2.1.0** (2026-08-24) — **7,044 → 7,738 landmarks**, still 141 countries; no schema change, so every column and its position is exactly as in v2.0.0. Two things drove the growth, and both came from readers rather than from a scheduled refresh. **A whole shelf of Wikidata was unreachable**: Blenheim Palace — a World Heritage Site and the eleventh most-read landmark in the atlas — was missing because Wikidata types it an *English country house*, not a palace, and Highclere the same, Kinloch Castle a *mansion*, Eltham Palace a *historic house museum*. None of those classes descends from castle, fortress, palace, château, fort, citadel or fortification, so no query could see them however famous they were; 49 landmarks across fifteen countries were recovered. Then **a Spanish reader counted Jaén's castles and found nine.** He was right, and the cause was a rule rather than a gap: the atlas admitted landmarks in national fame order, so a dense province lost every slot to Catalonia's better-read castles. Reading that province's admissible tier by hand took Jaén to 29, and the same correction applied outward added 645 landmarks across 57 countries. Category counts: 3,409 castles · 1,496 fortresses · 1,336 palaces · 1,497 ruins. 5,727 records now carry a founding year.

- **v2.0.0** (2026-08-17) — **2,435 → 7,044 landmarks, 129 → 141 countries**, the largest expansion the dataset has had. It closes the gap that the previous release opened up between this file and the live atlas: the map had grown for a month while the published dataset stood still, so anyone downloading it was getting a third of the atlas. Thin countries were raised toward a per-country floor (Spain 500, Germany 475, France 456, Italy 416, Poland 360, England 315, Japan 296), whole classes that had been unreachable were admitted — the fortification superclass is now resolved globally rather than per country, which alone recovered 56 well-known fortifications — and Andean, Australian and Gulf sites were added from reader reports. Category counts: 3,180 castles · 1,453 fortresses · 1,024 palaces · 1,387 ruins. Four new fields: `year_approx`, `image_by`, `image_licence` and `url`; the CSV also carries `url`, which previously only the GeoJSON did, so a row can now be linked back to its page. Founding years were re-audited against each landmark's Wikipedia lead in eleven further languages.

- **v1.2.0** (2026-07-19) — 27 corrections. 26 founding years that were really renovation or heritage-designation dates in Wikidata (the Tang-dynasty Daming Palace claimed 2010 → now 634; Chapultepec 1944 → 1785; Sanok 2010 → 1523; a cluster of Czech castles stamped with their 2000 national-monument decree…) were fixed to the documented construction start, and Erebuni Fortress moved from the defunct historical state "Urartu" to Armenia — the dataset now spans 129 countries. These years power the new oldest-castles ranking: https://thecastlemap.com/castles/oldest/

- **v1.1.0** (2026-07-19) — 2,400 → 2,435 landmarks (4 Norwegian fortresses and 9 Indian landmarks added on reader request, plus 22 further ruins; the phantom "French Third Republic" country is gone — the Imperial City of Huế now sits under Vietnam, so 130 countries). 225 category corrections: an unambiguous display name now beats Wikidata's often-sloppy P31 typing (83 fixes — Kufstein Fortress is no longer a "castle"), and *ruin* is now a state that wins over the building type, read from each monument's English Wikipedia lead (142 fixes — Heidelberg, Poenari, Tantallon, the Slovak hilltop castles). Category counts: 1,031 castles · 427 fortresses · 716 palaces · 261 ruins.
- **v1.0.0** (2026-07-12) — first release: 2,400 landmarks across 131 countries.

## License

**Facts/data: [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/)** — public domain dedication; use for anything, no permission needed. Attribution to [Castlemap](https://thecastlemap.com) is appreciated but not required.

Photos and Wikipedia texts referenced by URL are **not** part of this dataset and remain under their own licenses (see each Commons/Wikipedia page).
