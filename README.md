# Patient.md: Framework to Organize Medical Data for AI Assistants

Patient.md is a framework to organize medical data for artificial intelligence (AI) assistants. It defines a schema for representing cases as a single Markdown file comprising standard clinical details and condition-specific data.

By structuring medical data into one file designed for AI assistant context windows, Patient.md can simplify case sharing for second opinions and promote patient autonomy. It may further enable AI assistants to act as personalized tutors, lowering barriers to case understanding and treatment exploration for both physicians and patients.

Finally, the Patient.md format creates a foundation for AI agent workflows such as case monitoring and clinical trial matching.

Note: Patient.md is for educational and productivity purposes only. It cannot offer medical advice and cannot replace clinical judgment.


## 🚀 Quick Start

Choose an AI assistant, share medical data, and the agent will automatically generate your `PATIENT.md` manifest. All are free to use.

### 1. Custom GPT
* **Link:** [Patient-md Custom GPT](https://chatgpt.com/g/g-69b7376d9d008191a097dab45aa5c995-patient-md)
* **How to use:** Open the link, then share your medical data (such as notes or clinical reports). The custom GPT transforms this data into one or more Patient.md manifests.

### 2. Claude Skill
* **File:** [`agents/claude/patient-md/SKILL.md`](agents/claude/patient-md/SKILL.md)
* **How to use:** In Claude, go to **Customize** → **Create new skill** → **Upload a skill**, and upload our `SKILL.md` file. Then type `/patient-md-architect` in your chat.


## 📖 Why Patient.md?

Current approaches to organizing patient data are not designed for AI assistants like GPT and Gemini. Scattered medical records and volumes of clinical data can overwhelm both human reviewers and AI assistants. Patient.md addresses this by:

* **Consolidating Data:** Combines standard clinical details and complex modules (like molecular testing) into one file designed for AI context windows.
* **Tailored Understanding:** Tailors understanding of conditions for different people, adapting information depth to someone's background.
* **Maintaining Traceability:** Uses an optional registry to link summaries directly to source patient records.


## 🤝 How to Help

* Create methods (e.g., OpenClaw integration) to automate the creation of Patient.md manifests.
* Create automated agents and pipelines to help patients explore the treatment landscape and stay current on the literature.
* Create prompts and workflows for specific conditions, such as never-smoker non-small cell lung cancer, triple-negative breast cancer, or Alzheimer’s disease.


## 📚 Citation

If you use this work, please cite:

```bibtex
@article{patientmd2026,
  title        = {Patient.md: Framework to Organize Medical Data for AI Assistants},
  author       = {Hu, Clarence C. and Cardona, Juan J. and Lee, Karel and Danish, Ali and Kamtam, Devanish N.},
  year         = {2026},
  publisher    = {Hotpot.ai},
  address      = {Palo Alto, California, USA},
  note         = {
    Affiliations:
      1. Hotpot.ai, Palo Alto, California, USA.
      2. Department of Neurosurgery, Stanford University School of Medicine, Stanford, California, USA.
      3. Division of Thoracic Surgery, Department of Cardiothoracic Surgery, Stanford University School of Medicine, Stanford, California, USA
    Corresponding author: clarence@hotpot.ai
  }
}
