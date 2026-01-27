# Linux Basics

## Introduction

If you're transitioning from Windows to Linux for coding and scientific computing, this guide focuses on the essential aspects you'll need. Linux excels in these areas due to its powerful command-line tools, package management, and efficiency for handling large datasets and computations. We'll cover the core concepts and commands that will help you get productive quickly.

## Why Linux for Coding and Scientific Computing?

Linux provides:
- **Powerful Shell**: Automate tasks, run scripts, and process data efficiently.
- **Package Managers**: Easily install programming languages, libraries, and tools.
- **File System**: Hierarchical structure ideal for organizing code and data.
- **Stability**: Reliable for long-running computations and remote work.

## Basic Linux Operating Logic

### Kernel and User Space

- **Kernel**: Manages hardware and resources. As a coder, you interact with it indirectly through system calls.
- **User Space**: Where your programs run. Includes the Shell for executing commands.

### Shell and Command Line

The Shell (e.g., Bash) is your primary interface for coding:
- Run scripts, compilers, and analysis tools.
- Automate workflows with scripts.
- Connect to remote servers (e.g., HPC clusters) via SSH.

Key: Everything in scientific computing—data processing, model training—can be scripted and run from the command line.

**Example: Simple Shell Script for Data Processing**
```bash
#!/bin/bash
# Process CSV data: filter valid rows and compute average
echo "Processing data.csv..."
grep "^[0-9]" data.csv | awk -F',' '{sum+=$2; count++} END {print "Average:", sum/count}' > results.txt
echo "Results saved to results.txt"
```
Run it with: `sh ./process.sh`

## File Management for Coders

### Directory Structure

Organize your projects logically:
- `/home/user`: **Your workspace** (store code, data, results).
- `/usr/bin`: System binaries (compilers, interpreters).
- `/tmp`: Temporary files for computations.

Use absolute/relative paths consistently in scripts.

### File Permissions

Critical for shared projects or servers:
- Set executable permissions on scripts: `chmod +x script.sh`
- Understand ownership to avoid access issues with data files.

### Superuser Access with sudo

In Linux, most users operate with limited permissions to prevent accidental system damage. However, system-level tasks like installing software or modifying system files require root (administrator) privileges. `sudo` (Superuser DO) allows you to run commands as root temporarily.

**Why Important on Personal Computers:**
- **Security**: Avoids logging in as root, reducing risk of mistakes that could break your system.
- **Convenience**: Grants elevated access only when needed, without switching users.
- **Best Practice**: Essential for package installation, system configuration, and hardware management in coding/scientific setups.

**Basic Usage:**
- Prefix any command with `sudo`: `sudo apt update`
- You'll be prompted for your password (not root's).
- Examples:
  - Install packages: `sudo apt install python3-dev`
  - Edit and write system files: `sudo nano /etc/hosts`
  - Change permissions on system dirs: `sudo chmod 755 /usr/local/bin`

**Advanced Tips:**
- Run multiple commands: `sudo bash -c "apt update && apt upgrade"`
- Edit sudoers file (carefully): `sudo visudo` to add users or change timeouts.
- Avoid `sudo` for user files; use it only for system operations.

For coders: Use `sudo` when installing compilers, libraries, or configuring development tools, but keep your coding projects in user directories.

- Absolute: `/home/user/project/data.csv`
- Relative: `./data/input.txt` (from project root)
- Use `cd`, `pwd` to navigate efficiently.

## Essential Commands for Coding and Computing

### File and Directory Operations

| Task | Command | Example | Notes |
|------|---------|---------|-------|
| List files | `ls -la` | `ls -la ~/project` | Shows hidden files, permissions; output like: `-rw-r--r-- 1 user group 1024 Jan 27 data.csv` |
| Navigate | `cd` | `cd ~/project/src` | Use `cd -` to go back; `cd ..` up one level |
| Print working directory | `pwd` | `pwd` | Shows current full path; useful in scripts: `echo "Current dir: $(pwd)"` |
| Create dirs | `mkdir -p` | `mkdir -p data/results` | Creates nested directories; `mkdir models experiments` for multiple |
| Copy files | `cp -r` | `cp -r src/ backup/` | Recursive for directories; `cp *.py backup/` copies all Python files |
| Move/rename | `mv` | `mv old.py new.py` | Also for renaming; `mv file.txt /tmp/` moves to temp |
| Remove files | `rm` | `rm temp.txt` | Deletes files; `rm -i *.log` prompts before deletion |
| Remove directories | `rm -r` | `rm -r old_project/` | Recursive delete; `rm -rf cache/` forces without prompts (dangerous!) |

**Additional Examples:**
- Check disk usage: `du -h ~/project` (shows folder sizes)
- Find files: `find . -name "*.py" -type f` (locate Python files)
- Create symbolic link: `ln -s /path/to/target link_name` (shortcut to files/dirs)

