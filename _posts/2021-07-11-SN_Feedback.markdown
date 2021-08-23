---
layout: default
title:  "SN Feedback"
date:   2021-07-11 09:00:00 -0400
categories: disk feedback
---



## Supernova Feedback 

Poisson implementation of the supernovae (SN) feedback:
![energy feedback](../../../../../assets/images/2021/07/feedback.png "feedback prescription")

Stellar clusters are expected to undergo 1 SN per $$100\mathrm{M}_\odot$$ of mass, spread out over $$10^7$$ yr.  
For this preliminary study we used uniform cluster mass of $$10^5 \mathrm{M}_\odot$$, which resulted in a SN rate (SNR) of $$0.1$$ SN/kyr for each cluster.
Each SN was assumed to eject $$10\mathrm{M}_\odot$$ of mass and release $$10^{51}$$ ergs of energy.  This feedback was injected into the ISM given sufficient
simulation resolution.  The resolution sufficiency criterion, based on numerical convergence results (Kim & Ostriker, 2015), being that the 
radius of SN shell formation ($$r_{sf}$$) needs to be 3 times greater than the grid resolution.  We take $$r_{sf} = 30.2\, \mathrm{pc}\, n_0^{-0.46}$$ (eq 31, Kim & Ostriker, 2015).
In the event of insufficient resolution, only momentum was added to the ISM.  The magnitude of this momentum is $$p_{final} = 2.8\times 10^5 \mathrm{M}_\odot \mathrm{km\,s^{-1}}\, n_0^{-0.17}$$.
$$1/\sqrt{3}\, p_{final}$$ is used in each direction.


### Cloud In Cell (CIC) implementation

Feedback is shared with neighboring cells in proportion to the proximity to the SN. 

We undertook several simulations at the University of Pittsburgh's Center for Research Computing (CRC).  All simulations modeled the central 2 kpc of the Galactic center.

At $$9$$ Myr here is a slice along the galactic plane of the gas temperature when not accounting for resolution effects:
![9 Myr gas temperature](../../../../../assets/images/2021/07/9Myr_xy_gas_temp.png "9Myr xy gas temp")
...and a slice along the xz plane (perpendicular to the galactic plane):
![9 Myr gas temperature](../../../../../assets/images/2021/07/9Myr_xz_gas_temp.png "9Myr xz gas temp")

Full video of xy (galactic plane) gas temperature (running for 15 Myr), without taking resolution effects into account:
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/07/xy_gas_temp.mp4' | relative_url }}" type="video/mp4"/>  -->
</video>
Temperature on the xz plane from the same simulation as above:
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/07/xz_gas_temp.mp4' | relative_url }}" type="video/mp4"/>  -->
</video>

After modifying the algorithm to deal with lack of resolution, here are the equivalent videos/images as above:

XY temperature at 9 Myr:
![9 Myr gas temperature](../../../../../assets/images/2021/07/9Myr_xy_gas_temp_momentum_imp.png "9Myr xy gas temp")
..and the corresponding XZ temperature:
![9 Myr gas temperature](../../../../../assets/images/2021/07/9Myr_xz_gas_temp_momentum_imp.png "9Myr xz gas temp")
XY density at 9 Myr:
![9 Myr gas density](../../../../../assets/images/2021/07/9Myr_xy_gas_temp_momentum.png "9Myr xy gas density")
..and the corresponding XZ density:
![9 Myr gas density](../../../../../assets/images/2021/07/9Myr_xz_gas_temp_momentum.png "9Myr xz gas density")

XY (galactic plane) gas temperature (running for 20 Myr):
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/07/xy_gas_temp_20Myr_momentum.mp4' | relative_url }}" type="video/mp4"/>  -->
</video>
XZ plane temperature:
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/07/xz_gas_temp_20Myr_momentum.mp4' | relative_url }}" type="video/mp4"/>  -->
</video>

XY gas density:
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/07/xy_gas_density_20Myr_momentum.mp4' | relative_url }}" type="video/mp4"/>  -->
</video>
XZ gas density:
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/07/xz_gas_density_20Myr_momentum.mp4' | relative_url }}" type="video/mp4"/>  -->
</video>
XY speed distribution:
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/07/xy_gas_velocity_20Myr_momentum.mp4' | relative_url }}" type="video/mp4"/>  -->
</video>


---

