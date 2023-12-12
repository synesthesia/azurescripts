# Python example of using MS Graph with per-user authentication

## Introduction

This folder contains the Microsoft example code for interacting with the MS Graph from Python using per-user authentication.

With this form of authentication the script is limited to accessing data relating top the logged-in user.

## Configuration

Follow all steps in the [top-level README](../../README.md) and the [Python README](../README.md).

Ensure that you have an Azure AD application registration for per-user access to the MS Graph API as documented in the top-level [README](../../README.md).

In this directory copy the file `config.sample.cfg` to `config.cfg` and populate with the Client ID and Tenant Id for the application registration.
> **NOTE**
The `config.cfg` file is ignored by Git so you don't accidentally check secrets into the repository.

To run the code:
- in your shell with active conda environment, change into this directory
- open VS Code (`code .`)
- in VS code open `main.py`
- run the code in the file using the run button (see [VS Code documentation for Python](https://code.visualstudio.com/docs/languages/python))
- OR at the conda prompt in this directory just run `python main.py`

## Understanding the code

If you follow the [Microsoft tutorial steps](https://learn.microsoft.com/en-us/graph/tutorials/python?tabs=aad&tutorial-step=2) you will see how the code has been built up
