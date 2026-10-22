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
├── README.md
├── requirements.txt
└── LICENSE
```

## Methodology

The proposed **Refined Grey Wolf Optimisation-based Bidirectional Long Short-Term Memory (R-GWO-BiLSTM)** framework combines metaheuristic optimisation with deep temporal feature learning for wearable sensor-based fall detection.

The experimental workflow consists of the following stages:

### 1. Data Preprocessing

Accelerometer and gyroscope recordings from the MobiFall v2.0 dataset are processed to prepare the input sequences for model training and evaluation.

The preprocessing procedure includes:

- Loading accelerometer and gyroscope measurements.
- Resampling sensor measurements to a frequency of 100 Hz.
- Segmenting the recordings into two-second observation windows.
- Preparing six-channel inertial sensor sequences.
- Normalising the input features using training-derived parameters.

Each observation window contains **200 time samples and six sensor channels**, producing an input dimension of **200 × 6**.

### 2. Subject-Independent Data Partitioning

A subject-independent evaluation strategy is adopted to reduce participant-level information leakage and assess model generalisation to previously unseen individuals.

The dataset is divided into three independent partitions:

- **Training:** 16 participants.
- **Validation:** 4 participants.
- **Testing:** 4 participants.

Participants assigned to one partition are excluded from the remaining partitions.

### 3. BiLSTM Architecture

The proposed framework employs a Bidirectional Long Short-Term Memory (BiLSTM) network to capture temporal dependencies in accelerometer and gyroscope measurements.

The architecture incorporates:

- A first BiLSTM layer with 69 units per direction.
- A second BiLSTM layer with 22 units per direction.
- A fully connected layer containing 32 neurons.
- A sigmoid output layer for binary fall classification.

The selected architecture contains **71,761 trainable parameters**.

### 4. Grey Wolf Optimisation

Grey Wolf Optimisation (GWO) is employed to identify suitable BiLSTM hyperparameter configurations through a population-based search process.

The optimisation mechanism incorporates:

- Initialisation of candidate hyperparameter configurations.
- Fitness evaluation using validation average precision.
- Selection of alpha, beta, and delta search agents.
- Adaptive encircling and candidate position updates.
- Iterative exploration and exploitation of the search space.
- Selection of the best-performing configuration.

The fitness function is defined as:

**J(λ) = 1 − AP(validation)(λ)**

where **λ** represents a candidate hyperparameter configuration and **AP(validation)** denotes average precision evaluated on the validation dataset.

The optimisation seeks to minimise the fitness function while maintaining a clear separation between model development and final testing.

<p align="center">
<img src="https://github.com/shahid3167/R-GWO-BiLSTM-Fall-Detection/blob/main/Results/GWO.png" width="900" height="700">

<p align="left">
Hierarchical search and optimization mechanism of the Grey Wolf Optimizer (GWO) with adaptive position updates and fitness-based selection.

### 5. Multi-Seed Evaluation

Leading configurations identified through GWO are evaluated across multiple random training seeds.

This procedure is intended to:

- Assess the stability of candidate configurations.
- Reduce dependence on a single training outcome.
- Examine variability caused by random initialisation.
- Support more reliable model selection.

### 6. Classification Threshold Optimisation

The classification threshold is selected exclusively using validation data.

The optimal threshold is determined by maximising the **Matthews Correlation Coefficient (MCC)** over a set of candidate thresholds.

After selection, the threshold is fixed and applied to the held-out test dataset without further adjustment.

### 7. Model Evaluation

The final R-GWO-BiLSTM model is evaluated using the independent test partition.

Classification performance is assessed using:

- Accuracy
- Precision
- Recall
- F1-score
- Specificity
- ROC-AUC
- PR-AUC
- Confusion matrix

Computational efficiency is also examined through parameter count, FLOPs, model size, and inference latency.

---

## How to Run

### Requirements

The framework is developed in Python and uses deep-learning, machine-learning, and numerical computing libraries.

Install the required dependencies using:

```bash
pip install -r requirements.txt
```

### Dataset Preparation

Obtain the MobiFall v2.0 dataset from its authorised source and place the required files in the `data/` directory.

The dataset must be organised according to the paths expected by the preprocessing scripts or experimental notebook.

### Run the Experimental Notebook

Open the Jupyter notebook:

```text
notebooks/R_GWO_BiLSTM.ipynb
```

Execute the notebook cells sequentially to perform data preprocessing, subject-independent partitioning, GWO optimisation, model training, threshold selection, and final evaluation.

### Run the Python Implementation

If the modular Python package is included and configured, the framework can be executed using:

```bash
python -m src.rgwo_bilstm.main
```

**Note:** The commands and file paths should be checked against the final repository implementation.

---

## Results

The proposed R-GWO-BiLSTM framework is evaluated in terms of fall identification performance and computational efficiency.

### Classification Performance

| Evaluation Metric | R-GWO-BiLSTM |
|:------------------|-------------:|
| Accuracy | 99.16% |
| Precision | 99.70% |
| Recall | 99.68% |
| F1-score | 99.00% |
| Specificity | 99.63% |

**Note:** The reported F1-score should be verified against the final simulation results and the averaging method used.

### Computational Efficiency

| Computational Metric | R-GWO-BiLSTM |
|:---------------------|-------------:|
| Trainable Parameters | 71,761 |
| FLOPs | 16.62 MFLOPs |
| Inference Latency | 0.4049 ms |
| Model Size | 0.287 MB |

The reported inference latency was measured in an offline computing environment rather than on a deployed wearable or edge device.

The computational analysis considers the balance between classification performance, model complexity, storage requirements, and inference efficiency.

Detailed experimental results and comparisons with existing fall-detection techniques are presented in the associated research manuscript.

---

## Example Output

An illustrative execution of the framework produces the following sequence:

```text
R-GWO-BiLSTM Framework Running...

