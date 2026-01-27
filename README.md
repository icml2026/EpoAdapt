# EpoAdapt
Anonymous code, datasets, and notebooks for reproducing the experiments in the accompanying ICML submission.

## Repository Overview
This repository contains the experimental suite for "EpoAdapt" applied to Influence Maximization (IM). All core artifacts required for reproduction—including source code, datasets, and run logs—are bundled in the `EpoAdapt.zip` archive.

## Contents of `EpoAdapt.zip`
Unzipping the archive reveals the following structure. As demonstrated in the Colab notebooks, the scripts are configured to read from the shared `outdegree` folder to ensure all algorithms are evaluated on identical data.

* **`outdegree/`**: A folder containing the specific graph datasets used in all experiments (`graph100`, `graph200`, `insecta`).
* **`scripts/`**: The Python scripts for the EpoAdapt method.
* **`Results/`**: Pre-computed logs and output files from the EpoAdapt experiments.
* **`EPOL/`**: A folder containing the benchmarking script used to evaluate the competitive baselines (EPOL, POMC, and FPOMC).
    * Contains the logs in `Result_01/` demonstrating the comparison under the budget constraint ($B=100$) and computation limit ($4 \cdot n \cdot K_B$).

## External Baselines (EPOL, POMC, FPOMC)
To ensure a fair comparison, we utilized the official EPOL implementation to run the baseline algorithms.
* **Scope**: This script was used to generate results for EPOL, POMC, and FPOMC to compare against EpoAdapt.
* **Constraints**: All baselines were evaluated under the strict conditions detailed in the paper: a fixed budget of 100 and a computation limit of $4 \cdot n \cdot K_B$.
* **Source**: The script was downloaded from the official repository at [https://github.com/lamda-bbo/EPOL](https://github.com/lamda-bbo/EPOL) and configured to read from the common `outdegree/` folder for data consistency.

## Reproducibility Guide

### 1. Verification (No Run Required)
The included notebooks serve as verifiable proof of execution. They have been saved with **all cell outputs preserved**.
* Open any `.ipynb` file in `notebooks/` to inspect the code execution, runtime metrics, and final outputs reported in the paper.

### 2. Running the Experiments
To re-run the experiments:
1.  Download `EpoAdapt.zip` and upload it to your Google Drive or Colab environment.
2.  Unzip the archive.
3.  Open the desired notebook in Google Colab.
4.  **Setup**: Ensure the directory structure remains intact so that both EpoAdapt and baseline scripts can locate the `outdegree/` folder.
5.  Run all cells.
