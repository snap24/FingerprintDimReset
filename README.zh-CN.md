<div align="center">
  <h1>FingerprintDimReset</h1>
  <p>轻量级 Xposed 模块，通过指纹传感器防止屏幕超时</p>
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

**[English](README.md)** | **简体中文**

FingerprintDimReset 是一个专用的 Xposed 模块，旨在优化 Android 的电源管理。它会监视系统的“暗屏 (Dimming)”状态，允许您只需触摸指纹传感器即可重置屏幕超时，无需与屏幕或物理电源按钮进行交互。

> 本模块受传音 (Transsion) OEM 系统 (XOS) 的启发，这是目前唯一原生支持此功能的 Android 厂商。本模块通过 Xposed/LSPosed 将这一便捷的功能带给所有 Android 设备。

## 工作原理

当系统进入暗屏阶段（屏幕关闭前的最后几秒钟）时，该模块会钩入 `DisplayPowerController` 并激活一个静默、隐形的指纹身份验证会话。如果检测到指纹触摸，它会注入 `PowerManager.userActivity()` 信号 —— 从而立即恢复屏幕亮度并重新计算屏幕超时时间。

## 功能特点

- **系统级集成：** 深度钩入 `DisplayPowerController`，实现原生且无缝的行为。
- **高硬件效率：** 极低的 CPU 开销 —— 指纹监听器仅在屏幕暗屏阶段激活，并在 3 秒后自动取消。
- **无用户界面：** 没有启动图标，没有设置页面。在 LSPosed 中启用即可，完全无感。
- **隐私至上：** 无网络权限，不收集任何数据，无后台服务。
- **广泛的兼容性：** 通过多策略字段反射，完美兼容 AOSP、三星 OneUI、小米 HyperOS 等各大厂 OEM 系统。

## 安装步骤

1. 安装 APK 并在 **LSPosed Manager** 中启用该模块。
2. 将模块作用域设置为 **系统框架** (`android`)。
3. 重启您的设备。
4. 完成 —— 无需打开任何 App，它会在后台静默工作。

## 技术细节

| 参数 | 值 |
|---|---|
| 最低 SDK 版本 | 26 (Android 8.0) |
| 目标 SDK 版本 | 35 (Android 15) |
| 依赖框架 | Xposed API 82+ |
| 构建系统 | Gradle (标准 Android 构建) |
| 钩子函数 (Hooks) | `DisplayPowerController.updatePowerState()`, `AuthenticationClient.onAcquired()` |

## 源码构建

```bash
git clone https://github.com/snap24/FingerprintDimReset.git
cd FingerprintDimReset
./gradlew assembleRelease
```

构建需要 JDK 8+ 和 Android SDK 环境。

## 许可证

<a href="LICENSE"><img src="metadata/images/gplv3.svg" height="90" alt="GPLv3"></a>

本项目采用 GNU General Public License v3.0 开源许可证。详情请参阅 [LICENSE](LICENSE) 文件。

---
<div align="center">
  由 Chinmai H B 维护
</div>
