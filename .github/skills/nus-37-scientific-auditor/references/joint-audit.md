# Joint physics–sustainability audit and claims-certification protocol

## Invariant scientific chain
Material and experimental conditions → physical measurements/mechanisms → service or design consequences → environmental/economic/social indicators → decision and uncertainty.

For each arrow assign DIRECTLY_MEASURED, CALCULATED_BY_AUTHOR, MODEL_MEDIATED, FUNCTIONALLY_NORMALIZED, MULTICRITERIA_COMBINED, PARALLEL_ONLY, or UNDEMONSTRATED. If unsure, report precisely what evidence is missing.

## Mandatory source and arithmetic checks
- Do not classify author background citations as measurements from the focal paper.
- Do not infer full lifecycle analysis from an ISO citation or sustainable title.
- Do not infer cost LCC from material prices or formal S-LCA from surveys alone.
- Do not classify one publication's figures under different functional units as directly comparable without a defensible conversion.
- Do not infer physical causality from aggregate predictive R-squared or observational correlation.
- Inspect PDF page images for equations, figures and tables whose text was extracted ambiguously.
- Independently verify critical data, calculation, sign, units, uncertainty, percent reduction, base value, per-strength denominator and age. Label derived quantities.
- Treat source contradictions as SOURCE_CONTRADICTION, not silent editorial corrections.
- Preserve study-specific system boundaries, service life, geography, factor database version and exclusions.

## Priority triage
1. NEW_EXCEL_ERROR: the actual current Excel claim contradicts the original source.
2. EVIDENCE_ANCHOR_REPAIR: the Excel claim is sound but linked to the wrong/inadequate PDF passage/page.
3. SOURCE_CONTRADICTION: the author's own equations/tables/figures conflict; keep both and note limitations.
4. PENDING_SOURCE_VERSION: accepted manuscript needs publisher final comparison.
5. VERIFIED_WITH_LIMIT: correct only within specific conditions.
6. VERIFIED: independently supported, including consequential numeric checks where relevant.
7. UNVERIFIED: source unavailable or checks incomplete.
8. REVIEWER_INFERENCE: inference not attributed to author.

## Historical corpus context (must recheck latest Drive bytes)
- The 25-paper block Verified A14:T38 has 25 paper identity cells and 475 scientific cells. Previously 208 direct evidence entries, 267 without one-to-one entries. Those counts can change.
- Existing P-column revisions: P18, P21, P23, P25, P30, P32, P33, P34.
- Ten previously weak page/evidence anchors: J19, J21, J28, Q26, Q30, C33, C34, G23, G32, R22.
- NUS-132 Q14 and NUS-52/94/153/25/210/183 source/method matters are known issues, not automatically NEW corrections.
- Full scope Verified A2:T38 (37 papers, 703 scientific fields) includes 12 earlier papers beyond that 25-paper block.

## Exact PDF_Evidence data schema
Inspect actual sheet before relying on the historical mapping:
A NUS-PAPER-ID; B DOI; C PDF filename; D Excel cell; E page; F location/section; G literal support text. Avoid off-by-one mapping error.

## Reproducibility package
For each reviewed scientific field: identity, exact current text, checkable atomic claims, source PDF metadata, semantic proof, independent calculations, status, source limitations and correction requirement. A field can have several independently classified claims. Produce count coverage derived from actual records, not a claimed prior count.

Output NEW_CORRECTIONS (only active), EVIDENCE_REPAIRS, SOURCE_ISSUES, FIELD_REGISTER, CROSS_PAPER_SYNTHESIS, SUPERVISOR_BRIEF and UNCERTIFIED_BACKLOG.

No direct writes by default. Any authorized workbook changes must preserve original macros/drawings/formatting and require a fresh post-write readback.
