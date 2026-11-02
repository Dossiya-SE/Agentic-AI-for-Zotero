# NUS-37 expert scientific inspection — Usage

This skill is a source-grounded, read-only independent materials-science and sustainability audit of NUS.xlsm.

## In GitHub Copilot Chat (VS Code)
Open this repository as the workspace, ensure the original Google Drive workbook and PDFs are accessible, then run:

    /nus-full-inspection

Prompt definition: ../../prompts/nus-full-inspection.prompt.md in the repository root .github/prompts directory.

If your GitHub Copilot environment does not recognize slash prompts, use this exact text:

    Read .github/skills/nus-37-scientific-auditor/SKILL.md and all reference files. Audit the CURRENT NUS.xlsm at https://drive.google.com/file/d/1Hd6_WI1IcuZWx2xaFck8eIa4I1ERtroM/view against the 37 PDFs in https://drive.google.com/drive/folders/1Q9xqQ3UZ1ItdeMRH0jeGDBR75L17Wy-k. Inspect Verified!A2:T38, PDF_Evidence, all relevant numerical source tables, units, experimental and sustainability methods, and cross-paper comparability. Report ONLY outstanding new inaccuracies or missing essential evidence, plus a full field register. Read-only. Do not alter NUS.xlsm.

## In ChatGPT with connected GitHub and Google Drive
Ask: "Read the NUS scientific skill at https://github.com/Dossiya-SE/Agentic-AI-for-Zotero/blob/main/.github/skills/nus-37-scientific-auditor/SKILL.md and all three references; run its full read-only audit on the current Google Drive NUS.xlsm and 37 original PDFs. Show only new corrections, missing evidence, and uncensored verification status."

## Scientific and safety guarantees
- The skill text is not an autonomous background process; it needs an active agent, access to the workbook and PDF bytes, and a per-claim evidence audit.
- Version, DOI and PDF-page matches are not complete scientific certification.
- Do not claim either Dr Damian Palin or Dr Jinying Xu endorsed this work.
- Source .xlsm is read-only unless the user separately authorizes a verified, reversible edit.
