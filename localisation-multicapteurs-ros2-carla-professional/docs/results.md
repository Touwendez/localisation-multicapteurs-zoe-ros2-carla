# Results

## Public notebook experiment

The notebook contains 210 paired samples per configuration, at an effective frequency of approximately 20 Hz and a duration of 10.45 s.

| Configuration | RMSE x | RMSE y | RMSE 2D | Frequency |
|---|---:|---:|---:|---:|
| Odometry only | 0.0000 m | 0.0000 m | 0.0000 m | 20 Hz |
| IMU only | 180.0822 m | 116.2434 m | 214.3412 m | 20 Hz |
| Odometry + IMU | 6.2418 m | 4.0608 m | 7.4464 m | 20 Hz |

The recorded timestamp-offset columns are zero in the notebook outputs for these runs.

## Interpretation

### Odometry only

The CARLA odometry topic is also used as the reference trajectory, so the zero error is expected and should be treated as a property of the evaluation setup rather than a localization performance result.

### IMU only

The large error illustrates the drift produced by integrating inertial measurements without an external position correction.

### Odometry + IMU

The experiment demonstrates the complete fusion and evaluation workflow. Because the reference and odometry source are closely related in this simulation setup, the numerical results should not be generalized to a real vehicle.

## Recommended next experiments

A stronger validation protocol would include:

- noisy or degraded odometry;
- GNSS dropouts or injected GNSS noise;
- independent ground truth;
- longer trajectories;
- repeated runs;
- real-platform measurements;
- separate evaluation of LiDAR or visual localization modules before fusion.
