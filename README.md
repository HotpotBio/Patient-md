# Patient.md: Framework for AI-Augmented Second Opinions and Treatment Exploration

Patients seeking second opinions often hit a wall of fragmented records and specialist bottlenecks that make it hard to ask the right questions. Patient.md proposes a single, AI-friendly Markdown case file (with optional traceability to source records) that lets patients and reviewers create tailored case versions for faster, more targeted AI-assisted review and treatment exploration.


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


## Contributing

- Use the reference system prompt above with any AI assistant to draft a Patient.md guided workflow for a specific condition.
- Provide clinical data by uploading files and/or pasting content directly into the assistant.
- Share large data in stages: for example, start with lightweight text (diagnosis, summary, and medications); then key reports (pathology, genomics, imaging reports); finally, large files (images or long reports).
- When finished uploading, confirm the Patient.md specification (text or file) before manifest generation; if needed, fetch the latest spec online and upload it.
- Run the prompt + specification + clinical inputs to generate a Patient.md manifest from the provided data.


## Citation

If you use this work, please cite:

### BibTeX

```bibtex
@article{patientmd2026,
  title        = {Patient.md: Framework for AI-Augmented Second Opinions and Treatment Exploration},
  author       = {Hu, Clarence C. and Cardona, Juan J. and Lee, Karel and Danish, Ali},
  year         = {2026},
  publisher    = {Hotpot.ai},
  address      = {Palo Alto, California, USA},
  note         = {
    1. Hotpot.ai, Palo Alto, California, USA.
    2. Department of Neurosurgery, Stanford University School of Medicine, Stanford, California, USA.
    Corresponding author: clarence@hotpot.ai
  }
}
