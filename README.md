# SeaLion Mission Workspace (Kasm Image)

## Introduction

This repo provides a workspace for the SeaLion team to work on GNU Radio, Flight Software, & Ground Station based on the [Ansible based template for KASM Ubuntu Focal Images](https://github.com/j-simmons-phd/kasm-core-focal-template) template provided by @j-simmons-phd.  The workspace is configured with the following software:

- git cli
- [Keychain](https://www.funtoo.org/Keychain)
- Chrome
- Python 3.8.x (part of the image template) with the following packages (not part of the image template)
    - pip
    - [JupyterLab](https://jupyter.org/)
    - [Jupyter Notebook](https://jupyter.org/)
    - [Voilà](https://voila.readthedocs.io/en/stable/index.html)
    - [Pint](https://pint.readthedocs.io/en/stable/)
- VS Code with the following extensions (note, auto-updates are disabled)
    - [Python extension by Microsoft](https://marketplace.visualstudio.com/items?itemName=ms-python.python)

## Requirements

1. Docker
2. Git
3. A Bash terminal (standard terminal environment for *nix and macOS).

NOTE: To Windows 10 users: Windows Command Prompt will not satisfy this dependency. We recommend installing [Ubuntu on WSL2 for Windows 10](https://ubuntu.com/tutorials/install-ubuntu-on-wsl2-on-windows-10).

## How to Use this Repo

1. Clone this repo and change directory into `kasm-sealion-workspace`.
1. Run `docker-compose build` (Note: Linux users may need to prepend this command with `sudo`) to build the workspace image.  Note, debugging build errors is easier when you switch the docker-compose [progress mode](https://docs.docker.com/engine/reference/commandline/compose_build/#options) to plain (`docker-compose build --progress plain`).  Alternatively, you can pull the published version (when available) by calling `docker-compose pull`.
1. Be sure to add a repository secret named `GHCR_AUTH_TOKEN` containing a valid token value with packages write access to properly enable GitHub CI.

If you encounter Ansible errors, revise the requirements and playbook files as necessary.  

## Using the image locally

Once built, the image can be pushed into the Kasm server per Kasm documentation or it can be run locally on port 6901 using docker-compose.

- **Starting the image locally:** Run `docker-compose up -d`
- **Stopping the image locally:** Run `docker-compose down`

When running locally, the workspace can be accessed at https://localhost:6901 with
- **User:** `kasm_user`
- **Passwordd:** `password`
