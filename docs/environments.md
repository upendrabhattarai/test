# Environments availables

## scGPT

Only available at FAS computing resources.

Please, reach out to platform to access for the first time to this env:

- Add the environment first:
    - Only the first time, add the env to the notebook kernels:
        - `echo "n/holylfs05/LABS/hsph_bioinfo/Lab/shared_resources/scgpt-2" >> ~/.conda/environments.txt`

- Start a python notebook on the [ondemand web-page](https://rcood.rc.fas.harvard.edu/pun/sys/dashboard/batch_connect/sessions). 
    - You need to be connected to the VPN to be connected. 
    - Use `gpu` partition and if you need more than one GPU or `gpu_test` if you need something that won't take a long time 
        - add these to the sbatch options `--gres=gpu:n` in the advance options, they are below in the page.
    - Add `gcc/13.2.0-fasrc01` to the list of modules to load
- Once connected, if you get asked to use a password, just close the windows and open again.
    - If you didn't add module `gcc/13.2.0-fasrc01`, do this now:
        - Initiate a terminal session
        - `module load gcc/13.2.0-fasrc01`
    - Then, start a notebook choosing as kernel `scgpt-2`
- Validate everything works with these commands in the python notebook
    - `import torch`
    - `torch.cuda.is_available()` -> Should return `True`
    - `torch.cuda.device_count()` -> Should return `
    - `import scgpt`

