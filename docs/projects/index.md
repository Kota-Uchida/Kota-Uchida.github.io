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
  - title: Autonomous Underwater Vehicle
    period: 2026 – present
    summary: >-
      Placeholder entry. A small underwater vehicle used as a testbed for
      depth and heading control, onboard sensing, and embedded software.
    thumbnail: assets/images/projects/placeholder.svg
    tags: [Marine robotics, Embedded systems, Control]
    page: projects/autonomous-underwater-vehicle.md
    selected: true

  - title: Fluid–Structure Interaction Simulation
    period: 2026
    summary: >-
      Placeholder entry. Coupled simulation of a flexible body in a viscous
      flow, used to study how passive compliance changes the dynamics of
      swimming and flapping structures.
    thumbnail: assets/images/projects/placeholder.svg
    tags: [Nonlinear dynamics, Simulation, Fluid mechanics]
    page: projects/fsi-simulation.md
    links:
      - label: Notes
        url: notes/simulation/ode-integrators.md
    selected: true

  - title: Underwater Acoustic Simulation
    period: 2023
    summary: >-
      Placeholder entry. Numerical models of sound propagation in shallow
      water, intended for evaluating acoustic positioning and communication
      for small underwater robots.
    tags: [Acoustics, Simulation]

  - title: Robotics Hardware Prototyping
    period: 2022 – present
    summary: >-
      Placeholder entry. A collection of small mechanisms, actuator mounts,
      and sensor boards built with 3D printing and rapid PCB fabrication.
    tags: [Hardware, Mechanical design]
---

# Projects

Research, engineering, and personal projects, most recent first.
All entries below are placeholders: replace them in `docs/projects/index.md`.
