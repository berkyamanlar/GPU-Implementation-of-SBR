# GPU-Accelerated Radar Cross Section (RCS) Simulation

## Description
This project focuses on the development of a GPU-accelerated Radar Cross Section (RCS) simulation, aimed at enhancing the computational efficiency of the Shooting and Bouncing Rays (SBR) method. The SBR technique estimates RCS by simulating electromagnetic ray propagation and interactions with an object's surfaces, defined by triangle meshes. Utilizing parallel processing on Graphics Processing Units (GPUs) accelerates ray-tracing significantly, reducing computational time while maintaining simulation accuracy. The simulation environment is visually rendered using OpenGL, with an example shown below for an F-15 fighter jet.

![Rendered Simulation Environment](https://github.com/berkyamanlar/GPU-Implementation-of-SBR/blob/main/assets/f15.png)

*Rendered simulation environment for an F-15 fighter jet.*

The full thesis can be found [here](https://github.com/berkyamanlar/GPU-Implementation-of-SBR/blob/main/Final_Report.pdf).

## Validation
To validate the accuracy of the RCS simulations, simple objects with analytical solutions were used. Below are the results for a flat plate with different polarizations:

### Horizontal Polarization Results
In blue, the analytical solution is displayed, while the simulation results are shown in red.

![Horizontal Polarization](https://github.com/berkyamanlar/GPU-Implementation-of-SBR/blob/main/assets/accuracy1.png)

*Horizontal polarization RCS results for a flat plate.*

### Vertical Polarization Results
Similar to the horizontal case, analytical results are in blue, and the simulation results are in red.

![Vertical Polarization](https://github.com/berkyamanlar/GPU-Implementation-of-SBR/blob/main/assets/accuracy2.png)

*Vertical polarization RCS results for a flat plate.*

## Performance Analysis
The timing comparison between CPU and GPU implementations across different frequencies shows significant improvements with the GPU approach.

![Timing Comparison](https://github.com/berkyamanlar/GPU-Implementation-of-SBR/blob/main/assets/timingcomparison.jpg)

*Timing comparison of CPU and GPU processing at various frequencies.*

## Shadowing Effect
The simulation accurately models shadowing effects. For instance, when a cylinder blocks the rays, the area behind it remains unaffected.

![Shadowing Effect](https://github.com/berkyamanlar/GPU-Implementation-of-SBR/blob/main/assets/shadowing.png)

*Shadowing effect in the simulation, where the cylinder prevents rays from hitting the region behind it.*

## Bounding Volume Optimization
Despite parallel ray tracing, each ray still requires checking for interactions at every bounce, which can be time-consuming. In this project, a combination of Octrees and KD trees was proposed for optimization. Initially, each triangle was assigned to a bounding volume using cubes, simplifying the process. However, since each cube has six faces, defined by two triangles each, it resulted in 12 intersection checks per volume. To reduce this, bounding spheres were employed, allowing for a more efficient ray-sphere interaction equation.

### Bounding Cubes
![Bounding Cubes](https://github.com/berkyamanlar/GPU-Implementation-of-SBR/blob/main/assets/bounding1.png)

*Bounding cubes used for spatial partitioning.*

### Bounding Spheres
![Bounding Spheres](https://github.com/berkyamanlar/GPU-Implementation-of-SBR/blob/main/assets/bounding2.png)

*Bounding spheres for optimizing ray-volume interaction checks.*
