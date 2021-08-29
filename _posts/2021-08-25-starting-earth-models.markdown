---
layout: post
title:  "Starting Earth Models"
date:   2021-09-25 15:18:18 +0000
categories:
---

Mantle convection and the associated plate tectonics are some of the
most fundamental yet complex processes here on Earth. The complexity
arises from several physical processes governing the mantle
circulation at different temporal and spatial scales. With the recent
increase in the availability of computational resources and advanced
numerical techniques, global mantle flow models have become possible
to investigate the underlying physics of plate tectonics. Here, we
will discuss one such model developed as part of the NSF-funded
project,
[Integrated Geodynamic Earth Models](https://integrated-earth.github.io/).

We setup instantaneous mantle convection models using
[ASPECT](https://aspect.geodynamics.org/), an open-source code that
simulates problems in the Earth’s mantle, with the goal to reproduce
present-day GPS velocities and deformation patterns. The material
properties in our models are constrained using recent high-resolution
geophysical observations. The main components of our models and
corresponding parameter values are mentioned below:

1) Input global tomography model: Several global seismic tomography
models have emerged since early 21st century revealing detailed
heterogeneity throughout the mantle. The models differ in the input
travel-times of a seismic phase and frequency content of that
phase. Currently, we use the joint P and S wave tomography model,
LLNL-G3D-JPS, by Simmons et al.,(2015) with a resolution of ~1 degree
in the upper mantle and ~2 degrees in the lower mantle.

2) Density model: Our models are driven by buoyancy forces which are
calculated using depth-dependent scaling of density anomalies with the
S-wave anomalies. We base densities in the crust from Crust1.0 model
(Laske et al., 2013) averaging over the upper crust, middle crust and
lower crust layers.

3) Temperature model: We compute temperature variations from a mantle
adiabat using a constant scaling factor, -4.2, with the S-wave
anomalies in the global tomography model (see Figure below). The lower
wavelength variations heterogeneity expected in the upper mantle are
often smoothed in the global tomography models. Therefore, we use a
high-resolution temperature model (TM1 in Tutu et al., 2018) in the
top 300 km that includes the variable ages of continental lithosphere,
cooling of oceanic lithospheres and cold slab structures.

4) Plate boundaries: We prescribe plate boundaries from the Global
Earthquake fault database in
[WorldBuilder](https://github.com/GeodynamicWorldBuilder/WorldBuilder),
an open-source code that can prescribe complex initial conditionsin
geodynamic models.

5) Rheology computation: We use dislocation and diffusion creep with
different prefactors for different mineral phases. The average lateral
variations in viscosity are scaled to a reference viscosity profile
(Steinberger and Calderwood, 2006) that is consistent with the
observed geoid. Additionally, we weaken the plate boundaries to
localize deformation along them.

We include all these components in a modular fashion to test the
relative importance of each component to best-match the surface GPS
observations.

![]({{site.baseurl}}/images/sem-fig1.png)


To resolve the high deformation at the plate boundaries, we use
adaptive mesh refinement in ASPECT. Our current highest-resolution
models have refinement cell size of up to ~ 10 km:

![]({{site.baseurl}}/images/sem-fig2.png)

