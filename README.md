<div align="center">
  <h1>FingerprintDimReset</h1>
  <p>Lightweight Xposed module to prevent screen timeout via fingerprint sensor</p>
  <img src="metadata/images/icon.png" width="128" height="128" />
  <br><br>
  
  [![Version](https://img.shields.io/badge/Version-v1.0.0-9575CD?style=flat-square)](https://github.com/snap24/FingerprintDimReset/releases)
  [![License](https://img.shields.io/badge/License-Apache_2.0-blue?style=flat-square)](LICENSE)
  [![Platform](https://img.shields.io/badge/Platform-Xposed/LSPosed-brightgreen?style=flat-square)](https://github.com/snap24/FingerprintDimReset)
  
  <br><br>
  <img src="metadata/images/demo.gif" alt="Demo" width="300"/>
</div>

---

FingerprintDimReset is a specialized Xposed module that enhances Android's power management. It monitors the system's "Dimming" state and allows you to reset the screen timeout by simply touching your fingerprint sensor, eliminating the need to interact with the display or physical power buttons.

## How it Works

When the system enters the dimming phase (the final few seconds before the screen turns off), the module activates a low-level hook. If a fingerprint event is detected, it injects a "User Activity" signal, restoring full brightness and resetting the countdown timer.

## Features

- **System Integration:** Deep integration with `DisplayPowerController` for native behavior.
- **Hardware Efficiency:** Minimal CPU overhead; only active during the screen dimming phase.
- **Privacy Oriented:** No internet permissions, no data collection, and 100% offline.
- **Compatibility:** Optimized for modern Android versions (10+) and LSPosed.

## Technical Configuration

- **Minimum SDK:** 29 (Android 10).
- **Framework:** Xposed API 82+.
- **Build System:** Gradle (Standard Android).

## Build Requirements

1. **Clone:** `git clone https://github.com/snap24/FingerprintDimReset.git`
2. **Environment:** Android Studio Koala+, JDK 17.
3. **Dependencies:** Xposed API must be available during compilation (provided via `compileOnly`).

## License

Distributed under the Apache License 2.0. See `LICENSE` for further information.

---
<div align="center">
  Maintained by snap24
</div>
