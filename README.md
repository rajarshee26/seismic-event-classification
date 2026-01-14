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


### Data Limitations
- Limited number of independent seismic events
- Overlapping windows extracted from continuous waveforms
- Class labels derived at the window level, not event level

These limitations are explicitly considered during evaluation and analysis.

