# Get Started - Python

## Use this directory to offer global setup instructions for using the geospatial workbook.

**Note: this workflow is optimal for a Jupyter Interactive server where you can access the terminal and jupyter notebooks from one place**

1. Configure conda settings on HPC
   - initiate shell or On Demand
   - initiate interactive session *Note: if using GPU for analyses, start your interactive session on a GPU node to ensure package compatibility*
   - in home directory, open your .condarc file: `nano .condarc`
   - update channels, envs_dirs, pkgs_dirs fields so environments and packages are installed to your project directory  
   
```
default_channels:
  - https://conda.anaconda.org/conda-forge

channels:
  - conda-forge
  - defaults
  - bioconda
  - pytorch
allow_other_channels: false
auto_update_conda: false
envs_dirs:
  - /project/<project.name>/software/anaconda/envs
pkgs_dirs:
  - /project/<project.name>/.conda_pkgs
```

2. Create conda environment (skip to step 3 if you already created your environment)
    - load miniconda module: `ml miniconda`
    - Upload the [geospatial-env yaml file](blob:https://github.com/2439a0b4-8fb7-4b21-9bd3-004463453bc1) to an easily accessible directory
    - navigate to directory where geospatial-env.yml is stored: `cd /path/to/dir`
    - create the environment with the key the packages you'll need using the command: `conda env create -f geospatial-env.yml`

3. Activate your environment
    - load miniconda module: `ml miniconda`
    - activate your environment: `source activate geospatial-env`
    - NOTE: you can manually add packages with the command options:
        - `conda install <package.name>`
        - `pip install <package.name>`

4. Set up Jupyter Notebooks (one-time)
   - enable Jupyter App to recognize your conda environment with the command: `python -m ipykernel install --user --name geospatial-env`

      