Loading MobiFall v2.0 dataset...
Preprocessing accelerometer and gyroscope data...
Generating temporal observation windows...
Creating subject-independent data partitions...
Initializing BiLSTM architecture...
Running Grey Wolf Optimisation...
Evaluating candidate hyperparameter configurations...
Performing multi-seed evaluation...
Selecting validation-based classification threshold...
Evaluating the final model on the test dataset...
Calculating classification performance...
Analysing computational complexity...

Experiment completed.
```

*This output is illustrative and may differ from the actual notebook or Python implementation.*

---

## Figures and Experimental Outputs

The `results/` directory is intended to contain the figures and experimental outputs generated during the study.

### System Architecture

- IoT-enabled fall-detection system architecture.
- Wearable sensor data acquisition and processing workflow.
- Proposed R-GWO-BiLSTM framework architecture.

### Optimisation Results

- GWO hierarchical search mechanism.
- Hyperparameter optimisation results.
- Candidate configuration evaluation.
- Multi-seed training stability analysis.

### Classification Results

- Training and validation accuracy curves.
- Training and validation loss curves.
- Confusion matrix.
- Receiver Operating Characteristic (ROC) curve.
- Precision–Recall (PR) curve.
- Classification performance comparisons.

### Computational Analysis

- Trainable parameter analysis.
- FLOPs estimation.
- Model size comparison.
- Inference latency comparison.

The corresponding figures and result files can be organised within the `results/` directory.

---

## Data Availability

The experiments are conducted using the MobiFall v2.0 dataset.

Users should obtain the dataset from its authorised source and comply with the applicable access, citation, and redistribution conditions.


---

## Citation

If you use this work, please cite the associated research manuscript:

**"An IoT-Enabled Metaheuristic-Optimized BiLSTM Framework for Fall Detection in Elderly and Disabled People."**

**Authors:**

- Abdulrahman A. Alzahrani
- Shahid Hussain
- Sahbi Boubaker

The complete bibliographic citation, publication details, and DOI will be provided when available.

---

## Authors

**Abdulrahman A. Alzahrani**
Assistant Professor
Department of Information System and Technology, 
College of Computer Science and Engineering, 
University of Jeddah, Jeddah, Saudi Arabia
Email: aasalzahrani1@uj.edu.sa

**Shahid Hussain**  
Assistant Professor in Data Analytics  
Atlantic Technological University (ATU), Galway, Ireland  
Email: shahid.hussain@atu.ie

**Sahbi Boubaker**  
Professor  
Department of Computer and Network Engineering  
College of Computer Science and Engineering  
University of Jeddah, Saudi Arabia  
Email: sboubaker@uj.edu.sa

For questions, feedback, or research collaboration, please contact the authors.

---

## License

The licence for this repository will be specified upon release.

Any third-party datasets, software libraries, and other resources remain subject to their respective licences and terms of use.


