devroadmap
==========

rOpenSci Development Road Map

This document does not track every project/package within rOpenSci,
but rather the larger efforts we are undertaking.

Packages/projects within ropenscilabs are considered in more draft
form, so won't generally be included here.

Go to Issues/Milestones for each respective package to get up
to date information on issues and planned release dates.

For past changes on a per pacakge bases: All rOpenSci repositories do 
or will soon have notes on each release in the `releases` tab for 
each repo (e.g., [releases for rgbif](https://github.com/ropensci/rgbif/releases)). If releases is missing see the `NEWS`/`NEWS.md` file in the
repository.

Format of this roadmap in part inspired by [jupyter/roadmap](https://github.com/jupyter/roadmap)

--------

## documentation

### ropensci.org tutorials

rOpenSci packages mostly have at least one vignette. We use these vignettes to create html versions fitting the style of our website ([https://ropensci.org/](https://ropensci.org/)) - which live at [https://ropensci.org/tutorials](https://ropensci.org/tutorials). We plan to make two major improvements:

* These are currently manually kept up to date with latest versions of those in each package. We plan to automate this process, so humans don't have to update tutorials on the website, but rather get the updated tutorial docs when they are updated by any package maintainer.
* There is a barrier to trying new packages, especially when a package has dependencies that take a long time to install or are hard to install. We plan to make examples in tutorials on our website interactive so that users do not have to first install the software to try it. They can try it with examples relavant to them instead of simply the examples we have thought of.

## taxize

### Next

* incorporate Wikipedia as a data source [ropensci/taxize#317](https://github.com/ropensci/taxize/issues/317)
* make `synonyms()` easier to work with, make it easier to extract names from the varied outputs from the different data sources [ropensci/taxize#533](https://github.com/ropensci/taxize/issues/533)
* improve taxon ID classes - from the current simple/dumb S3 object to something more compact and which we can then manipulate easily in various contexts [ropensci/taxize#508](https://github.com/ropensci/taxize/issues/508)

### Future

For [Milestone v1.0](https://github.com/ropensci/taxize/milestones/v1.0):

* More vignettes [ropensci/taxize#544](https://github.com/ropensci/taxize/issues/544)
* Separate out long running tests, but still on CI [ropensci/taxize#279](https://github.com/ropensci/taxize/issues/279)
* Finalize package API - which should ideally not break after this version [ropensci/taxize#480](https://github.com/ropensci/taxize/issues/480)

## rgbif

### Next

* improvements to parsing arguments for `occ_download` [ropensci/rgbif#217](https://github.com/ropensci/rgbif/issues/217)
* Integrate new GBIF API features: repatriation fields and queries, faceting, full text search [ropensci/rgbif#214](https://github.com/ropensci/rgbif/issues/214) [ropensci/rgbif#215](https://github.com/ropensci/rgbif/issues/215) [ropensci/rgbif#216](https://github.com/ropensci/rgbif/issues/216)
* new vignette covering known problems with scientific names in GBIF [ropensci/rgbif#209](https://github.com/ropensci/rgbif/issues/209)
* better support for parameters in the API that can be used multiple times, not all are supported right now [ropensci/rgbif#200](https://github.com/ropensci/rgbif/issues/200)

### Future

For [Milestone v1.0](https://github.com/ropensci/rgbif/milestones/v1.0):

* Settle on a user interface for cleaning GBIF data - we have a set o functions right now, but is it idea, should anything be changed. [ropensci/rgbif#111](https://github.com/ropensci/rgbif/issues/111)
* Performance improvements: we've focused in `rgbif` on a good user interface, but have only recently started making performance improvements. We'll continue to do this [ropensci/rgbif#194](https://github.com/ropensci/rgbif/issues/194)
* Finalize package API - which should ideally not break after this version. Think about how to reduce future package API changes given unpredictable changes in the GBIF API [ropensci/rgbif#189](https://github.com/ropensci/rgbif/issues/189)
