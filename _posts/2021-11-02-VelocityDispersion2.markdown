---
layout: default
title:  "Velocity Dispersion 2"
date:   2021-11-02 09:00:00 -0400
categories: disk feedback
---

## Gas Velocity Dispersion (Continued)

Closeups of what happens before a velocity dispersion spike reveale the presence of unresolved SNe.  They also indicate a failure to adjust the subsequent time step to account 
for the large increase in momentum.  For example the following plot
![Gas Velocity Dispersion Closeup]({{'/assets/images/2021/11/detailed_dispersion.png' | relative_url}}) 
shows that around time 252.2 kyr an unresolved SN preceded the jump in velocity dispersion.  The next data point, at the velocity dispersion maxima, comes at 253 kyr.  Subsequent 
time steps are closer to $$0.04$$ kyr.  Clearly the time step following the unresolved SN is too large and the results suspect.

---

Updating the time step based on changes to the cells receiving feedback and re-running the 38 clusters simulation for 20 Myr:
![Improved Gas Velocity Dispersion]({{'/assets/images/2021/11/gas_velocity_dispersion_fixed_issue_timestep.png' | relative_url}}) 

There are still jumps due to unresolved SNe, as is made clear by looking at the first $$2$$ Myr:  
![Gas Velocity Dispersion first 2 Myr]({{'/assets/images/2021/11/dispersion_0_2000_kyr.png' | relative_url}}) 

Zooming in on the last obvious jump around $$0.9$$ Myr: 
![Gas Velocity Dispersion around 0.9 kyr]({{'/assets/images/2021/11/dispersion_908_kyr.png' | relative_url}}) 
we again see that the jump is associated with an unresolved SN.  However in this case the unresolved SN occurs at the velocity dispersion maximum and the ubsequent time step is greatly reduced.  Previously we saw a similar rise in velocity dispersion at the time of the unresolved SN, but the failure to shorten the next time step lead to a much larger dispersion jump in the subsequent step.


