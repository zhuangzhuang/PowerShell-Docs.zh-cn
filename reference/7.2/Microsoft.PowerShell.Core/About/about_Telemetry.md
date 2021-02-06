---
description: 描述在 PowerShell 中收集的遥测数据以及如何选择退出。
Locale: en-US
ms.date: 08/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_telemetry?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Telemetry
ms.openlocfilehash: 677d43b405fdc92e6b68d6e903847b11cb671a2c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597053"
---
# <a name="about-telemetry"></a>关于遥测

## <a name="short-description"></a>简短说明

描述在 PowerShell 中收集的遥测数据以及如何选择退出。

## <a name="long-description"></a>详细说明

PowerShell 将基本遥测数据发送给 Microsoft。
此数据帮助我们更好地了解使用 PowerShell 的环境，并能确定新功能和修复的优先级。
记录以下遥测点：

- PowerShell 计数按类型 (API vs console) 
- 唯一 PowerShell 使用计数
- 以下执行类型的计数：
  - 应用程序 (本机命令) 
  - ExternalScript
  - Script
  - 函数
  - Cmdlet
- 已启用的 Microsoft 拥有的实验功能或 PowerShell 随附的实验功能的计数
- 托管会话计数
- 已加载的 Microsoft 拥有的模块计数

此数据包括 OS 名称、OS 版本、PowerShell 版本和分发通道。

若要选择退出此遥测，请将环境变量 POWERSHELL_TELEMETRY_OPTOUT 设置为 true、yes 或1。

