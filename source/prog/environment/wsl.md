# Windows Subsystem for Linux (WSL)

If you use Windows, [WSL](https://docs.microsoft.com/en-us/windows/wsl/) allows you to run Linux on Windows without a virtual machine.

## Why Use WSL?

WSL provides several advantages over traditional dual-booting or virtual machines:

- **Seamless Integration**: Run Linux commands and tools directly on Windows without rebooting
- **Performance**: Better performance than traditional virtual machines for file operations
- **Resource Sharing**: Access Windows files from Linux and vice versa
- **Development Continuity**: Use familiar Windows applications alongside Linux tools
- **Easy Setup**: Simple installation compared to setting up virtual machines or dual systems

### Advantages for Machine Learning Development

WSL is particularly beneficial for machine learning projects:

- **Native Linux Tools**: Access to Linux-specific ML frameworks and libraries that may not work well on Windows
- **GPU Support**: Direct access to NVIDIA GPUs for CUDA acceleration
- **Package Management**: Use apt, conda, and pip seamlessly for managing ML dependencies
- **Docker Integration**: Run Docker containers natively for reproducible ML environments
- **Large Ecosystem**: Full access to Linux ML tools like TensorFlow, PyTorch, Jupyter, etc.
- **File System Performance**: Faster file operations compared to virtual machines, crucial for large datasets

## Installing WSL

### System Requirements

Before installing WSL, ensure your system meets these requirements:

- **Windows Version**: Windows 10 version 2004 (Build 19041) or higher, or Windows 11
- **Architecture**: 64-bit processor
- **Virtualization**: Virtualization must be enabled in BIOS/UEFI
- **Storage**: At least 2GB free disk space
- **Memory**: At least 4GB RAM (8GB recommended for development)

### Check Virtualization

1. Open Task Manager (Ctrl+Shift+Esc)
2. Go to Performance tab
3. Check if "Virtualization" shows "Enabled"

If disabled, restart your computer and enter BIOS (usually Del, F2, or F10 key) to enable virtualization.

### Installation Steps

Follow documentation from Microsoft for the latest instructions: [Install WSL](https://docs.microsoft.com/en-us/windows/wsl/install)

#### Method 1: Automatic Installation (Recommended)

1. **Open PowerShell as Administrator**:
   - Press Windows key, type "PowerShell"
   - Right-click "Windows PowerShell" and select "Run as administrator"

2. **Run the Installation Command**:
   ```powershell
   wsl --install
   ```
   This command installs WSL2 by default with Ubuntu as the default distribution.

3. **Restart Your Computer** when prompted.

4. **Complete Setup**:
   - After restart, Ubuntu will open automatically
   - Set up your Linux username and password
   - The installation is complete!

#### Method 2: Manual Installation (if automatic fails)

If the automatic method doesn't work:

1. **Enable WSL Feature**:
   ```powershell
   dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
   ```

2. **Enable Virtual Machine Platform**:
   ```powershell
   dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
   ```

3. **Restart your computer**

4. **Download and Install Linux Kernel Update Package**:
   - Visit: https://aka.ms/wsl2kernel
   - Install the package

5. **Set WSL2 as Default**:
   ```powershell
   wsl --set-default-version 2
   ```

6. **Install Ubuntu from Microsoft Store**:
   - Open Microsoft Store
   - Search for "Ubuntu" (or other distributions like "Ubuntu 22.04 LTS")
   - Click "Get" to install

### Choosing a Linux Distribution

Popular options in [Microsoft Store](https://apps.microsoft.com):

- [**Ubuntu**](https://apps.microsoft.com/detail/9pdxgncfsczv?hl=en-GB&gl=CA): Most popular, great for general development
- [**Ubuntu 22.04 LTS**](https://apps.microsoft.com/detail/9pn20msr04dw?hl=en-GB&gl=CA): Long-term support version
- [**Debian**](https://apps.microsoft.com/detail/9msvkqc78pk6?hl=en-GB&gl=CA): Lightweight and stable
- [**openSUSE**](https://apps.microsoft.com/detail/9mssk2zxxn11?hl=en-GB&gl=CA): Good for enterprise users
- [**Fedora**](https://apps.microsoft.com/detail/9n6gdm4k2hnc?hl=en-GB&gl=CA): Cutting-edge features

### Verifying Installation

After installation, verify WSL is working:

1. Open PowerShell or Command Prompt
2. Run:
   ```cmd
   wsl --list --verbose
   ```
   You should see your distribution listed with STATE: Running and VERSION: 2

3. Test Linux commands:
   ```bash
   wsl
   uname -a  # Should show Linux kernel info
   ```

### Troubleshooting Common Issues

Here are solutions to common WSL installation and setup problems:

#### Error: "WSL 2 requires an update to its kernel component"

**Solution:**
- Download and install the Linux kernel update package from [https://aka.ms/wsl2kernel](https://aka.ms/wsl2kernel)
- Restart your computer after installation

#### Error: "The requested operation could not be performed because of an invalid parameter"

**Solution:**
- Ensure virtualization is enabled in your BIOS/UEFI settings
- Run PowerShell or Command Prompt as administrator
- Check that your Windows version supports WSL2 (Windows 10 version 2004+ or Windows 11)

#### Error: "Installation failed with error 0x80070003"

**Solution:**
- Ensure you have at least 2GB of free disk space
- Try running the installation command from a different directory
- Temporarily disable antivirus software during installation

#### Network Issues in WSL

**Symptoms:** Unable to connect to internet, slow downloads, DNS resolution failures

**Solutions:**
- Restart WSL: Open PowerShell and run `wsl --shutdown`, then start WSL again
- Reset network settings: Run `wsl --shutdown` in PowerShell, then restart WSL
- Check Windows network settings and ensure they're working
- If using a VPN, try disabling it temporarily

#### WSL Not Starting or Crashing

**Solutions:**
- Update WSL: `wsl --update`
- Reset WSL: `wsl --shutdown` followed by `wsl`
- Reinstall the Linux distribution: `wsl --unregister <DistributionName>` then reinstall from Microsoft Store

#### Permission Denied Errors

**Solutions:**
- Ensure you're running commands with appropriate permissions (`sudo` for admin tasks)
- Check file permissions: `ls -la <filename>`
- If accessing Windows files from WSL, ensure the Windows drive is mounted correctly

### Updating WSL

Keep WSL updated:

```powershell
wsl --update
```

Check for distribution updates:

```bash
sudo apt update && sudo apt upgrade
```

```bash
sudo apt update && sudo apt upgrade
```

## Configuring WSL

After installation:

1. Open the Ubuntu app
2. Set username and password
3. Update the system:
   ```bash
   sudo apt update
   sudo apt upgrade
   ```

<!-- ### Setting Up for Machine Learning

For machine learning development, install essential tools:

1. **Install Python and pip**:
   ```bash
   sudo apt install python3 python3-pip
   ```

2. **Install Miniconda** (recommended for ML):
   ```bash
   wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
   bash Miniconda3-latest-Linux-x86_64.sh
   # Follow the prompts, then restart terminal
   ```

3. **Create a conda environment for ML**:
   ```bash
   conda create -n ml python=3.10
   conda activate ml
   conda install numpy pandas scikit-learn matplotlib jupyter
   ```

4. **Install CUDA Toolkit** (if you have NVIDIA GPU):
   ```bash
   # Add NVIDIA repository and install
   wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-keyring_1.0-1_all.deb
   sudo dpkg -i cuda-keyring_1.0-1_all.deb
   sudo apt-get update
   sudo apt-get install cuda-toolkit-12-2
   ``` -->
