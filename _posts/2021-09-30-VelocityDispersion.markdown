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

What clearly stands out are the large jumps in velocity dispersion at early times.  The data for each plot came from repeating the same scenario using fixed seeds, making the 
dispersion jump seen on the `analytic` plot but missing on the `poisson` plot (at around 950 kyr) surprising.  I thought the difference due to a multithreading bug in the feedback 
implementation, while Dr. Schneider thought it could be due to unresolved SNe resulting from higher than expected ISM density variations.  The following plot takes a closer look 
at the relevant data.

![Zoomed in Gas Velocity Dispersion]({{'/assets/images/2021/09/zoom_in_dispersion.png' | relative_url}}) 

The blue curve represents the velocity dispersion measurements.
The vertical gray dotted lines indicate the occurrence in time of resolved SNe, while the red dotted lines mark the occurrence of unresolved SNe.  Interestingly two unresolved SNe took place
just before the rise in velocity dispersion.  The previous unresolved SN happened at time 460 kyr and no other unresolved SN took place after.   It seems plausible that the `poisson` 
method for calculating velocity dispersion is better able to "smooth-over" the local vagaries of density perturbations.

Looking at a previous spike in the `analytic` curve at time 325 kyr
![Zoomed in Gas Velocity Dispersion2]({{'/assets/images/2021/09/zoom_in_dispersion2.png' | relative_url}}) 
and at time 220 kyr
![Zoomed in Gas Velocity Dispersion3]({{'/assets/images/2021/09/zoom_in_dispersion3.png' | relative_url}}) 
we also find a correlation with unresolved SNe.

If we expand the view for the data at 220 kyr
![Zoomed in Gas Velocity Dispersion4]({{'/assets/images/2021/09/zoom_in_dispersion4.png' | relative_url}}) 
we see that not all unresolved SNe are associated with dispersion spikes.  This is to be expected if an unresolved SN takes place in a very localized high-density 
region surrounded by low density gas.

---

Gas density in the galactic plane at a million years (just after the last velocity dispersion spike in the `analytic` plot):
![Gas Density]({{'/assets/images/2021/09/10.png' | relative_url}}) 

Gas speed in the galactic plane for the simulation marked `analytic` in the velocity dispersion plot:
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/09/20Myr_xy_hydro_speed.mp4' | relative_url }}" type="video/mp4"/> 
</video>
[comment]: <> (vid comes from data from CRC Sep29_21_Wednesday-09-42_38_particle_hydro_feedback_stats_ANALYTIC_20Myr)

The logarithm base 10 of the same plot as above (`analytic`):
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/09/20Myr_xy_hydro_log_speed.mp4' | relative_url }}" type="video/mp4"/> 
</video>

Gas density for the same simulation as above (`analytic`):
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/09/20Myr_xy_hydro_density.mp4' | relative_url }}" type="video/mp4"/> 
</video>


---

Plotting the difference between the gas speed and the "mean speed":

<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/09/20Myr_xy_hydro_log_disp_with_pressure.mp4' | relative_url }}" type="video/mp4"/> 
</video>

The peak velocity dispersion values appear to exceed the peak gas velocity values.  The problem is with the inclusion of the pressure gradient in the calculation of the mean streaming velocity.  While this
makes sense in calculating near-equilibrium gas circular velocities, it breaks down when dealing with SNe.
Removing this term results in the following better behaved velocity dispersion video:

<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/09/20Myr_xy_hydro_log_disp_no_pressure.mp4' | relative_url }}" type="video/mp4"/> 
</video>

