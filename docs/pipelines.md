# Introduction to HCBC pipelines

## Nextflow in O2

Example of running in single node Nextflow/nf-core/rnaseq in O2.

```
#!/bin/bash

#SBATCH --job-name=Nextflow      # Job name
#SBATCH --partition=priority            # Partition name
#SBATCH --time=1-23:59                 # Runtime in D-HH:MM format
#SBATCH --nodes=1                      # Number of nodes (keep at 1)
#SBATCH --ntasks=1                     # Number of tasks per node (keep at 1)
#SBATCH --cpus-per-task=8            # CPU cores requested per task (change for threaded jobs)
#SBATCH --mem=128G                     # Memory needed per node (total)
#SBATCH --error=jobid_%j.err           # File to which STDERR will be written, including job ID
#SBATCH --output=jobid_%j.out          # File to which STDOUT will be written, including job ID
#SBATCH --mail-type=ALL                # Type of email notification (BEGIN, END, FAIL, ALL)

module load java/jdk-21.0.2
export NXF_APPTAINER_CACHEDIR=/n/app/singularity/containers/shared/bcbio/
export NXF_SINGULARITY_LIBRARYDIR=/n/app/singularity/containers/shared/bcbio/

./nextflow run nf-core/rnaseq -profile singularity,test --outdir here
```