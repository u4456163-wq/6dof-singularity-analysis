# ROBOTIN — Failure-Driven Kinematic & Singularity Analysis  
### From Modeling to Breakdown: Understanding Where Robots Fail

---

## Overview

ROBOTIN is a robotics analysis framework focused on **understanding failure conditions in robotic manipulators**, rather than only achieving nominal behavior.

The project implements a full pipeline:

- Kinematic modeling (Denavit–Hartenberg)
- Inverse kinematics
- Jacobian-based singularity analysis
- CAD modeling (FreeCAD)
- URDF generation
- Simulation using ROS 2

Unlike conventional robotics projects, this system is intentionally driven into **non-ideal and failure states** to analyze:

> when, why, and how a robotic system breaks

---

## Simulation Environment

The simulation stack is built using:

- ROS 2 Jazzy Jalisco  
- Docker-based environment for reproducibility  
- RViz for visualization  
- Gazebo for physics simulation  

This setup enables:

- Reproducible and isolated environments  
- Scalable deployment across systems  
- Compatibility with modern ROS 2 workflows  

---

## System Pipeline

D-H Modeling → Jacobian Analysis → CAD (FreeCAD)  
→ Mesh Export (STL) → URDF → ROS 2 (RViz / Gazebo)

---

## Core Philosophy

Most robotics systems are designed under ideal assumptions.

ROBOTIN focuses on:

- Misaligned coordinate systems (LCS vs GCS)  
- Invalid joint constraints  
- Mesh-induced instability  
- Simulation breakdown under real-world imperfections  

> A robot is not defined by where it works,  
> but by where it stops working  

---

## Current Implementation

- 1 DOF system fully modeled and simulated  
- 2 DOF system validated with stable kinematics  
- 6 DOF manipulator under progressive development  
- RViz visualization operational  
- Gazebo integration via Docker  

---

## Failure Cases (Key Contribution)

### 1. Joint Misalignment
- Cause: Incorrect frame definition (Local vs Global)
- Effect: Invalid kinematic chain behavior

---

### 2. Mesh-Induced Instability
- Cause: STL inconsistencies or incorrect orientation
- Effect: Simulation crashes or unstable dynamics

---

### 3. Constraint Breakdown
- Cause: Overconstrained or poorly defined joints
- Effect: Non-physical motion or solver failure

---

## Physics Integration (In Progress)

- Gravity modeling  
- Potential energy formulation  
- Mass distribution analysis  

These elements are being incorporated to evaluate how physical parameters affect system stability and singular behavior.

---

## Project Structure

---

math/        → Kinematic and Jacobian analysis  
cad/         → Mechanical design in FreeCAD  
urdf/        → Robot description and meshes  
simulation/  → RViz, Gazebo, Docker setup  
docs/        → Theory, explanations, images  
tests/       → Validation and singularity cases  

---

Kinematic Model

The robot is modeled using Denavit–Hartenberg parameters.

This includes:

- Forward kinematics (homogeneous transformations)
- Inverse kinematics (analytical / numerical)
- Jacobian matrix derivation

Detailed derivations are available in:

docs/theory.md
math/

---

Jacobian & Singularities

Singularities are detected through:

- Jacobian determinant → det(J) = 0
- Loss of rank in J
- Velocity amplification effects

These configurations are tested and visualized in simulation.

---

CAD Modeling (FreeCAD)

The robot geometry is designed in FreeCAD and exported using a URDF workbench.

Key considerations:

- Joint alignment
- Correct placement (critical)
- Mesh orientation

Common issues during export are documented in:

cad/notes.md

---

URDF Generation

The URDF model includes:

- Links and joints
- Collision models
- Visual meshes

Special care is required to avoid:

- Misaligned joints
- Broken kinematic chains

---

Simulation (RViz & Gazebo)

The robot is deployed using ROS with Docker support.

Features:

- Interactive joint control
- Collision validation
- Real-time visualization

---

## How to Run

```bash
# Clone repository
git clone https://github.com/u4456163-wq/6dof-singularity-analysis.git

# Run Docker environment
cd simulation/docker
docker-compose up --build

# Enter container
docker exec -it robotin_container bash

# Launch visualization
ros2 launch robotin display.launch.py
```
---

Validation

The following aspects are verified:

- Forward kinematics consistency
- Inverse kinematics solutions
- Jacobian correctness
- Behavior near singularities

---

Key Insight

This project is not about achieving perfect motion.

It is about understanding the limits of the system:

«A robot is not defined by where it works,
but by where it stops working.»

---

Status

Work in progress (private development)
---

Contributions

Not open yet — this is an ongoing internal development.

---

Author

Uriel A. Ramírez
Engineering approach: build → break → understand

---
