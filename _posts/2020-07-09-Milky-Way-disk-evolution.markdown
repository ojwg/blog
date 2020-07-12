---
layout: post
title:  "MW Disk Evolution"
date:   2020-07-09 16:00:00 -0400
categories: disk
---

## Milky-Way like disk evolution.
---

Disk simulation with MW parameters ran for the default 1 hour on 4 `amdMI60` GPUs on Poplar.  

Compiler flags used:

 DFLAG | value 
------|-------|
CUDA |  
MPI_CHOLLA |  
PRECISION | 2 
OUTPUT | 
HDF5 | 
SLICES | 
PPMC | 
HLLC | 
VL | 
DDE | 
COOLING_GPU | 
CPU_TIME | 
STATIC_GRAV | 
PARALLEL_OMP | 
DN_OMP_THREADS | 16
DO_HIP | 

First run produced results that clearly different than what was expected.  This turned out to be due to still running with the `DENSITY_FLOOR` and `TEMPERATURE_FLOOR` flags. 

### Density at 9.8 Myr
##### Midplane:
![Density at 9.8 Myr](../../../../assets/images/2020/7/xyD98.png "Midplane density")
<video width="620" height="620" controls>
  <source src="../../../../assets/videos/2020/7/d_xy.mp4" type="video/mp4"/>
</video> 
##### Transverse:
![Density at 9.8 Myr](../../../../assets/images/2020/7/xzD98.png "Transverse density")
<video width="620" height="620" controls>
  <source src="../../../../assets/videos/2020/7/d_xz.mp4" type="video/mp4"/>
</video> 

### Midplane velocity magnitude  at 9.8 Myr
![Speed at 9.8 Myr](../../../../assets/images/2020/7/xyV98.png "Midplane velocity magnitude")
<video width="620" height="620" controls>
  <source src="../../../../assets/videos/2020/7/v_xy.mp4" type="video/mp4"/>
</video> 

### Temperature  at 9.8 Myr
##### Midplane:
![Temperature at 9.8 Myr](../../../../assets/images/2020/7/xyTemp98.png "Midplane temperature")
<video width="620" height="620" controls>
  <source src="../../../../assets/videos/2020/7/T_xy.mp4" type="video/mp4"/>
</video> 
##### Transverse:
![Temperature at 9.8 Myr](../../../../assets/images/2020/7/xzTemp98.png "Transverse temperature")
<video width="620" height="620" controls>
  <source src="../../../../assets/videos/2020/7/T_xz.mp4" type="video/mp4"/>
</video> 






