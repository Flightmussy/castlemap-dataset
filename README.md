# Castles of the World — 2,435 castles, fortresses & palaces

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21322359.svg)](https://doi.org/10.5281/zenodo.21322359)

A curated, hand-checked dataset of the world's **2,435 great castles, fortresses, palaces and ruins across 130 countries** — every landmark verified to have exact coordinates, a real Wikimedia Commons photo and an English Wikipedia article.

This is the exact dataset behind **[Castlemap](https://thecastlemap.com)**, a free interactive night-map of all 2,435 landmarks.

- 🗺️ Interactive map: https://thecastlemap.com
- 📄 Dataset page & downloads: https://thecastlemap.com/data/
- 🏆 Fame ranking (methodology): https://thecastlemap.com/castles/ranked/
- 🤖 Live MCP server for AI agents: `https://thecastlemap.com/mcp` (Model Context Protocol, streamable HTTP, no key — tools: `search_castles`, `get_castle`, `castles_near`, `top_castles`, `list_countries`, `random_castle`)

## Files

| File | Format | Contents |
|---|---|---|
| `castles.geojson` | GeoJSON FeatureCollection | 2,435 Point features with all properties |
| `castles.csv` | CSV (UTF-8, header row) | Same records, flat |

## Fields

| Field | Description |
|---|---|
| `qid` | Wikidata item ID (e.g. `Q2946`) — join key to the whole linked-data web |
| `name` | English name |
| `category` | `castle` \| `fortress` \| `palace` \| `ruin` |
| `country`, `iso` | Country name and ISO 3166-1 alpha-2 code |
| `lat`, `lon` | WGS84 coordinates (verified) |
| `year`, `century` | Founding year and century, where documented |
| `wikipedia` | English Wikipedia article URL |
| `image` | Wikimedia Commons photo URL |
| `sitelinks` | Number of Wikipedia language editions covering the landmark |
| `pageviews` | English Wikipedia pageviews (trailing 365 days) |
| `fame_rank` | Global fame rank 1…2435 — a blend of Wikipedia language coverage (`sitelinks`) and readership (`pageviews`). Rank 1 = Palace of Versailles. [Methodology](https://thecastlemap.com/castles/ranked/) |

## Provenance & method

Curated from **[Wikidata](https://www.wikidata.org)** (CC0). Candidates are filtered to significant, well-documented sites: exact coordinates required, a real Commons photo required, an English Wikipedia article required; categories normalized; countries normalized; duplicates and phantom entries removed by hand. The dataset refreshes from Wikidata — spot an error or a missing castle? Improve its Wikidata entry and it flows into the next release.

## Mirrors & citation

- GitHub: https://github.com/Flightmussy/castlemap-dataset
- Hugging Face: https://huggingface.co/datasets/Flightmussy/castles-of-the-world
- Kaggle: https://www.kaggle.com/datasets/albanius/castles-of-the-world-2400-castles-and-palaces
- **Citable DOI (Zenodo): [10.5281/zenodo.21322359](https://doi.org/10.5281/zenodo.21322359)**

## Releases

- **v1.1.0** (2026-07-19) — 2,400 → 2,435 landmarks (4 Norwegian fortresses and 9 Indian landmarks added on reader request, plus 22 further ruins; the phantom "French Third Republic" country is gone — the Imperial City of Huế now sits under Vietnam, so 130 countries). 225 category corrections: an unambiguous display name now beats Wikidata's often-sloppy P31 typing (83 fixes — Kufstein Fortress is no longer a "castle"), and *ruin* is now a state that wins over the building type, read from each monument's English Wikipedia lead (142 fixes — Heidelberg, Poenari, Tantallon, the Slovak hilltop castles). Category counts: 1,031 castles · 427 fortresses · 716 palaces · 261 ruins.
- **v1.0.0** (2026-07-12) — first release: 2,400 landmarks across 131 countries.

## License

**Facts/data: [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/)** — public domain dedication; use for anything, no permission needed. Attribution to [Castlemap](https://thecastlemap.com) is appreciated but not required.

Photos and Wikipedia texts referenced by URL are **not** part of this dataset and remain under their own licenses (see each Commons/Wikipedia page).
