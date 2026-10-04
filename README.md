# BubbleRob Mobile Robot Simulation

![CoppeliaSim](https://img.shields.io/badge/Simulator-CoppeliaSim%20Edu-blue)
![Language](https://img.shields.io/badge/Language-Lua-2C2D72)
![Physics](https://img.shields.io/badge/Physics-Bullet%202.78-green)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

A differential-drive mobile robot simulation developed in **CoppeliaSim Edu**. The robot, *bubbleRob*, operates inside a ring of cylindrical obstacles and is equipped with a proximity sensor and a vision sensor. Obstacle clearance is plotted in real time, and the robot's speed can be adjusted during simulation through a custom UI slider.

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Demo](#demo)
- [Screenshots](#screenshots)
- [System Design](#system-design)
- [Implementation Steps](#implementation-steps)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Repository Structure](#repository-structure)
- [Author](#author)
- [License](#license)

## Overview

This project covers the full workflow of building a simple mobile robot in simulation: constructing the robot model, adding sensors, creating an environment, writing Lua control scripts, and visualising sensor data during a run.

## Key Features

- **Differential-drive robot** with independent left and right motors and wheels
- **Proximity sensor ("sensing nose")** for detecting nearby obstacles
- **Vision sensor** mounted on the robot, with edge detection applied to the captured image
- **Real-time graph** of obstacle clearance (m) against simulation time
- **Interactive speed slider** to change motor speed while the simulation is running
- **Obstacle environment** of cylinders arranged in a ring around the robot
- **Lua scripting** for robot control and vision processing

## Demo

![Simulation preview](demo/simulation-preview.gif)

The full screen recording (about 65 seconds) is available at [`demo/simulation-demo.mp4`](demo/simulation-demo.mp4). It shows the simulation running with the live clearance graph, the vision sensor output and the speed slider.

## Screenshots

| Scene hierarchy | Obstacle environment |
|---|---|
| ![Scene hierarchy](images/01-scene-hierarchy.jpg) | ![Obstacle ring](images/04-obstacle-ring.jpg) |

| Vision sensor attached to robot | Simulation running |
|---|---|
| ![Vision sensor](images/06-vision-sensor-attached.jpg) | ![Simulation running](images/11-simulation-running.jpg) |

Additional screenshots, including graph setup, sensor configuration and the Lua scripts, are available in [`images/`](images/).

## System Design

| Component | Purpose |
|---|---|
| `bubbleRob` | Main robot body and control script |
| `bubbleRob_leftMotor` / `bubbleRob_rightMotor` | Drive the left and right wheels |
| `bubbleRob_sensingNose` | Proximity sensor for obstacle detection |
| `visionSensor` | Camera sensor with edge-detection processing |
| `bubbleRob_graph` | Plots obstacle clearance over time |
| `bubbleRob speed` (UI) | Slider to adjust robot speed at runtime |

**Vision pipeline:** the vision sensor script copies the sensor image to a work image, applies edge detection (threshold `0.2`), and writes the result back to the sensor image.

## Implementation Steps

1. Built the `bubbleRob` model with body, motors, wheels, slider and proximity sensor.
2. Added a graph object to record clearance to obstacles.
3. Placed cylindrical obstacles around the robot to create the test environment.
4. Attached and configured a vision sensor on the sensing nose.
5. Wrote Lua scripts for robot initialisation, motor control, the speed-slider callback and vision processing.
6. Ran the simulation and analysed the clearance graph and sensor output.

## Tech Stack

- CoppeliaSim Edu 4.x
- Bullet 2.78 physics engine
- Lua

## Getting Started

**Prerequisites:** [CoppeliaSim Edu](https://www.coppeliarobotics.com/) installed.

1. Clone the repository:
   ```bash
   git clone https://github.com/kishan-kumarx07/bubblerob-coppeliasim-simulation.git
   ```
2. Open CoppeliaSim and load the scene from the `scene/` folder (**File → Open scene**).
3. Press **Start** (▶) to run the simulation.
4. Use the speed slider to change the robot's speed and watch the clearance graph update.

## Repository Structure

```
bubblerob-coppeliasim-simulation/
├── demo/        # Simulation recording and GIF preview
├── images/      # Screenshots of the build and simulation
├── scene/       # CoppeliaSim scene file (.ttt)
├── scripts/     # Lua scripts
├── LICENSE
└── README.md
```

## Author

**Kishan Kumar Mahato**

- GitHub: [kishan-kumarx07](https://github.com/kishan-kumarx07)
- LinkedIn: [Kishan Kumar Mahato](https://www.linkedin.com/in/kishan-kumar-mahato-251a74333/)

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
