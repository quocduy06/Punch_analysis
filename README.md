# Martial-Arts-Signal-Analysis: Punch Intensity Tracker

A multi-sensor data acquisition and processing system (IMU + PPG) designed for recognizing punch intensity and tracking physiological responses in Martial Arts (Aikido). The system is deployed on an ESP32-S3 microcontroller, operating in real-time with a 100Hz sampling frequency.

---

## 🛠 Hardware Configuration

*   **MCU:** ESP32-S3 (Lolin S3 Mini) – Selected for efficient edge-computing and signal processing.
*   **IMU (Inertial Measurement Unit):** MPU6050
    *   *Configuration:* Configured to $\pm16g$ full-scale range to capture high-impact, wide-dynamic-range martial arts strikes without saturation.
*   **PPG (Photoplethysmography):** MAX30102
    *   *Operational Status:* Infrared (IR) raw values stabilized between $100k - 200k$ to actively mitigate Motion Artifacts (MA) during intense physical movement.

---

## 📂 Project Architecture

The repository is structured following standard Embedded Systems and Data Science pipeline conventions for seamless handovers and scalability:

```text
Aikido_Project/
├── data/
│   ├── raw/                  # Contains 17+ raw telemetry CSV files collected from sparring sessions
│   └── processed/            # Contains `master_dataset_aikido.csv` after cleaning, alignment, and formatting
├── firmware/
│   ├── main.cpp              # Primary C++ source code for ESP32-S3 (Sensor polling and data streaming)
│   └── classifier.h          # Embedded C implementation for real-time Heart Rate Recovery (HRR) calculation
├── scripts/
│   └── collect_data.py       # Python script for automated Serial data streaming (Relative-path ready)
├── notebooks/
│   ├── 5th_analyze_data.ipynb      # Quality Control (QC) notebook: Signal saturation and clipping detection
│   └── 6th_master_processing.ipynb # Data integration pipeline and deep Feature Engineering
├── docs/
│   └── visual_qc/            # Storage for clean, visualized signal plots used for reporting
└── README.md
