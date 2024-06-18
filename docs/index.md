# Welcome to HCBC Platform

Welcome to our Platform guidelines web-page. Here analysts and developers will find guidelines on how to work with our most common environments.

We are developing platforms for each analysis type we have experience with at HCBC. Currently we fully support:

- bulk RNAseq analysis ![](https://img.shields.io/badge/status-beta-blue)

Got to each analysis type section to learn how to use our platform.

## RNAseq

* Using O2 open OnDemand: 
    * Remove `bcbio` from you `PATH` by commenting the line in your `.bashrc` if you have it
    * Start Rstudio With these modules on: `gcc/9.2.0 imageMagick/7.1.0 geos/3.10.2 cmake/3.22.2 R/4.3.1 fftw/3.3.10 gdal/3.1.4 udunits/2.2.28  boost/1.75.0`
    * When the session is started, set you library path typing this command in your console Rstudio window:  `.libPaths("/n/app/bcbio/R4.3.1")`

* load bcbioR with `library(bcbioR)`
* Make sure the version is 0.1.3 with this command `packageVersion("bcbioR")` or re-install with `devtools::install_github("bcbio/bcbioR",build_manual = TRUE, build_vignettes = TRUE)`, if you are in your own environment
* Follow this instruction https://bcbio.github.io/bcbioR/#set-base-project to start you project
* Follow this instruction https://bcbio.github.io/bcbioR/#set-rnaseq-report-folder to start your RNAseq analysis

# BCBIOR Supported Templates

We used `bcbioR` to deploy folders and code to our project directories to improve robustness in our analysis.

You can install `bcbioR` as indicated here: `https://github.com/bcbio/bcbioR/tree/main`

RNAseq ![](https://img.shields.io/badge/status-alpha-blue)
TEASeq ![](https://img.shields.io/badge/status-concept-yellow)
COSMX ![](https://img.shields.io/badge/status-concept-yellow)
scRNAseq ![](https://img.shields.io/badge/status-concept-yellow)