### Text Processing and Data Handling

Scientific computing involves lots of text/data manipulation:

| Task | Command | Example | Notes |
|------|---------|---------|-------|
| View files | `head/tail` | `head -n 10 data.csv` | Preview large files; `tail -f log.txt` for live logs |
| Search text | `grep` | `grep "error" log.txt` | Find patterns in code/logs; `grep -r "import" .` searches recursively |
| Edit files | `nano/vim` | `nano script.py` | Quick edits; learn Vim for power |
| Process data | `awk/sed` | `awk '{sum+=$1} END {print sum}' data.txt` | Simple data analysis; `sed 's/old/new/g' file.txt` replaces text |

**Examples:**
- Filter CSV rows: `grep "^[^#]" data.csv | head -20` (skip comments, show first 20)
- Count lines: `wc -l *.py` (count lines in Python files)
- Extract columns: `cut -d',' -f2 data.csv | sort | uniq -c` (count unique values in column 2)

### Running Code and Processes

| Task | Command | Example | Notes |
|------|---------|---------|-------|
| Run script | `./script.sh` | `python main.py` | Execute Python/R scripts; `./train.sh` for custom scripts |
| Background jobs | `&` | `python train.py &` | Run long computations in background; use `jobs` to list |
| Check processes | `ps/top` | `top` | Monitor CPU/memory usage; `ps aux | grep python` finds Python processes |
| Kill process | `kill` | `kill %1` | Stop runaway jobs; `kill -9 PID` forces kill |

**Examples:**
- Run with arguments: `python script.py --input data.csv --output results.txt`
- Monitor GPU: `nvidia-smi` (if NVIDIA GPU installed)
- Batch run: `for file in *.py; do python $file; done` (run all Python scripts in directory)

### Package Management

Install tools for coding and computing:

- **System Packages**: `apt/yum` for compilers, libraries.
  - Example: `sudo apt install build-essential python3-dev`
- **Language-Specific**: Use `pip` (Python), `install.packages` (R), or `conda` for environments.
  - Conda is great for scientific computing: `conda install numpy scipy`
- **Version Control**: `git` for code management.
  - `git clone`, `git commit`, etc.

**Examples:**
- Install scientific stack: `conda install -c conda-forge numpy pandas matplotlib scikit-learn`
- Create environment: `conda create -n myenv python=3.9 && conda activate myenv`
- Install from requirements: `pip install -r requirements.txt`
- Update all: `conda update --all` or `pip list --outdated`

## Advanced Tips for Coders

1. **Shell Scripting**: Automate repetitive tasks.
   - Example: Write a script to preprocess data and run analysis.
   ```bash
   #!/bin/bash
   # Backup and run analysis
   cp data.csv backup/
   python analyze.py data.csv > results.log 2>&1
   echo "Analysis complete. Check results.log"
   ```

2. **Pipes and Redirection**: Chain commands for data pipelines.
   - `cat data.txt | grep valid | sort > clean.txt`
   - Examples: `ls *.csv | xargs wc -l` (count lines in all CSVs); `python -c "print('hello')" | tee output.txt` (save and display output)

3. **Environment Variables**: Set paths for tools (e.g., `export PATH=$PATH:/usr/local/bin`)
   - Example: `export PYTHONPATH=$PYTHONPATH:~/my_modules` for custom Python modules

4. **Virtual Environments**: Isolate projects with `venv` or `conda env`.
   - Example: `python -m venv myenv && source myenv/bin/activate`

5. **Remote Work**: Use `ssh` and `scp` for cloud/HPC computing.
   - Example: `ssh user@server.com` to connect; `scp results.txt user@server.com:/data/` to upload

6. **File Compression**: `tar/gzip` for handling large datasets.
   - Example: `tar -czf archive.tar.gz data/` compress; `tar -xzf archive.tar.gz` extract

## Common Pitfalls and Solutions

- **Permission Denied**: Use `sudo` for system installs (see Superuser Access section); check file permissions with `ls -l`.
- **Path Issues**: Always use absolute paths in scripts to avoid ambiguity.
- **Memory/CPU Limits**: Monitor with `htop` or `top`; optimize code or use background jobs.
- **Dependencies**: Use requirements.txt or environment.yml for reproducibility; avoid mixing package managers.

## Summary

Mastering Linux basics will boost your coding and scientific computing productivity. Focus on the command line, package management, and file handling. Practice by setting up a project, installing tools, and running computations. For deeper learning, explore Shell scripting and tools like Jupyter for interactive computing.

:::{admonition} Next Steps
- Set up a development environment with VSCode + WSL or native Linux.
- Learn Python for data science; use Conda/Mamba for package management.
- Experiment with HPC basics if doing large-scale computing.
:::