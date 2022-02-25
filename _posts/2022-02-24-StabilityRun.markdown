---
layout: default
title:  "1 Gy Hydro+Particles run"
date:   2022-02-22 09:00:00 -0400
categories: disk feedback gpu
---

## code changes for GPU support

Support handling particle attributes such as indentity and age on the GPU, requiring proper setup of host/device variables and the handling of these attributes on the boundaries. 
One minor outcome of this is the proper setup of particle IDs when running with more than one MPI rank.  Other code changes improve the handling of the analytic potential contribution 
to the gravitational potential.  This contribution is from external mass distributions (dark matter, non-modeled disk populations, etc.) and is assumed to not vary during the simulation.  

SN feedback has also been implemented on the GPU leveraging cuRAND to generate the Poisson SNe distribution.

---

##  Simulation Settings

Disk gas and 38 star clusters were evolved over 1 Gy to get a sense of stability over time. A $$256^3$$ grid and 4 MPI ranks were used to model the $$4^3$$ kpc$$^3$$ region around the 
galactic center.

| Compilation Flags|
|------------------|
| MPI_GPU |
| HYDRO_GPU |
| PARTICLES |
| PARTICLES_GPU |
| PARTICLE_IDS |
| SINGLE_PARTICLE_MASS |
| PARTICLE_AGE |
| GRAVITY |
| GRAVITY_GPU |
| PARIS_GALACTIC |
| GRAVITY_ANALYTIC_COMP |
| GRAVITY_5_POINTS_GRADIENT |
| CUDA |
| MPI_CHOLLA |
| BLOCK |
| PRECISION=2 |
| PPMP |
| HLLC |
| VL |
| DISK_ICS |
| DENSITY_FLOOR |
| TEMPERATURE_FLOOR |
| COOLING_GPU |
| DE |
| AVERAGE_SLOW_CELLS |
| OUTPUT |
| HDF5 |
| SLICES |
| PARALLEL_OMP |
| N_OMP_THREADS=16 |

---

## Results

The gas density slice in the plane of the disk:
 <video width="640" height="640" controls>
    <source src="{{ '/assets/videos/2022/02/xy_density.mp4' | relative_url }}" type="video/mp4"/>  -->
 </video>
and perpendicular to the disk:
 <video width="640" height="640" controls>
    <source src="{{ '/assets/videos/2022/02/xz_density.mp4' | relative_url }}" type="video/mp4"/>  -->
 </video>

 The gas temperature along the plane of the disk:
 <video width="640" height="640" controls>
    <source src="{{ '/assets/videos/2022/02/xy_temp.mp4' | relative_url }}" type="video/mp4"/>  -->
 </video>
and perpendicular to the disk:
 <video width="640" height="640" controls>
    <source src="{{ '/assets/videos/2022/02/xz_temp.mp4' | relative_url }}" type="video/mp4"/>  -->
 </video>

 The gas speed:
 <video width="640" height="640" controls>
    <source src="{{ '/assets/videos/2022/02/xy_speed.mp4' | relative_url }}" type="video/mp4"/>  -->
 </video>

 The star cluster orbits:
 <video width="640" height="640" controls>
    <source src="{{ '/assets/videos/2022/02/orbits.mp4' | relative_url }}" type="video/mp4"/>  -->
 </video>


