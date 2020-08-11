---
layout: post
title:  "Particles-only Disk Evolution"
date:   2020-08-11 16:00:00 -0400
categories: disk
---

## Initial Particle-only Evolution
---

Particle-ony simulation for 4kpc sided box with MW-initial potential.   The particles are assumed to be stellar clusters with a fixed mass of $10^4 M_{\odot}$ Ran for the default 1 hour on 4 `amdMI60` GPUs on Poplar.  

Compiler flags used:

 DFLAG | value 
------|-------|
CUDA |  
MPI_CHOLLA |  
BLOCK |
PFFT |
PRECISION | 2 
OUTPUT | 
HDF5 | 
SLICES | 
PPMC | 
HLLC | 
VL | 
DDE | 
COOLING_GPU | 
TEMPERATURE_FLOOR | 
CPU_TIME | 
GRAVITY | 
GRAVITY_LONG_INTS |
COUPLE_GRAVITATIONAL_WORK |
GRAVITY_5_POINTS_GRADIENT | 
PARTICLES |
PARTICLES_CPU |
ONLY_PARTICLES |
SINGLE_PARTICLE_MASS |
PARTICLE_LONG_INTS |
PARTICLE_KDK |
PARTICLE_IDS |
PARALLEL_OMP | 
N_OMP_THREADS | 16
PRINT_OMP_DOMAIN |
DO_HIP | 

The reason for running particle-only was to get a feel for the evolution after about 10 Myr. Adding hydrodynamics slows the simulation down to the point that only about 1 Myr evolution is undertaken before the one hour time constraint is up. 

### Particle Density Evolution to 10 Myr
##### Midplane:
The particle density appears to clump up in time and to assume the boxy shape of the initial simulation volume.  
Perhaps a combination of the assumed initial speed distribution and the addition of the analytical (dark matter) potential is not quite right.
<video width="620" height="620" controls>
  <source src="../../../../assets/videos/2020/8/xy_part_density.mp4" type="video/mp4"/>
</video> 

### Particle Motions to 10 Myr
A randomly selected subset of 300 particles are followed for 10 Myr.  At the limit of R \approx 2 kpc there appears to be a glitch calculating the velocities as the particles approach the domain boundaries.
<video width="820" height="820" controls>
  <source src="../../../../assets/videos/2020/8/particles.mp4" type="video/mp4"/>
</video> 

