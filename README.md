# Multi-Dimensional Operational Domain Computation for Silicon Dangling Bond Logic

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="logo/mnt_light.svg" width="60%">
    <img src="logo/mnt_dark.svg" width="60%">
  </picture>
</p>

This repository provides supplementary data for the paper *Multi-Dimensional Operational Domain Computation for Silicon
Dangling Bond Logic* by M. Walter, J. Drewniok, S. S. H. Ng, K. Walus, and R. Wille submitted to TNANO (under review).

## Operational Domain Analysis

The *Operational Domain* was proposed as a methodology to evaluate the extent of physical parameter variations that an
SiDB logic gate can tolerate by plotting the logical correctness of that gate's behavior across a predetermined range of
physical parameters. Given an SiDB layout *L* and a Boolean function *f : 𝔹ⁿ ⟶ 𝔹ᵐ*, the operational domain of *L* given
*f* is defined in the parameter space as the set of coordinate points for which *L* implements *f*. To determine whether
*L* implements *f* at any given coordinate point *(x, y, z)*, this point can be sampled, i.e., by conducting *2ⁿ*
physical simulations—one for each possible input pattern of *L*.

### Benchmark Layouts

We performed operational domain analyses for benchmark layouts taken from the literature. The layouts are provided in
the `benchmarks/` folder in `*.sqd` format.
This format is supported in the SiDB CAD tool [*SiQAD*](https://github.com/siqad/siqad).
Utilizing this tool, the layouts can be visualized and their behavior can be validated by physical simulations. Both
tasks can also be performed in the *Munich Nanotech Toolkit* (MNT) [*fiction*](https://github.com/cda-tum/fiction).

#### SiQAD

The SiQAD gates are taken from the
paper ["SiQAD: A Design and Simulation Tool for Atomic Silicon Quantum Dot Circuits"](https://ieeexplore.ieee.org/abstract/document/8963859)
by S. S. H. Ng, J. Retallick; H. N. Chiu, et al. published in IEEE Transactions on Nanotechnology (TNANO) 2019.

In this repository, they are located in
the [`benchmarks/siqad/`](https://github.com/cda-tum/mnt-operational-domains/tree/main/benchmarks/siqad) folder.

#### Bestagon

The Bestagon gates are taken from the
paper ["Hexagons are the Bestagons: Design Automation for Silicon Dangling Bond Logic"](https://dl.acm.org/doi/abs/10.1145/3489517.3530525)
by M. Walter, S. S. H. Ng, K. Walus, and R. Wille in the Design Automation Conference (DAC) 2022.

In this repository, they are located in the
[`benchmarks/bestagon/`](https://github.com/cda-tum/mnt-operational-domains/tree/main/benchmarks/bestagon) folder.

### Plots

In this work, we present two novel algorithms for the obtainment of operational domains: *Flood Fill* and *Contour
Tracing*. Additionally, we compare these algorithms to the state-of-the-art *Grid Search* algorithm while also
mentioning *Random Sampling* in the paper.

Operational domain data generated with all applicable algorithms for all benchmark layouts is provided in
the [`operational_domains/`](https://github.com/cda-tum/mnt-operational-domains/tree/main/operational_domains) folder in
various file formats.

#### CSV

The raw operational domain data is provided in CSV format. Each file contains the operational domain data for a single
benchmark layout. The columns represent the evaluated physical parameters and the logical correctness of the
gate at the respective parameter values.

Such a (2D) CSV file might look as follows:

```csv
epsilon_r, lambda_tf, operational status
3.15     , 1.90     , 0
2.20     , 7.85     , 0
7.75     , 6.70     , 1
8.25     , 7.90     , 1
1.70     , 1.75     , 0
6.05     , 6.85     , 1
1.90     , 9.25     , 0
...
```

#### PNG

The operational domain plots are visualized in PNG format.

For 2D spaces, each file contains a plot of the operational domain for a single benchmark layout using a single
algorithm. The plot shows the logical correctness of the gate at the respective parameter values in purple.
Non-operational samples are shown in gray.

For 3D spaces, all benchmark layouts' plots are depicted from three azimuth angles: 45°, 135°, and 225°, with a constant
elevation angle of 30°. In 3D plots, non-operational samples are omitted while operational samples are colored according
to their location in the parameter space.

<p align="center">
    <picture>
        <img src="https://github.com/cda-tum/mnt-operational-domains/blob/main/operational_domains/siqad/png/3d/grid_search/3D_Grid_Search_SiQAD_OR_view_1.png?raw=true" width="32%" alt="3D Operational Domain Grid Search SiQAD OR (View 1)">
    </picture>
    <picture>
        <img src="https://github.com/cda-tum/mnt-operational-domains/blob/main/operational_domains/siqad/png/3d/grid_search/3D_Grid_Search_SiQAD_OR_view_2.png?raw=true" width="32%" alt="3D Operational Domain Grid Search SiQAD OR (View 2)">
    </picture>
    <picture>
        <img src="https://github.com/cda-tum/mnt-operational-domains/blob/main/operational_domains/siqad/png/3d/grid_search/3D_Grid_Search_SiQAD_OR_view_3.png?raw=true" width="32%" alt="3D Operational Domain Grid Search SiQAD OR (View 3)">
    </picture>
</p>

#### HTML

The 3D operational domain plots are additionally visualized in interactive HTML format.

For each benchmark layout and algorithm, an HTML file is provided that contains an interactive 3D plot of the
operational domain using the same color scheme as in the PNG case. The plot can be rotated and zoomed in any web
browser.

> [!NOTE]
> The HTML files must be downloaded to be viewed. Large files may break the plot rendering in some browsers.
