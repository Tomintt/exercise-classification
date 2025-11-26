# exercise-classification
Fitness Application for Automated Real-Time Bicep Curl Form Assessment

This project implements a smartwatch-powered system that detects bicep curl sets, segments repetitions, and classifies exercise form in real time using machine-learning techniques. Built for my university dissertation, the system combines an Android Wear OS smartwatch application with a Python processing pipeline to deliver automated, real-time feedback on exercise quality.

The system streams live accelerometer and gyroscope data from a Samsung Gear Live smartwatch, automatically detects the start and end of exercise sets, segments repetitions using a novel trough-based retrospective segmentation approach, and classifies each repetition into one of four form classes:

Correct Form

Partial Range of Motion

Moving Elbow/Shoulder

Excessive Use of Momentum

A hyper-tuned Support Vector Machine (SVM) model was selected after evaluation against MLP and Random Forest classifiers, achieving an average real-time prediction accuracy of 78.88%, surpassing comparable studies in exercise form classification.

Key features include:

Real-time sensor streaming from a wearable device

Dynamic windowing for automated set detection

Repetition segmentation based on whole-set trough analysis

Extraction of 30 optimised statistical time-domain features

Live form classification integrated into a desktop application

Persistent workout history stored via SQLite and displayed through a GUI

Full pipeline from data collection → training → deployment

This project demonstrates a full end-to-end machine learning deployment for real-time human-movement classification on wearable devices, contributing toward the broader goal of developing intelligent virtual personal training systems.
