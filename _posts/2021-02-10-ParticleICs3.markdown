---
layout: default
title:  "Initial Conditions part 2"
date:   2021-02-10 09:00:00 -0400
categories: disk
---



##  Surface Mass Density

Surface mass density of $$6.5\mathrm{x}10^8$$ particles, each with a mass of $$100\mathrm{M}_\odot$$, slowly evolved without gas to 500 kyr.

<video width="620" height="620" controls>
<!--  <source src="../../../../assets/videos/2021/02/particle_surface_density_disk.mp4" type="video/mp4"/>  -->
   <source src="{{ '/assets/videos/2021/02/particle_surface_density_disk.mp4' | relative_url }}" type="video/mp4"/>  -->
</video>

---

To test the relative stability longer runs were needed, so I reduced the number of particles to $$6.5\mathrm{x}10^6$$. With a couple restarts the 
system was evolved to 18 Myr.

<video width="620" height="620" controls>
  <source type="video/mp4" src="{{ '/assets/videos/2021/02/particle_surf_density_disk.mp4' | relative_url }}" />
</video>


The above clearly shows that the surface density is decreasing with time.  Particles are migrating out of the simulation volume.  Plotting the values at 
a few times gives a clearer picture. 
![Surface Density]({{ '/assets/images/2021/02/6.5M_surf_density.png' | relative_url }})

Taking the natural logarithm of the initial surface density data and fitting to a one degree polynomial yields a disk length scale of $$3.53$$ kpc. This is the 
expected value for our Milky Way model and is the value used by the initial conditions generator code.

The y-intercept of the polynomial fit is $$\ln(\frac{M_d}{2\pi R_d^2})$$, where $$M_d$$ is the disk mass and $$R_d$$ is the disk length scale.  Using the estimated
value for $$R_d$$ yields $$M_d = 6.6\mathrm{x}10^{10} M_\odot$$, which is close to the expected value of $$6.5\mathrm{x}10^{10} M_\odot$$.

Similarly, integrating the inital mass density along horizontal slices gives the following vertical mass distribution:
![Vertical Mass Distribution]({{'/assets/images/2021/02/vert_mass_distro.png' | relative_url }})

Trimming the data to exclude the mass on the disk plane and those values of height for which the mass approaches zero results in an exponential decay fit with a scale 
height of $$0.78$$ kpc, which is close to that assumed by Cholla's Milky Way model ($$0.7$$ kpc).
