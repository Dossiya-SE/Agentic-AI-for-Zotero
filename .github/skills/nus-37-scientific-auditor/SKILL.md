---
name: nus-37-scientific-auditor
description: Read-only scientific inspection of all 37 papers in NUS.xlsm, matching source PDFs, materials physics, sustainability accounting and claim-level evidence.
---
# NUS 37-paper scientific inspection skill

This is an **independent** review framework inspired by Dr Damian Palin's public materials-science work at Cambridge and Dr Jinying Xu's public research on carbon data, sustainability and infrastructure at NUS. Neither researcher authored, approved or endorsed this skill.

## Required references
Read every file before making scientific judgments:
- references/palin-materials.md
- references/xu-sustainability.md
- references/joint-audit.md

## Live source authority
- NUS macro-enabled workbook: https://drive.google.com/file/d/1Hd6_WI1IcuZWx2xaFck8eIa4I1ERtroM/view
- Original 37-paper PDFs: https://drive.google.com/drive/folders/1Q9xqQ3UZ1ItdeMRH0jeGDBR75L17Wy-k
- Existing Zotero provenance rules in repository root SKILL.md and NUS_FROZEN37_CASEBOOK.md, as appropriate.

Always read the **current** Google Drive workbook and original PDF bytes, not only an old snapshot or summary. The GitHub repository does not itself grant access to Drive. Mark missing source material as unverified.

## Mandatory coverage
- Inspect all 37 paper rows, Verified!A2:T38 (19 scientific fields B:T per row, up to 703 fields); do not stop at the prior 25-paper subset A14:T38.
- Reconcile PDF_Evidence against exact worksheet headers and Excel cells. Previous schema was A NUS-ID, B DOI, C original PDF filename, D Excel cell, E PDF page, F section/table/equation/figure, G supporting excerpt; re-check live.
- Preserve Acronym_Glossary, Acronym_Change_Log, visual and general, and other workbook parts.
- Verify identity, DOI, title, publication version and exact source location for every paper.

## Ten ordered gates
G0. Capture file version and manifest; confirm 37 identities and source variants. Record file hash where feasible.
G1. Split each scientific Excel cell into checkable factual or interpretative claims, including author result vs independent reviewer inference.
G2. Verify focal methods: controls, physical parameters, specimen, conditions, repetitions, measured vs modeled outcomes, statistical uncertainty.
G3. Compare every important numerical value to the **original** PDF table, figure or equation. Independently calculate units, baselines, percentages, denominators, time and uncertainty. Render PDF pages visually when mathematical text or tables are ambiguous.
G4. Establish true environmental assessment type and functional unit, boundary, LCA impact method/database version, allocation and assumptions.
G5. Distinguish LCC from price comparisons, social scoring from formal S-LCA, MCDA from LCA, source-measured carbon capture from background claims.
G6. Identify the exact engineering-to-sustainability bridge: functional-unit normalization, changed design quantities, modeled consequences, weighted criteria, parallel comparison or unproven link.
G7. For every evidence anchor check both **correct page** and **semantic fit** to the exact Excel claim. Source page found does not mean claim proved.
G8. Read back current Excel and all approved previous corrections. Propose **only new outstanding** factual errors or essential missing evidence. Preserve source-paper contradictions as source issues.
G9. Produce bounded cross-paper synthesis, a full per-cell verification register, and a supervisor briefing. Do not pool incomparable impact numbers.

## Per-claim statuses
VERIFIED; VERIFIED_WITH_LIMIT; NEW_EXCEL_ERROR; EVIDENCE_ANCHOR_REPAIR; SOURCE_CONTRADICTION; PENDING_SOURCE_VERSION; REVIEWER_INFERENCE; UNVERIFIED; NOT_APPLICABLE.

No paper or field is called fully certified unless its scientific claims, original source, calculations and limitations have been independently inspected.

## Historical issues to recheck, not automatically repeat as new
- Prior eight sustainability-scope revisions P18, P21, P23, P25, P30, P32, P33, P34 were already implemented.
- NUS-132 Q14: exact SimaPro 9.3.0.3, ecoinvent 3.4, ReCiPe 2016 methods, 125 stakeholder surveys and Mean Item Score; distinguish social data from ECM inputs.
- Ten previously weak evidence anchors: J19 J21 J28 Q26 Q30 C33 C34 G23 G32 R22.
- NUS-52 Equation 6/Table 8 inconsistency; NUS-94 accepted manuscript vs publisher final; NUS-153 unrelated clinical-AI introduction; NUS-25 "204% reduction" wording; NUS-210 transport assumptions; NUS-183 conflicting costs.
- Previous 25-paper register: 208 direct PDF_Evidence references and 267 without an individual reference, including reviewer-inferred SDGs. These are historical and **must be recounted on the latest workbook**.
- Screening history 282 screened, 12 initially analyzed, 37-paper enlarged corpus needs traceable inclusion/exclusion records; do not invent PRISMA compliance.

## Required output
1. Executive scientific-readiness verdict with exact *verified* counts, coverage limits and source version.
2. New scientific errors only: paper ID, exact cell, existing statement, exact correction, why, original PDF page/table/equation, calculation, confidence and priority.
3. Evidence-only repairs: separate PDF_Evidence anchors, without changing already-correct cell science.
4. Publisher-version issues and author-source contradictions.
5. 37-paper / 703-field status register and independently verified numerical calculations where applicable.
6. Cross-paper synthesis and research contribution, properly qualifying incomparable functional units and study boundaries.
7. Supervisor briefing: established findings, open issues, next three actions and three specific questions.

## File integrity and authorization
READ ONLY BY DEFAULT. Do not modify Google Drive NUS.xlsm, local workbook, PDFs or Zotero records unless the user explicitly instructs a specific write. Do not convert .xlsm to .xlsx and silently lose macros, images, drawings, formulas or relationships. Any future authorized edit must be reversible with exact before/after text and post-write verification.

If a complete audit cannot be finished during the active response, present completed checks and an explicit incomplete register. Never promise background work, invent certainty, or report certification unsupported by claim-level proof.
