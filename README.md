# cloud-arch-synth
## Repository Structure

| File                                          | Description                                                                                                               |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **`archs_generator_en.ipynb`**                | **Main file** of the project. Executes the entire workflow for generating and analyzing synthetic cloud architectures. |
| `arquitecturas_etiquetadas.pkl`               | Labeled architectures dataset.                                                                                            |
| `arquitecturas_con_servicios.pkl`             | Dataset containing architectures with their list of cloud services.                                                       |
| `arquitecturas_clasificadas_con_metadata.csv` | Metadata file with classified architectures.                                                                              |
| `Bootstrap_Test.ipynb`                        | Optional notebook for running the Bootstrap .632 statistical test.                                                        |
| `Survey_results.ipynb` | Jupyter notebook with the analysis and visualization of the post-activity survey results. |
| `survey_results_group1.csv` | Raw dataset with responses to all questions from the student of group 1 survey conducted after the activity. |
| `survey_results_group2.csv` | Raw dataset with responses to all questions from the student of group 2 survey conducted after the activity. |
| `EvaluationRubric.md` | Markdown file describing the evaluation rubric used to assess student work during the activity. |
| `Survey.md` | Markdown file that describes the post-activity survey completed by the students. |
| `activity_schedule.md` | Markdown file describing the activity schedule, including the time allocation for each activity step and the checkpoints used to monitor progress and guide the final submission. |
| `activity_printout.md` | Student-facing activity handout with instructions to draw the architecture/service flow diagram and guiding questions on changes (services added/removed), design assumptions, and proposed validations/metrics. |
| `MasterMap_NOTES_ES_EN.csv` | Cloud service equivalence master map (AWS → Azure/GCP/OSS alternatives). Includes Quality (EXACT/CLOSE/APPROX/NA) and bilingual notes (Notes_ES, Notes_EN) to justify the mapping and highlight key differences. |
| `MappingEquivalencies.ipynb` | Jupyter/Colab notebook that loads MasterMap_NOTES_ES_EN.csv and provides a lookup workflow to retrieve Azure/GCP/OSS alternatives for one or more AWS services (comma-separated). |
| `MasterMap_Description.md` | Documentation guide explaining how to interpret and maintain the cloud service equivalence master map (columns, Quality, Notes, conventions, and special cases like UserCompany*/UserConsumer*).|
---

## Generalized Generation and Customization

The main notebook includes a generalized generation section, which serves as the core logic for creating synthetic architectures. From this section, users can easily modify parameters or conditions to generate architectures with specific characteristics — for example, focusing on Edge architectures or emphasizing the presence of particular cloud services. To illustrate how such adaptations can be implemented, we provide an additional complete section within the notebook that demonstrates how to generate Edge-oriented architectures. This example is intended to guide readers in customizing and extending the main generation code according to their own research goals or experimental needs.

## How to Use

### 1. Run the Main File

The core of the project is **`archs_generator_en.ipynb`**, which must be executed in a Jupyter-compatible environment (locally or in Google Colab).

Before running the first code cell, make sure to **upload the following files to your runtime environment**:

- `arquitecturas_etiquetadas.pkl`
- `arquitecturas_con_servicios.pkl`
- `arquitecturas_clasificadas_con_metadata.csv`

Once these files are loaded, you can start executing the notebook from the **first code cell**.

---

### 2. Optional: Bootstrap Test

The repository includes an additional file named **`Bootstrap_Test.ipynb`**.  
This notebook is **optional** and should only be used if you wish to perform a **Bootstrap .632 statistical test**.

To use it:

1. **Download** the main file `archs_generator_en.ipynb` and run it **locally** (recommended, since execution in Google Colab is significantly slower for this part).
2. Copy **all the code** from `Bootstrap_Test.ipynb`.
3. Paste it at the **end of the main notebook** (`archs_generator_en.ipynb`).
4. Execute the appended cells to run the Bootstrap test.

---

## Survey and Evaluation Materials (Used in the classroom activity)

In addition to the generation and analysis code, the repository includes files related to the **post-activity survey** and the **evaluation rubric** used in the learning activity:

-  **`Survey_results.ipynb`** analyzes the results of the survey conducted with students after the activity and generates visualizations based on their responses.  
-  **`survey_results_group1.csv`** contains the complete dataset with all survey responses to each question (Group 1).  
-  **`survey_results_group2.csv`** contains the complete dataset with all survey responses to each question (Group 2). 
-  **`EvaluationRubric.md`** details the rubric used to assess student work, including criteria, descriptions, and point allocations.
-  **`Survey.md`** details the post-activity survey completed by the students.
-  **`activity_schedule.md`** outlines the classroom activity schedule, specifying the time allocation for each step (Edge vs. HPC explanation, diagramming, Q1–Q3) and the progress checkpoints used to keep teams on track through submission.
- **`activity_printout.md`** provides the student-facing activity handout. It includes instructions to draw the architecture/service flow diagram and a set of guiding questions covering (i) services added/removed (up to three changes), (ii) design assumptions (Edge vs. HPC processing, stream vs. batch data movement, and storage choices), and (iii) proposed validations and metrics (latency, throughput, scalability, and fault tolerance).

---

## Service Equivalence Mapping (AWS ↔ Azure ↔ GCP ↔ OSS)

This section documents the Cloud Service Equivalence Toolkit, including the MasterMap (AWS → Azure/GCP/OSS alternatives), its interpretation guide (MasterMap_Description.md), and the Colab workflow (MappingEquivalencies.ipynb) used to query and export equivalences for one or multiple services.

- **`MasterMap_NOTES_ES_EN.csv`** This master map is a **living document**. The listed equivalences and notes are **not fixed** and may change over time due to cloud provider updates (new services, deprecations, feature changes) and differing architectural interpretations. The mapping is also **explicitly instructor-editable**: the instructor running the activity may refine, correct, or extend entries based on course needs and feedback. This is **intended and valid** for the activity—the goal is to provide a practical baseline for cross-cloud reasoning, not an immutable “official truth”.**FOR USAGE AND MAINTENANCE DETAILS, PLEASE REVIEW "MasterMap_Description.md".**
- **`MappingEquivalencies.ipynb`** Jupyter/Google Colab notebook that queries the equivalence dictionary by accepting one or multiple comma-separated service keys (e.g., S3, EKS, EC2) and returning their mapped values (Azure, GCP, Open Source, Quality, Notes_EN). It handles UserCompany* / UserConsumer* as end-user actors (not cloud services) and exports the lookup results to a CSV saved in the same folder as the dictionary, with an underscore-joined filename.
- **`MasterMap_Description.md`** Complete documentation for the Cloud Service Equivalence Master Map. It defines the file scope and intent (AWS → Azure/GCP/OSS alternatives), explains what each row represents (cloud-service entries vs. special non-cloud actor/end-user entries), and details how to interpret each column (Servicio AWS, Azure, GCP, Open Source, Quality, Notes_ES, Notes_EN). It formalizes the meaning of Quality (EXACT, CLOSE, APPROX, NA), clarifies how to read multi-option mappings (A / B, A + B, -, empty cells), and explains the role of Notes as justification and tradeoff documentation. It also documents special handling for UserCompany* / UserConsumer* entries as end-user actors/endpoints (not cloud services) and includes a short disclaimer that the map is instructor-editable and expected to evolve with cloud changes and course feedback.


---

## Recommended Environment

- **Local execution (recommended):** For running the Bootstrap test and other compute-intensive tasks (K-Fold).  
- **Google Colab:** Suitable for running core workflow, generation processes, but not ideal for heavy analysis like bootstrap.

---
