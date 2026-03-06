# Visual Studio Code (VSCode)

VSCode is a free code editor developed by Microsoft, powerful and easy to use.

## Installing VSCode

1. Visit the [VSCode official website](https://code.visualstudio.com/)
2. Download the version suitable for your operating system
3. Run the installer and follow the prompts to complete the installation

## Why Configure a Good Development Environment?

A well-configured development environment can significantly improve your programming efficiency and learning experience. Here's why it's important:

- **Productivity Boost**: Proper extensions and settings automate repetitive tasks, allowing you to focus on coding logic rather than manual operations.
- **Error Prevention**: Linters and formatters catch potential bugs and enforce consistent code style before you run the code.
- **Learning Acceleration**: Integrated tools provide instant feedback, helping you understand concepts faster and correct mistakes early.
- **Collaboration Ready**: Consistent configurations make it easier to work with others and share code across different machines.
- **Future-Proofing**: A good setup adapts as your skills grow, supporting more complex projects and languages.

## Basic Configuration

After installation, open VSCode:

### 1. Customize the Interface

A comfortable interface makes coding more enjoyable:

1. **Change Theme**:
   - Press `Ctrl+K Ctrl+T` (Windows/Linux) or `Cmd+K Cmd+T` (Mac)
   - Choose a theme like "Dark Modern" or "Light Modern", I prefer "One Dark Pro".
   - You can also install more themes from the marketplace (Extensions sidebar)

2. **Adjust Font and Size**:
   - Go to left bottom corner and click the gear icon to open Settings
   - Search for "font"
   - Set "Editor: Font Family" to `'Fira Code', 'Consolas', monospace` (Fira Code has ligatures for better readability)
   - Set "Editor: Font Size" to 14 or 16 for better visibility

3. **Customize Layout**:
   - Drag panels to rearrange (Explorer, Terminal, etc.)
   - Use View menu to show/hide panels

4. **Login to Sync Settings**:
   - Click on the Accounts icon (bottom left)
   - Turn on Settings Sync to keep your settings across devices

### 2. Install and Configure Extensions

Extensions add powerful features to VSCode:

1. **Essential Extensions**:
   - For Python development:
     - **Python** by Microsoft: For Python development
     - **Pylance**: Enhanced Python language support
     - **Jupyter**: For Jupyter notebooks
   - For web development:
     - **ESLint**: JavaScript/TypeScript linting
     - **Live Server**: Launch a local development server with live reload
     - **HTML CSS Support**: Auto-completion for HTML/CSS 
   - For C/C++ and Fortran development:
     - **C/C++** by Microsoft: For C/C++ development
     - **Modern Fortran**: For Fortran language support
     - **Cmake Tools**: For CMake project support
   - For remote development:
     - **Remote - WSL**: Develop in Windows Subsystem for Linux
     - **Remote - SSH**: Develop on remote machines via SSH
   - For AI assistance:
     - **GitHub Copilot Chat**: AI-powered code completion

2. **Install Extensions**:
   - Click the Extensions icon in the sidebar (or `Ctrl+Shift+X`)
   - Search and install the extensions above

### 3. Editor Settings

Configure the code editing experience:

1. **Auto Save**:
   - In Settings, search for "auto save"
   - Set "Files: Auto Save" to "afterDelay" or "onFocusChange"

2. **Formatting**:
   - Enable "Editor: Format On Save" and "Editor: Format On Paste"
   - Set "Editor: Tab Size" to 4 (or 2 for Fortran)
   - Enable "Editor: Insert Spaces" instead of tabs
   :::{note}
   The indent settings is **VERY IMPORTANT for Python**
   :::

3. **Minimap and Breadcrumbs**:
   - Enable "Editor: Minimap" for code overview
   - Enable "Breadcrumbs" for navigation

### 4. Terminal Integration

VSCode has a built-in terminal:

1. **Open Terminal**: Terminal > New Terminal
2. **Configure Shell**:
   - In Settings, search for "terminal"
   - Set default shell if needed (PowerShell, bash, etc.)

### 5. Settings Sync

Keep your settings across devices:

1. Go to Accounts (bottom left) > Turn on Settings Sync
2. Sign in with Microsoft/GitHub account
3. Choose what to sync: settings, extensions, etc.

This configuration provides a solid foundation for programming. As you learn more languages, you can add specific extensions and settings for each one.