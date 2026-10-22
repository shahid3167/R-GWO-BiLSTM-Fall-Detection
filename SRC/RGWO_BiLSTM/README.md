
# R-GWO-BiLSTM Implementation

This directory contains the complete Jupyter notebook implementation of the **Refined Grey Wolf Optimisation-based Bidirectional Long Short-Term Memory (R-GWO-BiLSTM)** framework for IoT-enabled fall detection in elderly and disabled people.

## Implementation

The complete experimental workflow is provided in:

**R_GWO_BiLSTM.ipynb**

The notebook covers the following stages:

1. MobiFall v2.0 dataset loading and preprocessing.
2. Accelerometer and gyroscope signal processing.
3. Temporal window generation.
4. Subject-independent training, validation, and testing.
5. BiLSTM model development.
6. Grey Wolf Optimisation for hyperparameter selection.
7. Multi-seed model evaluation.
8. Validation-based classification threshold optimisation.
9. Final classification performance evaluation.
10. Computational complexity and inference analysis.

## Execution

The notebook can be executed using Jupyter Notebook or Google Colab.

To reproduce the experiments:

1. Download the MobiFall dataset using the link provided in the repository's `data/README.md`.
2. Install the required Python dependencies.
3. Open `R_GWO_BiLSTM.ipynb`.
4. Update the dataset paths to match your environment.
5. Execute the notebook cells sequentially.

## Reproducibility

The framework employs subject-independent data partitioning and validation-based model selection to reduce information leakage.

The held-out test dataset is reserved for final performance evaluation.
