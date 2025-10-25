# **Doxy-PEP Individual-based Model**

This repository contains the source code for the Doxycycline Post-Exposure Prophylaxis (Doxy-PEP) individual-based model, as described in our manuscript submitted to *Nature Communications*. The model simulates STI transmission dynamics (*Neisseria gonorrhoeae*, *Chlamydia trachomatis*, and *Treponema pallidum*) and evaluates the impact of various Doxy-PEP intervention strategies.

***

## **1. System Requirements**

The model has been tested on the following environments:

* **Operating Systems**:
    * Windows 11
    * macOS 12.6
    * Linux (Ubuntu 22.04)
* **Software Environment**:
    * Python 3.10+ (The model was tested with version 3.12.3).
    * An IDE such as Spyder (v5.4.3+) or VSCode is recommended for running the scripts.
* **Python Dependencies**:
    The model relies on several Python packages. The packages listed below are included in standard Anaconda distributions but can also be installed manually.
    * **External Packages (Installation Required)**:
        * `numpy` (~1.26.4)
        * `pandas` (~2.2.1)
        * `matplotlib` (~3.8.4)
        * `scipy` (~1.13.0)
        * `joblib` (~1.4.0)
        * `openpyxl` (for reading `.xlsx` files with pandas)
    * **Standard Libraries (No Installation Required)**:
        * `pickle` (for loading/saving data files)
        * `datetime` (for timing the simulation)
        * `importlib` (for reloading modules during development)
* **Hardware Requirements**:
    * **CPU**: A multi-core processor is highly recommended to take advantage of parallel processing. The runtimes noted in this document were benchmarked on a system using **dual Intel Xeon Platinum 8458P processors** (88 cores / 176 threads total).
    * **RAM**: Minimum 32 GB of RAM is recommended for running the full simulation with parallel processing.
    * **Storage**: Approximately **3 GB** of free space is needed for the output data files (`Results_of_All_ParameterSets.pkl` and intermediate outputs).

***

## **2. Installation Guide**

**Estimated Installation Time**: 15-20 minutes.

We recommend using the **Anaconda Distribution** of Python, as it simplifies package management.

1.  **Install Anaconda**: Download and install Anaconda from the official website: [anaconda.com/download](https://www.anaconda.com/download).
2.  **Create an Environment (Recommended)**: Open the Anaconda Prompt (or terminal on macOS/Linux) and create a dedicated environment to avoid package conflicts:
    ```bash
    conda create -n doxy_pep_env python=3.12
    conda activate doxy_pep_env
    ```
3.  **Install Packages**: Install the required external libraries into the new environment:
    ```bash
    conda install -c conda-forge numpy pandas matplotlib scipy joblib openpyxl
    ```
4.  **Download Project Files**: Download or clone this repository to your local machine and set it as the working directory in your IDE. The expected folder structure, including the pre-generated results file, is:
    ```
    Doxy_PEP_python/
    ├── README.md
    ├── Doxy_PEP_Simulation_1024.py
    ├── Doxy_PEP_Simu_functions_1024.py
    ├── Doxy_PEP_Analysis_Visualization_1024.py
    ├── Doxy_PEP_Ana_Vis_functions_1024.py
    ├── Data_tobe_called/
    └── Data_output/
    ```

***

## **3. Demo and Reproduction Instructions**

This section provides complete instructions on how to run the provided software and data to reproduce the results presented in our manuscript.

### **Stage 1: Run the Core Simulation**

This step runs the main individual-based model to simulate STI transmission across multiple parameter sets and intervention scenarios.

* **Instructions**:
    1.  Open `Doxy_PEP_Simulation_1024.py` in your IDE (e.g., Spyder).
    2.  Run the script.
* **Expected Output**: A single file named `Results_of_All_ParameterSets.pkl` will be created in the `Data_tobe_called/` folder. This file contains the complete results from all simulation runs.
* **Expected Run Time**: Approximately **30 hours** on dual Intel Xeon Platinum 8458P processors (88 cores / 176 threads).
* **Note**: To facilitate rapid reproduction of our results, we have provided the output file from this stage, `Results_of_All_ParameterSets.pkl`, in the `Data_tobe_called/` folder. This file was generated using the hardware specified in Section 1.

### **Stage 2: Generate Analysis and Visualizations**

This step processes the simulation output to generate the figures and tables for the manuscript.

* **Instructions**:
    1.  Open `Doxy_PEP_Analysis_Visualization_1024.py` in your IDE.
    2.  Run the script.
* **Expected Output**:
    1.  **Saved Figures**: Four PDF files will be saved in the `Data_output/` folder (`STI_Incidence.pdf`, `NG_Resistance_Trends.pdf`, etc.).
    2.  **Displayed Plots**: Additional plots will be generated and displayed in your IDE's plot pane, including efficient frontier plots and sensitivity analysis plots. An example is shown below:
        ![Example of plots displayed in the IDE](Data_output/Expected_outputs_in_spyder.png)
* **Expected Run Time**: Approximately **5 minutes**.

***

## **4. Instructions for Use**

The primary purpose of this software package is to ensure the full reproducibility of the results presented in our manuscript.

Given that the full functionality of the code—including its handling of large datasets, parallel processing for simulations, and complex statistical analyses—is best demonstrated with the complete dataset, we have chosen to use the original data files from our study for the demonstration in Section 3.

Therefore, the instructions for using this software to replicate our findings are detailed in **Section 3**.
