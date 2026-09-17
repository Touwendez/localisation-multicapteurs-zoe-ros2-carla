# Multi-Sensor Localization for Autonomous Driving

## ROS 2, CARLA and EKF evaluation on a robotic Renault Zoe platform

This project studies localization and state-estimation methods for an autonomous vehicle, with a focus on ROS 2 integration, CARLA simulation and Extended Kalman Filter evaluation.

The work combines a literature review of GNSS/INS, LiDAR-SLAM and Visual-Inertial Odometry approaches with practical integration and evaluation on a robotic Renault Zoe platform and its CARLA digital twin.

## Project scope

The project addresses three complementary aspects:

- review and comparison of localization approaches for autonomous vehicles;
- integration and calibration of localization sensors and ROS 2 modules;
- experimental evaluation of EKF configurations in CARLA using reproducible metrics and recorded data.

## Technical stack

- ROS 2
- CARLA
- Python
- Linux
- Jupyter Notebook
- NumPy, pandas, Matplotlib
- Extended Kalman Filter (EKF)
- RViz

## Platform and sensors

The target robotic platform includes:

| Sensor | Example hardware / role |
|---|---|
| GNSS | Absolute positioning |
| INS / IMU | Inertial motion estimation |
| LiDAR | 3D environment sensing and localization support |
| Camera | Visual perception / visual localization support |
| Wheel odometry | Vehicle motion estimate |

The repository also documents the intended real platform configuration, including an Intel RealSense D435i camera, an SBG Ellipse-E inertial system and a Hesai Pandar XT-32 LiDAR.

## EKF experiment available in this repository

The included notebook `test_ekf.ipynb` evaluates three configurations on the same CARLA replay:

1. **Odometry only**
2. **IMU only**
3. **Odometry + IMU**

The filtered output `/odometry/filtered` is compared against the CARLA reference topic `/carla/hero/odometry`.

### Metrics

The notebook computes:

- RMSE on x and y;
- 2D position RMSE;
- mean and maximum timestamp offset;
- effective sampling frequency;
- run duration.

For the recorded example included in the notebook, each configuration contains 210 samples at approximately 20 Hz over 10.45 s.

| Configuration | RMSE 2D |
|---|---:|
| Odometry only | 0.0000 m |
| IMU only | 214.3412 m |
| Odometry + IMU | 7.4464 m |

> **Important interpretation:** these values are a demonstration of the evaluation pipeline, not a general performance benchmark. CARLA odometry is also used as the reference trajectory, which explains the zero error obtained by the odometry-only configuration. The IMU-only case illustrates strong inertial drift when no absolute or external correction is available.

## ROS 2 / CARLA workflow

```mermaid
flowchart LR
    A[CARLA simulation] --> B[ROS 2 bridge]
    B --> C[Odometry]
    B --> D[IMU]
    B --> E[LiDAR / sensor streams]
    C --> F[EKF / robot_localization]
    D --> F
    F --> G[/odometry/filtered]
    B --> H[CARLA reference odometry]
    G --> I[Evaluation logger]
    H --> I
    I --> J[CSV logs]
    J --> K[Jupyter analysis]
    K --> L[RMSE, latency, trajectories]
    B --> M[RViz visualization]
```

## Demonstration

The current repository already includes a ROS 2 / CARLA / RViz demonstration showing vehicle motion, sensor visualization and localization outputs.

https://github.com/user-attachments/assets/da7d7c57-9a8b-4318-9f9b-78eda55cb568

<p align="center">
  <img width="900" alt="ROS 2 CARLA RViz localization demo" src="https://github.com/user-attachments/assets/95580bf7-3f11-4388-a766-4d02e38dd873" />
</p>

## Repository contents

```text
.
├── README.md
├── README_FR.md
├── ProjetsSMART25-26_ToSyMA_EZ_sujet3-4.pdf
├── test_ekf.ipynb
└── docs/
    ├── methodology.md
    ├── results.md
    └── limitations.md
```

## Reproduce the notebook analysis

The notebook expects CSV files generated from repeated runs of the same CARLA rosbag with different EKF configurations. The original local paths shown in the notebook are environment-specific and are not part of this public repository.

A typical analysis flow is:

```text
CARLA rosbag
   -> replay with EKF configuration
   -> compare_logger.py
   -> CSV
   -> test_ekf.ipynb
   -> RMSE / latency / trajectory analysis
```

## What this repository demonstrates

- multi-sensor localization concepts for autonomous vehicles;
- ROS 2 integration and sensor-data workflows;
- CARLA-based reproducible simulation;
- EKF configuration and comparison;
- quantitative evaluation with RMSE and timing metrics;
- RViz visualization and recorded-data analysis.

## Limitations

- The quantitative notebook currently compares odometry-only, IMU-only and odometry + IMU configurations.
- LiDAR and camera are part of the broader localization study and platform integration, but they are not part of the EKF comparison shown in `test_ekf.ipynb`.
- CARLA odometry is used as the reference in the available notebook, so the odometry-only result is not an independent localization benchmark.
- The repository does not currently provide the CSV logs or the complete ROS 2 workspace needed for one-command reproduction.

See [docs/limitations.md](docs/limitations.md) for details.

## Original project brief

The original academic project specification is available here:

[ProjetsSMART25-26_ToSyMA_EZ_sujet3-4.pdf](ProjetsSMART25-26_ToSyMA_EZ_sujet3-4.pdf)

## Author

**Touwende OUEDRAOGO**  
Master 2 SMaRT, Universite de Lille
