# Spacecraft Trajectory Optimization Project Report


## Project Overview

The essence of the project was to compute optimal trajectories for a spacecraft equipped with only two functional lateral thrusters. The goal was to reach a predefined target location while avoiding obstacles and minimizing fuel consumption, under the constraints of spacecraft dynamics and control limitations.

The results presented are based on simulations, as we did not have access to a physical rocket for testing.


<p float="left">
  <img src="https://github.com/CamillaMazzoleni/RocketLanding_SCvx/assets/109732478/85fe672f-6c8a-4fed-8cb0-26ee7ded8488" width="300" />
  <img src="https://github.com/CamillaMazzoleni/RocketLanding_SCvx/assets/109732478/6463292a-f1c5-4b7d-a8c8-9e9d91da04c4" width="300" /> 
</p>

[Rocket dynamics code implementation](./src/pdm4ar/exercises/ex09/planner.py)


## Methodological Approach
We developed the solution based on the following paper [(Convex Optimisation for Trajectory Generation)](https://arxiv.org/pdf/2106.09125.pdf) on SCvx, the planning method used in 2021 by spaceX to land their rocket on a moving platform in the middle of the ocean.

### Sequential Convex Programming (SCvx)

SCvx stood at the core of our approach, offering a framework to iteratively linearize and solve the non-convex trajectory optimization problem as a series of convex subproblems. This method is particularly suited for dealing with the nonlinear dynamics and constraints of spacecraft navigation.

[SCvx code implementation](./src/pdm4ar/exercises/ex09/planner.py)


### Discretization

To apply SCvx effectively, the project employed discretization techniques, including ZeroOrderHold and FirstOrderHold, to approximate the spacecraft's continuous-time dynamics with discrete-time models. This step was critical for linearizing the spacecraft’s dynamics around a reference trajectory, facilitating the application of convex optimization tools.

[Discretization implementation](./src/pdm4ar/exercises/ex09/discretization.py)



## Results
The results presented here are from simulations designed to closely mimic the real-world dynamics and constraints of spacecraft navigation.
### Scenario 1: Dodging Planets with a Static Goal
The first scenario introduced the basic challenge of navigating around static obstacles (planets) to reach a fixed goal. The primary challenge was accurately modeling the planets as obstacles and generating efficient paths that minimize fuel consumption and time.

https://github.com/CamillaMazzoleni/RocketLanding_SCvx/assets/109732478/93d01f6b-f09e-402d-93ab-e667514e0bfb



### Scenario 2: Dodging a Planet and Its Satellites with a Static Goal

Building on the complexity, the second scenario added moving obstacles (satellites) orbiting a planet. The dynamic nature of the obstacles required more sophisticated prediction and avoidance strategies, testing the flexibility and adaptability of our SCvx implementation.


https://github.com/CamillaMazzoleni/RocketLanding_SCvx/assets/109732478/2bbe1305-33d1-4dde-ac15-e0cc2dc0f418

### Scenario 3: Dodging a Planet and Its Satellites with a Time-Varying Goal

The final scenario introduced a moving goal, linked with one of the satellites, elevating the problem's complexity by requiring the spacecraft to predict the future position of the moving goal while avoiding the orbiting satellites. This scenario pushed the limits of our trajectory optimization framework, demanding high precision in trajectory planning and control.



https://github.com/CamillaMazzoleni/RocketLanding_SCvx/assets/109732478/a4c656fd-50b8-4892-b841-f74bef4fbf0c




