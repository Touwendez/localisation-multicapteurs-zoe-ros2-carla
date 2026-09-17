# Methodology

## 1. Localization study

The broader project studies several localization families for autonomous vehicles:

- GNSS/INS integration;
- LiDAR-based localization and LiDAR-SLAM;
- Visual-Inertial Odometry;
- multi-sensor state estimation;
- learning-based localization approaches.

The objective is to compare their operating principles, integration constraints and relevance for a robotic vehicle platform.

## 2. ROS 2 and CARLA integration

CARLA is used as a digital twin environment. Sensor and vehicle data are exposed through ROS 2, allowing localization modules to be configured and evaluated with repeatable recorded sequences.

RViz is used for visualization of vehicle motion, localization outputs and available sensor data.

## 3. EKF experiment

The public notebook compares three EKF configurations:

- odometry only;
- IMU only;
- odometry + IMU.

All configurations are evaluated from the same CARLA replay.

The notebook compares `/odometry/filtered` to `/carla/hero/odometry` and computes:

- x-axis RMSE;
- y-axis RMSE;
- 2D position RMSE;
- mean and maximum time offset;
- effective sampling frequency;
- run duration.

## 4. Data-processing flow

1. Replay the same CARLA rosbag.
2. Run a selected EKF configuration.
3. Log the reference and filtered pose.
4. Export paired samples to CSV.
5. Load the CSV files in `test_ekf.ipynb`.
6. Compute metrics and visualize trajectories and errors.

## 5. Interpretation rule

The CARLA vehicle odometry is used as the reference in the public notebook. Therefore, the odometry-only configuration is not an independent estimate and its zero RMSE must not be interpreted as real-world localization accuracy.
