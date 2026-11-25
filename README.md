About gdar-base-feedstock
=========================

Feedstock license: [BSD-3-Clause](https://github.com/conda-forge/gdar-base-feedstock/blob/main/LICENSE.txt)

Home: https://pypi.org/project/gdar-base

Package license: Apache-2.0

Summary: GDAR -- The Generic Data Raster

Documentation: https://earth-observation-public.pages.norce.dev/gafa-doc

GDAR — the Generic Data Raster — is a Python library for working with
gridded geospatial data. Its central abstraction is the DataRaster,
which combines a data source with metadata describing the grid the data
lives on (shape, origin, sample spacing, coordinate reference system)
and the meaning of its values (data type, nodata sentinel, units).
The data source can be a NumPy-like array already in memory, a file read
on demand, or a get_data() callable that computes the necessary subset
of the data when invoked. That last option gives DataRaster pull semantics:
an entire processing chain can be assembled in which intermediate steps
are neither written to disk nor ever materialised in their entirety -
data is produced only for the regions that downstream consumers actually
request. Once data is wrapped in a DataRaster, operations that would
otherwise require juggling separate geo-transforms, masks, and projection
strings - indexing by physical coordinates, resampling onto another grid,
cropping, reading and writing native file formats - become straightforward
method calls that keep the spatial bookkeeping in sync with the pixel data.
A companion abstraction, the Collection, groups multiple related
DataRasters that belong together - for example time slices of a dataset,
bands from a multi-spectral instrument, or polarimetric channels from a
SAR acquisition.
gdar-base is the core of the library and has deliberately few dependencies:
NumPy, with optional extras for plotting (matplotlib) and map-projection
support. It forms the foundation for a family of companion packages that
build on the same DataRaster abstraction:
  * gdar-crs - coordinate reference systems and map projections
  * gdar-orbit - satellite orbit propagation and geometry
  * gdar-sar - synthetic-aperture radar processing primitives
  * gdar-optical - remotely-sensed optical data
  * gafa - geometry- and frequency-agnostic SAR focusing and simulation

Current build status
====================


<table><tr>
    <td>All platforms:</td>
    <td>
      <a href="https://github.com/conda-forge/gdar-base-feedstock/actions/workflows/conda-build.yml">
        <img src="https://github.com/conda-forge/gdar-base-feedstock/actions/workflows/conda-build.yml/badge.svg?event=push&branch=main">
      </a>
    </td>
  </tr>
</table>

Current release info
====================

| Name | Downloads | Version | Platforms |
| --- | --- | --- | --- |
| [![Conda Recipe](https://img.shields.io/badge/recipe-gdar--base-green.svg)](https://anaconda.org/conda-forge/gdar-base) | [![Conda Downloads](https://img.shields.io/conda/dn/conda-forge/gdar-base.svg)](https://anaconda.org/conda-forge/gdar-base) | [![Conda Version](https://img.shields.io/conda/vn/conda-forge/gdar-base.svg)](https://anaconda.org/conda-forge/gdar-base) | [![Conda Platforms](https://img.shields.io/conda/pn/conda-forge/gdar-base.svg)](https://anaconda.org/conda-forge/gdar-base) |

Installing gdar-base
====================

Installing `gdar-base` from the `conda-forge` channel can be achieved by adding `conda-forge` to your channels with:

```
conda config --add channels conda-forge
conda config --set channel_priority strict
```

How to use
----------

<details>
<summary>With conda</summary>

```
conda install gdar-base
```

</details>

<details>
<summary>With mamba</summary>

```
mamba install gdar-base
```

</details>

<details>
<summary>With pixi</summary>

```
# for adding to your local project
pixi add gdar-base
# for installing globally
pixi global install gdar-base
```

</details>

Search package versions
-----------------------

It is possible to list all of the versions of `gdar-base` available on your platform:

<details>
<summary>With conda</summary>

```
conda search gdar-base --channel conda-forge
```

</details>

<details>
<summary>With mamba</summary>

```
mamba search gdar-base --channel conda-forge
```

</details>

<details>
<summary>With pixi</summary>

```
pixi search gdar-base --channel conda-forge
```

</details>

<details>
<summary>With mamba repoquery, which may provide more information</summary>

```
# Search all versions available on your platform:
mamba repoquery search gdar-base --channel conda-forge

# List packages depending on `gdar-base`:
mamba repoquery whoneeds gdar-base --channel conda-forge

# List dependencies of `gdar-base`:
mamba repoquery depends gdar-base --channel conda-forge
```

</details>


Optional Dependencies
---------------------

`gdar-base-feedstock` defines the following [CEP-44] optional
dependency groups:

| Install | Optional Dependencies |
| --- | --- |
| `gdar-base[extras=crs]` | `rasterio` |
| `gdar-base[extras=interactive]` | `ipython` |
| `gdar-base[extras=plotting]` | `matplotlib` |

[CEP-44]: https://github.com/conda/ceps/blob/main/cep-0044.md


About conda-forge
=================

[![Powered by
NumFOCUS](https://img.shields.io/badge/powered%20by-NumFOCUS-orange.svg?style=flat&colorA=E1523D&colorB=007D8A)](https://numfocus.org)

conda-forge is a community-led conda channel of installable packages.
In order to provide high-quality builds, the process has been automated into the
conda-forge GitHub organization. The conda-forge organization contains one repository
for each of the installable packages. Such a repository is known as a *feedstock*.

A feedstock is made up of a conda recipe (the instructions on what and how to build
the package) and the necessary configurations for automatic building using freely
available continuous integration services. Thanks to the awesome service provided by
[Azure](https://azure.microsoft.com/en-us/services/devops/) and [GitHub](https://github.com/)
it is possible to build and upload installable packages to the
[conda-forge](https://anaconda.org/conda-forge) [anaconda.org](https://anaconda.org/)
channel for Linux, Windows and OSX respectively.

To manage the continuous integration and simplify feedstock maintenance,
[conda-smithy](https://github.com/conda-forge/conda-smithy) has been developed.
Using the ``conda-forge.yml`` within this repository, it is possible to re-render all of
this feedstock's supporting files (e.g. the CI configuration files) with ``conda smithy rerender``.

For more information, please check the [conda-forge documentation](https://conda-forge.org/docs/).

Terminology
===========

**feedstock** - the conda recipe (raw material), supporting scripts and CI configuration.

**conda-smithy** - the tool which helps orchestrate the feedstock.
                   Its primary use is in the construction of the CI ``.yml`` files
                   and simplify the management of *many* feedstocks.

**conda-forge** - the place where the feedstock and smithy live and work to
                  produce the finished article (built conda distributions)


Updating gdar-base-feedstock
============================

If you would like to improve the gdar-base recipe or build a new
package version, please fork this repository and submit a PR. Upon submission,
your changes will be run on the appropriate platforms to give the reviewer an
opportunity to confirm that the changes result in a successful build. Once
merged, the recipe will be re-built and uploaded automatically to the
`conda-forge` channel, whereupon the built conda packages will be available for
everybody to install and use from the `conda-forge` channel.
Note that all branches in the conda-forge/gdar-base-feedstock are
immediately built and any created packages are uploaded, so PRs should be based
on branches in forks, and branches in the main repository should only be used to
build distinct package versions.

In order to produce a uniquely identifiable distribution:
 * If the version of a package **is not** being increased, please add or increase
   the [``build/number``](https://docs.conda.io/projects/conda-build/en/latest/resources/define-metadata.html#build-number-and-string).
 * If the version of a package **is** being increased, please remember to return
   the [``build/number``](https://docs.conda.io/projects/conda-build/en/latest/resources/define-metadata.html#build-number-and-string)
   back to 0.

Feedstock Maintainers
=====================

* [@avalentino](https://github.com/avalentino/)
* [@ylarsen](https://github.com/ylarsen/)

