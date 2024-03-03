# Spacecraft Trajectory Optimization Project Report


## Project Overview

The essence of the project was to compute optimal trajectories for a spacecraft equipped with only two functional lateral thrusters. The goal was to reach a predefined target location while avoiding obstacles and minimizing fuel consumption, under the constraints of spacecraft dynamics and control limitations.

## Methodological Approach
We developed the solution based on the following paper (Convex Optimisation for Trajectory Generation) on SCvx, the planning method used in 2021 by spaceX to land their rocket on a moving platform in the middle of the ocean.

### Sequential Convex Programming (SCvx)

SCvx stood at the core of our approach, offering a framework to iteratively linearize and solve the non-convex trajectory optimization problem as a series of convex subproblems. This method is particularly suited for dealing with the nonlinear dynamics and constraints of spacecraft navigation.

### Discretization

To apply SCvx effectively, the project employed discretization techniques, including ZeroOrderHold and FirstOrderHold, to approximate the spacecraft's continuous-time dynamics with discrete-time models. This step was critical for linearizing the spacecraft’s dynamics around a reference trajectory, facilitating the application of convex optimization tools.


## Scenarios and Challenges

### Scenario 1: Dodging Planets with a Static Goal
- [Trajectory Optimization Animation](https://github.com/CamillaMazzoleni/RocketLanding_SCvx/blob/main/out/09/index.html_resources/Evaluation-Final23-config-mov-target-EpisodeVisualisation-figure1-Animation.mp4)

<video width="320" height="240" controls>
  <source src="https://github.com/CamillaMazzoleni/RocketLanding_SCvx/blob/main/out/09/index.html_resources/Evaluation-Final23-config-mov-target-EpisodeVisualisation-figure1-Animation.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
The first scenario introduced the basic challenge of navigating around static obstacles (planets) to reach a fixed goal. The primary challenge was accurately modeling the planets as obstacles and generating efficient paths that minimize fuel consumption and time.

### Scenario 2: Dodging a Planet and Its Satellites with a Static Goal

Building on the complexity, the second scenario added moving obstacles (satellites) orbiting a planet. The dynamic nature of the obstacles required more sophisticated prediction and avoidance strategies, testing the flexibility and adaptability of our SCvx implementation.

### Scenario 3: Dodging a Planet and Its Satellites with a Time-Varying Goal

The final scenario introduced a moving goal, linked with one of the satellites, elevating the problem's complexity by requiring the spacecraft to predict the future position of the moving goal while avoiding the orbiting satellites. This scenario pushed the limits of our trajectory optimization framework, demanding high precision in trajectory planning and control.

