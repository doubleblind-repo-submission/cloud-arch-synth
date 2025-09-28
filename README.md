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
| `survey_results.csv` | Raw dataset with responses to all questions from the student survey conducted after the activity. |
| `EvaluationRubric.md` | Markdown file describing the evaluation rubric used to assess student work during the activity. |

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

## Survey and Evaluation Materials (Used in the workshop)

In addition to the generation and analysis code, the repository includes files related to the **post-activity survey** and the **evaluation rubric** used in the learning activity:

-  **`Survey_results.ipynb`** analyzes the results of the survey conducted with students after the activity and generates visualizations based on their responses.  
-  **`survey_results.csv`** contains the complete dataset with all survey responses to each question.  
-  **`EvaluationRubric.md`** details the rubric used to assess student work, including criteria, descriptions, and point allocations.


---

## Recommended Environment

- **Local execution (recommended):** For running the Bootstrap test and other compute-intensive tasks (K-Fold).  
- **Google Colab:** Suitable for running core workflow, generation processes, but not ideal for heavy analysis like bootstrap.

---
