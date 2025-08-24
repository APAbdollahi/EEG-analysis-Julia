# EEG Network Analysis in Julia (Julia translation of Maryam Rahimi's code)

This project provides a Julia-based toolkit for the analysis of EEG (Electroencephalography) data through the lens of complex network theory. 
This is based entirely on Maryam Rahimi's Python toolkit, so credit goes to her. I have only translted this to Julia.

The primary goal is to build brain connectivity networks from multi-channel EEG signals and extract meaningful graph-theoretic measures. These measures can be used to study brain dynamics, compare different subject groups (e.g., based on age), and investigate phenomena like neural rewiring.

This repository contains the Julia implementation of an analysis pipeline originally developed in Python.

## Key Concepts & Features

The analysis pipeline is built around several core concepts:

-   **EEG Data Processing**: Reads standard EEG data formats (specifically, `.edf` and raw binary files).
-   **Signal Filtering**: Decomposes raw EEG signals into standard frequency bands (e.g., Delta, 0.1-4 Hz) using digital filters.
-   **Network Construction**: Defines hypothetical edges between EEG channels to build a graph representation of the brain's functional network. This is achieved by:
    -   Calculating a correlation matrix between all channel pairs.
    -   Applying a Bonferroni statistical correction to determine significant connections, forming an adjacency matrix.
-   **Graph Analysis**: Extracts a suite of network measures from the constructed graphs using `Graphs.jl`. Calculated measures include:
    -   Global Efficiency
    -   Average Clustering Coefficient
    -   Average Shortest Path Length
    -   Maximum Betweenness Centrality
    -   Graph Diameter
    -   Graph Energy (from eigenvalues)
    -   Mean Degree

## Prerequisites

To run this project, you will need the following installed on your system:

-   **Julia**: Version 1.6 or later is recommended. You can download it from the [official Julia website](https://julialang.org/downloads/).
-   **Jupyter Notebook or JupyterLab**: The analysis is presented in a Jupyter Notebook.
-   **IJulia Kernel**: To run Julia code within Jupyter.

## Installation & Setup

Follow these steps to set up the project environment.

**1. Clone the Repository**
```bash
git clone <your-repository-url>
cd <repository-directory>
```
**2. Install Packages**
Open the Julia REPL (command line) and run the single code block below. This will install the IJulia kernel (for Jupyter) and all the necessary packages for data handling, signal processing, and network analysis.
```bash
using Pkg
Pkg.add(["IJulia", "EDF", "DataFrames", "Statistics", "CSV", "LinearAlgebra", "MultipleTesting", "HypothesisTests", "DSP", "Graphs", "XLSX"])
```

**3. Place Your Data**

The script is configured to read data from a specific directory.

    Create a directory (e.g., data/) in the project folder.

    Place your EEG .edf or binary .dat files inside this directory.

    You must update the file paths inside the EEG_Analysis.ipynb notebook to point to your data files. 

    Look for variables like edf_filepath and directory.


