# Introduction to HCBC pipelines

Content ![](https://img.shields.io/badge/status-WorkInProgress-yellow)

## Nextflow in Seqera platform

- Create an user here: https://cloud.seqera.io/login
- Ask Platform team to add you to HCBC workspace
- Transfer data to HCBC S3: Ask Alex/Lorena. Files will be at our S3 bucket `input/rawdata` folder
- Prepare the CSV file according this [instructions](https://nf-co.re/rnaseq/3.14.0/docs/usage#multiple-runs-of-the-same-sample). File should look like this:

```csv
sample,fastq_1,fastq_2,strandedness
CONTROL_REP1,s3path/AEG588A1_S1_L002_R1_001.fastq.gz,s3path/AEG588A1_S1_L002_R2_001.fastq.gz,auto
CONTROL_REP1,s3path/AEG588A1_S1_L003_R1_001.fastq.gz,s3path/AEG588A1_S1_L003_R2_001.fastq.gz,auto
CONTROL_REP1,s3path/AEG588A1_S1_L004_R1_001.fastq.gz,s3path/AEG588A1_S1_L004_R2_001.fastq.gz,auto
```

Use `bcbio_nfcore_check(csv_file)` to check the file is correct.

You can add more columns to this file with more metadata, and use this file as the `coldata` file in the templates.

- Safe the file under `meta` folder
- Upload this file to our `Datasets` in Seqera using the name of the project but starting with `rnaseq-pi_lastname-hbc_code`
- Go to `Launchpad`, select `nf-core_rnaseq` pipeline, and select the previous created `Datasets` in the `input` parameter after clicking in `Browser`
  - Select an output directory with the same name used for the `Dataset` inside the `results` folder in S3
- When pipeline is done, data will be copied to our on-premise HPC in the scratch system under `scratch/groups/hsph/hbc/bcbio/` folder


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
export NXF_APPTAINER_CACHEDIR=/n/app/singularity/containers/shared/bcbio/nf-core-rnaseq-3.14.0
export NXF_SINGULARITY_LIBRARYDIR=/n/app/singularity/containers/shared/bcbio/nf-core-rnaseq-3.14.0

./nextflow run nf-core/rnaseq -r 3.14.0 -profile singularity,test --outdir here -resume
```

## Nextflow in FAS


```
module load jdk/21.0.2-fasrc01
```

Use nextflow at `/n/holylfs05/LABS/hsph_bioinfo/Lab/shared_resources/nextflow`

Use config file at `/n/holylfs05/LABS/hsph_bioinfo/Lab/shared_resources/nextflow/fas.config`

Example command to run in an interactive job:

```
/n/holylfs05/LABS/hsph_bioinfo/Lab/shared_resources/nextflow run nf-core/rnaseq -profile test,singularity --outdir tmp -c /n/holylfs05/LABS/hsph_bioinfo/Lab/shared_resources/nextflow/fas.config
```

For non-test data, this is the head job you need to submit. Copy first the config files and modified as  needed:

```
cp /n/holylfs05/LABS/hsph_bioinfo/Lab/shared_resources/nextflow/fas.config .
cp /n/holylfs05/LABS/hsph_bioinfo/Lab/shared_resources/nextflow/rnaseq.config .
```

And then modify this template as needed before using it:

```
#!/bin/bash

#SBATCH --job-name=Nextflow      # Job name
#SBATCH --partition=shared            # Partition name
#SBATCH --time=0-48:59                 # Runtime in D-HH:MM format
#SBATCH --nodes=1                      # Number of nodes (keep at 1)
#SBATCH --ntasks=1                     # Number of tasks per node (keep at 1)
#SBATCH --mem=16G                     # Memory needed per node (total)
#SBATCH --error=jobid_%j.err           # File to which STDERR will be written, including job ID
#SBATCH --output=jobid_%j.out          # File to which STDOUT will be written, including job ID
#SBATCH --mail-type=ALL                # Type of email notification (BEGIN, END, FAIL, ALL)

module load jdk/21.0.2-fasrc01

export NXF_APPTAINER_CACHEDIR=/n/holylfs05/LABS/hsph_bioinfo/Lab/shared_resources/nextflow/nfcore-rnaseq
export NXF_SINGULARITY_LIBRARYDIR=/n/holylfs05/LABS/hsph_bioinfo/Lab/shared_resources/nextflow/nfcore-rnaseq

OUTPUT=path_to_results

/n/holylfs05/LABS/hsph_bioinfo/Lab/shared_resources/nextflow run nf-core/rnaseq -r 3.14.0 \
  -profile singularity \
  -c analysis.config \
  -c rnaseq.config \ 
  --outdir $OUTPUT -c fas.config \
   -resume
```
