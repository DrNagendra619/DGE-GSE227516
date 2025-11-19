# DGE-GSE227516
DGE GSE227516
# 🏃 DESeq2 DGE Pipeline: Exercise vs. Sedentary (GSE227516)

This R script automates a comprehensive and reproducible pipeline for **Differential Gene Expression (DGE)** analysis of the **GSE227516** RNA-Seq dataset. The study compares gene expression in **mouse pancreatic islets** under **Exercise** conditions versus **Sedentary** controls.

The workflow uses the robust **`DESeq2`** package, performs extensive Quality Control (QC) checks, and generates a suite of diagnostic and results plots, ensuring a complete and publication-ready analysis.

## 🚀 Key Features

* **Complete DGE Workflow:** Follows the gold-standard analysis steps using the **`DESeq2`** package, including normalization, dispersion estimation, and statistical testing.
* **Integrated QC & Transformation:** Includes **rlog** and **VST** transformations, generating plots for:
    * **Dispersion Estimates**
    * **QC Scatter Plots** (log2 vs. rlog vs. VST)
    * **QC Histograms**
* **Comprehensive Visualization:** Generates a suite of 7 informative plots:
    * **PCA Plot** for sample clustering.
    * **Sample Distance Heatmap** for sample-to-sample similarity.
    * **MA Plot** and **Volcano Plot** for DGE results.
    * **Heatmaps** for the Top 10 Up-regulated and Top 10 Down-regulated genes.
* **Filtering and Thresholding:** Filters low-count genes and identifies significant DEGs using $\text{padj} < 0.05$ and $|\text{log2FC}| > 1$.
* **Reproducible Output:** Saves the list of significant DEGs to a CSV file and records the complete session environment via `sessionInfo()`.

---

## 🔬 Analysis Overview

| Component | Method / Test | Purpose |
| :--- | :--- | :--- |
| **Dataset** | GSE227516 (External CSV Inputs) | Mouse pancreatic islet cells under Exercise vs. Sedentary conditions. |
| **DGE Tool** | `DESeq2` | Statistical method optimized for RNA-Seq count data. |
| **QC Transformation** | **rlog / VST** | Stabilizes variance for accurate plotting. |
| **Comparison** | Exercise vs. Sedentary | Identifies genes regulated by exercise. |
| **Significance** | $\text{padj} < 0.05$ and $|\text{log2FC}| > 1$ | Criteria for identifying Differentially Expressed Genes (DEGs). |

---

## 🛠️ Prerequisites and Setup

### 📦 Input Files Required

This script requires two external data files to be located in the specified relative path:

1.  **`GSE227516_counts.csv`**: The raw gene count matrix.
2.  **`sample_information.csv`**: The metadata file containing the `condition` variable (Exercise/Sedentary).

***Note:*** *The script uses specific, relative file paths (`D:/DOWNLOADS/...`). Before running, ensure these data files exist and the paths in the script are updated to your local file structure.*

### ⚙️ Execution

1.  **Download** the `DGE GSE227516.R` script and the required data files.
2.  **Ensure all packages are installed** (the script includes auto-installation checks for `DESeq2`, `RUVSeq`, `pheatmap`, etc.).
3.  **Execute** the script in your R environment:
    ```R
    source("DGE GSE227516.R")
    ```

---

## 📁 Output Files (7 Plots + 1 CSV)

The script creates an output folder structure (`result/plots/`) and saves the following files to the execution directory:

### Statistical Results

| Filename | Type | Description |
| :--- | :--- | :--- |
| `result/significant_DE_genes.csv` | CSV | Final list of genes meeting the significance criteria ($\text{padj} < 0.05$, $|\text{log2FC}| > 1$). |

### Visualization and QC Plots (`result/plots/`)

| Plot | Analysis Stage | Description |
| :--- | :--- | :--- |
| `scatter_plots.png` | QC | Comparison of $\log_2$, rlog, and VST transformations. |
| `hist_plots.png` | QC | Histograms of transformed counts to check for normalized distributions. |
| `s2s_heatmap_plot.png` | QC | **Sample-to-Sample Distance Heatmap** (rlog data) for quality assessment. |
| `pca_plot.png` | QC / Results | **Principal Component Analysis (PCA)** plot showing sample clustering by condition. |
| `dispersion_plot.png` | QC | **Dispersion Plot** showing estimated and fitted dispersion functions. |
| `ma_plot.png` | Results | **MA Plot** (Mean-Difference Plot) of $\log_2 \text{FC}$ vs. Average Expression. |
| `volcano_plot.png` | Results | **Volcano Plot** highlighting significant up- and down-regulated genes. |
| `upreg_heatmap.png` | Results | **Heatmap** of the Top 10 Up-Regulated DEGs. |
| `downreg_heatmap.png` | Results | **Heatmap** of the Top 10 Down-Regulated DEGs. |
