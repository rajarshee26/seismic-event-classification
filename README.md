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

### Data Limitations
- Limited number of independent seismic events
- Overlapping windows extracted from continuous waveforms
- Class labels derived at the window level, not event level

These limitations are explicitly considered during evaluation and analysis.

