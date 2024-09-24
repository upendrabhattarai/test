# Welcome to HCBC Platform

Welcome to our Platform guidelines web-page. Here analysts and developers will find guidelines on how to work with our most common environments.

We are developing platforms for each analysis type we have experience with at HCBC. Currently we fully support:

- bulk RNAseq analysis ![](https://img.shields.io/badge/status-beta-blue)

Go to each analysis-type section to learn how to use our platform.

## Set up the package

* Using O2 open OnDemand: 
    * Remove `bcbio` from you `PATH` by commenting the line in your `.bashrc` if you have it
    * Start Rstudio with these modules on: `gcc/9.2.0 imageMagick/7.1.0 geos/3.10.2 cmake/3.22.2 R/4.3.1 fftw/3.3.10 gdal/3.1.4 udunits/2.2.28  boost/1.75.0`
    * Add `--exclude=compute-f-17-[09-25]` to the 'Slurm Custom Arguments' field
    * When the session is started, set you library path typing this command in your console Rstudio window:  `.libPaths("/n/app/bcbio/R4.3.1_rnaseq")`

* Load bcbioR with `library(bcbioR)`
* Make sure the version is 0.1.3 with this command `packageVersion("bcbioR")` or re-install with `devtools::install_github("bcbio/bcbioR",build_manual = TRUE, build_vignettes = TRUE)`, if you are in your own environment

## General Project

Use the [hcbc app](https://hcbc.connect.hms.harvard.edu/content/8cd62872-0ec9-4905-8920-c745d2375758) to set up projects names. This name will be used for O2/FAS/github and dropbox. They may be already defined in the Trello card.

This set up needs [bcbioR](https://github.com/bcbio/bcbioR) and [usethis](https://usethis.r-lib.org) packages.

Make sure the version is `0.1.3` with this command `packageVersion("bcbioR")` or re-install with `devtools::install_github("bcbio/bcbioR",build_manual = TRUE, build_vignettes = TRUE)`, if you are in your own environment

* Create an R Project located in your project folder: `usethis::proj_activate("/path/to/analysis/folder")`
* Deploy folders/files compatible with any project: `bcbioR::bcbio_templates(type="base", outpath="/path/to/analysis/folder")`
* Start a git repository: `usethis::use_git()`

If you want to push this project to GitHub, follow these steps:

* Only once every 30 days, set up your github credentials: `usethis::gh_token_help()`
  * **NOTE** You may want to run this first to keep this token working in future sessions in O2/FAS: `git config --global credential.helper store`
* Push repository to HBC github as private: `usethis::use_github(org="hbc",private=TRUE)`

## RNAseq

* Follow the previous step to set up the [base](#general-project) project
* Follow this instruction https://bcbio.github.io/bcbioR/#set-rnaseq-report-folder to start your **RNAseq** analysis

## scRNAseq

Please, change to this common library path to perform you  analysis: `.libPaths("/n/app/bcbio/R4.3.1_singlecell")`.

## ChipSeq

Please, change to this common library path to perform you  analysis: `.libPaths("/n/app/bcbio/R4.3.1_chipseq")`.

# bcbioR supported templates

We used `bcbioR` to deploy folders and code to our project directories to improve robustness in our analysis.

You can install `bcbioR` as indicated here: `https://github.com/bcbio/bcbioR/tree/main`

- RNAseq ![](https://img.shields.io/badge/status-alpha-blue)
- CELLCHAT ![](https://img.shields.io/badge/status-alpha-yellow)
TEASeq ![](https://img.shields.io/badge/status-concept-yellow)
- COSMX ![](https://img.shields.io/badge/status-concept-yellow)
- scRNAseq ![](https://img.shields.io/badge/status-concept-yellow)


# Note
>These materials have been developed by members of the teaching and platform team at the Harvard Chan Bioinformatics Core (HBC) RRID:SCR_025373. 