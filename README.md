# Patient.md: Framework to Organize Medical Data for AI Assistants

Current approaches to organizing patient data are not designed for AI assistants like GPT and Gemini. Instead of structuring patient data for human-only consumption or machine-to-machine communication, Patient.md proposes a framework for consolidating medical data into a single file designed for AI context windows and joint human-AI collaboration. This may allow patients to more easily understand medical conditions, share information for second opinions, and explore treatment options.

## Abstract

### Background
Poorly understood conditions and specialist shortages may compel patients to take agency over their care, yet seeking second opinions and exploring treatment options can be challenging. This journey is often slowed by scattered medical records, repeated explanations of the same history, and volumes of clinical data that can overwhelm both human reviewers and AI assistants.

### Methods
We propose Patient.md, a framework to organize medical data for artificial intelligence (AI) assistants. Patient.md defines a schema for representing cases as a single Markdown file comprising standard clinical details and condition-specific data such as molecular testing in cancer care. An optional registry links summaries to patient records for traceability and efficient retrieval in AI assistant workflows. The framework enables tailored files for different reviewers, supports local or cloud operation, and provides a system prompt for drafting Patient.md files via guided workflows.

### Results
We demonstrate Patient.md with a lung cancer patient sharing three case versions: minimal, public facing for trial matching, and detailed for deeper investigation.

### Conclusion
By consolidating medical data into one structured file designed for AI assistant context windows, Patient.md can simplify case sharing for second opinions and promote patient autonomy. It may further enable AI assistants to act as personalized tutors, lowering barriers to case understanding and treatment exploration for both physicians and patients. This structured format may also lay a foundation for AI agent workflows such as case monitoring and clinical trial matching.



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
