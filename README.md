# GPU-Accelerated Radar Cross Section (RCS) Simulation

## Description
This project focuses on the development of a GPU-accelerated Radar Cross Section (RCS) simulation, aimed at improving the computational efficiency of the Shooting and Bouncing Rays (SBR) method. The SBR method estimates RCS by simulating electromagnetic ray propagation and scattering interactions with an object's surfaces, defined by triangle meshes. Utilizing parallel processing on Graphics Processing Units (GPUs) significantly accelerates ray-tracing, reducing computational time while maintaining simulation accuracy. Future work includes implementing a bounding volume hierarchy (BVH) to further optimize the number of ray-triangle intersection checks. The simulation environment is visually rendered using OpenGL for enhanced insight.

## Implementation Overview
- **Platform:** C++ with GPU parallel programming (CUDA)
- **Techniques:** Multi-threading, SIMD, and OpenGL rendering
- **Hardware:** Developed and tested on a system with a modern NVIDIA GPU

## Results
- Achieved significant speedup compared to traditional CPU-based methods
- Accurate RCS estimation for high-frequency simulations with complex geometries

## Future Work
- Integrate a bounding volume hierarchy (BVH) to optimize ray-triangle intersection calculations
