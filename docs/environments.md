# Environments availables

## scGPT

Only available at FAS computing resources.

Please, reach out to platform to access for the first time to this env:

- Start a python notebook on the [ondemand web-page](https://rcood.rc.fas.harvard.edu/pun/sys/dashboard/batch_connect/sessions). You need to be connected to the VPN to be connected.
- Once connected (This step is tricky because you need to find the password to access the notebook)
    - Initiate a terminal session
    - `module load gcc/13.2.0-fasrc01`
    - Only the first time, add the env to the notebook kernels:
        - `python -m ipykernel install --prefix=/n/holylfs05/LABS/hsph_bioinfo/Lab/shared_resources/scgpt-2 --name 'dcgpt2' --display-name 'scgpt-2'`
    - Then, start a notebook choosing as kernel `scgpt-2`
- Validate everything works with these commands in the python notebook
    - `import torch`
    - `torch.cuda.is_available()` -> Should return `True`
    - `torch.cuda.device_count()` -> Should return `
    - `import scgpt`

