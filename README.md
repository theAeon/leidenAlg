[![Build Status](https://travis-ci.com/kharchenkolab/leidenAlg.svg?branch=master)](https://travis-ci.com/kharchenkolab/leidenAlg)
[![CRAN status](https://www.r-pkg.org/badges/version/leidenAlg)](https://cran.r-project.org/package=leidenAlg)
[![CRAN downloads](https://cranlogs.r-pkg.org/badges/leidenAlg)](https://cran.r-project.org/package=leidenAlg)

# leidenAlg

Implements the Leiden algorithm via an R interface

## Summary

The Leiden algorithm is an iterative community detection algorithm on networks---the algorithm is designed to converge to a partition in which all subsets of all communities are locally optimally assigned, yielding communities guaranteed to be connected.

The algorithm was written to improve upon defects of the Louvain algorithm. Consequently, the Leiden algorithm is faster, scales well, and can be run on graphs of millions of nodes (as long as they can fit in memory).

The basic steps are:
* (1) local moving of nodes to quickly find partitions
* (2) refinement of partitions
* (3) aggregation of the network based on the refined partition, using the non-refined partition to create an initial partition for the aggregate network. Steps are iterated until convergence.

For details on the algorithm, see ["From Louvain to Leiden: guaranteeing well-connected communities"](https://www.nature.com/articles/s41598-019-41695-z) Traag, Waltman, van Eck. Sci Rep 9, 5233 (2019). https://doi.org/10.1038/s41598-019-41695-z

For the original implementation in C++ with python bindings, see: https://github.com/vtraag/leidenalg

## Installation

To install the stable version from [CRAN](https://CRAN.R-project.org/package=leidenAlg), use:

```r
install.packages('leidenAlg')
```

To install the latest version, use:

```r
install.packages('devtools')
devtools::install_github('kharchenkolab/leidenAlg', build_vignettes = TRUE)
```

Note that this package depends on [igraph](https://CRAN.R-project.org/package=igraph), which requires various libraries to install correctly e.g. `libxml2`. Please see the installation instructions at that page for more details. 

Debian-based users of Linux can install `libxml2` via

```
sudo apt-get update
sudo apt-get install libxml2-dev
```

For Mac OS, the commands with the Homebrew package manager are as follows:

```
brew update
brew install libxml2
```

## Functions

* `leiden.community()`: Detect communities using Leiden algorithm, output as `fakeCommunities` class for downstream use.

* `rleiden.community()`: Recursive leiden communities, constructs an n-step recursive clustering, using leiden.community.detection. Returns a `fakeCommunities` object that has methods membership(), without dendrogram.

* `as.dendrogram()`: Returns pre-calculated dendrogram from `"fakeCommunities"` object

* `membership()`: Returns pre-calculated membership factor from `"fakeCommunities"` object

## Citation
If you find `leidenAlg` useful for your publication, please cite:

```
Peter Kharchenko, Viktor Petukhov and Evan Biederstedt (2021).
leidenAlg: Implements the Leiden Algorithm via an R Interface. R
package version 0.1.1. https://github.com/kharchenkolab/leidenAlg
```
