# Vayu Tools & Utilities

<div align="center">

![Vayu Tools Banner](https://img.shields.io/badge/Device-Poco%20X3%20Pro-FF6900?style=for-the-badge&logo=xiaomi)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)
![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20Windows%20%7C%20Android-blue?style=for-the-badge)

**A comprehensive, cross-platform toolkit for Xiaomi Poco X3 Pro (vayu)**

*From stock firmware flashing to advanced Android and Linux utilities*

[Features](#-features) • [Installation](#-installation) • [Usage](#-usage) • [Roadmap](#-roadmap) • [Contributing](#-contributing)

</div>

---

## 📖 About

Vayu Tools is a curated collection of utilities, scripts, and firmware resources designed specifically for the **Xiaomi Poco X3 Pro (codename: vayu)**. This project aims to be a one-stop solution for device maintenance, recovery, customization, and optimization across multiple platforms.

### Why Vayu Tools?

- 🎯 **Device-Specific**: Tailored exclusively for Poco X3 Pro
- 🔄 **Cross-Platform**: Native support for Linux, Windows, and Android
- 🛡️ **Safe & Tested**: All tools thoroughly tested to minimize brick risk
- 📦 **All-in-One**: Everything you need in a single repository
- 🔓 **Open Source**: Transparent, community-driven development

---

## ✨ Features

### Current Features

#### 📱 Stock Firmware Management
- **Complete firmware package** (V14.0.3.0 Global)
- **Multiple flashing modes**:
  - Clean flash (factory reset)
  - Dirty flash (preserve data)
  - Flash with bootloader relock
- **Cross-platform scripts** for Linux and Windows
- **Automated process** with error handling

### 🚧 Coming Soon

<details>
<summary><b>🤖 Android Utilities</b> (Click to expand)</summary>

- Custom recovery installation tools
- TWRP/OrangeFox backup managers
- Magisk/KernelSU integration scripts
- Advanced partition management
- ROM migration assistants
- Boot image patchers
- System debloating tools
- Performance profilers

</details>

<details>
<summary><b>🐧 Linux Tools</b> (Click to expand)</summary>

- ADB/Fastboot installer scripts
- USB driver configuration helpers
- Device recognition automation
- Linux-specific optimization tools
- Udev rules generators
- Kernel module managers
- Performance monitoring utilities

</details>

<details>
<summary><b>🔧 General Utilities</b> (Click to expand)</summary>

- Device diagnostics suite
- Firmware integrity checkers
- Batch operation tools
- Backup/restore solutions
- Log analyzers
- Partition size calculators
- Anti-rollback protection checkers

</details>

---

## 📂 Repository Structure

```
vayu_tools/
├── 📁 stock_partitions/          # Stock firmware & flashing tools
│   └── V14.0.3.0_Global/
│       ├── images/               # Partition images (boot, system, etc.)
│       ├── flash_all.sh          # 🐧 Linux: Clean flash
│       ├── flash_all.bat         # 🪟 Windows: Clean flash
│       ├── flash_all_except_storage.sh    # 🐧 Dirty flash
│       ├── flash_all_except_storage.bat   # 🪟 Dirty flash
│       ├── flash_all_lock.sh     # 🐧 Flash + relock bootloader
│       └── flash_all_lock.bat    # 🪟 Flash + relock bootloader
│
├── 📁 android_tools/             # [Planned] Android-specific utilities
├── 📁 linux_tools/               # [Planned] Linux system tools
├── 📁 windows_tools/             # [Planned] Windows utilities
├── 📁 scripts/                   # [Planned] Universal scripts
├── 📁 docs/                      # [Planned] Detailed documentation
└── 📁 recovery/                  # [Planned] Recovery images & tools
```

---

## 🚀 Installation

### Prerequisites

Before using any tools, ensure you have:

| Requirement | Description | Link |
|------------|-------------|------|
| **Android Platform Tools** | Latest ADB & Fastboot | [Download](https://developer.android.com/tools/releases/platform-tools) |
| **USB Drivers** | Proper device drivers installed | [Mi USB Drivers](https://developer.android.com/studio/run/oem-usb) |
| **Unlocked Bootloader** | Required for most operations | [Unlock Guide](https://en.miui.com/unlock/) |
| **Adequate Battery** | Minimum 50% charge | - |

### Clone the Repository

```bash
git clone https://github.com/itachi-re/vayu_tools.git
cd vayu_tools
```

---

## 💡 Usage

### Flashing Stock Firmware

#### Step 1: Prepare Your Device

1. **Backup your data** (clean flash will erase everything)
2. **Charge your device** to at least 50%
3. **Enable USB Debugging** (Settings → About Phone → tap MIUI Version 7 times → Developer Options → USB Debugging)

#### Step 2: Boot into Fastboot Mode

**Method 1:** Using ADB
```bash
adb reboot bootloader
```

**Method 2:** Hardware Keys
- Power off device completely
- Hold **Volume Down + Power** until Fastboot logo appears

#### Step 3: Verify Connection

```bash
fastboot devices
# Should output: [device_serial_number]    fastboot
```

#### Step 4: Execute Flashing Script

Navigate to firmware directory:
```bash
cd stock_partitions/V14.0.3.0_Global
```

**🐧 Linux Users:**

```bash
# Option 1: Clean flash (erases all data)
sudo chmod +x flash_all.sh
sudo ./flash_all.sh

# Option 2: Dirty flash (preserves user data)
sudo chmod +x flash_all_except_storage.sh
sudo ./flash_all_except_storage.sh

# Option 3: Flash and relock bootloader (⚠️ Use with caution)
sudo chmod +x flash_all_lock.sh
sudo ./flash_all_lock.sh
```

**🪟 Windows Users:**

```cmd
# Option 1: Clean flash (erases all data)
flash_all.bat

# Option 2: Dirty flash (preserves user data)
flash_all_except_storage.bat

# Option 3: Flash and relock bootloader (⚠️ Use with caution)
flash_all_lock.bat
```

---

## ⚠️ Critical Warnings

> ### 🚨 READ BEFORE PROCEEDING

| Warning | Details |
|---------|---------|
| **🔒 Bootloader Relocking** | **NEVER** relock bootloader with custom ROMs or modified system. This will **permanently brick** your device. Only use `flash_all_lock` with **complete, unmodified stock firmware**. |
| **💾 Data Loss** | `flash_all` scripts perform **factory reset**. All photos, apps, and personal data will be **permanently deleted**. Backup first! |
| **⚡ Power Requirement** | Ensure **minimum 50% battery**. Device shutdown during flashing can cause hard brick. |
| **🎯 Device Compatibility** | These tools are **ONLY** for Poco X3 Pro (vayu). Using on other devices **will brick them**. |
| **📡 Internet Connection** | Some operations may download additional components. Ensure stable connection. |
| **🔧 Anti-Rollback** | Check anti-rollback index before flashing older firmware. Mismatched ARB can brick device. |

---

## 🐛 Troubleshooting

<details>
<summary><b>Device not detected in Fastboot mode</b></summary>

**Solutions:**
1. Try a different USB cable (use original if possible)
2. Use USB 2.0 port instead of 3.0
3. Reinstall USB drivers
4. Run command prompt as Administrator (Windows)
5. Check `fastboot devices` output
6. Disable VirtualBox/VMware USB controllers

</details>

<details>
<summary><b>Permission denied error (Linux)</b></summary>

**Solutions:**
1. Run scripts with `sudo`
2. Add user to plugdev group:
   ```bash
   sudo usermod -aG plugdev $USER
   ```
3. Configure udev rules:
   ```bash
   echo 'SUBSYSTEM=="usb", ATTR{idVendor}=="2717", MODE="0666", GROUP="plugdev"' | sudo tee /etc/udev/rules.d/51-android.rules
   sudo udevadm control --reload-rules
   ```
4. Reboot and try again

</details>

<details>
<summary><b>Flashing fails midway</b></summary>

**Solutions:**
1. Verify bootloader is unlocked: `fastboot oem device-info`
2. Check file integrity (re-download if corrupted)
3. Ensure adequate free space on PC
4. Try different USB port
5. Disable antivirus temporarily
6. Use minimal ADB & Fastboot tools

</details>

<details>
<summary><b>Device stuck in bootloop after flash</b></summary>

**Solutions:**
1. Boot into recovery and factory reset
2. Re-flash using `flash_all.sh/bat` (clean flash)
3. Flash stock recovery first, then complete firmware
4. Check if firmware matches your region

</details>

<details>
<summary><b>Anti-rollback protection error</b></summary>

**Solutions:**
1. Do **NOT** flash firmware with lower ARB index
2. Check current ARB version before flashing
3. Only flash firmware with equal or higher ARB
4. Contact community for compatible firmware versions

</details>

---

## 🗺️ Roadmap

### Phase 1: Foundation (Current)
- [x] Stock firmware collection
- [x] Cross-platform flashing scripts
- [x] Basic documentation
- [ ] Firmware integrity verification tools

### Phase 2: Android Tools (Q1 2025)
- [ ] Custom recovery installers
- [ ] Magisk integration scripts
- [ ] Partition backup utilities
- [ ] System debloater
- [ ] Performance optimizer

### Phase 3: Linux Tools (Q2 2025)
- [ ] ADB/Fastboot auto-installer
- [ ] Driver configuration wizard
- [ ] Udev rules generator
- [ ] Linux optimization suite

### Phase 4: Advanced Features (Q3 2025)
- [ ] GUI application (Python/Qt)
- [ ] Firmware migration tool
- [ ] Advanced diagnostics
- [ ] Automated backup system
- [ ] One-click root solutions

### Phase 5: Community (Q4 2025)
- [ ] Web-based tool dashboard
- [ ] ROM compatibility database
- [ ] Community script repository
- [ ] Tutorial video series

---

## 🤝 Contributing

We welcome contributions from the community! Here's how you can help:

### How to Contribute

1. **🍴 Fork the repository**
2. **🌿 Create a feature branch**
   ```bash
   git checkout -b feature/AmazingFeature
   ```
3. **💻 Make your changes**
4. **✅ Test thoroughly** on your device
5. **📝 Commit with descriptive messages**
   ```bash
   git commit -m "Add: New recovery flashing tool"
   ```
6. **⬆️ Push to your branch**
   ```bash
   git push origin feature/AmazingFeature
   ```
7. **🎉 Open a Pull Request**

### Contribution Guidelines

- **Test everything** before submitting
- **Document your code** with clear comments
- **Follow existing code style** and structure
- **Update README** if adding new features
- **Include safety warnings** for potentially dangerous operations
- **Specify compatibility** (which firmware versions, etc.)

### Ways to Contribute

- 🐛 Report bugs and issues
- 💡 Suggest new features
- 📝 Improve documentation
- 🔧 Submit new tools and utilities
- 🧪 Test tools on different configurations
- 🌐 Translate documentation
- ⭐ Star the repository to show support

---

## 📜 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

### Third-Party Licenses
- Stock firmware: © Xiaomi Inc.
- Android tools: © Android Open Source Project
- Platform tools: © Google LLC

---

## 🙏 Acknowledgments

- **Xiaomi** for device firmware and documentation
- **Android Open Source Project** for core tools
- **Linux community** for invaluable utilities
- **XDA Developers** for technical insights
- **Contributors** who make this project possible
- **Testers** who help ensure safety and reliability

---

## 📞 Support & Contact

- **Issues**: [GitHub Issues](https://github.com/itachi-re/vayu_tools/issues)
- **Discussions**: [GitHub Discussions](https://github.com/itachi-re/vayu_tools/discussions)
- **Maintainer**: [@itachi-re](https://github.com/itachi-re)

### Before Asking for Help

1. ✅ Check [Troubleshooting](#-troubleshooting) section
2. ✅ Search existing [Issues](https://github.com/itachi-re/vayu_tools/issues)
3. ✅ Verify you're using correct device (Poco X3 Pro - vayu)
4. ✅ Include error logs when reporting issues

---

## ⚖️ Disclaimer

> **Important Legal Notice**

This project is provided "as is" without warranty of any kind. The maintainers and contributors are **not responsible** for:
- Bricked devices
- Data loss
- Warranty voidance
- Any damage resulting from use of these tools

**By using these tools, you acknowledge:**
- You understand the risks involved
- You have backed up your data
- You accept full responsibility for any consequences
- Your device warranty may be voided

**Always proceed with caution and at your own risk.** 🔒

---

<div align="center">

### Star History

[![Star History Chart](https://api.star-history.com/svg?repos=itachi-re/vayu_tools&type=Date)](https://star-history.com/#itachi-re/vayu_tools&Date)

---

**Made with ❤️ for the Poco X3 Pro community**

*If this project helped you, consider giving it a ⭐ star!*

</div>
