---
layout: default
title:  "Velocity Dispersion On The GPU"
date:   2022-04-04 09:00:00 -0400
categories: disk feedback gpu
---
[comment]: <> (data comes from running on CRC /ihome/eschneider/ojw4/projects/another_o_cholla/Apr01_22_Friday-11-16_feedback-analysis-4mpi-10My)

# SN Feedback Simulations on the GPU

## Cluster Population

I evolved 35 clusters drawn from a mass distribution of form $$1/\mathrm{mass}$$ bounded by $$10^4 \mathrm{M}_\odot$$ and $$5\times10^6 \mathrm{M}_\odot$$.
The total mass in these cluster particles was $$2.1\times 10^7 \mathrm{M}_\odot$$, or almost an order of magnitude more than in the previous CPU simulations.
These clusters were placed at radial positions drawn from a gamma distribution ($$\alpha=2$$, $$\theta=1$$), multiplied by the disk radial scale length and constrained to 
lie within 2 kpc radius of the galactic center. 

## Gas Density

These videos correspond to the gas density evolution over 10 Myr.
Density on the disk plane:
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2022/04/xy_density_hydro_clusters.mp4' | relative_url }}" type="video/mp4"/> 
</video>
Note that the cluster positions are represented by red star icons with the relative size denoting the cluster mass.

Similarly the density perpendicular to the disk plane:
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2022/04/xz_density_hydro_clusters.mp4' | relative_url }}" type="video/mp4"/> 
</video>
In the above video a cluster position is shown if the distance perpendicular to the x-z plane is within $$0.5$$~kpc. 

## Gas Velocity Dispersion (Turbulence)

Unlike in the case of the CPU feedback simulations only the type of velocity dispersion previously called "analytic'' was calculated.  
This prescription subtracts the analytical circular velocity from the gas velocity at all grid points and computes its squared density weighted average.
What is plotted is the square root of this value over the simulation time.

![Gas Velocity Dispersion]({{'/assets/images/2022/04/dispersion_10Myr_GPU.png' | relative_url}}) 

Although the v$$_{\mathrm{rms}}$$ around the time of SNe cutoff at 10 Myr is similar to that found in the CPU runs, the prior evolution is different.  
In the previous study contributions from regions of gas with densities less than $$0.01 \mathrm{cm}^{-3}$$ were not counted, but the mass from these 
regions did contribute to the normalizing overall mass.   This bug was fixed for the runs on the GPU.  However this would tend to make the CPU values smaller 
that expected; not what was seen.  Another difference between the two studies is the cluster mass distribution.  The present simulations having more mass would also lead me to 
expect greater turbulence.  On the other hand, the previous runs featured uniform mass clusters which would more uniformly cover the simulation volume, perhaps yielding more 
turbulence.

Plot of the first 400 kyr to better see the region of unresolved SNe:
![Gas Velocity Dispersion]({{'/assets/images/2022/04/dispersion_10Myr_GPU_zoomed.png' | relative_url}}) 

Looking at the last "bump'' in the curve around time 230 kyr, and also plotting the times of SNe (gray dotted lines: resolved SNe, red dotted lines: unresolved SNe):
![Gas Velocity Dispersion]({{'/assets/images/2022/04/dispersion_zoomed_into_last_blip.png' | relative_url}}) 
As seen in the CPU runs, jumps in turbulence are associated with momentum injection from SNe whose shell-forming radii are not resolved with the given grid spacing.  No further
unresolved SNe were seen after this time.  Looking at the x-y density slice at 23 kyr perhaps the nearby clusters located at x$$\approx -0.7$$ kpc and y$$\approx 1.1$$kpc are 
responsible for this unresolved SN since the overlapping bubbles could create higher densities in the cluster environment which would result in a smaller shell-forming radius. 
![Gas XY Density]({{'/assets/images/2022/04/23.png' | relative_url}}) 

Zooming in on a couple other turbulent jumps:
![Gas Velocity Dispersion]({{'/assets/images/2022/04/dispersion_first_large_blip.png' | relative_url}}) 
![Gas Velocity Dispersion]({{'/assets/images/2022/04/dispersion_unresolved_region.png' | relative_url}}) 


---



