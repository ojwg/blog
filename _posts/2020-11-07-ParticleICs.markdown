---
layout: default
title:  "Particle ICs"
date:   2020-11-07 09:00:00 -0400
categories: disk
---


# Disk ICs

Disk ICs are based off the notes written by [Dr. Nicole Drakos](https://ndrakos.github.io/blog/cholla/Disk_ICs/)  with a few changes detailed in this post.

## Radial Position

Since the surface mass density $$\Sigma(R) = \frac{M_d}{2\pi h^2} \mathrm{exp}(-R/h)$$, the cumulative probability that a particles is located at radius $$R$$ or less is

$$ P(<R) = 1 - (1 + R/h)\mathrm{exp}(-R/h) .$$ 

I used the $$\Gamma(\alpha, \beta)$$ distribution, with $$\alpha, \beta = 2, 1$$ to generate the randomly selected radial distribution.

## Radial Velocity

The critical dispersion for disk stability is given by Hernquist as 

$$\sigma_R\vert_{crit} = \frac{3.36G\Sigma}{\kappa},$$ 

with $$\kappa$$ given by 

$$\kappa^2 = \frac{3}{R}\frac{\partial\Phi}{\partial R} + \frac{\partial^2\Phi}{\partial R^2}.$$

To guarantee stability the Toomre $$Q$$ parameter is set to 1.5 and $$Q\sigma_R\vert_{crit}$$ is evaluated at a reference point $$R_{ref} \approx 2-3 h$$.
I set the reference point to be equal to $$2.5h$$.  To recap, at $$R_{ref}$$,

$$ \overline{v_R^2} = \left(Q\sigma_R\vert_{crit}\right)^2.$$

Since $$\overline{v_R^2} \propto \mathrm{exp}(-R/h)$$, for general $$R$$ I have that 

$$\overline{v_R^2} = \left(Q\sigma_R\vert_{crit}\right)^2\mathrm{exp}\left(\frac{R_{ref} - R}{h}\right).$$

However, as noted by Nicole, for small enough $$R$$ this form for the radial velocity dispersion leads to imaginary values of the average azimuthal streaming velocity.  To overcome this problem, following Hernquist's prescription, I set

$$ \overline{v_R^2} = \left(Q\sigma_R\vert_{crit}\right)^2\mathrm{exp}\left(\frac{R_{ref} - \sqrt{R^2 + \frac{1}{8}h^2}}{h}\right),$$ 

when $$R < h/4.$$
I multiplied the square root of the expression for $$\overline{v_R^2}$$ with standard normal variates to generate the radial velocity population.


Another difference from the treatment by Nicole is that I assumed analytic forms for the disk and halo potentials.  Although this simplifies the calculations, these forms may not be entirely consistent with the assumed mass distribution.  As a result, Nicole's generated samples may be more self-consistent.

## Vertical Velocity

I follow closely Nicole's approach for generating sample vertical velocities.  The only change I introduce is that I apply the same softening factor used for the radial velocity distribution when $$R < h/4$$.  In this way the ratio of vertical to radial velocity dispersion is a constant value throughout the disk.

