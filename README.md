# Replication Code and Data: Conspiracy theories are central to the complex system of predictors of Italian vaccine hesitancy

This repository contains the data, intermediate objects, and R scripts necessary to fully reproduce the analyses, tables, and figures for the associated research article.

## Workflow and Repository Structure

This project is structured following the **IPO (Input-Process-Output) protocol** to ensure a clean, transparent, and reproducible workflow. 

### 1. `Input/`
This folder contains the raw data required to begin the analysis (e.g., the ResPOnsE dataset and valid cases spreadsheets). 
* **Fast Reproducibility:** To save time and avoid forcing users to re-run highly resource-intensive operations (such as non-parametric case-dropping bootstraps for centrality stability and network edge accuracy), this folder also includes pre-computed `.rds` objects (e.g., `CommunityStabTotal.rds`, `edgeacc.rds`, `centstab.rds`). 
* If you wish to re-run these heavy computations from scratch, you can uncomment the respective lines in the scripts.

### 2. Processing (Scripts)
The analysis is divided into cleanly separated R Markdown (`.Rmd`) scripts:
* **`1 - Database.Rmd`**: Handles raw data ingestion, filtering, variable recoding (polarity inversion, index creation), Principal Component Analysis (PCA) for index dimensionality, and generates the clean dataset (`W3.rds`) along with descriptive statistics.
* **`2 - mgm_r1.Rmd`**: Contains the core complex systems analysis. It fits the Mixed Graphical Models (MGM), performs community detection, computes network predictability and centrality metrics, executes robustness checks (bootstrapping, Network Comparison Tests), fits standard logistic regressions, and extracts coefficients for structural comparisons.

### 3. `Output/`
All generated artifacts are automatically routed here.
* **`Article/`**: Contains the main figures and tables used in the primary manuscript (e.g., predictability network plots, centrality scatterplots, summary tables).
* **`Supplement/`**: Contains additional figures and robustness checks for the Supplementary Information (e.g., community stability plots, bootstrap confidence intervals, edge weight matrices).

## How to Reproduce the Analysis

The scripts are designed with maximum flexibility in mind. You can run them **sequentially** from start to finish, or you can run them **in isolation**. 

Because all necessary intermediate files (like the cleaned `W3.rds` dataset and the heavy computational objects) are already provided in the `Input/` folder, you can open `2 - mgm_r1.Rmd` and run it immediately without needing to execute script 1 first.

### Requirements & Setup
1. **R Environment:** Ensure you have a recent version of R and RStudio installed.
2. **Project File:** It is highly recommended to open this repository using the provided `.Rproj` file. The scripts utilize the `here` package, which automatically resolves relative file paths based on the project root directory. This eliminates the need to manually set your working directory using `setwd()`.
3. **Package Management:** The scripts use the `pacman` package to automatically check for, install, and load all required dependencies (such as `tidyverse`, `qgraph`, `mgm`, `bootnet`, etc.). 

### Execution
Simply open the desired `.Rmd` file in RStudio and click "Run All" or knit the document to generate the environment objects and output files. 
