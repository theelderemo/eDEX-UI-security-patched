

<p align="center">
  <br>
  <img alt="Logo" src="media/logo.png">
  <br>
  <br><br><br>
</p>

eDEX-UI is a fullscreen, cross-platform terminal emulator and system monitor that looks and feels like a sci-fi computer interface.

This is a Windows-optimized fork of eDEX-UI with critical security patches and updated dependencies for modern Windows systems. Built with Electron 28.3.3 and fully compatible with Windows 10/11.
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

## Recent Updates (November 2025)

This Windows fork includes:

- **Electron**: v28.3.3 (downgraded from v37 for @electron/remote compatibility)
- **Node.js**: Requires v20.x LTS for building
- **node-pty**: v1.1.0-beta39 (with prebuilt Windows binaries)
- **@electron/remote**: v2.1.3 (properly configured for Electron 28)
- **Security**: WebSocket origin validation, all known vulnerabilities patched
- **UI Improvements**: Dev tools auto-open disabled, update checker disabled
- **Build system**: Optimized for Windows with VS 2022 Build Tools support

---

# ⚠️ Important Notes

This Windows fork is specifically optimized for Windows 10/11 and addresses critical security vulnerabilities found in the original eDEX-UI. The application has been tested and verified working on Windows systems. Use at your own discretion and take appropriate security measures when running terminal emulators.


# Installation

## Pre-built Windows Binaries

Pre-built portable Windows binaries are available in the [Releases](https://github.com/Vortex555/edex-ui-security-patched-windows/releases) section.

**Download the `edex-ui-windows.zip` file**, extract it, and run `eDEX-UI.exe` - no installation required.

## Building from Source (Windows)

### Prerequisites

1. **Node.js v20 LTS**: Download from [nodejs.org](https://nodejs.org/)
2. **Python 3**: Download from [python.org](https://www.python.org/downloads/) - Check "Add Python to PATH" during installation
3. **Visual Studio 2022 Build Tools**: Download from [Visual Studio Downloads](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2022)
   - Select "Desktop development with C++" workload
   - Include "MSVC v143 - VS 2022 C++ x64/x86 build tools"
   - Include "Windows SDK" (latest version)
   - Include "MSVC v143 - VS 2022 C++ x64/x86 Spectre-mitigated libs"
4. **Git for Windows**: Download from [git-scm.com](https://git-scm.com/download/win)

### Build Steps

1. **Clone the repository:**
   ```powershell
   git clone https://github.com/Vortex555/edex-ui-security-patched-windows.git
   cd edex-ui-security-patched-windows
   ```

2. **Install dependencies:**
   ```powershell
   npm run install-windows
   ```

3. **Build the application:**
   ```powershell
   npm run prebuild-windows
   ```

After the build completes, you'll find the portable application in `dist\edex-ui-windows\`. Run `eDEX-UI.exe` to launch.

### Running from Source (Development)

To run the application directly without building:
```powershell
npm start
```

### Troubleshooting

**node-pty build errors:**
- Ensure Visual Studio 2022 Build Tools are properly installed with C++ workload
- Verify Python is in PATH: `python --version`
- Check Node.js version: `node --version` (should be v20.x)
- Try rebuilding manually:
  ```powershell
  cd src
  npm install
  npx @electron/rebuild
  ```

**Application won't start:**
- Make sure no other instances are running: `taskkill /F /IM eDEX-UI.exe`
- Check terminal output for errors
- Verify all dependencies installed correctly: `npm run install-windows`

# Contributing

Community contributions are highly encouraged! If you'd like to help, please feel free to:
-   **Report bugs:** Open an issue to report any bugs you find.
-   **Suggest features:** Open an issue to suggest new features or enhancements.
-   **Submit pull requests:** If you've made a change you'd like to contribute, please submit a pull request.

# Original Credits

eDEX-UI was created by [GitSquared (Gabriel Saillard)](https://github.com/GitSquared).

Sound effects by [IceWolf](https://soundcloud.com/iamicewolf).

Globe visualization by [Rob "Arscan" Scanlon](https://github.com/arscan).

# Windows Fork Maintainer

This Windows-optimized fork is maintained by [Vortex555](https://github.com/Vortex555).

Based on the security-patched fork by [theelderemo](https://github.com/theelderemo).

If you discover any issues, please report them by opening an issue in this repository.

# License

Licensed under the [GPLv3.0](https://github.com/GitSquared/edex-ui/blob/master/LICENSE), the same as the original project.
