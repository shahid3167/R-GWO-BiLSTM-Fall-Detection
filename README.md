# R-GWO-BiLSTM: Robust Grey Wolf Optimisation-Based Bidirectional LSTM for Fall Detection
A robust Grey Wolf Optimisation-based Bidirectional LSTM framework for wearable sensor-based fall detection, incorporating subject-independent evaluation, multi-seed hyperparameter selection, and validation-based classification threshold optimisation.


# Overview
The proposed **Refined Grey Wolf Optimisation-based Bidirectional Long Short-Term Memory (R-GWO-BiLSTM)** framework integrates metaheuristic optimisation with deep temporal learning to identify falls from wearable inertial sensor measurements.
The framework evaluates:

- Fall detection and activities of daily living (ADL) classification.
- Grey Wolf Optimisation (GWO) for BiLSTM hyperparameter selection.
- Multi-seed evaluation of candidate configurations to assess training stability.
- Subject-independent training, validation, and testing.
- Validation-based classification threshold optimisation.
- Classification performance and computational efficiency.

The study uses the MobiFall v2.0 dataset, containing accelerometer and gyroscope measurements collected during fall events and daily activities.

# IoT-Enabled Fall Detection Framework
The proposed architecture considers an IoT-enabled monitoring environment in which wearable inertial sensors acquire body-motion measurements. The sensor data are processed and analysed using the proposed R-GWO-BiLSTM framework to distinguish falls from normal activities.

The architecture includes wearable sensing, data acquisition, preprocessing, temporal feature learning, GWO-based model selection, activity classification, and potential fall-alert generation.

<p align="center">
<img src="https://github.com/shahid3167/R-GWO-BiLSTM-Fall-Detection/blob/main/Results/SystemModel.png" width="900" height="700">

<p align="left">
System model of the proposed IoT-Enabled GWO-BiLSTM Framework for fall detection and activity monitoring.

# Features
- **IoT-enabled sensing architecture:** Supports a wearable sensor-based monitoring framework for elderly and disabled individuals.
- **Bidirectional temporal modelling:** Employs BiLSTM layers to learn motion patterns from accelerometer and gyroscope sequences.
- **Metaheuristic optimisation:** Uses GWO to explore candidate model configurations.
- **Validation-based fitness evaluation:** Minimises the fitness function defined as one minus validation average precision.
- **Multi-seed model evaluation:** Examines the stability of leading candidate configurations across repeated training runs.
- S**ubject-independent evaluation:** Separates participants across training, validation, and test partitions.
- **Threshold refinement:** Selects the classification threshold using validation Matthews Correlation Coefficient (MCC).
- **Computational assessment:** Evaluates parameter count, floating-point operations, model size, and inference latency.

#  Dataset
The framework is evaluated using MobiFall v2.0, a wearable inertial-sensor dataset containing recordings of falls and activities of daily living.


## Dataset

The proposed R-GWO-BiLSTM framework is evaluated using the **MobiFall v2.0 dataset**, containing accelerometer and gyroscope measurements recorded during falls and activities of daily living (ADLs).

| Dataset Characteristic | Description |
|:-----------------------|:------------|
| Dataset | MobiFall v2.0 |
| Participants | 24 |
| Total Recordings | 630 |
| ADL Recordings | 342 |
| Fall Recordings | 288 |
| Sensor Modalities | Accelerometer and Gyroscope |
| Input Channels | 6 |
| Sampling Frequency | 100 Hz |
| Observation Window | 2 seconds |
| Input Dimensions | 200 × 6 |
| Evaluation Strategy | Subject-Independent |

### Subject-Independent Data Partitioning

| Data Partition | Participants |
|:---------------|------------:|
| Training | 16 |
| Validation | 4 |
| Testing | 4 |
| **Total** | **24** |



## Repository Structure

```text
R-GWO-BiLSTM-Fall-Detection/
├── src/
│   └── rgwo_bilstm/
│       ├── __init__.py
│       ├── data_preprocessing.py
│       ├── subject_split.py
│       ├── bilstm_model.py
│       ├── gwo_optimizer.py
│       ├── multiseed_validation.py
│       ├── threshold_optimization.py
│       ├── model_evaluation.py
│       ├── computational_analysis.py
│       └── main.py
│
├── notebooks/
│   └── R_GWO_BiLSTM.ipynb
│
├── data/
│   └── README.md
│
├── results/
│   ├── figures/
│   ├── classification/
│   ├── optimization/
│   └── computational/
│
├── models/
├── requirements.txt
├── pyproject.toml
├── .gitignore
├── LICENSE
└── README.md
```

