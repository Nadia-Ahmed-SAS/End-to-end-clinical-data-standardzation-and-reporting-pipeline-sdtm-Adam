# End-to-end-clinical-data-standardzation-and-reporting-pipeline-sdtm-Adam
SAS pipeline transforming EDC data to SDTM/ADaM and generating TLFs.

Clinical SAS Programming Portfolio: End-to-End Pipeline
Protocol ID: BEL-2026-041 (Belgium-based Human Medicine Study)
Executive Summary
I developed a robust, automated SAS-based pipeline to transform raw clinical data into submission-ready CDISC standards (SDTM & ADaM) and final TFLs. This project emphasizes Data Integrity, Regulatory Compliance (EMA), and Pharmacovigilance (PV) safety standards.
Technical Framework (The 5 Phases)
1. Environment & Ingestion Integrity
Portable Architecture: Established a macro-driven environment (&root, &study) for seamless data portability.
Audit Trail: Used PROC PRINT (NOOBS) for initial data verification and ODS Triple-Closure logic to flush system buffers, ensuring every output is physically saved and traceable.
2. SDTM Mapping (Standardization)
Compliance: Mapped raw data to SDTM IG 3.4 (DM, AE, VS, EX, LB, DS) using ATTRIB to prevent truncation.
Standardized Identifiers: Applied the z3. format for USUBJID and converted dates to ISO 8601 using VTYPE and the ?? modifier for a clean, error-free SAS Log.
Medical Coding: Integrated MedDRA terms via PROC FORMAT to ensure clinical consistency.
3. Advanced Medical Conversions
EMA Standards: Programmed mathematical normalizations in VS (Fahrenheit to Celsius, lb to kg) and LB (SI Unit conversions for Glucose/Cholesterol) to align with European regulatory requirements.
4. ADaM Derivation (Analysis Readiness)
Master Dataset (ADSL): Derived treatment start/end dates using MIN/MAX logic from Exposure data.
Safety Analysis (ADAE): Merged AE with ADSL to derive the Treatment Emergent Adverse Event (TEAE) flag, comparing onset dates with the first dose to support Pharmacovigilance safety signals.
5. TFL Generation & Validation
Outputs: Automated Tables (Disposition/Severity), Listings (Subject-level data), and Figures (Bar charts/Box plots/Pie charts) using PROC SGPLOT.
Final QC: Used %SYSFUNC and %PUT for dynamic time-stamping and version control within the SAS Log.
Key Performance Indicators (KPIs)
100% CDISC Compliance: Zero mapping errors in SDTM/ADaM domains.
Clean Log Policy: No Errors, Warnings, or "Invalid Argument" notes.
Patient Safety Focus: Automated Edit Checks (Queries) for high-severity safety alerts (e.g., future dates, extreme vitals).
