# QSAR Extrapolation

This repository contains the Jupyter notebook associated with the manuscript **“Beyond the Domain: A Practical Recipe for QSAR Extrapolation”** by Sankalp Jain and Alexey V. Zakharov, National Center for Advancing Translational Sciences (NCATS), National Institutes of Health (NIH).

## Overview

The notebook implements a differential quantitative structure-activity relationship (QSAR) workflow for predicting compounds that are more potent than those represented in the model-training data.

The differential model learns activity differences from differences in molecular descriptors between compound pairs. The resulting activity estimates are combined using three aggregation strategies:

* Mean aggregation
* k-nearest-neighbor aggregation (`k = 3`)
* 10% quantile aggregation

These approaches are compared with direct descriptor-based QSAR and Chemprop.

## Notebook

`chembl35_qsar_extrapolation_workflow.ipynb`

The notebook performs:

* Extraction of activity data from a local ChEMBL 35 SQLite database
* Curation and preparation of target-specific datasets
* Potency-based external-validation splitting
* Calculation and scaling of RDKit molecular descriptors
* Differential neural-network modeling
* Mean, kNN, and 10% quantile aggregation
* Direct descriptor-based QSAR modeling
* Chemprop modeling
* Generation of target-specific prediction files

## Data source

The workflow uses publicly available data from [ChEMBL 35](https://doi.org/10.6019/CHEMBL.database.35). The ChEMBL database is not included in this repository.

The notebook requires:

1. A local SQLite copy of ChEMBL 35.
2. A CSV file containing the assay and target ChEMBL identifiers to be processed. The notebook expects the assay identifier in the first column and the target identifier in the second column.

The SQL query retrieves exact IC50 measurements reported in nM from assays with a ChEMBL confidence score greater than 6. Nonpositive IC50 values are excluded before activity transformation.

## Software requirements

The notebook uses:

* Python
* JupyterLab
* pandas
* NumPy
* RDKit
* scikit-learn
* TensorFlow/Keras
* PyTorch
* Lightning
* Chemprop
* Matplotlib

A CUDA-capable GPU is required by the current Chemprop trainer configuration.


## Citation

If you use this workflow, please cite the associated article after publication:

> Jain S, Zakharov AV. *Beyond the Domain: A Practical Recipe for QSAR Extrapolation.*
