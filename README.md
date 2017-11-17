devroadmap
==========

rOpenSci Development Road Map

This document does not track every project/package within rOpenSci,
but rather the larger efforts we are undertaking.

Go to Issues/Milestones for each respective package to get up
to date information on issues and planned release dates.

For past changes on a per pacakge basis: All rOpenSci repositories should
have notes on each release in the `releases` tab for
(e.g., [releases for rgbif](https://github.com/ropensci/rgbif/releases)). If
releases is missing see the `NEWS`/`NEWS.md` file in the repository.

--------

## CRAN PACKAGES

 - [jeroen@berkeley.edu](https://cran.r-project.org/web/checks/check_results_jeroen_at_berkeley.edu.html)
 - [myrmecocystus@gmail.com](https://cran.r-project.org/web/checks/check_results_myrmecocystus_at_gmail.com.html) & [myrmecocystus+r@gmail.com](https://cran.r-project.org/web/checks/check_results_myrmecocystus_r_at_gmail.com.html)

### Magick and Image Processing

Jeroen working on new infrastructure for image processing and analysis in R.

 - ~Implement magick feature requests~ **complete**
 - ~Implement drawing system (perhaps via a graphics device)~ **complete**
 - ~Integrate with Tesseract~ **complete**
 - ~Blog post~ **complete**
 - Update latest libmagick++: Done but need to do again.
 - Refactoring documentation: **in progress**
 - To do: Extract image classes, make pkg more extensible
 - To do: Implement image analsysis tools

### Overdue Maintenance

 - CRAN has requested maintenance on the `brotli` package. Also the upstream library has had a lot of breaking changes in v1.0
 - ~The `tesseract` package seems broken all of a sudden. Probably breaking upstream changes.~ **complete**
 - The `RAppArmor` package needs cleanup now that most functionality has been extracted into `unix`.

### Tutorial / Playground

Ideas for the new website:

 - Create rOpenSci `rmarkdown` theme to generate rOpenSci tutorials as vignettes
 - Experiment with interactive tutorials (playground) for rOpenSci tools using new OpenCPU
 - Blog about `ropensci.ocpu.io` for remotely calling ropensci tools

### security

Improve security in R. We want to bootstrap a trust network based on the ropensci community to make it safer to install R packages from arbitrary sources (github, cran, etc). Git's ability to sign commits, combined with Github's GPG API and/or keybase for identifying peers.

* [gpg](https://cran.r-project.org/web/packages/gpg/vignettes/intro.html) needs work to support multiple keyrings.
* [notary](https://github.com/ropenscilabs/notary) developed at unconf17, experiment with a version of `install_github` that shows and verifies signatures.

Bob Rudis has a keybase package which interacts with the keybase API that we might borrow from. I also want to look into another approached based off letsencrypt.

* [openssl](https://cran.r-project.org/web/packages/openssl/index.html) needs a mainenance release to address bugs and features
* [jose](https://cran.r-project.org/web/packages/jose/) implements Javascript Object Signing and Encryption based on `openssl` and `jsonlite` packages. Needed for letsencrypt client.
* `acme` is the protocol used by letsenrypt. It uses `jose` for signing and encrypting tokens. To get started I will implement a letsencrypt client for R (which also allows for further testing and developing `jose`). One that works, perhaps we can use the certificates for other purposes as well.

Also doing research into additional methods of securing R such as libcgroups and docker).

### geospatial 

No big new projects in this space, but rather the focus here is to try to get some more traction for the GeoJSON workflow in R. Using pkgs we've developed and others out there, I want to get out a numbef of blog posts/screencasts/vignettes for how to do spatial work centered around GeoJSON - and point out where its worse and where better than the sp/sf workflow. 

There's already a lot of traction for `geojsonio` package (see [SO questions](https://stackoverflow.com/search?tab=newest&q=%5br%5d%20%27geojsonio%27)) - so that seems like a definite area to focus on.

Does include though some new pkgs or versions:

* [geoops](https://github.com/ropenscilabs/geoops) - first version is up on CRAN - but lots more to do adding methods and optimizing, etc.
* [geofilter](https://github.com/ropenscilabs/geofilter) - not on CRAN yet. hoping to get up soon. will help users filter through GeoJSON just like you can for data.frame's/tibble's - using `jq`. i think this is an important piece for people to consider using a GeoJSON based workflow.

### CRAN checks API

A REST API for cran check results. code: https://github.com/ropensci/cchecksapi api: https://cranchecks.info/heartbeat  The main work done, but tweaking from feedback from various folks. 

Once it's basically done, may try to set up a notification system to ropensci pkg maintainers (and others) to opt in to notifications (email, etc.) when there's errors, warnings, notes, etc. 

### http mocking/caching

__target date: late January 2018__

`webmockr` mocks HTTP requests, and `vcr` is used mostly to integrate with unit tests to cache HTTP requests. `webmockr` is now on CRAN and improvements are being made. `vcr` is very close to a CRAN release.

* [webmockr](https://github.com/ropensci/webmockr) __now on CRAN__
* [vcr](https://github.com/ropensci/vcr) _close to 1st version on CRAN_

Both above will right away integrate with [crul](https://github.com/ropensci/crul) - but both will integrate with other http clients later (`httr`, `curl`, `RCurl`, etc.)

I will use `vcr` heavily in test suites in probably all the API wrappers I maintain. (and `vcr` depends on `webmockr`) - should see wide adoption outside of ropensci as there's nothing like these two out there currently.

Update: taking longer to get to this than I thought - so busy with maintenance and other projects.

### text mining

__target date: February 2018__

A few pkgs need updates, will try to organize releases to coincide + blog post:

* [fulltext](https://github.com/ropensci/fulltext) - shooting for [milestone v0.2](https://github.com/ropensci/fulltext/milestone/3) - lots of new things, demo abstract mining, full text mining, etc.
* [microdemic](https://github.com/ropenscilabs/microdemic) - new pkg to work with Microsoft Academic Search API
* [rcoreoa](https://github.com/ropensci/rcoreoa) - new pkg to work with CORE search API - also used in OpenknowledgeMaps
* [jaod](https://github.com/ropenscilabs/jaod) - new pkg to work with Directory of Open Access Journals API
* [crminer](https://github.com/ropensci/crminer) - new version to go out
* [rbace](https://github.com/ropenscilabs/rbace) - new pkg to work with BASE search API - also used in OpenknowledgeMaps


### biodiversity data

__target date: February 2018__

Continual patch releases of these are put out, but targeting a grouped single date to release new versions of a suite of these pkgs:

* [rgbif](https://github.com/ropensci/rgbif) - shooting for [milestone v1.0](https://github.com/ropensci/rgbif/milestone/10)
* [spocc](https://github.com/ropensci/spocc) - [milestone v0.8](https://github.com/ropensci/spocc/milestone/15)
* [ecoengine](https://github.com/ropensci/ecoengine) - @karthik maintaining - not sure if there's an obvious milestone that can be reached for this
* [scrubr](https://github.com/ropenscilabs/scrubr) - [milestone v0.3](https://github.com/ropensci/scrubr/milestone/4)
* [mapr](https://github.com/ropensci/mapr) - [milestone v0.4](https://github.com/ropensci/mapr/milestone/5)
* [seaaroundus](https://github.com/ropensci/seaaroundus) - recently took this over - __pushing out a 1st CRAN version soon__
* etc... there are more



## Completed

### text processing and analysis

Lots of [suggestions](https://github.com/ropensci/textworkshop17/issues/5) from the textworkshop in London for wrapping new text processing libraries and utilities.

* [antiword](https://cran.r-project.org/web/packages/antiword/index.html) DONE: on cran
* [~dynamic topic models~](https://github.com/blei-lab/dtm): Started wrapping but turns out to be bad library. Discontinued.
* [bigartm](https://github.com/bigartm/bigartm)
* [compact language detector 2](https://github.com/CLD2Owners/cld2) DONE: on cran
* [compact language detector 3](https://github.com/google/cld3) DONE: on cran
* [unrtf](https://github.com/ropensci/unrtf) Done: on cran

### taxonomy

`taxize` is our core taxonomy package that's been around for years, and is used widely. We're targeting a [v1.0 release](https://github.com/ropensci/taxize/milestones/v1.0) for late in 2017, but will have a pre v1 for this target release.

* [taxize](https://github.com/ropensci/taxize)
* [taxizedb](https://github.com/ropenscilabs/taxizedb) - use SQL dumps of taxonomic databases locally __ON CRAN__
* [binomen](https://github.com/ropensci/binomen) - dplyr like interface for taxonomic data __being merged with `taxa`__
* [taxa](https://github.com/ropensci/taxa) - classes for taxonomic data - in the future to be used by all other taxonomy packages __waiting on this getting to CRAN, should be very soon__ - co-maintiner and his PI and I writing a paper on this as well
* [wikitaxa](https://github.com/ropensci/wikitaxa)
* [ritis](https://github.com/ropensci/ritis)

### infrastructure

We are working on a new system for massively concurrent requests in `curl` to support high performance scarpers and crawlers. Because this is a big update, it needs a few more rounds of tweaking and testing and revision.

* [curl](https://github.com/jeroenooms/curl)

### system infrastructure

Jeroen is working on new packages `sys` and `unix` to improve interacting with low level system from R. This will make packages that require system calls more robust and easier to develop.

* [unix](https://cran.r-project.org/web/packages/unix/index.html)
* [sys](https://cran.r-project.org/web/packages/sys/index.html) (used by e.g `antiword`, `unrtf`, etc)

### geospatial

J and S are working on `geojson`, a pkg for geojson classes, which we can use in other packages. We can pair this release with `geoops`, a package to do geospatial operations without the gdal/geos stack, and a new version of `geojsonio`, our geojson I/O client. We could include new release of `geojsonlint` if appropriate. Perhaps throw in `wellknown` if I can get around to updating it.

* [geojsonio](https://github.com/ropenscilabs/geojsonio)
* [geojson](https://github.com/ropenscilabs/geojson)
* [geoops](https://github.com/ropenscilabs/geoops)
* [geosonlint](https://github.com/ropenscilabs/geojsonlint)
* [wellknown](https://github.com/ropenscilabs/wellknown)
* Implement `geobuf` format (binary geojson) in [protolite](https://github.com/jeroenooms/protolite) - this is now done ✔ - implementing now in the `geojson` package so users can optionally read and write geobuf format



