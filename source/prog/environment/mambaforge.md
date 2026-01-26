# Python Environment: Mambaforge

Mambaforge is a powerful package management system that provides fast and reliable installation of scientific packages and their dependencies.

## What is Mambaforge?

Mambaforge is a distribution of the conda package manager that uses the fast mamba solver instead of the traditional conda solver. It includes:

- **Mamba**: A fast, cross-platform package manager
- **Conda**: The classic conda package manager
- **Python**: A Python interpreter
- **Essential packages**: numpy, pandas, scipy, etc.

## Why Choose Mambaforge?

- **Speed**: Mamba is significantly faster than conda (often 10-100x faster)
- **Reliability**: Better dependency resolution
- **Cross-platform**: Works on Windows, macOS, and Linux
- **Large ecosystem**: Access to millions of packages via conda-forge
- **Environment management**: Create isolated environments for different projects

## Installation

### Download Mambaforge

1. Visit the official download page: [https://github.com/conda-forge/miniforge#mambaforge](https://github.com/conda-forge/miniforge#mambaforge)

2. Choose the installer for your operating system:
   - **Windows**: Download `Mambaforge-Windows-x86_64.exe`
   - **macOS**: Download `Mambaforge-MacOSX-x86_64.sh` (Intel) or `Mambaforge-MacOSX-arm64.sh` (Apple Silicon)
   - **Linux (WSL)**: Download `Mambaforge-Linux-x86_64.sh`

### Install on Windows

1. Run the downloaded `.exe` file
2. Follow the installation wizard
3. Choose installation location (recommended: `C:\Users\<username>\mambaforge`)
4. Check "Add Mambaforge to PATH" (optional, but recommended for beginners)
5. Complete installation

:::{note}
I recommend using Windows Subsystem for Linux (WSL) for a more Unix-like experience when working with Mambaforge on Windows. Please see the [WSL setup guide](wsl.md) for more details.
:::

### Install on macOS/Linux (including WSL)

1. Open Terminal
2. Navigate to download directory:
   ```bash
   cd path/to/downloads
   ```

3. Run the installer script:
   ```bash
   sh Mambaforge-*.sh
   ```

4. Follow the prompts:
   - Press Enter to read the license
   - Type `yes` to accept
   - Choose installation location (default is recommended)
   - Type `yes` to initialize Mambaforge

5. Restart your terminal or run:
   ```bash
   exec $SHELL
   ```

### Verify Installation

After installation, verify it works:

```bash
mamba --version
conda --version
```

You should see version numbers for both mamba and conda.

## Basic Usage

### Understanding Environment Isolation

One of Mambaforge's most powerful features is **environment isolation**. This is crucial for beginners to understand and use properly.

#### Why Do You Need Environment Isolation?

Imagine you're working on multiple projects:

- **Project A**: Uses TensorFlow 2.10 and Python 3.9
- **Project B**: Uses PyTorch 2.0 and Python 3.10
- **Project C**: Uses scikit-learn for simple machine learning

**Without environments:**
- Installing different versions of the same package can cause conflicts
- One project's requirements might break another project
- You can't easily share or reproduce your setup
- System Python gets cluttered with packages

**With environments:**
- Each project has its own isolated space
- Different projects can use different package versions
- Easy to switch between projects
- Clean, reproducible setups

#### How Environment Isolation Works

Each conda environment is like a separate Python installation:

- **Separate package directories**: Packages are installed in isolated locations
- **Independent Python versions**: Each environment can have different Python versions
- **Isolated dependencies**: Package conflicts are contained within each environment
- **Clean separation**: Removing an environment doesn't affect others

#### Real-World Examples

```bash
# Data Science Environment
mamba create -n data-science python=3.9
mamba activate data-science
mamba install jupyter pandas numpy matplotlib seaborn scikit-learn

# Deep Learning Environment
mamba create -n deep-learning python=3.10
mamba activate deep-learning
mamba install tensorflow pytorch jupyter

# Computer Vision Environment
mamba create -n cv python=3.11
mamba activate cv
mamba install opencv pillow scikit-image
```


#### Environment Management Best Practices

1. **Use descriptive names**: `mamba create -n web-dev-2024 python=3.11`
2. **Keep environments focused**: One environment per project or purpose
3. **Document your environments**: Save environment specifications
4. **Regular cleanup**: Remove unused environments
5. **Version control environments**: Include `environment.yml` in your projects

#### Switching Between Environments

```bash
# Check current environment (shows * next to active)
mamba env list

# Activate an environment
mamba activate my-project

# Check which Python is being used
which python
python --version

# Deactivate current environment
mamba deactivate

# Deactivate all environments (back to base)
mamba deactivate
```

#### Sharing and Reproducing Environments

**Export environment specification:**
```bash
mamba activate my-project
mamba env export > environment.yml
```

**Create environment from specification:**
```bash
mamba env create -f environment.yml
```

**Example environment.yml:**
```yaml
name: my-project
channels:
  - conda-forge
  - defaults
dependencies:
  - python=3.10
  - numpy
  - pandas
  - matplotlib
  - scikit-learn
```

### Update Mambaforge

Keep your installation updated:

```bash
mamba update mamba
mamba update conda
```

### Create a New Environment

Create isolated environments for different projects:

```bash
# Create a new environment with Python 3.10
mamba create -n myenv python=3.10

# Activate the environment
mamba activate myenv

# Deactivate
mamba deactivate
```

### Install Packages

Install packages in your environment:

```bash
# Install a single package
mamba install numpy

# Install multiple packages
mamba install numpy pandas matplotlib

# Install from a specific channel
mamba install -c conda-forge tensorflow
```

### List Environments and Packages

```bash
# List all environments
mamba env list

# List packages in current environment
mamba list

# List packages in specific environment
mamba list -n myenv
```

### Remove Environments and Packages

```bash
# Remove a package
mamba remove package_name

# Remove an entire environment
mamba env remove -n myenv
```

### Using Jupyter Notebook/Lab

After installation:

```bash
# Activate your ML environment
mamba activate ml

# Start JupyterLab
jupyter lab

# Or start Jupyter Notebook
jupyter notebook
```

This will open a browser window where you can create and run notebooks.

## Environment Management Best Practices

1. **Use environments liberally**: Create separate environments for different projects
2. **Keep environments small**: Only install what you need
3. **Update regularly**: Keep packages updated for security and performance
4. **Export environment**: Save environment specifications for reproducibility

```bash
# Export environment to file
mamba env export > environment.yml

# Create environment from file
mamba env create -f environment.yml
```

## Getting Help

- Official documentation: [https://mamba.readthedocs.io/](https://mamba.readthedocs.io/)
- Conda documentation: [https://docs.conda.io/](https://docs.conda.io/)
- Community forums: [https://github.com/mamba-org/mamba](https://github.com/mamba-org/mamba)