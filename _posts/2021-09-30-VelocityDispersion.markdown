---
layout: default
title:  "Velocity Dispersion"
date:   2021-09-30 09:00:00 -0400
categories: disk feedback
---

## Gas Velocity Dispersion

I evolved 38 $$10^5 \mathrm{M}_\odot$$ clusters for 20 Myr.  In this scenario SN feedback turns off at 10 Myr.  The following plots the gas velocity distribution over time:
![Gas Velocity Dispersion]({{'/assets/images/2021/09/gas_velocity_dispersion.png' | relative_url}}) 

The velocity dispersion plot labeled `poisson` is calculated by first subtracting the local circular speed at each gas element as determined the local gravitational acceleration.  
Likewise, the plot labeled `analytic` is calculated by first subracting off the circular speed given by a Miyamoto-Nagai disk and NFW halo gravitational acceleration.
Also included are two plots for the same simulation but without the SN feedback contribution. 

---

What clearly stands out are the large jumps in velocity dispersion at early times.  The data for each plot came from repeating the same scenario using a fixed seed when setting up the 
initial cluster locations as well as when initializing the SNe poisson random number generator.  Since the `analytic` data show velocity dispersion jumps not seen in the `poisson` case one
potential explanation is that this is an artifact of contention problems when adding feedback to the gas.   However this doesn't explain why these jump are prevalent towards the start of the 
simulation.

---

Gas speed in the galactic plane for the simulation marked `analytic` in the velocity dispersion plot.
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/09/20Myr_xy_hydro_speed.mp4' | relative_url }}" type="video/mp4"/> 
</video>
[comment]: <> (vid comes from data from CRC Sep29_21_Wednesday-09-42_38_particle_hydro_feedback_stats_ANALYTIC_20Myr)

Gas density for the same simulation as above (`analytic`)
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/09/20Myr_xy_hydro_density.mp4' | relative_url }}" type="video/mp4"/> 
</video>



