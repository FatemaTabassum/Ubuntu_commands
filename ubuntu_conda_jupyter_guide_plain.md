# 🖥️ System & Environment Information

### Check Ubuntu version
```
lsb_release -a
```

### Verify kernel architecture
```
dpkg --print-architecture
```

### Get CPU architecture details
```
lscpu
```

---

# 🐍 Conda & Python

### List conda environments with Python version
```
conda env list | grep -v "^$\|#" | awk '{print $1;}' | xargs -I{} -d "\n" sh -c 'printf "Env: {}\t"; conda list -n {} | grep "^python\s";'
```

### Common conda commands
```
# List all environments
conda info --envs 

# Create new environment
conda create --name envname

# Remove environment
conda remove --name envname --all

# Clone environment
conda create --name clone_envname --clone envname
```

### Install specific Python version in an environment
```
conda activate my_env
conda install python=3.6
```

### Update/upgrade conda
```
conda update --all
conda install -n base conda=23.11.0
```

### Channel configuration
```
# Remove conda-forge if slowing things down
conda config --show-sources
conda config --remove-key channels

# Set channel priority to flexible
conda config --set channel_priority flexible
conda config --show-sources
```

---

# 📓 Jupyter & Virtual Environments

### Add virtual environment to Jupyter
```
# Activate your environment
conda activate my_env

# Install kernel
pip install --user ipykernel
python -m ipykernel install --user --name=myenv

# Install Jupyter inside env if needed
conda install jupyter
```

### Open Jupyter Notebook in a specific directory
```
jupyter notebook --notebook-dir /data/paperswithcode_fatema/linevd_graph_dataset
```

### Run Jupyter Notebook in a conda environment
```
conda activate myenv
conda install numpy ipykernel
python -m ipykernel install --user --name=myenv
```

### Fix nbconvert / internal server errors
```
pip install --upgrade nbconvert
```

---

# 📦 Package Installation

### Install custom package (with setup.py)
```
pip install -e .
```

---

# 🛠️ Anaconda Installation & Management

### Clean install Anaconda
```
# Remove old installation
rm -rf ~/anaconda3
rm -rf ~/.condarc ~/.conda ~/.continuum
```

Follow installation guide:  
- [PhoenixNAP](https://phoenixnap.com/kb/how-to-install-anaconda-ubuntu-18-04-or-20-04)  
- [Medium: Installing Anaconda Navigator](https://thecraftman.medium.com/installing-anaconda-navigator-on-linux-ubuntu-18-04-d805d5a0f71a)  

Steps:
```
cd /tmp
curl -O https://repo.anaconda.com/archive/Anaconda3-2022.05-Linux-x86_64.sh
sha256sum Anaconda3-2022.05-Linux-x86_64.sh
bash Anaconda3-2022.05-Linux-x86_64.sh
```

### Post-install commands
```
conda search python
conda search --full-name python
conda update python
conda install python=3.9
conda config --set auto_activate_base false
```

⚠️ If `anaconda-navigator` stops working after disabling auto_activate_base, revert to `true`.

---

# 📂 Environment Export/Import

### Export environment to YAML
```
conda env export > environment_droplet.yml
```

### Create environment from YAML
```
conda env create -f environment.yml
```

### Update environment from YAML
```
conda activate myenv
conda env update --file local.yml --prune
```

---

# 🚀 CUDA & Drivers

- [Install CUDA on Ubuntu](https://www.cherryservers.com/blog/install-cuda-ubuntu)  
- [Fix unmet dependencies with CUDA](https://forums.developer.nvidia.com/t/unmet-dependencies-nvidia-dkms-535-package-conflict-breaks-ubuntu-22-04-install/265788)  

---

# 📝 VS Code

- [Linuxiac: Install VS Code Ubuntu 22.04](https://linuxiac.com/install-visual-studio-code-on-ubuntu-22-04/)  
- [Medium: Install VS Code Ubuntu 22.04](https://medium.com/@GRajeevan/how-to-install-visual-studio-code-on-ubuntu-22-04-bfc87b52cc40)  

---

# 📊 Weights & Biases (W&B)

- [W&B Guide](https://docs.wandb.ai/guides/track)

```
conda env create --name envname --file=environments.yml
```

---
