# Jupyter notebooks

This folder is for some experiments in using [Jupyter notebooks](https://jupyter.org/) within VS Code to interact with the Graph API.

## Python environment

As we need some additional dependencies, we are going to create a new environment for these tests.

First, please follow all the setups in the main [Python README](../README.md).

Then to set uip the environment open a conda prompt in this directory and either:

`conda env create -f environment.yml`

or, to set up from scratch:

```
conda activate base

conda create --name graphjupyter python=3.11

conda activate graphjupyter

conda install -c Microsoft azure-identity

conda install pandas scikit-learn matplotlib jupyter jupyterlab sqlalchemy seaborn pip git ipykernel notebook

conda install -c conda-forge jupyter_contrib_nbextensions

conda update --all
```
Then because `msgraph-sdk` is currently only available via pip:

`pip install msgraph-sdk`

**Warning**

 Please read the Anaconda documentation about [mixing `pip` with `conda`](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#using-pip-in-an-environment) - if as you develop scripts you want to add further dependencies using conda you are advised to start with a new virtual environment
