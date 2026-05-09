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
```
## Requirements
Python 3.x
OpenCV
NumPy
Pandas
Matplotlib
tqdm
joblib

## Install dependencies:
```text
pip install -r requirements.txt
```
## Hardware Used
Raspberry Pi 3B+
USB Webcam
CPU-only inference

## Models Used
Haar Cascade
Used for fast face region proposal.
SSD Face Detector
ResNet-10 based SSD model using OpenCV DNN module.

Model files:

deploy.prototxt
```text
res10_300x300_ssd_iter_140000.caffemodel
Running Real-Time Detection
python hybrid_detection.py

Press q to quit the application.
```

## Evaluation

The evaluation script computes:

Precision
Recall
F1-score
mAP
Precision--Recall curve

Run:

``` text
python evaluation.py
```
Outputs:
```text
pr_curve.csv
pr_curve.png
Performance
Method	Precision	Recall	F1-Score	FPS
Haar Only	0.78	0.72	0.75	25
SSD Only	0.91	0.88	0.89	10
Hybrid (Proposed)	0.90	0.86	0.88	18
Temporal ROI Optimization
```

The system reduces computation using temporal Region of Interest (ROI) tracking. Instead of scanning the entire frame repeatedly, Ddtection is restricted around the previously detected face region. Full-frame detection is used only when tracking fails.

This significantly improves FPS on embedded hardware.

## Applications
Smart surveillance systems
Attendance systems
Edge AI cameras
Smart home security
Human--computer interaction
Future Improvements
Quantized deep learning models
YOLO Nano / MobileNet-SSD integration
Multi-face tracking
Hardware accelerator support
TensorFlow Lite optimization
## References
Viola, P., and Jones, M., “Rapid Object Detection using a Boosted Cascade of Simple Features,” CVPR, 2001.
Liu, W. et al., “SSD: Single Shot MultiBox Detector,” ECCV, 2016.
He, K. et al., “Deep Residual Learning for Image Recognition,” CVPR, 2016.

## Author

Anupam Verma

## License

This project is intended for academic and research purposes.
