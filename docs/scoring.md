# Scoring — How we compute priority (short)

Score formula
- Score = Likelihood × Impact
  - Likelihood: 1 (very unlikely) to 5 (very likely)
  - Impact: 1 (minor) to 5 (severe)
  - Score range: 1–25

Priority bands (example)
- 1–6: Low
- 7–12: Medium
- 13–18: High
- 19–25: Critical

How to use
1. For each risk, estimate Likelihood (1–5) and Impact (1–5).
2. Compute Score = Likelihood × Impact.
3. Map the Score into a Priority band.
4. Assign an Owner and propose one or more Mitigations.
5. If a mitigation is implemented, estimate Residual Likelihood/Impact and compute Residual Score (optional).

Example
- Risk: Payment gateway outage  
  - Likelihood = 4, Impact = 5 → Score = 20 → Priority = Critical  
  - Mitigation: Add retry logic and alternate gateway → Residual Likelihood might reduce to 2 (Residual Score = 10 → Medium)

Tips for consistency
- Be conservative with Impact for customer-facing failures (err on the higher side).
- Use the same scale across the register. Document any deviations in the Notes column.
- When in doubt, assign an Owner (even "You") so the risk has someone responsible.

Why this matters (short)
- The Score lets you prioritise mitigations and focus limited effort on the highest-exposure risks.
- The scoring doc is a small governance artifact you can show in interviews to explain your decision process.
