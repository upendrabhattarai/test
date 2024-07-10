# Build platforms

Content ![](https://img.shields.io/badge/status-WorkInProgress-yellow)


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

### Installing sc packages in O2

### CELLCHAT

Add `python/3.9.14` to the modules load to Rstudio in O2 ondemand.

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


# To use it
reticulate::use_virtualenv("/n/app/bcbio/R4.3.1_python_cellchat")
reticulate::py_config() # check it is pointing to right versions: umap-learn 0.5.5 and umap 1.26
Sys.getenv("PYTHONPATH") # needs to be empty

py_module_available(module = 'umap')
reticulate::import(module = "umap", delay_load = TRUE)
library(CellChat)
```