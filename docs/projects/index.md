---
# ---------------------------------------------------------------------------
# Project list. Each entry under `projects:` becomes one row on this page.
# Only `title` is required. Entries appear in the order written here.
#
#   title:      Project name
#   period:     "2024", "2023 – 2024", "2024 – present", ...
#   summary:    Two or three plain-text sentences
#   thumbnail:  Image path inside docs/ (optional; 16:10, about 640×400 px)
#   tags:       List of topics
#   page:       Detail page inside docs/ (optional), e.g. projects/my-project.md
#   links:      List of {label, url} (GitHub, paper, video, website, ...)
#   selected:   true to also show the project on the home page
# ---------------------------------------------------------------------------
template: projects.html
title: Projects

projects:
  - title: Acoustic Simulation for ocean survey
    period: Nov 2026 - Feb 2027
    summary: >-
      There are several open-source simulator for underwater acoustics, but not many of them can bridge AUV control and acoustic signal processing at the same time. The unique feature of our simulator is that it can funtion as a stand-alone acoustic simulator, and at the same time able to bridge to ROS2-based robot simulators.
    thumbnail: assets/images/projects/placeholder.svg
    tags: [Underwater Acoustics, Simulation, C++, CUDA]
    page: projects/acoustic-simulation.md
    selected: true

  - title: Multi AUV operation 
    period: Aug 2026 - Feb 2027
    summary: >-
      In order to accelerate the underwater survey, theoretically, it is very effective to use multiple AUVs at a time. This project aims to solve operational, communicational issues in multi-AUV system and to develop an user-friendly interface to operate AUV swarm. I'm responsible for everything from hardware design (Solidworks, KiCAD) to software (ROS2).
    thumbnail: assets/images/projects/placeholder.svg
    tags: [Marine robotics, Embedded system, Multi Agent]
    page: projects/multi-auv.md
    selected: true

  - title: UUV-USV joint system
    period: Feb 2026 – Jun 2026
    summary: >-
      UUV(Unmanned Underwater Vehicle) and USV(Unmanned Surface Vehicle) are connected via tether cable. This enables flexible teleoperation by adjusting the position of the cable.
    thumbnail: assets/images/projects/placeholder.svg
    tags: [Marine robotics, Embedded systems, Control]
    page: projects/autonomous-underwater-vehicle.md
    selected: false

  - title: Robotani-Shohei
    period: Nov 2025 - Dec 2025
    summary: >-
      Using a robot simulator "Drake", our team control the Kuka Iiwa robot to play baseball. Major techniques used were MPC (model predictive control), object detection with RGB-D, ball state estimation using RLS (Recursive Least Squares).
    thumbnail: assets/images/projects/placeholder.svg
    tags: [Model predictive control, Computer vision]
    page: projects/robotani-shohei.md
    selected: false

  - title: Underwater 3D reconstruction using VGGT
    period: Oct 2025 - Dec 2025
    summary: >-
      It is difficult to realize robust underwater 3D reconstruction underwater because of the attenuation of the specific frequency of light. This project aims to post-train VGGT using generated data from Infinigen, to enhance the reconstruction fidelity especially of underwater scenes.
    thumbnail: assets/images/projects/placeholder.svg
    tags: [3D reconstruction, Post training, Underwater SLAM]
    page: projects/underwater-reconstruction-vggt.md
    selected: false
  
  - title: CanSat (Software Development)
    period: Jan 2025 - Mar 2025
    summary: >-
      I joined a CanSat development team as a software member. Realtime state estimation algorithm using EKF (Extended Karman Filter) was developed with C++.
    thumbnail: assets/images/projects/placeholder.svg
    tags: [Extended Karman Filter, C++]
    selected: false
---

# Projects

History of my pursuit in science and engineering through projects.
