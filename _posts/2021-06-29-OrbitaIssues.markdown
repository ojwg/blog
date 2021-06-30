---
layout: default
title:  "Orbital Issues"
date:   2021-06-29 09:00:00 -0400
categories: disk
---



##  Stellar Clusters on Circular Orbits

Simulating 38 $$10^5 \mathrm{M}_\odot$$ stellar clusters orbiting within 2 kpc of the Galactic Center (GC).

<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/06/bad_orbits.mp4' | relative_url }}" type="video/mp4"/>  -->
</video>

There are a couple problems illustrated by the video.  The most serious is that particles placed on circular trajectories are not actually following circular paths 
(problems arise as the radius approaches 2 kpc).  
The second issue is that clusters moving out of the simulation volume are still shown.  

For the second problem I needed to implement open boundary conditions for particles.  I made changes to `boundary_conditions.cpp`:
![boundary conditions](../../../../assets/images/2021/06/boundary_conditions.png "code changes")
and created the `Set_Particles_Open_Boundary` method in `particles_boundaries_cpu.cpp`.  

At first I deleted the particles outside the domain (that are not MPI transfers), using the `stl::vector::erase` method.  Since all elements after the one that's deleted need to be moved, 
this approach would be fine when dealing with 38 clusters, but not in general.  Initially this didn't quite work because I hadn't deleted the corresponding elements in the velocity vector 
(as well as the other vectors with particle data, such as IDs).  I tweaked things by moving the transfered particles far away from the simulation volume.  Although a clunky approach, it 
avoided the linear complexity of vector `erase` calls  and had the benefit of actually working:

<video width="620" height="620" controls>
   <source src="{{ '/assets/videos/2021/06/particle_orbits_open_bc2.mp4' | relative_url }}" type="video/mp4"/>  -->
</video>

I setup a call with Bruno, who verified my general approach and also showed me delete particle data code he wrote that avoids the linear `erase` complexity.  In brief, the code swaps out the 
particle-to-be-deleted's data with data from the last particle. A call to `std::vector::pop` removes the latter's now-duplicated data.  This is constant in time ... and very clever.

---

