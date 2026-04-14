6DOF Singularity Analysis

From Kinematics to Simulation (URDF + Gazebo)

---

Overview

This project explores the complete pipeline of a 6 DOF robotic manipulator:

- Kinematic modeling (Denavit–Hartenberg)
- Inverse kinematics
- Jacobian analysis
- Singularity behavior
- CAD modeling (FreeCAD)
- URDF generation
- Simulation in RViz and Gazebo

The main focus is not just making the robot move, but understanding:

«when and why it stops behaving correctly»

---

Why Singularities Matter

In robotic manipulators, singularities represent configurations where:

- The robot loses one or more degrees of freedom
- Small inputs generate unstable or undefined motion
- The Jacobian matrix becomes non-invertible

This project intentionally works with a robot that reaches these limits, in order to analyze them.

---

Preview

Simulation| Singularities
docs/images/robot_overview.gif| docs/images/singularity_case.gif

---

Project Structure

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

How to Run

# Clone repository
git clone https://github.com/your_user/6dof-singularity-analysis.git

# Run simulation (example)
cd simulation/docker
docker-compose up

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

License

MIT (optional)

---

Contributions

Not open yet — this is an ongoing internal development.

---

Author

Uriel A. Ramírez
Engineering approach: build → break → understand

---
