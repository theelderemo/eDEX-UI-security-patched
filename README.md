

<p align="center">
  <br>
  <img alt="Logo" src="media/logo.png">
  <br>
  <br><br><br>
</p>

eDEX-UI is a fullscreen, cross-platform terminal emulator and system monitor that looks and feels like a sci-fi computer interface.

This is a community-driven fork of the original eDEX-UI, which was archived in October 2021. This fork aims to revive the project, apply security patches, and continue its development.

# 🛡️ Security Fix Information
- CVE: Not assigned (discovered post-archive)
- Severity: Critical
- Impact: Remote Command Execution via WebSocket hijacking

## Vulnerability Details
The original eDEX-UI contained a security vulnerability where malicious websites could connect to the internal terminal control WebSocket and execute arbitrary shell commands on the user's system.

## The Fix
This fork implements proper origin validation for WebSocket connections:
- Only accepts connections from the local Electron application (file:// protocol)
- Rejects all web-based connection attempts (http://, https://)
- Logs rejected connection attempts for security monitoring
- Fixed in: `src/classes/terminal.class.js`

---

# ⚠️ Important Notes

This is a fork of the original eDEX-UI, which is no longer actively maintained. While this fork addresses a critical security vulnerability, it should be considered a work in progress. Community contributions are welcome to help revive and improve the project. Please use this software "as-is" and take appropriate security measures when running any terminal emulator with network capabilities.


# Installation

## Pre-built Binaries

⚠️ **Note: Pre-built binaries from the original repository contain the vulnerability. Only use builds from this fork or build from source.**

Head over to releases and download the correct prebuild

## Building from Source (Recommended for Security)

This fork has been updated with modern versions of all dependencies. Following these steps will ensure you have a working, patched version with up-to-date components.

### 1. Environment Setup (Linux/Ubuntu)

The build process requires modern versions of Node.js and Python.

-   **Install `nvm` (Node Version Manager):** This is the best way to manage Node.js versions.
    
    
    ```
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
    source ~/.bashrc
    
    ```
    
-   **Install and Use Node.js v20 LTS:** This project now requires Node.js v20 LTS for the latest Electron version.
    
    
    
    ```
    nvm install 20
    nvm use 20
    
    ```
    
-   **Install Python 3:** The build scripts require Python 3 (3.8 or later recommended).
    
    
    ```
    sudo apt update
    sudo apt install -y python3 python3-pip
    
    ```
    
-   **Install Build Tools:**
    
    
    
    ```
    sudo apt install -y build-essential git
    
    ```
    

### 2. Clone and Build the Application

Now, with the correct environment set up, you can clone and build the project.

-   **Clone  repository:**
    
    
    ```
    git clone https://github.com/theelderemo/eDEX-UI-security-patched.git
    cd eDEX-UI-security-patched
    
    ```
    
-   **Install dependencies:**
        
    ```
    npm run install-linux
    
    ```
    
-   **Build the binary:**
        
    ```
    npm run build-linux
    
    ```
    

After the build completes, you will find the installable `.AppImage` and `.deb` files in the `dist/` directory.


# Contributing

Community contributions are highly encouraged! If you'd like to help, please feel free to:
-   **Report bugs:** Open an issue to report any bugs you find.
-   **Suggest features:** Open an issue to suggest new features or enhancements.
-   **Submit pull requests:** If you've made a change you'd like to contribute, please submit a pull request.

# Original Credits

eDEX-UI was created by [GitSquared (Gabriel Saillard)](https://github.com/GitSquared).

Sound effects by [IceWolf](https://soundcloud.com/iamicewolf).

Globe visualization by [Rob "Arscan" Scanlon](https://github.com/arscan).

# Security Fork Maintainer

This security-patched fork is maintained by [theelderemo](https://github.com/theelderemo).

If you discover any additional security issues, please report them by opening an issue in this repository.

# License

Licensed under the [GPLv3.0](https://github.com/GitSquared/edex-ui/blob/master/LICENSE), the same as the original project.
