---
layout: default
title:  "SN Feedback"
date:   2021-07-11 09:00:00 -0400
categories: disk feedback
---



## Energy Feedback 

Poisson implementation of the supernovae (SN) feedback:
![energy feedback](../../../../../assets/images/2021/07/feedback.png "feedback prescription")

Stellar clusters are expected to undergo 1 SN per $$100\mathrm{M}_\odot$$ of mass, spread out over $$10^7$$ yr.  
For this preliminary study we used uniform cluster masses of $$10^5 \mathrm{M}_\odot$$, which meant a SN rate (SNR) of $$0.1$$ SN/kyr for each cluster.
Each SN was assumed to eject $$10\mathrm{M}_\odot$$ of mass and release $$10^{51}$$ ergs of energy.  This feedback was injected into the ISM given sufficient
simulation resolution.  The resolution sufficiency criterion, based on numerical convergence results (Kim & Ostriker, 2015), being that the 
radius of SN shell formation ($$r_{sf}$$) needs to be 3 times greater than the grid resolution.  We take $$r_{sf} = 30.2\, \mathrm{pc}\, n_0^{-0.46}$$ (eq 31, Kim & Ostriker, 2015).
In the event of insufficient resolution, only momentum was added to the ISM.  

### Cloud In Cell (CIC) implementation

Feedback is shared with neighboring cells in proportion to the proximity to the SN. 

At $$9$$ Myr here is a slice along the galactic plane of the gas temperature:
![9 Myr gas temperature](../../../../../assets/images/2021/07/9Myr_xy_gas_temp.png "9Myr xy gas temp")
There are appear to be very slight temperature warm spots.  Whether these are actual or relevant is debatable. 

Full video of xy (galactic plane) gas temperature:
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/07/xy_gas_temp.mp4' | relative_url }}" type="video/mp4"/>  -->
</video>
Likewise for xy gas density:
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/07/xy_gas_density.mp4' | relative_url }}" type="video/mp4"/>  -->
</video>

Time steps are mostly around 2kyr, falling occasionally under 1kyr.  

---

