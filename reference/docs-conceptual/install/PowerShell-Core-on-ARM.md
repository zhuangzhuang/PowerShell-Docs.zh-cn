---
title: 在 ARM 上安装 PowerShell Core
description: 在基于 ARM 的系统上安装 PowerShell Core
ms.date: 11/11/2020
ms.openlocfilehash: 1477b99767c19d24f8540714942f63c8347550e9
ms.sourcegitcommit: ef25c8bc95df12697725958c9814f0e187cfc683
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/12/2021
ms.locfileid: "98130133"
---
# <a name="powershell-core-on-arm"></a>ARM 上的 PowerShell Core

ARM 上的 PowerShell 支持基于 **.NET Core 支持的 OS 生命周期策略**。

PowerShell 7.0 基于 [.NET Core 3.1 支持的 OS 生命周期策略](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)，并支持以下平台：

|         (OS)          |          Version           | 体系结构 |          生命周期           |
| ------------------- | -------------------------- | ------------- | ---------------------------- |
| Windows Nano 服务器 | 版本 1803+              | ARM32         | [Windows][Windows-lifecycle] |
| Alpine Linux        | 3.10+                      | ARM64         | [Alpine][Alpine-lifecycle]   |
| Debian              | 9+                         | ARM32、ARM64  | [Debian][Debian-lifecycle]   |
| Ubuntu              | 20.10、20.04、18.04、16.04 | ARM32、ARM64  | [Ubuntu][Ubuntu-lifecycle]   |

PowerShell 7.1 基于 [.NET 5.0 支持的 OS 生命周期策略](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md)，并支持以下平台：

|        (OS)         |          Version           | 体系结构 |          生命周期           |
| ----------------- | -------------------------- | ------------- | ---------------------------- |
| Windows 10 客户端 | 版本 1709+              | ARM64         | [Windows][Windows-lifecycle] |
| Alpine Linux      | 3.11+                      | ARM64         | [Alpine][Alpine-lifecycle]   |
| Debian            | 9+                         | ARM32、ARM64  | [Debian][Debian-lifecycle]   |
| Ubuntu            | 20.10、20.04、18.04、16.04 | ARM32、ARM64  | [Ubuntu][Ubuntu-lifecycle]   |

[Windows-lifecycle]: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet
[Alpine-lifecycle]: https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases
[Debian-lifecycle]: https://wiki.debian.org/DebianReleases
[Ubuntu-lifecycle]: https://wiki.ubuntu.com/Releases

有关安装说明，请参阅以下文章：

- [基于 ARM 的 Windows 10](installing-powershell-core-on-windows.md#installing-the-zip-package)
- [Windows 10 IoT 企业版](installing-powershell-core-on-windows.md#deploying-on-windows-10-iot-enterprise)
- [Windows 10 IoT Core](installing-powershell-core-on-windows.md#deploying-on-windows-10-iot-core)
- [Raspbian](installing-powershell-core-on-linux.md#raspbian)
