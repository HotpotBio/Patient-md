# Patient.md: Framework for AI-Augmented Second Opinions and Treatment Exploration

Current approaches to organizing patient data focus on machine-to-machine exchange or human-to-human handoff rather than joint human-AI investigation. Instead of structuring patient data for human consumption or machine-to-machine communication, Patient.md proposes a framework for consolidating medical data into a single AI-friendly file. This may allow patients to more easily seek second opinions and explore treatment options with AI assistants like ChatGPT and Gemini.

## Abstract

### Background
Poorly understood conditions and specialist shortages may compel patients to take agency over their care, seeking second opinions or exploring treatment options on their own. Yet this journey is often hindered by fragmented medical records and the need for expert interpretation across specialties such as pathology and disease biology. Clinicians, family members, and patient advocates must navigate volumes of data, with no systematic way to tailor case review or ask targeted questions.

### Methods
We propose Patient.md, a framework for artificial intelligence (AI)-augmented second opinions and treatment exploration. Patient.md defines a schema for representing cases as a single Markdown file comprising standard clinical details and condition-specific data such as molecular testing in cancer care. An optional registry links summaries to patient records for traceability and efficient retrieval in AI assistant workflows. The framework enables tailored files for different reviewers, supporting local or cloud operation, and provides a system prompt for drafting Patient.md files via guided workflows.

### Results
We demonstrate Patient.md with a lung cancer patient sharing three case versions: minimal, public-facing for tracking and trial matching, and detailed for deeper investigation.

### Conclusion
By consolidating medical data into a single AI-friendly file, Patient.md may enable patients to more easily seek second opinions and explore treatment options with AI assistants like ChatGPT and Gemini. The framework allows AI assistants to act as personalized tutors and promote patient autonomy, lowering the barrier for understanding the condition, asking targeted questions, and gaining informed perspectives.


## Reference System Prompt
The framework uses a system prompt to transform user-provided clinical data into one or more Patient.md manifests via guided workflows.

- Prompt: [`prompts/system_prompt.md`](prompts/system_prompt.md)
- Version: v1.0.0


## How to Use Patient.md

- Use the reference system prompt above with any AI assistant to draft a Patient.md guided workflow for a specific condition.
- Provide clinical data by uploading files and/or pasting content directly into the assistant.
- Share large data in stages: for example, start with lightweight text (diagnosis, summary, and medications); then key reports (pathology, genomics, imaging reports); finally, large files (images or long reports).
- When finished uploading data, upload or paste in the Patient.md specification.
- Run the prompt + specification + clinical inputs to generate a Patient.md manifest from the provided data.

## How to Help

- Create methods (e.g., OpenClaw integration) to automate the creation of Patient.md manifests.
- Create prompts and workflows for specific conditions, such as never-smoker non-small cell lung cancer or triple-negative breast cancer.


## Citation

If you use this work, please cite:

### BibTeX

```bibtex
@article{patientmd2026,
  title        = {Patient.md: Framework for AI-Augmented Second Opinions and Treatment Exploration},
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
