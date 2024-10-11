# Build platforms

Content ![](https://img.shields.io/badge/status-WorkInProgress-yellow)

## App development

- Use HBC or bcbio organization
- Private repo prior to release
- Test data needs to be part of the code
- README to explain how to use the test data
- First release should be prior to client
    - Must be usable at First release
    - At least one other person to review and approve 
    - After that main branch get blocked and version numbers start at 1.0.0
    - Then start dev branch
- Each time we merge a Pull request, we need to make a release
- Publish on Posit connect with a new name that matches the version

## Data management

### AWS 

- Samplesheet input files for pipelines
    - `pipelineName_PI_hbcNNNNNN`
    - Have a copy in project folder in O2
    - Manually removing weekly during platform meeting
- Raw data is under `input` folder 
    - Alex and Lorena and Emma can move data from O2/FAS to S3
    - `pipelineName_PI_hbcNNNNNN`
    - lifecycle 14 days
- Pipeline outputs are under `results`:
    - `pipelineName_PI_hbcNNNNNN`
    - lifecycle 14 days for bigger than 1gb
    - Move output pipeline to project folder under `final` folder
- Data cleaning every platform meeting
- Quarterly Evaluation: RNAseq, CHIPseq

## Configure to use posit package manager

[source](https://packagemanager.posit.co/client/#/repos/bioconductor/setup?bioconductor_version=3.18)

```
# Configure BioCManager to use Posit Package Manager:
options(BioC_mirror = "https://packagemanager.posit.co/bioconductor")
options(BIOCONDUCTOR_CONFIG_FILE = "https://packagemanager.posit.co/bioconductor/config.yaml")

# Configure a CRAN snapshot compatible with Bioconductor 3.18:
options(repos = c(CRAN = "https://packagemanager.posit.co/cran/2024-05-01"))
```

### Creating env in Data Studio

Set up the package manager [properly](https://packagemanager.posit.co/client/#/repos/bioconductor/setup?distribution=ubuntu-22.04):

```
# Configure BioCManager to use Posit Package Manager:
options(BioC_mirror = "https://packagemanager.posit.co/bioconductor/latest")
options(BIOCONDUCTOR_CONFIG_FILE = "https://packagemanager.posit.co/bioconductor/latest/config.yaml")

# Configure a CRAN snapshot compatible with Bioconductor 3.20:
options(repos = c(CRAN = "https://packagemanager.posit.co/cran/__linux__/jammy/latest"))
install.packages("BiocManager")
```

Install minimum system library packages from [ubuntu22](ubuntu22.system.ready.txt).

Install all needed packages, and stop the server to get the first checkpoint with the packages installed. 

After this, other users can start a new DataStudio from it with the dependencies already installed.

### Installing sc packages in O2

### CELLCHAT

Use these modules when starting Rstudio in O2:

```
gcc/9.2.0 imageMagick/7.1.0 geos/3.10.2 cmake/3.22.2 R/4.3.1 fftw/3.3.10 gdal/3.1.4 udunits/2.2.28  boost/1.75.0 python/3.9.14
```

In the R console you can load deps with these lines:

```
# To use it
reticulate::use_virtualenv("/n/app/bcbio/R4.3.1_python_cellchat")
reticulate::py_config() # check it is pointing to right versions: umap-learn 0.5.5 and umap 1.26
Sys.getenv("PYTHONPATH") # needs to be empty

py_module_available(module = 'umap')
reticulate::import(module = "umap", delay_load = TRUE)
.libPath("/n/app/bcbio/R4.3.1_cellchat")
library(CellChat)
```

To install it:

```
# To install python deps
virtualenv_install("/n/app/bcbio/R4.3.1_python_cellchat", packages="umap-learn==0.5.5",python_version="3.9",force=TRUE)
virtualenv_install("/n/app/bcbio/R4.3.1_python_cellchat", packages="numpy==1.26",python_version="3.9")
#.rs.restartR() # restart R manually if outside RStudio
reticulate::py_config() # check it is pointing to right versions: umap-learn 0.5.5 and umap 1.26
Sys.getenv("PYTHONPATH") # needs to be empty

# R package
BiocManager::install("BiocNeighbors")
install.packages('NMF')
install.packages("circlize")
devtools::install_github("jinworks/CellChat")
```