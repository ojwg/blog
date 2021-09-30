---
layout: default
title:  "SN Feedback (Continued)"
date:   2021-09-10 09:00:00 -0400
categories: disk feedback
---

## Shell Formation Radius determination.

The end of the Sedov-Taylor phase is characterized by non-negligible radiative loses which lead to formation of a dense shell bounding the supernova remnant.  
The analytic expression for this radius for the case of uniform expansion into a homogeneous ISM is $$r_{sf} = 22.6\, \mathrm{pc}\, E_{51}^{0.29}\,n_0^{-0.42}$$.

Kim & Ostriker find a power law fit, $$r_{sf} = 30.2\, \mathrm{pc}\, n_0^{-0.46}$$, (equation 31) valid for the more general case of a 2-phase ISM.  
However, there is no expression for how $$r_{sf}$$ varies as a function of SN energy, which is needed when handling stellar clusters that can harbor more than 1 SN per timestep.
As a work-around, I assumed the form $$r_{sf} =  30.2\, \mathrm{pc}\,E_{51}^{0.29}\, n_0^{-0.46}$$.  Just as the measured density exponent differs from the analytic uniform ISM value, 
I was under no illusion that the energy exponent would be the same as in the analytical expression. However it is probably a good first approximation.   In a similar vein I modified Kim & Ostriker's
equation 34 for the total injected momentum by using the analytic energy dependence of $$p_{sf}$$, resulting in $$p_{final} = 2.8 \times 10^5 \, M_\odot\, \mathrm{km\, s^{-1}}\,E_{51}^{0.93}\,n_0^{-0.17}$$. 

---

## Turbulence Calculation

The above feedback formulation was tested on a simulation of a single $$10^5 \mathrm{M}_\odot$$ cluster placed at a radius of 1.5 kpc from the Galactic Center and evolved for 15 Myr.
To gauge the effect of the SN feedback on theh ISM I calculated the gas velocity dispersion after subtracting the circular speed.  Initially the circular speed was calculated via the 
analytic expression for the galactic gravitational potential (Miyamoto-Nagai disk and NFW halo potentials).  Initial velocity rms values were $$\approx 0.3\,\mathrm{km/s}$$.  Refining the
algorithm to use the calculated gravitational field resulted in initial velocity rms values $$\approx 4.8\,\mathrm{km/s}$$.  

At simulation start $$v_{rms}$$ for the gas should be something close to 0 km/s, so why did it increase with a more exact acceleration calculation?  One possibility is that the gas initial 
velocity was calculated based of the analytic potential form.  The calculated potential included the gas self-gravity, which could account for the up-to 10% difference in gravitational force. 
Another possibility was that I made a mistake in handling the various grid indices.

The looping over the gas grid looks like the following:
```c++
  for (k=H.n_ghost; k<H.nz-H.n_ghost; k++) {
    for (j=H.n_ghost; j<H.ny-H.n_ghost; j++) {
      for (i=H.n_ghost; i<H.nx-H.n_ghost; i++) {
        id = i + j*H.nx + k*H.nx*H.ny;
        id_grav = (i + ghost_diff) + (j + ghost_diff)*nx_grav + (k + ghost_diff)*nx_grav*ny_grav;
```

Here the `ghost_diff` is the difference between numbers of ghost cells between the gravity grid and the hydro grid: `Particles.G.n_ghost_particles_grid - H.n_ghost`.

`nx_grav` is `Particles.G.nx_local + 2*Particles.G.n_ghost_particles_grid` (and similarly for `ny_grav`).
With these values of `id` and `id_grav` the radial graviational acceleration component was computed from `Particles.G.gravity_x[id_grav]*x/r + Particles.G.gravity_y[id_grav]*y/r`

I.E. the circular speed is `vc = sqrt(r*fabs(Particles.G.gravity_x[id_grav]*x/r + Particles.G.gravity_y[id_grav]*y/r - dPdr/C.density[id]));`   
as opposed to the previous value `vc = sqrt(r*fabs(Galaxies::MW.gr_total_D3D(r, z)- dPdr/C.density[id]));`

---

## Single $$10^5\, M_\odot$$ Cluster.

Evolving a single $$10^5\, M_\odot$$ cluster for 15 Myr generated a total 1023 SNe.  957 of these were resolved (meaning that 3 times the grid spacing was less than the $$r_{sf}$$) while
8 where unresolved.  Note that these two numbers don't add up to the total number of SNe since at any given timestep there can be more than 1 SN.  These multiple SNe are treated as one SN
event.   The total supernovae number was roughly what was expected (1 SN per $$100 M_\odot$$ spread out over 10 Myr)

A total of $$1.02\times 10^{54}$$ erg was injected, as was $$4.64\times 10^{6} M_\odot$$ km/s of momentum along the x-axis.  $$v_{rms}$$ at the final timestep was $$7.46 \mathrm{km/s}$$. 
Note that $$v_{rms}$$ was 8.11 km/s at 10 Myr when SN activity was turned off.  


