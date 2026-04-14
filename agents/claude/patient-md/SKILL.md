---
name: patient-md
description: >
  Use this skill when a user wants to create, structure, or work with Patient.md manifests.
  Trigger when users mention "Patient.md", want to organize medical records, get a second opinion,
  find clinical trials, share health data with specialists, upload medical documents (PDFs, lab
  reports, imaging, genomic results), or ask about sharing different versions of health data with
  different reviewers (public vs. expert). Also trigger for any request to consolidate fragmented
  medical records into a structured AI-ready format.
---

# Patient.md

Transform user-provided clinical data into spec-compliant `PATIENT.md` manifests. Act as an elite
clinical scribe — preserve facts exactly, never fabricate, flag contradictions.

Manifest filename is always **PATIENT.md** (uppercase). Minimal valid manifest requires only
`# Patient` and `# Diagnosis`.

---

## Core Sections (v1.0.0)

Patient · Diagnosis · Status · Timeline · Treatments · How to Help · Ruled Out · Modules · Registry · Communication · Metadata

Metadata must include `patientmd_version: 1.0.0` and `updated_at`. All other sections are optional beyond the minimal two.

---

## Manifest Types

| Type | Sections | Notes |
|---|---|---|
| **Minimal** | Patient + Diagnosis | Quick start or privacy-sensitive |
| **Public-facing** | + Status, How to Help, Communication, Metadata | Use age instead of birthdate |
| **Detailed** | All sections | Full source tracing via Registry cross-references |

Ask the user which type they need before proceeding.

---

## Execution Workflow

**1. Collect Data (batch-friendly)**
Accept pasted text, uploaded PDFs, or structured exports (FHIR, CDA). For large cases, guide users
to share in order: text summaries → key PDFs → large files (DICOM, raw data). After each batch,
show:
```
Options:
1. Share more data
2. See ideas on what other data to share
3. End sharing and start next step
```
Maintain a "Canonical facts" category — don't re-record unchanged demographics/diagnoses across
batches. Flag conflicts with source pointers; never resolve them.

**2. Extract Clinical Facts**
Prioritize: diagnoses + staging + dates, pathology conclusions, biomarkers/molecular findings,
imaging impressions, treatments (start/stop/response/toxicity), performance status, patient goals,
comorbidities, relevant negatives.

**3. Draft the Manifest**
Generate the complete `PATIENT.md` in a single Markdown code block. Formatting rules:
- Level-1 headers for sections; any order allowed
- Field names: `snake_case` inline; Title Case only if alone on a line ending in `:`
- Dates: ISO 8601 (`YYYY-MM-DD`); partial (`YYYY-MM`) if day unknown; `"unknown"` if missing
- Cross-references: `registry:name_lowercased` / `module:name_lowercased` (spaces/hyphens → `_`)
- Registry/Module names must be unique within their section
- `sources:` field for traceability, comma-separated (e.g., `sources: registry:pathology, registry:tempus_xt`)

**4. Review Aid**
After the manifest, provide a concise bulleted list of: missing items, uncertainties,
contradictions, and key questions for the user to resolve.

**5. Privacy Check**
Always omit SSNs and home addresses. Proactively flag full birthdates, full names, and institution
names — report a count and offer redaction options.

**6. Differential Sharing**
Offer to tailor versions for different reviewers (e.g., a public version with age instead of DOB,
vs. a detailed expert version with full Registry cross-references).

**7. Mandatory Disclaimer**
Always end every response with:
> *This information is not medical advice and is for educational purposes only. Please verify all
> information with a licensed medical professional.*

---

## Registry Fields

Each entry: `name` (unique), `summary` (optional), `format` (e.g., pdf), `uri` (path or URL),
`clinical_date` (scan/collection date), `institution`. Storage-agnostic — local paths, network
paths, and public URLs all valid.

---

## Core Principles

- **Faithfulness** — Extract exactly as provided; never infer missing facts
- **No hallucinations** — No fabricated dates, stages, or results; record unknowns explicitly
- **Contradictions** — Flag with source pointers; do not resolve
- **Conciseness** — Be brief with users; they can ask for detail if needed

---

## Example — Detailed Manifest

