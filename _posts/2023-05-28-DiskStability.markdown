---
layout: default
title:  "Gas Disk Stability and Average Slow Cells"
date:   2023-05-28 09:00:00 -0400
categories: disk stability slow cells
---
[comment]: <> (data comes from running on CRC )

# Disk Stability

This post describes the latest sets of simulations exploring questions of simulation stability.

## Resolved SNe and slow cell averaging

Ran a disk simulation for 42 Myr treating all supernovae (SNe) with the resolved 8-cell prescription. The code 
was modified to print out locations of cells where "slow cell averaging" happened.  The $$1467$$ events are represented in the following videos as orange squares.  Note that
while the videos are of density slices, the slow-cell locations are either projections in the x-y video, or within $$0.6$$ kpc of the y plane in the x-z video.

Density on the disk plane:
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2023/05/gas_density_xy_cc_resSNe_redo_42Myr_withAveSlowC.mp4' | relative_url }}" type="video/mp4"/> 
</video>
Density on a perpendicular slice along the y plane:
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2023/05/gas_density_xz_cc_resSNe_redo_42Myr_withAveSlowC.mp4' | relative_url }}" type="video/mp4"/> 
</video>

Distribution of events over time:
![Time distribution]({{'/assets/images/2023/05/resSNe_aveSlow_hist.png' | relative_url}})

Average slow events tend to happen near regions of rapid density change in the xy density slice video.



## Resolved SNe after turbulence generation.

The resolved SNe xz density videos clearly show the gas disk initially collapsing due to cooling.  
We explored first running a collisionally ionized equilibrium (CIE) cooling sim -- 
with resolved/unresolved SNe and stellar wind feedback -- followed by the Cloudy cooling (CC), resolved-SNe-only prescription sim.  The idea being to stave
off the initial collapse when starting the Cloudy cooling sim via the previously generated ISM turbulence.

The CIE sim ran for $$40$$ Myr.  The xz density video shows how the disk doesn't collapse in this scenario:
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2023/05/gas_density_xz_cie_allFeedback.mp4' | relative_url }}" type="video/mp4"/> 
</video>

The vrms plot comparing this scenario with the previous one:
![VRMS]({{'/assets/images/2023/05/CC_CIE_vrms.png' | relative_url}})

The above plot indicates a consistent level of turbulence of around 10 km/s is quickly reached.  The state at 20 Myr was used to kick off the next phase of CC resolved SNe
evolution.  That phase ran from 20 through 80 Myr.  The xz density video shows the gas disk quickly collapsing, suggesting that turbulence alone may not prevent collapse in
realistic simulations.
<div> <label for="vid_col">Collapsing gas density during CC simulation:</label></div>
<video width="620" height="620" id="vid_col" controls>
   <source src="{{ '/assets/videos/2023/05/gas_density_xz_readGrid.mp4' | relative_url }}" type="video/mp4"/> 
</video>

<p/>
The resulting collapse can be seen in the initial "bump" in the vrms plot:
![VRMS]({{'/assets/images/2023/05/CC_CIE_CC_vrms.png' | relative_url}})

<div> <label for="vid_col1">CC simulation gas density xy slice:</label></div>
<video width="620" height="620" id="vid_col1" controls>
   <source src="{{ '/assets/videos/2023/05/gas_density_xy_readGrid.mp4' | relative_url }}" type="video/mp4"/> 
</video>

<div> <label for="vid_col2">CC simulation gas temperature xy slice:</label></div>
<video width="620" height="620" id="vid_col2" controls>
   <source src="{{ '/assets/videos/2023/05/gas_temp_xy_readGrid.mp4' | relative_url }}" type="video/mp4"/> 
</video>

<div> <label for="vid_col3">CC simulation gas temperature xz slice:</label></div>
<video width="620" height="620" id="vid_col3" controls>
   <source src="{{ '/assets/videos/2023/05/gas_temp_xz_readGrid.mp4' | relative_url }}" type="video/mp4"/> 
</video>

## No feedback runs

We ran no-feedback disk simulations with CIE cooling to test inate disk stability. The first sim ran for 82 Myr, followed by a second run from 82-160 Myr. 

<div> <label>First run simulation gas density xy slice:</label></div>
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2023/05/gas_density_xy_cie_noFeedback_1e4kFloor_82Myr.mp4' | relative_url }}" type="video/mp4"/> 
</video>
<div> <label>Second run simulation gas density xy slice:</label></div>
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2023/05/gas_density_xy_noFeedback_1e4kFloor_82Myr-160Myr.mp4' | relative_url }}" type="video/mp4"/> 
</video>
<div> <label>First run simulation gas density xz slice:</label></div>
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2023/05/gas_density_xz_cie_noFeedback_1e4kFloor_82Myr.mp4' | relative_url }}" type="video/mp4"/> 
</video>
<div> <label>Second run simulation gas density xz slice:</label></div>
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2023/05/gas_density_xz_noFeedback_1e4kFloor_82Myr-160Myr.mp4' | relative_url }}" type="video/mp4"/> 
</video>

<p/>

<div> <label>First run simulation gas temperature xy slice:</label></div>
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2023/05/gas_temp_xy_cie_noFeedback_1e4kFloor_82Myr.mp4' | relative_url }}" type="video/mp4"/> 
</video>
<div> <label>Second run simulation gas temperature xy slice:</label></div>
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2023/05/gas_temp_xy_noFeedback_1e4kFloor_82Myr-160Myr.mp4' | relative_url }}" type="video/mp4"/> 
</video>
<div> <label>First run simulation gas temperature xz slice:</label></div>
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2023/05/gas_temp_xz_cie_noFeedback_1e4kFloor_82Myr.mp4' | relative_url }}" type="video/mp4"/> 
</video>
<div> <label>Second run simulation gas temperature xz slice:</label></div>
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2023/05/gas_temp_xz_noFeedback_1e4kFloor_82Myr-160Myr.mp4' | relative_url }}" type="video/mp4"/> 
</video>

While the disk doesn't collapse during the 160 Myr time span covered in these runs, the system is not in quasi-equilibrium either.
Interestingly the halo appears to collapse around 100 Myr.
<p/>

<div> <label>First run phase diagram:</label></div>
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2023/05/phase_cie_nofeedback_1e4Kfloor_82Myr.mp4' | relative_url }}" type="video/mp4"/> 
</video>
<div> <label>Second run phase diagram:</label></div>
<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2023/05/phase_cie_nofeedback_1e4Kfloor_82-160Myr.mp4' | relative_url }}" type="video/mp4"/> 
</video>

<p/>
<p/>

There were 602 average slow cell events during the first 82 Myr and only 2 during the rest of the time.
The following projections show these events were located at the edge of the disk.
![xy projection]({{'/assets/images/2023/05/xy_ave_slow_cells.png' | relative_url}})
![xz projection]({{'/assets/images/2023/05/xz_ave_slow_cells.png' | relative_url}})
![yz projection]({{'/assets/images/2023/05/yz_ave_slow_cells.png' | relative_url}})

The following illustrates the distribution of the events over time.
![slow cell averaging events]({{'/assets/images/2023/05/histogram_ave_slow_cells.png' | relative_url}})

---
