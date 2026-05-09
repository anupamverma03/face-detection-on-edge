# Hybrid Haar + SSD Face Detection for Edge Devices

Real-time hybrid face detection system designed for low-power embedded platforms such as Raspberry Pi.  
The project combines the speed of Haar Cascade detection with the robustness of SSD-based deep learning verification to achieve a balance between computational efficiency and detection accuracy.

---

## Features

- Hybrid Haar Cascade + SSD face detection
- Real-time inference on Raspberry Pi
- Temporal ROI optimization
- SSD execution at fixed frame intervals
- FPS monitoring and logging
- Precision--Recall curve evaluation
- Edge-device optimized deployment
- Threaded video capture for improved performance

---

## System Overview

The proposed pipeline follows a two-stage hybrid detection approach:

1. Haar Cascade is used for fast face region proposal.
2. SSD verifies candidate regions to reduce false positives.
3. Temporal ROI tracking limits detection to previously detected face regions.
4. SSD inference is selectively executed every N frames to reduce computational load.

---

## Project Structure

```text
Hybrid-Face-Detection/
│
├── models/
│   ├── deploy.prototxt
│   ├── res10_300x300_ssd_iter_140000.caffemodel
│
├── haarcascade_frontalface_default.xml
│
├── hybrid_detection.py
├── evaluation.py
├── pr_curve.csv
├── pr_curve.png
├── hybrid_face_detection_log.csv
│
├── dataset/
│
├── README.md
└── requirements.txt
