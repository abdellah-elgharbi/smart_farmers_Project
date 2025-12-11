# Dual-Model Architecture for Cow Health Monitoring

**Authors:**  
- **EL GHARBI Abdellah** – abdellahelgharbi200229@gmail.com  
- **EL MASKYNE Mohamed-Amine** – mohamedamine.ing@elmaskyne.com  
- **AIT OUAHDA Younes** – younes.aitouahda@gmail.com  

**Affiliation:**  
École Nationale des Sciences Appliquées d’El Jadida (ENSAJ), Université Chouaib Doukkali, El Jadida, Morocco  

---

## Table of Contents
- [Overview](#overview)  
- [Features](#features)  
- [System Architecture](#system-architecture)  
- [Datasets](#datasets)  
- [Installation](#installation)  
- [Usage](#usage)  
- [Results](#results)  
- [Future Work](#future-work)  
- [License](#license)  

---

## Overview

This project presents a **dual-model architecture** for automated cow health monitoring. The system integrates **deep learning-based behavioral classification** with **machine learning-driven disease detection** to provide early alerts for health issues, including mastitis.  

The cascading pipeline is designed to process IoT sensor data efficiently, transforming behavioral patterns into actionable health insights for dairy farmers.  

---

## Features

- Real-time classification of cow behaviors: Eating, Resting, Ruminating, Moving, Grazing, Salt-licking.  
- 24-hour behavioral aggregation to compute health biomarkers.  
- Hierarchical health prediction system for general health anomalies.  
- Specialized mastitis detection using **XGBoost** with **SMOTE-balanced training**.  
- Integrated alert system to notify farmers proactively.  

---

## System Architecture

The system consists of three main modules:

1. **Behavior Classification (Model 1)**  
   - CNN-based model processing accelerometer and temperature sensor data.  
   - Sliding window (5 sec) with 75% overlap.  
   - Outputs instantaneous behavior labels.  

2. **24-Hour Behavioral Aggregation Module**  
   - Converts behavior labels into duration-based health features.  
   - Examples: eating_duration, ruminating_duration, walking_capacity.  

3. **Health & Disease Prediction (Models 2 & 3)**  
   - **Model 3:** Predicts overall health status using behavioral summaries + physiological data.  
   - **Model 2:** Activated if unhealthy; detects mastitis using XGBoost with SMOTE and probability calibration.  


---

## Datasets

1. **Behavior Classification Dataset**  
   - 1,391,224 accelerometer samples from 6 cows.  
   - 6 behavior classes (ETC, RES, RUS, MOV, GRZ, SLT).  
   - Balanced to 403,558 samples for training.  

2. **Mastitis Detection Dataset**  
   - 6,600 samples, 18 features including breed, milk metrics, and health indicators.  
   - Class imbalance: 83% healthy, 17% mastitis-positive.  

3. **Health Prediction Dataset**  
   - 178 cow records, 14 features including behavioral durations and physiological measurements.  

---

## Installation

1. Clone the repository:  
```bash
git clone https://github.com/username/cow-health-monitoring.git
cd cow-health-monitoring
