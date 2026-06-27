<div align="center">
  <h1>FingerprintDimReset</h1>
  <p>Lightweight Xposed module to prevent screen timeout via fingerprint sensor</p>
  <img src="metadata/images/icon.png" width="128" height="128" />
  <br><br>

  [![Latest Version](https://img.shields.io/badge/Version-v1.0.0-9575CD?style=flat&logo=github&logoColor=white)](https://github.com/snap24/FingerprintDimReset/releases)
  ![Java](https://img.shields.io/badge/Java-8-ED8B00?style=flat&logo=openjdk&logoColor=white)
  ![Android](https://img.shields.io/badge/API-26%2B-3DDC84?style=flat&logo=android&logoColor=white)
  [![License](https://img.shields.io/badge/License-GPLv3-blue?style=flat&logo=gnu&logoColor=white)](LICENSE)
  ![Xposed](https://img.shields.io/badge/Framework-Xposed%2FLSPosed-brightgreen?style=flat&logo=android&logoColor=white)

  <br><br>
  <img src="metadata/images/demo.gif" alt="Demo" />
</div>

---

**English** | [简体中文](README.zh-CN.md)

---

FingerprintDimReset is a specialized Xposed module that enhances Android's power management. It monitors the system's "Dimming" state and allows you to reset the screen timeout by simply touching your fingerprint sensor, eliminating the need to interact with the display or physical power buttons.

> Inspired by the Transsion OEM skin (XOS), which is the only Android OEM to natively include this feature. This module brings the same functionality to all Android devices via Xposed/LSPosed.

## How it Works

When the system enters the dimming phase (the final few seconds before the screen turns off), the module hooks into `DisplayPowerController` and activates a silent, invisible fingerprint authentication session. If a fingerprint touch is detected, it injects a `PowerManager.userActivity()` signal — restoring full brightness and resetting the countdown timer instantly.

## Features

- **System-Level Integration:** Deep hook into `DisplayPowerController` for native, seamless behavior.
- **Hardware Efficiency:** Minimal CPU overhead — fingerprint listener only activates during the dim phase and auto-cancels after 3 seconds.
- **Zero UI:** No launcher icon, no settings screen. Enable it in LSPosed and forget about it.
- **Privacy First:** No internet permissions, no data collection, no background services.
- **Wide Compatibility:** Works across AOSP, Samsung OneUI, Xiaomi HyperOS, and other OEMs via multi-strategy field reflection.

## Installation

1. Install the APK and enable the module in **LSPosed Manager**.
2. Set the scope to **System Framework** (`android`).
3. Reboot your device.
4. Done — there is no app to open. It works silently in the background.

## Technical Details

| Parameter | Value |
|---|---|
| Minimum SDK | 26 (Android 8.0) |
| Target SDK | 35 (Android 15) |
| Framework | Xposed API 82+ |
| Build System | Gradle (Standard Android) |
| Hooks | `DisplayPowerController.updatePowerState()`, `AuthenticationClient.onAcquired()` |

## Build

```bash
git clone https://github.com/snap24/FingerprintDimReset.git
cd FingerprintDimReset
./gradlew assembleRelease
```

Requires JDK 8+ and Android SDK.

## License

<a href="LICENSE"><img src="metadata/images/gplv3.svg" height="90" alt="GPLv3"></a>

This project is licensed under the GNU General Public License v3.0. See [LICENSE](LICENSE) for details.

---
<div align="center">
  Maintained by Chinmai H B
</div>