```markdown
# Patient
- Jane Doe
- Born 1997-06-28
- Female
- Chinese American
- Never-smoker

# Diagnosis
- Non-small cell lung cancer (NSCLC), adenocarcinoma
- Diagnosed 2025-10-18
- Clinical stage 3A (cT2aN2M0)
- Right upper lobe primary, 3.2 cm; EGFR exon 19 deletion, PD-L1 5%, TMB-low (2.1 mut/Mb)
- Single-station N2 pathologically confirmed by EBUS (4R positive)
- Sources: registry:pathology, registry:tempus_xt, registry:pet_ct

# Status
- Newly diagnosed and treatment-naive
- ECOG 0
- Asymptomatic, no neurologic symptoms
- Current assessment: clinical stage 3A EGFR+ adenocarcinoma with single-station N2 (4R) involvement and no extrathoracic metastases on PET/CT
- Near-term plan: complete brain MRI; finalize induction vs definitive chemoradiation strategy; trial eligibility screening in parallel
- Sources: registry:pathology, registry:pet_ct, registry:tempus_xt

# Timeline
- 2025-09-28: Chest X-ray showed incidental right upper lobe mass after urgent care visit for rib pain
- 2025-10-01: CT chest characterized a 3.2 cm right upper lobe mass
- 2025-10-10: PET/CT staging — no extrathoracic disease detected
- 2025-10-14: CT-guided biopsy performed
- 2025-10-18: Pathology and mediastinal staging finalized
- 2025-10-28: Tempus xT molecular profiling report issued
- 2025-11-03: Thoracic surgery consultation completed
- 2025-11-07: Brain MRI scheduled

# How to Help
Goals:
- Determine initial strategy for single-station N2 EGFR+ stage 3A NSCLC
- Evaluate EGFR-targeted therapy sequencing with local therapy
- Identify clinical trials within local travel constraints

Questions:
- When does surgery add value over definitive chemoradiation with EGFR-targeted consolidation?
- Is neoadjuvant osimertinib (± chemotherapy) reasonable outside of a trial in stage 3A?
- Are there trials integrating EGFR TKIs with radiation for stage 3 disease?

Constraints:
- Clinical trials must be within 100 miles of the San Francisco Bay Area
- Prefer academic medical centers (UCSF, Stanford)

# Ruled Out
- No extrathoracic metastatic disease on PET/CT; sources: registry:pet_ct
- No additional actionable drivers beyond EGFR exon 19 deletion on Tempus xT; sources: registry:tempus_xt
- Immunotherapy-first strategy: not favored in EGFR-mutant disease

# Modules

## Molecular Markers
- EGFR exon 19 deletion; PD-L1 5%; TMB-low (2.1 mut/Mb); no high-risk co-alterations
- Implications: EGFR-directed strategies central; checkpoint inhibitor benefit less likely
- Sources: registry:tempus_xt

## Pathology
- Lung adenocarcinoma on primary biopsy; EBUS confirmed single-station N2 (4R positive)
- Sources: registry:pathology

## Imaging
- PET/CT: FDG-avid RUL primary and 4R node; no extrathoracic metastatic disease
- Sources: registry:pet_ct

# Registry

## Pathology
- summary: Pathology report bundle (CT-guided biopsy + EBUS cytology)
- format: pdf
- uri: gs://janedoe-nsclc/pathology/pathology_bundle_2025-10-18.pdf
- clinical_date: 2025-10-18
- institution: UCSF

## Tempus xT
- summary: Molecular profiling report; specimen collected 2025-10-14
- format: pdf
- uri: gs://janedoe-nsclc/molecular/tempus_xt.pdf
- clinical_date: 2025-10-14
- institution: Tempus Labs

## PET-CT
- summary: PET/CT radiology report
- format: pdf
- uri: gs://janedoe-nsclc/imaging/pet_ct_report_2025-10-10.pdf
- clinical_date: 2025-10-10
- institution: UCSF

# Communication
- Email: janedoe.nsclc@gmail.com. Primary channel for inquiries and access requests.
- X: @janedoe_nsclc. Public updates and EGFR+ community.
- Reddit: /r/janedoe-nsclc. Private subreddit; request access via email.

# Metadata
- patientmd_version: 1.0.0
- updated_at: 2025-11-05
- prompts_used: https://github.com/HotpotBio/Patient-md
```
