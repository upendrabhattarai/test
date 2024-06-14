# Build platforms


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

```
module load  miniconda3/23.1.0

conda create -p /n/app/bcbio/R4.3.1_python -c conda-forge umap-learn

BiocManager::install("BiocNeighbors")
install.packages('NMF')
install.packages("circlize")
devtools::install_github("jinworks/CellChat")

library(reticulate)
# create a new environment 
virtualenv_create("/n/app/bcbio/R4.3.1_python_sc_20240522snapshot")
# install umap
virtualenv_install("/n/app/bcbio/R4.3.1_python_sc_20240522snapshot", "umap-learn")
# indicate that we want to use a specific virtualenv
use_virtualenv("/n/app/bcbio/R4.3.1_python_sc_20240522snapshot")
py_module_available(module = 'umap')
reticulate::import(module = "umap", delay_load = TRUE)
```