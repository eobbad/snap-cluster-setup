# evals-for-autoformalization

## Compute

### Sherlock
Quick Start:

- main website: https://www.sherlock.stanford.edu/docs/#what-to-expect
- Join their sherlock slack & follow their instructions (basically join the two channels they recommend by searching the channels in the slack app, they don't have a workspace it seems): https://www.sherlock.stanford.edu/docs/#user-community
- Support email, read this: https://www.sherlock.stanford.edu/docs/#email-recommended


### Set up Project in Sherlock

High level plan
1. ssh into the login/head node ```ssh your_sunetid@login.sherlock.stanford.edu``` e.g., ```brando9@login.sherlock.stanford.edu```
2. git clone the repo so it's accessible in any node when using the slurm resource manger
3. set up the conda env so it's accesible in any node and learn to use pip install -e . 
4. test the code by running with interactive job (srun) and background jon (sbatch)
5. modify the code, test again, and learn to push to repo
6. learn to vscode into sherlcok (either ssh or push file on save)
7. then do new experiment repeat
8. and request an optional pull rquest

note: you should understand (roughly) what everything means in here to be effective.
Google, gpt4/claude it etc. 
Tips:
- use `man` to understand bash command or if you want to chat with it use LLMs/GPT4/Claude.

#### 1 Login to Login/head node
```bash
ssh your_sunetid@login.sherlock.stanford.edu
```


## Tutorial on setting up a python project
1. create the `setup.py` file
2. Make sure your setup.py file has the following
```python
    package_dir={'': 'src'},
    packages=find_packages('src'),
```
so that `pip install -e .` knows were the python modules are when installing the python library. 
Anything outside `src`` won't be found for this libraries pip -e install.
Read the comments for those lines in `setup.py`` to understand it if you wish and refs.
3. Now you can do `pip install -e .` or `pip install -e $HOME/evals-for-autoformalization` (assuming you have your python env/conda env activated).

Now you should be able to import statements for this library in the expected way! e.g.,
```python
# TODO
```

## Python Envs with conda & using pip instlal -e <path>

```bash
# This script demonstrates the use of conda for managing Python environments and pip for installing Python packages.
# Conda is an open-source package management and environment management system.

# 1. List all the available conda environments on your system.
# The command 'conda info -e' will list all the environments available.
conda info -e

# 2. Update conda to the latest version.
# It's good practice to keep conda updated to the latest version to avoid any compatibility issues.
conda update --all

# 3. Upgrade pip to the latest version.
# Pip is the package installer for Python. Upgrading it ensures that you can install packages without issues.
pip install --upgrade pip

# 4. Create a new conda environment.
# 'conda create -n maf python=3.10' creates a new environment named 'maf' with Python version 3.10 installed.
# '-n maf' specifies the name of the environment, and 'python=3.10' specifies the Python version.
conda create -n af_evals python=3.10

# 5. Activate the newly created conda environment.
# 'conda activate maf' activates the 'maf' environment. Once activated, any Python packages installed will be specific to this environment.
conda activate af_evals

# To deactivate the current environment and return to the base environment, you can use:
# conda deactivate

# If you want to remove the 'maf' environment completely, you can use:
# conda remove --name af_evals --all

# 6. Install Python packages using pip in editable mode.
# 'pip install -e <path>' installs a package in 'editable' mode, meaning changes to the source files will immediately affect the installed package without needing a reinstall.
# Replace '<path>' with the path to the directory containing the 'setup.py' file of the package you want to install.
# pip install -e $HOME/evals-for-autoformalization
pip install -e .

# Test pytorch install with GPU
python -c "import torch; print(torch.version.cuda); print((torch.randn(2, 4).cuda() @ torch.randn(4, 1).cuda()))"

# Note: It's crucial to activate the correct conda environment before using pip install to avoid installing packages in the wrong environment.
```
ref: https://chat.openai.com/c/375d5d26-7602-4888-9ef5-9f92359330dc

## Basic Git
TODO
```bash
cd /afs/cs.stanford.edu/u/brando9/
git clone git@github.com:brando90/massive-autoformalization-maf.git
ln -s /afs/cs.stanford.edu/u/brando9/massive-autoformalization-maf $HOME/massive-autoformalization-maf
pip install -e ~/massive-autoformalization-maf
#pip uninstall ~/massive-autoformalization-maf
cd ~/massive-autoformalization-maf
```

## Basic Docker

## Basic Cluster use (Snap)
