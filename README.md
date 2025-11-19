# Language Indicator

A lightweight Windows desktop utility that displays the current keyboard input language indicator near the cursor. Shows a country flag icon corresponding to the active language layout in the system tray and as an overlay when pressing hotkeys.

![Language Indicator](https://img.shields.io/badge/Windows-10%2B-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Version](https://img.shields.io/badge/version-1.0.0-blue)

## Features

- 🌍 **Multi-language support** - Detects and displays flags for 20+ languages
- 🎯 **Smart positioning** - Indicator appears near cursor when pressing hotkeys
- 🖥️ **Multi-monitor support** - Works correctly on all connected monitors
- ⚙️ **Configurable hotkeys** - Choose between Ctrl+Shift or Alt+Shift
- 🚀 **Autostart option** - Launch automatically with Windows
- 🎨 **Dynamic tray icon** - System tray icon changes to show current language flag
- 🔒 **Lightweight** - Minimal resource usage, runs silently in background
- 🌐 **No internet required** - All flag images included locally

## Screenshots

*The indicator appears near the cursor when pressing the configured hotkey combination.*

## Installation

### Option 1: Microsoft Store (Recommended)
1. Search for "Language Indicator" in Microsoft Store
2. Click "Get" to install
3. The app will be automatically updated

### Option 2: Portable (Manual)
1. Download the latest release
2. Extract to any folder
3. Ensure the `flags` directory is in the same folder as `LanguageIndicator.exe`
4. Run `LanguageIndicator.exe`

## Usage

### Basic Usage
1. Launch the application
2. The app runs in the background - look for the icon in the system tray (notification area)
3. Press **Ctrl+Shift** or **Alt+Shift** (depending on your settings) to show the language indicator near the cursor
4. Release the keys to hide the indicator
5. The tray icon automatically updates to show the flag of the current input language

### Configuration
- **Right-click** the tray icon to access the context menu
- **Settings → Hotkey** - Choose between Ctrl+Shift or Alt+Shift
- **Settings → Autostart with Windows** - Enable/disable automatic startup
- **Settings → About** - View application information and open website

### Supported Languages
- 🇺🇦 Ukrainian (UA)
- 🇺🇸 English - United States (US)
- 🇬🇧 English - United Kingdom (GB)
- 🇷🇺 Russian (RU)
- 🇩🇪 German (DE)
- 🇫🇷 French (FR)
- 🇮🇹 Italian (IT)
- 🇵🇹 Portuguese (PT)
- 🇨🇿 Czech (CS)
- 🇵🇱 Polish (PL)
- 🇰🇷 Korean (KO)
- 🇯🇵 Japanese (JA)
- 🇨🇳 Chinese (ZH)
- 🇭🇺 Hungarian (HU)
- 🇩🇰 Danish (DA)
- 🇳🇱 Dutch (NL)
- 🇳🇴 Norwegian (NO)
- 🇸🇪 Swedish (SV)
- 🇫🇮 Finnish (FI)
- 🇹🇭 Thai (TH)
- 🇮🇩 Indonesian (ID)
- 🇪🇸 Spanish (ES)

*And more...*

## Building from Source

### Prerequisites
- **Visual Studio 2022** (or Visual Studio 2019) with C++ Desktop Development workload
- **Windows SDK** 10.0 or later
- **WiX Toolset** (optional, for MSI installer)
- **Windows SDK** (for MSIX packaging)

### Build Steps

#### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/MS_icon_languages.git
cd MS_icon_languages
```

#### 2. Download Flag Images
```bash
python download_flags.py
```
This will download all required flag PNG images to the `flags` directory.

#### 3. Build the Application

**Using Visual Studio:**
1. Open `LanguageIndicator.sln`
2. Select configuration (Debug or Release)
3. Select platform (x64)
4. Build → Build Solution (F7)

**Using Command Line:**
```bash
# Debug build
msbuild LanguageIndicator.sln /p:Configuration=Debug /p:Platform=x64

# Release build
msbuild LanguageIndicator.sln /p:Configuration=Release /p:Platform=x64
```

**Using Build Script:**
```bash
build.bat
```

The executable will be in `bin\x64\Release\LanguageIndicator.exe` (or `Debug` for debug builds).

#### 4. Build MSI Installer (Optional)
```bash
build_msi.bat
```
Requires WiX Toolset. The MSI will be in `dist\LanguageIndicator.msi`.

#### 5. Build MSIX Package (Optional)
```bash
build_msix.bat
```
Requires Windows SDK. The MSIX will be in `dist\LanguageIndicator.msix`.

## Project Structure

```
MS_icon_languages/
├── LanguageIndicator.sln          # Visual Studio solution
├── LanguageIndicator.vcxproj      # Main project file
├── main.cpp                        # Entry point
├── LanguageIndicator.h             # Main class header
├── LanguageIndicator.cpp            # Main class implementation
├── LanguageIndicator.rc             # Resource file
├── resource.h                      # Resource definitions
├── app.manifest                    # Application manifest
├── icon.ico                        # Application icon
├── Package.appxmanifest            # MSIX manifest
├── LanguageIndicator.wxs            # WiX installer source
├── flags/                          # Flag images directory
│   ├── ua.png
│   ├── us.png
│   ├── gb.png
│   └── ...
├── build.bat                       # Build script
├── build_msi.bat                   # MSI build script
├── build_msix.bat                  # MSIX build script
├── download_flags.py               # Flag downloader script
└── README.md                       # This file
```

## Technical Details

### Technologies Used
- **C++17** - Core language
- **Win32 API** - Windows integration
- **GDI+** - Image rendering and flag display
- **Windows Registry** - Settings storage
- **Shell API** - System tray integration

### System Requirements
- **OS:** Windows 10 version 1809 (17763) or later, Windows 11
- **Architecture:** x64
- **RAM:** Minimal (runs in background)
- **Disk:** ~2 MB (including flag images)

### Architecture
- **Single executable** - No external dependencies (except Windows system libraries)
- **Background service** - Runs silently in system tray
- **Overlay window** - Transparent, non-interactive overlay for indicator
- **Registry storage** - Settings stored in `HKEY_CURRENT_USER\Software\LanguageIndicator`

## Configuration

### Registry Settings
Settings are stored in the Windows Registry:
- **Path:** `HKEY_CURRENT_USER\Software\LanguageIndicator`
- **HotkeyCombination:** DWORD (0 = Ctrl+Shift, 1 = Alt+Shift)
- **Autostart:** `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run\LanguageIndicator`

### File Locations
- **Executable:** `Program Files\LanguageIndicator\LanguageIndicator.exe` (if installed via MSI)
- **Flags:** `Program Files\LanguageIndicator\flags\` (if installed via MSI)
- **Logs:** `debug.log` in the application directory (Debug builds only)

## Troubleshooting

### Indicator doesn't appear
- Check that you're pressing the correct hotkey combination (Ctrl+Shift or Alt+Shift)
- Verify the hotkey setting in Settings → Hotkey menu
- Check if the overlay is hidden: Right-click tray icon → Show Indicator

### Tray icon is missing
- Check the notification area (may be hidden)
- Click the "Show hidden icons" arrow in the system tray
- Restart the application

### Flags don't display
- Ensure the `flags` directory exists in the same folder as the executable
- Verify that PNG files are present in the `flags` directory
- Check `debug.log` for error messages (if available)

### Application won't start
- Check if another instance is already running
- Verify you have the required Windows version (Windows 10 1809+)
- Check `debug.log` for error details

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Development

### Running Tests
```bash
run_tests.bat
```

### Debugging
- Enable debug logging by running Debug build
- Check `debug.log` file in the application directory
- Use Visual Studio debugger for step-by-step debugging

### Adding New Languages
1. Add language code mapping in `LanguageIndicator::InitializeLanguageMap()`
2. Add flag file path in `LanguageIndicator::InitializeFlagMap()`
3. Download flag image to `flags` directory (or use `download_flags.py`)
4. Rebuild the application

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Author

**Dmytro Bazeliuk**
- Website: https://DevSecOps.CV
- Email: support@DevSecOps.CV

## Acknowledgments

- Flag images provided by [flagcdn.com](https://flagcdn.com)
- Built with Visual Studio and Windows SDK
- Uses GDI+ for image rendering

## Changelog

### Version 1.0.0
- Initial release
- Multi-language support (20+ languages)
- Configurable hotkeys (Ctrl+Shift / Alt+Shift)
- Multi-monitor support
- Autostart functionality
- Dynamic tray icon with country flags
- MSI and MSIX installer support



---

**Made with ❤️ for Windows users who work with multiple languages**
