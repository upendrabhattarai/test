# Welcome to HCBC Platform

Welcome to our Platform guidelines web-page. Here analysts and developers will find guidelines on how to work with our most common environments.

We are developing platforms for each analysis type we have experience with at HCBC.

Go to each analysis-type section to learn how to use our platform.

## Set up the package

* Log onto O2 via the command line (first-time only): 
    * Remove `bcbio` from you `PATH` by commenting the line in your `.bashrc` if you have it
    * Remove any path you load using the R env variables that could be in your `.Rprofile` or `.bashrc`
* Go to the [O2 Portal](https://o2portal.rc.hms.harvard.edu/) and select `HMS-RC Application`, then `RStudio Environment`
<p align="center"><img src="../img/O2_portal_page_with_label.png" width="700"></p>

* Start Rstudio with using your desired partition, memory, core and time directives. Add these modules to "Modules to be loaded":
  ```
  git/2.9.5  gcc/9.2.0 imageMagick/7.1.0 geos/3.10.2 cmake/3.22.2 R/4.3.1 fftw/3.3.10 gdal/3.1.4 udunits/2.2.28  boost/1.75.0
  ```
   Click "Launch"

<p align="center"><img src="../img/O2_portal_request.gif" width="700"></p>

* Open RStudio by clicking on the "Connect to RStudio Server"

<p align="center"><img src="../img/O2_connect_to_RStudio_with_label.png" width="700"></p>

* When the session is started, set you library path typing this command in your console Rstudio window in order to be able to load bcbioR:

```
.libPaths("/n/app/bcbio/R4.3.1")
```

* Next, load bcbioR with:

```
library(bcbioR)
```
  
* Check the package version of bcbioR using:

```
packageVersion("bcbioR")
```

Make sure the version is **v0.3.*** or later.

<p align="center"><img src="../img/Version_check_bcbioR.gif" width="700"></p>

> Note: If you are working in your local environment, install bcbioR with
> ```
> devtools::install_github("bcbio/bcbioR",build_manual = TRUE, build_vignettes = TRUE)
> ``` 

## General Project

Use the [hcbc app](https://hcbc.connect.hms.harvard.edu/content/8cd62872-0ec9-4905-8920-c745d2375758) to set up projects names. This name will be used for O2/FAS/github and dropbox. They may be already defined in the Trello card.

This set up needs [bcbioR](https://github.com/bcbio/bcbioR) and [usethis](https://usethis.r-lib.org) packages.

First create Rstudio project:

```
project_path <- "/n/scratch/groups/hsph/hbc/lp113/lastname_postdoc_rnaseq_human_heart_hbc00000"
# if path doesn't exists - normally not the case
dir.create(project_path)
usethis::proj_activate(project_path)
```

This will restart the session in the project directory:

```

# check current library to make sure it is your expected path
.libPaths()
# Reload bcbioR (wipe with project)
library(bcbioR)
# reload
`.libPaths("/n/app/bcbio/R4.3.1_rnaseq")`
`.libPaths("/n/app/bcbio/R4.3.1_singlecell")`
`.libPaths("/n/app/bcbio/R4.3.1_chipseq")`
`.libPaths("/n/app/bcbio/R4.3.1_cellchat")`
`.libPaths("/n/app/bcbio/R4.3.1_methylation")`
# check package version again
packageVersion("bcbioR")
# Set this library for future use - only once
bcbioR::use_library("/n/app/bcbio/R4.3.1_rnaseq")
bcbioR::use_library("/n/app/bcbio/R4.3.1_singlecell")`
bcbioR::use_library("/n/app/bcbio/R4.3.1_chipseq")`
bcbioR::use_library("/n/app/bcbio/R4.3.1_cellchat")`
bcbioR::use_library("/n/app/bcbio/R4.3.1_methylation")`
# Deploy base project
bcbioR::bcbio_templates(type="base", outpath=".", org="hcbc")
# Start local git repository
# Don't commit files and restart session
usethis::use_git()
```

Push this project to GitHub following these steps:

* Make sure you have git in your path
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
