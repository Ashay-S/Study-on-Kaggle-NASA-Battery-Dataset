# README

## NASA Battery Dataset Analysis

### Objective
This project analyzes the NASA Battery Dataset, downloaded from [Kaggle](https://www.kaggle.com/datasets/patrickfleith/nasa-battery-dataset), and ran on [this](https://colab.research.google.com/drive/1nUiMgO0xFMbGMQgjjNLIcHEowejlrYNu?usp=sharing) Google Colab Notebook to evaluate the aging of Li-ion batteries based on their operational profiles. The goal is to create visualizations using Plotly that demonstrate how the following parameters evolve over repeated charge/discharge cycles:

- **Battery Impedance**: Derived from electrochemical impedance spectroscopy.
- **Re (Electrolyte Resistance)**: Estimated resistance of the battery's electrolyte (Ohms).
- **Rct (Charge Transfer Resistance)**: Estimated resistance associated with the charge transfer process (Ohms).

### Dataset Description
The dataset includes impedance measurements obtained through electrochemical impedance spectroscopy (EIS), ranging from 0.1Hz to 5kHz. These measurements were collected as the batteries aged during repeated charge/discharge cycles. The experiments were terminated when the batteries reached their end-of-life (EOL) criteria.

---

### Steps to Process the Dataset and Generate Results

1. **Environment Setup**:
   - Configured Kaggle API using the `kaggle.json` file to download the dataset directly from Kaggle.
   - Installed required Python libraries such as `pandas`, `plotly`, `numpy`, `pillow`, `fpdf`, and `kaleido`.

2. **Dataset Download and Preparation**:
   - Downloaded and extracted the dataset using the Kaggle API.
   - Defined the paths for metadata, battery data files, and extra information.

3. **Metadata Handling**:
   - Loaded the `metadata.csv` file to extract relevant battery information.
   - Ensured that the `Re` and `Rct` columns were numeric and removed rows with missing values in critical columns (`Re`, `Rct`, `filename`, `battery_id`).

4. **Processing Individual Battery Files**:
   - For each battery, read the corresponding data file containing impedance data.
   - Calculated the magnitude of impedance (`Battery_impedance`) if the column existed.
   - Computed the average impedance per cycle.
   - Stored `Cycle_Index`, `Re`, `Rct`, and `Impedance` values in a structured format for further analysis.

5. **Visualization with Plotly**:
   - Created individual line plots for:
     - **Re vs. Cycle Index**: To observe changes in electrolyte resistance over cycles.
     - **Rct vs. Cycle Index**: To visualize the charge transfer resistance evolution.
   - Generated combined plots showing `Re`, `Rct`, and `Impedance` trends over cycles.
   - Saved all plots as images for further use.

6. **Exporting Results**:
   - Saved all plots as PNG files using Plotly's `kaleido` renderer.
   - Compiled the generated plots into a single PDF using the `FPDF` library for easy sharing and presentation.

---

### Output
- **Plots**:
  - Individual plots for `Re`, `Rct`, and combined parameters (Re, Rct, and Impedance) for each battery.
  - Plots demonstrate how key battery parameters evolve as the battery ages over repeated charge/discharge cycles.
  
- **PDF File**:
  - All plots are compiled into a single PDF (`all_battery_plots.pdf`), making it convenient to review and analyze the results.
  - The PDF file is stored in the `plots` directory along with the PNG images of individual graphs.

---

### Key Libraries Used
- **`pandas`**: For data loading, cleaning, and manipulation.
- **`plotly`**: For creating interactive and visually appealing plots.
- **`numpy`**: For numerical computations.
- **`fpdf`**: For compiling plots into a PDF document.
- **`kaleido`**: For saving Plotly graphs as images.

---

### How to Run
1. **Setup Environment**:
   - Ensure Python and necessary libraries are installed.
   - Download the dataset using Kaggle API.

2. **Run the Script**:
   - The script processes the metadata and data files, computes the required parameters, and generates the plots.

3. **Review Output**:
   - Open the `all_battery_plots.pdf` file in the `plots` folder to view the compiled visualizations.
   - Individual PNG files of the plots are also available in the same folder.

---

### Conclusion
This project successfully visualizes the changes in key battery parameters (`Re`, `Rct`, and Impedance`) as Li-ion batteries age over charge/discharge cycles. The provided PDF file contains all the visualizations for easy reference and analysis, fulfilling the assignment's requirements.

