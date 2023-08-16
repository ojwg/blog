---
layout: default
title:  "Frontier CGOLS I Planning"
date:   2023-08-16 09:00:00 -0400
categories: frontier feedback CGOLS
---
[comment]: <> (data comes from running on CRC )

### Feedback Only  ###
---

#### MW-like galaxy disk ####
---

 **Simulation volume**: 30 kpc-sided rectangular area by 10 kpc height ($$\pm 5$$ kpc)
 Assuming a 2 pc resolution and that each GPU can hold a $$256^3$$ subgrid, the simulation requires $$(30 \times 30 \times 10\, \textrm{kpc}^3) \times \left(\frac{1\, \textrm{GPU}}{0.512\, \mbox{kpc}}\right)^3,$$ or $$67,056\, \textrm{GPU}$$ (89% of Frontier).

**How long to run**:  Assuming stars orbit around the center once every $$250$$ Myr, a few orbits are required before limited equilibrium is reached.  However, stellar population distribution changes will be less important than ISM changes which happen on timescales $$\sim 100$$ Myr (*on my 4 kpc CRC runs*).  Also note that the semi-equilibrium state of the stellar population may be far less than expected on account of the particle density CIC approach.  A 2 pc resolution feedback simulation will take days to  to Whatever we decide the "burn in" time will be, we will probably want to vary the output frequency during this time (assuming it's of limited scientific importance).  We will also want to have a second entry in the slurm script to run the "read grid" scenario upon completion of the "burn in" period.

**convergence** : do we need to rerun entire simulation at, say 5 pc and 10 pc resolution? Or instead a limited time set of runs?  What measures will we use to show convergence, $$v_{rms}$$ ?

**Code changes** : <b>
<ol>
  <li> minor changes
    <ul>
        <li>look at how the analytic component is set to verify that it still makes sense</li>
        <li>change cluster total mass limit, max cluster age and SFR  (is $$1.6 \,\textrm{M}_\odot$$ per yr a good value?)</li>
        <li>manually adjust the disk gas cutoff (although it should be negligible at 15 kpc)</li>
    </ul>
  </li>
  <li> make sure clusters with age values greater than the current simulation time don't contribute to the gravitational potential.  Perhaps do the same for clusters that are sufficiently old. </li>
</ol>


**Scientific goals**: do we need tracer particles?
<ul>
  <li> characterize overall mass / energy loading of outflow (after removing fountain gas based on KE and gravitational potential?)</li>
  <li> phase diagrams of hot/warm components</li>
  <li> use Alwin's cloud finder to characterize component sizes</li>
  <li> compare with previous CGOLS results (highlighting differences in SN injection, stellar winds, variable cluster sizes, larger galaxy, etc.)</li>
  <li> other observations?</li>
</ul>


#### MW-like galaxy central region ####
---
From previous results can justify looking at the region above/below the galactic center
(do we need to put the galaxy in the middle of the box?)  In this way we could focus more on the central chimneys/Fermi Bubbles.  Do the cloud size distribution we find correspond to observations? (This analysis might be more relevant when running with Cloudy cooling)
Other synthetic observations?

