
# MobiFall Dataset

## Dataset Description

The proposed **R-GWO-BiLSTM** framework is evaluated using the **MobiFall v2.0 dataset**, which contains accelerometer and gyroscope measurements recorded during falls and activities of daily living (ADLs).

The dataset is used to train, validate, and evaluate the proposed fall-detection framework.

## Dataset Download

The dataset is not directly included in this GitHub repository.

Researchers interested in reproducing the experimental results are requested to download the dataset from Kaggle using the following link:

**Kaggle Dataset:** [Download MobiFall Dataset](https://www.kaggle.com/datasets/sha0401/mobifall-dataset-v2-0)

After downloading the dataset, extract the files and place them in the `data/` directory of this repository.

## Dataset Characteristics

| Characteristic | Description |
|:---------------|:------------|
| Dataset | MobiFall v2.0 |
| Participants | 24 |
| Total Recordings | 630 |
| ADL Recordings | 342 |
| Fall Recordings | 288 |
| Sensor Modalities | Accelerometer and Gyroscope |
| Sampling Frequency | 100 Hz (experimental resampling) |
| Observation Window | 2 seconds |
| Input Dimensions | 200 × 6 |
| Evaluation Strategy | Subject-Independent |

## Data Preparation

After downloading the dataset:

1. Extract the downloaded archive.
2. Place the extracted dataset files inside the `data/` directory.
3. Verify that the dataset paths match those specified in the experimental code.
4. Run the preprocessing scripts or Jupyter notebook to prepare the data for model training and evaluation.

## Data Usage and Attribution

The MobiFall dataset belongs to its original creators and contributors.

Users should acknowledge the original dataset authors and comply with the applicable Kaggle dataset terms and any original licensing or citation requirements.

This repository provides the experimental framework and implementation code but does not claim ownership of the dataset.

## Reproducibility

The proposed framework uses a subject-independent evaluation strategy, separating participants into training, validation, and testing partitions.

- **Training:** 16 participants
- **Validation:** 4 participants
- **Testing:** 4 participants

Researchers seeking to reproduce the reported results should follow the same preprocessing, participant partitioning, model configuration, and evaluation procedures described in the associated research manuscript.

