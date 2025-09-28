# cloud-arch-synth
Repository Structure

| File                                          | Description                                                                                                               |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **`archs_generator_en.ipynb`**                | **Main file** of the project. Executes the entire workflow for generating and analyzing synthetic cloud architectures. |
| `arquitecturas_etiquetadas.pkl`               | Labeled architectures dataset.                                                                                            |
| `arquitecturas_con_servicios.pkl`             | Dataset containing architectures with their list of cloud services.                                                       |
| `arquitecturas_clasificadas_con_metadata.csv` | Metadata file with classified architectures.                                                                              |
| `Bootstrap_Test.ipynb`                        | Optional notebook for running the Bootstrap .632 statistical test.                                                        |


The main notebook includes a generalized generation section, which serves as the core logic for creating synthetic architectures. From this section, users can easily modify parameters or conditions to generate architectures with specific characteristics — for example, focusing on Edge architectures or emphasizing the presence of particular cloud services. To illustrate how such adaptations can be implemented, we provide an additional complete section within the notebook that demonstrates how to generate Edge-oriented architectures. This example is intended to guide readers in customizing and extending the main generation code according to their own research goals or experimental needs.

How to Use

1. Run the Main File

The core of the project is archs_generator_en.ipynb, which must be executed in a Jupyter-compatible environment (locally or in Google Colab).

Before running the first code cell, make sure to upload the following files to your runtime environment:

arquitecturas_etiquetadas.pkl

arquitecturas_con_servicios.pkl

arquitecturas_clasificadas_con_metadata.csv

Once these files are loaded, you can start executing the notebook from the first code cell.


2. Optional: Bootstrap Test

The repository includes an additional file named Bootstrap_Test.ipynb.
This notebook is optional and should only be used if you wish to perform a Bootstrap .632 statistical test.

To use it:

Download the main file archs_generator_en.ipynb and run it locally (recommended, since execution in Google Colab is significantly slower for this part).

Copy all the code from Bootstrap_Test.ipynb.

Paste it at the end of the main notebook (archs_generator_en.ipynb).

Execute the appended cells to run the Bootstrap test.
