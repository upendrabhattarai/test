# Welcome to HCBC Platform

Welcome to our Platform guidelines web-page. Here analysts and developers will find guidelines on how to work with our most common environments.

We are developing platforms for each analysis type we have experience with at HCBC.

Go to each analysis-type section to learn how to use our platform.

## Set up the package

* Using O2 open OnDemand: 
    * Remove `bcbio` from you `PATH` by commenting the line in your `.bashrc` if you have it
    * Start Rstudio with these modules on: `gcc/9.2.0 imageMagick/7.1.0 geos/3.10.2 cmake/3.22.2 R/4.3.1 fftw/3.3.10 gdal/3.1.4 udunits/2.2.28  boost/1.75.0`
    * Add `--exclude=compute-f-17-[09-25]` to the 'Slurm Custom Arguments' field
    * When the session is started, set you library path typing this command in your console Rstudio window:  `.libPaths("/n/app/bcbio/R4.3.1")`

* Load bcbioR with `library(bcbioR)`
* Make sure the version is **v0.3.*** with this command `packageVersion("bcbioR")` or re-install with `devtools::install_github("bcbio/bcbioR",build_manual = TRUE, build_vignettes = TRUE)`, if you are in your own environment

## General Project

Use the [hcbc app](https://hcbc.connect.hms.harvard.edu/content/8cd62872-0ec9-4905-8920-c745d2375758) to set up projects names. This name will be used for O2/FAS/github and dropbox. They may be already defined in the Trello card.

This set up needs [bcbioR](https://github.com/bcbio/bcbioR) and [usethis](https://usethis.r-lib.org) packages.

Make sure the version is `v0.3.*` with this command `packageVersion("bcbioR")` or re-install with `devtools::install_github("bcbio/bcbioR",build_manual = TRUE, build_vignettes = TRUE)`, if you are in your own environment.

First create Rstudio project:

```
project_path <- "/n/scratch/groups/hsph/hbc/lp113/lastname_postdoc_rnaseq_human_heart_hbc00000"
# if path doesn't exists - normally not the case
dir.create(project_path)
usethis::proj_activate(project_path)
```

This will restart the session in the project directory:

```
# Make sure is v0.3*
packageVersion("bcbioR")
# check current library
.libPaths()
# set up needed library
.libPaths("/n/app/bcbio/R4.3.1_rnaseq")
# check package version again
packageVersion("bcbioR")
# Set this library for future use - only once
bcbioR::use_library("/n/app/bcbio/R4.3.1_rnaseq")
# Deploy base project
bcbioR::bcbio_templates(type="base", outpath=".", org="hcbc")
# Start local git repository
# Don't commit files and restart session
usethis::use_git()
```

Push this project to GitHub following these steps:

* Only once every 30 days, set up your github credentials: `usethis::gh_token_help()`
  * **NOTE** You may want to run this first to keep this token working in future sessions in O2/FAS: `git config --global credential.helper store`
* Push repository to HBC github as private: `usethis::use_github(org="hbc",private=TRUE)`

Read the REAME and any other Management checklist that is in the project folder.

## RNAseq

Use this common library path to perform your analysis: `bcbio::use_library("/n/app/bcbio/R4.3.1_rnaseq")`.
* Follow the previous step to set up the [base](#general-project) project if you haven't done it already
* Deploy templates with:

```
bcbioR::bcbio_templates(type="rnaseq", outpath="reports")
```

## scRNAseq

Please, change to this common library path to perform your analysis: 

```
bcbioR::use_library("/n/app/bcbio/R4.3.1_singlecell")
bcbioR::bcbio_templates(type="singlecell", outpath="reports")
```

## ChipSeq

Please, change to this common library path to perform your analysis: 

```
bcbioR::use_library("/n/app/bcbio/R4.3.1_chipseq")
bcbioR::bcbio_templates(type="chipseq", outpath="reports")
```

# bcbioR supported templates

We used `bcbioR` to deploy folders and code to our project directories to improve robustness in our analysis.

You can install `bcbioR` as indicated here: `https://github.com/bcbio/bcbioR/tree/main`

- RNAseq ![](https://img.shields.io/badge/status-stable-blue)
- ChipSeq ![](https://img.shields.io/badge/status-beta-yellow)
- scRNAseq ![](https://img.shields.io/badge/status-beta-yellow)
- CELLCHAT ![](https://img.shields.io/badge/status-draft-grey)
- TEASeq ![](https://img.shields.io/badge/status-draft-grey)
- COSMX ![](https://img.shields.io/badge/status-draft-grey)


# Note
>These materials have been developed by members of the teaching and platform team at the Harvard Chan Bioinformatics Core (HBC) RRID:SCR_025373. 