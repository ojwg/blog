---
layout: default
title:  "Troubleshooting Particle Evolution with SOR"
date:   2020-09-29 09:00:00 -0400
categories: disk
---

## Test particle evolution

300 test particles, each $$1 M_{\odot}$$, evolving for 30 Myr.  Initially the particles are distributed with radial positions $$\leq$$ 2 kpc and with purely circular orbital speeds.

The full analytic galactic potential is applied within the simulation region  and the boundary.

Without OpenMP and running on one 1 GPU:

<video width="620" height="620" controls>
  <source src="../../../../assets/videos/2020/9/300_particles_1gpu_no_openmp.mp4" type="video/mp4"/>
</video> 

Same scenario running on 4 GPUs and 7 OpenMP threads:

<video width="620" height="620" controls>
  <source src="../../../../assets/videos/2020/9/300_particles_4gpu.mp4" type="video/mp4"/>
</video> 

The issues with the simulation don't appear to be related to how the job is partitioned.


Alternatively the videos can be downloaded from [here (1 GPU)](https://github.com/ojwg/blog/raw/master/assets/videos/2020/09/300_particles_1gpu_no_openmp.mp4) and [here (4 GPU)](https://github.com/ojwg/blog/raw/master/assets/videos/2020/09/300_particles_4gpu.mp4)
