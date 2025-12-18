# Functional Enrichment Studio
**BioInfo Tools**

Functional Enrichment Studio app: upload annotations table + a gene list, pick a factor (KO, Pathway, COG, PFAM, GO, EC, Module, Reaction, BRITE, rclass, TC, CAZy, BiGG), hit Run, and explore analysis results via table or charts.


Main page: https://hugston.com/bioinfo


## Demo video
[![Watch the demo](https://img.youtube.com/vi/cHy_KOVhJqo/hqdefault.jpg)](https://youtu.be/cHy_KOVhJqo)

## Files used in the demo

1)


# Features

Hugston analysis everything runs in the browser.

- **Flexible inputs**: CSV / TSV / TAB / TXT / XLS / XLSX.
- **Smart column detection**: guesses `#query` / `query` / `New_locus_tag`, and factor columns like `KEGG_ko`, `KEGG_Pathway`, `PFAMs`, `GOs`, etc.
- **Multiple term families**: KO, Pathway, COG, PFAM, GO, EC, Module, Reaction, BRITE, rclass, TC, CAZy, BiGG.
- **Proper stats**: right-tail hypergeometric; BH/BY FDR.
- **Rich visuals**: Bar, Volcano, Sunburst, Manhattan, Heatmap, Sankey, Overview grid; interactive clicks deep-link to KEGG/GO/InterPro/etc.
- **Exports**: CSV/JSON for results, PNG for charts.
- **Demo**: “Load Demo” button seeds tiny test data and auto-runs.

---

## Functional Enrichment Studio: How to Use

1. **Upload files**  
   - **Annotations**: eggNOG-style table with a gene ID column (`#query` / `query` / `New_locus_tag`) and any of:  
     - `KEGG_ko`
     - `KEGG_Pathway`
     - `COG_category`
     - `PFAMs`
     - `GOs`
     - `EC`
     - `KEGG_Module`
     - `KEGG_Reaction`
     - `BRITE`
     - `KEGG_rclass`
     - `KEGG_TC`
     - `CAZy`
     - `BiGG_Reaction`
   - **Gene list**: one ID per line or a 1-column sheet (header optional).

2. **Pick settings**  
   - Factor (e.g., KO or Pathway)
   - Background set
   - Multi-hit handling
   - FDR method/cutoff

3. **Run**  
   Results render in the **Table tab**; charts appear in other tabs.

---

## Interact

- Click table rows to inspect **in-list vs background genes**.
- Click chart points to open external pages:
  - KEGG KO → DBGET (`ko:Kxxxxx`)
  - KEGG Pathway → map pages (`mapxxxxx`)
  - GO → AmiGO (`GO:nnnnnnn`)
  - PFAM → InterPro
  - EC → Expasy
  - BRITE / rclass / TC / CAZy / BiGG → respective portals

---

## Export

- **Results**: CSV / JSON
- **Charts**: PNG (active chart)

---

## Input Quirks It Handles

- **Delimiter auto-detect**: tab, comma, semicolon, pipe.
- **Normalizes KOs**: `ko:K00001` → `K00001`.
- **Sanitizes pathway tokens**: `map00010`, `ko00010` → usable forms.

---

## Under the Hood (Stats)

**Test**: Right-tail hypergeometric `P[X ≥ k]` with:
- `N` = background size
- `M` = term count in background
- `n` = list size
- `k` = overlap

**Multiple testing**: BH (default) or BY FDR.

**Extras**: 
- Odds ratio + 95% CI (Haldane–Anscombe 0.5 continuity)
- Specificity
- Information content
- Simple “escore” to rank terms for charts

---

## Privacy, Performance & CDNs

- **No data leaves the browser**: All parsing and stats run client-side.
- **External libraries**: Load via CDN by default (Plotly, jStat, PapaParse, XLSX, Cytoscape).  
  *Switch to local bundles if your environment blocks CDNs.*

---

## License

This project is **Hugston-licensed**. See `LICENSE` in Hugston.com.  
© 2025 Hugston. All rights reserved.

---

## Acknowledgements

© 2025 Hugston  
Klaudi Bregu https://github.com/Mainframework
