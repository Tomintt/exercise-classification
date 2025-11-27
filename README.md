# exercise-classification
## Fitness Application for Automated Real-Time Bicep Curl Form Assessment

This project implements a smartwatch-powered system that detects bicep curl sets, segments repetitions, and classifies exercise form in real time using machine-learning techniques. Built for my university dissertation, the system combines an Android Wear OS smartwatch application with a Python processing pipeline to deliver automated, real-time feedback on exercise quality.

The system streams live accelerometer and gyroscope data from a Samsung Gear Live (SM-R382) smartwatch — a first-generation Android wearable running Android Wear 1.0 (Android 4.4W KitKat, API Level 20). Given the device’s age and hardware limitations (Snapdragon 400, 512MB RAM, 4GB storage), the project was designed to operate within the constraints of early Wear OS hardware, which is no longer supported by modern updates.

Using a full pipeline of signal processing, dynamic windowing, and machine-learning classification, the system identifies exercise sets, segments individual repetitions, and categorises each repetition into one of four form-quality classes:

- Correct Form
- Partial Range of Motion
- Moving Elbow/Shoulder
- Excessive Use of Momentum

After evaluating multiple models (MLP, Random Forest, SVM), a tuned Support Vector Machine (SVM) achieved an average real-time prediction accuracy of 78.88%, surpassing results in comparable exercise classification literature.

---

## Key Features

- Real-time sensor streaming from a smartwatch
- Dynamic windowing for automated set detection
- Repetition segmentation using trough-based retrospective analysis
- Extraction of 30 optimised statistical time-domain features
- Live classification using a Python desktop application
- SQLite-based persistent workout history with GUI display
- Full end-to-end pipeline: data collection → preprocessing → training → deployment

---

# Repository Structure

The repository contains the three main components of the system.

---

## 1. Data Preprocessing and Model Training (Jupyter Notebook)

This notebook documents the complete machine-learning workflow, including:

- Preprocessing approximately 4,000 labelled smartwatch samples
- Noise reduction, feature extraction, and feature standardisation
- Handling class imbalance
- Evaluating SVM, MLP, and Random Forest models
- Selecting and exporting the final optimised SVM model

It explains how the classifier was built from raw sensor data through to the final deployed model.

---

## 2. Real-Time Listener and Classification Engine (Python Desktop Application)

A Python program that runs on a PC and performs real-time classification:

- Receives live accelerometer and gyroscope data
- Processes data windows in real time
- Detects sets and segments repetitions
- Applies the trained SVM model to each repetition
- Displays classification results
- Stores workout history using SQLite

This application delivers the real-time exercise assessment.

---

## 3. Smartwatch Data Streaming App (Android Wear OS Application)

An Android application developed specifically for the Samsung Gear Live (SM-R382).

### Device and OS Details

- OS: Android Wear 1.0
- Android Version: 4.4W “KitKat for Wearables”
- API Level: 20
- Hardware: 1.63" Super AMOLED display, Snapdragon 400 CPU, 512MB RAM, 4GB internal storage

As an early Android Wear device, the Gear Live does not support modern Wear OS versions. The app must target API Level 20 and operate efficiently within the constraints of the hardware.

### App Functionality

- Captures accelerometer and gyroscope sensor data
- Streams data over USB using Android Debug Bridge (ADB)
- Outputs a continuous timestamped data stream
- The Python listener application reads and processes this stream in real time

This app enables the data link between the smartwatch and the desktop classification engine.
