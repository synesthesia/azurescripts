# Python scripts

##  Introduction


THese instructions assume you are running in Windows.


## Prerequisites

- follow the general tool setup instructions in the main [README](../README.md) 


## Install Python distribution

### Installation

We use the [miniconda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/windows.html) distribution as it has some advantages over a raw Python installation

- download the latest miniconda installer
- follow the instructions

### Setup virtual environment for these scripts

- open conda prompt (search for "conda prompt")
- `conda create --name myenv`  
    (you probably want to call it something other than `myenv`, but we'll use that in these docs)
- `conda activate myenv`  
- `conda install -c Microsoft azure-identity`
- `pip install msgraph-sdk`
 
    > **Warning**
    Please read the Anaconda documentation about [mixing `pip` with `conda`](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#using-pip-in-an-environment) - if as you develop scripts you want to add further dependencies using conda you are advised to start with a new virtual environment

### Use and extend example scripts

The example scripts are in subdirectories below this one.

In your conda prompt, with the correct environment activated, change directory to the script, and follow any coinfiguration instructions in the README in that folder:

- [Microsoft MS Graph per-user example](./user-auth/README.md)
- [Microsoft MS Graph applicaiton permissions example](./app-auth/README.md)
