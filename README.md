# Seismic Event Classification System

## Overview
This project builds an end-to-end machine learning system to automatically
classify seismic waveform data into **earthquake** and **noise** events.

The objective is not only to achieve good classification performance, but also
to understand **why** models work, **where** they fail, and **how** such a system
would operate in a real-world seismic monitoring scenario.

The project combines signal processing, classical machine learning, deep learning,
explainability, and system-level design.

## Problem Statement
Seismic monitoring systems continuously record ground motion, but a large
portion of recorded signals correspond to noise rather than true earthquake
events. Manual inspection of waveforms is time-consuming and not scalable.

The goal of this project is to build a machine learning pipeline that can
automatically distinguish earthquake signals from noise using short
time-windowed seismic waveforms.

---

## Dataset
The dataset consists of seismic waveform data obtained from public seismic
data services (e.g., IRIS). The data includes:

- Earthquake waveform segments
- Noise-only waveform segments

Waveforms are treated as time-series signals and processed using standard
seismological preprocessing techniques before being used for machine learning.

## Methodology

The project is structured into multiple phases, each addressing a specific
stage of the machine learning lifecycle.

### Phase 1 — Data Loading & Inspection
Seismic waveform data is loaded and visualized to understand signal
characteristics and noise behavior.

### Phase 2 — Signal Preprocessing
Waveforms are detrended, band-pass filtered (1–20 Hz), segmented into
overlapping fixed-length windows, and normalized to create ML-ready samples.

### Phase 3 — Feature Engineering & Classical ML
Time- and frequency-domain features are extracted from each window.
Classical machine learning models (Logistic Regression and Random Forest)
are trained, improved using physics-informed features, and validated using
cross-validation.

### Phase 4 — Deep Learning (1D CNN)
A 1D Convolutional Neural Network is trained directly on raw waveform windows
to learn features automatically and compared against classical ML baselines.

### Phase 5 — Explainability (XAI)
Feature importance analysis is performed for classical ML models, and
gradient-based saliency maps are used to qualitatively interpret CNN behavior.

### Phase 6 — Error Analysis & Scientific Validation
Misclassified samples are analyzed to understand failure modes, and
limitations related to data size and sample independence are discussed.

## Results

The performance of different modeling approaches was evaluated using accuracy,
F1-score, and class-wise error analysis.

- Classical machine learning models with engineered time–frequency features
  achieved approximately **85% accuracy**, demonstrating strong performance
  on limited data.
- The 1D CNN achieved lower validation performance (≈ **65–70% accuracy**),
  indicating overfitting due to limited independent seismic events.

Rather than maximizing accuracy, the focus was on understanding model behavior
and limitations.

---

## Key Insights

- Physics-informed feature engineering significantly improves performance on
  small seismic datasets.
- Classical ML models outperform deep learning when data is limited and
  interpretability is important.
- CNNs require larger and more diverse datasets to generalize effectively.
- Most classification errors occur on low signal-to-noise or ambiguous waveform
  windows, which are difficult even for human analysts.



### Data Limitations
- Limited number of independent seismic events
- Overlapping windows extracted from continuous waveforms
- Class labels derived at the window level, not event level

These limitations are explicitly considered during evaluation and analysis.

## System Design Perspective

The project can be viewed as a conceptual seismic event classification system
operating on continuous waveform streams. A real-world deployment would include:

- Continuous waveform ingestion from seismic stations
- Real-time preprocessing using the same detrending and filtering pipeline
- Sliding window generation for near–real-time inference
- Model inference using a classical ML model for robustness and interpretability
- Temporal aggregation of predictions to reduce false alarms
- Human-in-the-loop review for low-confidence or ambiguous cases

This design prioritizes reliability, transparency, and practical deployment
constraints.

---

## Future Work

Several extensions could further improve the system:

- Validation on independent seismic events and multiple stations
- Use of multi-component (ZNE) waveform data
- Training on larger benchmark datasets (e.g., STEAD)
- Incorporation of confidence-based decision thresholds
- Exploration of hybrid models combining handcrafted features and deep learning


