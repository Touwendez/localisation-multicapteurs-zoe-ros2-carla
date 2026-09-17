# Scope and limitations

## Demonstrated in the public repository

- ROS 2 / CARLA localization workflow;
- EKF evaluation notebook;
- odometry-only configuration;
- IMU-only configuration;
- odometry + IMU fusion;
- RMSE and timing analysis;
- RViz / CARLA demonstration.

## Part of the broader project, but not demonstrated by the public EKF notebook

- GNSS/INS fusion;
- LiDAR-SLAM;
- Visual-Inertial Odometry;
- LiDAR fusion inside the public EKF comparison;
- camera fusion inside the public EKF comparison.

## Reproducibility limitations

The notebook references local CSV files and a local ROS 2 workspace that are not currently included in the repository. Therefore, the analysis is inspectable but not yet fully reproducible from a fresh clone.

## Evaluation limitation

The available notebook uses CARLA odometry as the reference trajectory while also evaluating an odometry-based filter configuration. This makes the odometry-only result unsuitable as an independent accuracy benchmark.
