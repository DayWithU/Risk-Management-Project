# Day 5 — Intake (Google Form → Google Sheets) instructions

Goal
Create a simple Google Form so stakeholders can submit new risks; have the linked Google Sheet compute Score and Priority automatically.

Quick overview
1. Create Google Form with questions from templates/google_form_questions.txt.
2. Link the form to a Google Sheet: Responses → Create spreadsheet.
3. In the Responses sheet, add two new columns: Score and Priority, and paste the formulas below.
4. Add data validation for Likelihood and Impact (1–5).
5. When you want to publish new entries to the repo, Export → CSV from the sheet and append to artifacts/risk-register.csv (or copy rows manually).

Exact form → sheet column mapping (typical "Form Responses 1" sheet)
- Column A: Timestamp (auto)
- Column B: Title
- Column C: Description
- Column D: Category
- Column E: Likelihood (1-5)
- Column F: Impact (1-5)
- Column G: Owner
- Column H: Mitigation
- Column I: Status (Open/In Progress/Mitigated/Closed)
- Column J.. : We'll add Score (next column) and Priority (after Score)

Form responses sheet formulas (paste into row 1 header then into row 2 for formulas):

- Add header cells after existing columns: in the header row add `Score` and `Priority` as new column titles.

- Score formula (put in Score column for row 2 and fill down):
`=IF(AND(ISNUMBER(E2),ISNUMBER(F2)),E2*F2,"")`

- Priority formula (put in Priority column for row 2 and fill down):
`=IF(G2="","",IF(G2<=6,"Low",IF(G2<=12,"Medium",IF(G2<=18,"High","Critical"))))`
Note: replace `G2` with the Score cell reference in your sheet if Score is in a different column (for example, if Score is in J2 then use `J2`).

Data validation (Likelihood & Impact)
- Select Likelihood column (E) → Data → Data validation → Criteria: Number → Between 1 and 5 → Show warning or Reject input.
- Repeat for Impact column (F).

Optional: Add a "Processed" column to mark rows you’ve copied into the repo (checkbox or text). This helps avoid duplicates.

How to move new Form responses into the repo
- Option 1 (manual, recommended for now):
  1. In the sheet, filter rows you haven’t yet exported (Processed column unchecked).
  2. File → Download → Comma-separated values (.csv)
  3. Open CSV and append rows to `artifacts/risk-register.csv` (maintain column order and compute ID).
  4. Commit and push as usual.
- Option 2 (automated, later): Use Google Apps Script to POST new rows to a GitHub repo or update a Google Drive file; this requires OAuth and is more advanced. We can do this after Day 7.

Tips
- Keep the same column order between Form Responses and artifacts/risk-register.csv to simplify appending.
- Add a unique ID when you append to artifacts/risk-register.csv (increment last ID).
- Mark rows as Processed after export to avoid duplicates.

What you learn today
- How to build a form-based intake for risks and connect it to a live sheet.
- How to add formulas so the scoring is automatic and consistent.
- A repeatable small process for stakeholders to submit risks (good governance + interview talking point).
