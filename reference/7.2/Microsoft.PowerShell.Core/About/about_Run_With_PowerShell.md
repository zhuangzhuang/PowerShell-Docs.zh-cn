---
description: 介绍如何使用 "使用 PowerShell 运行" 功能从文件系统驱动器运行脚本。
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_run_with_powershell?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Run_With_PowerShell
ms.openlocfilehash: 7070fa2bc8bb30e83f59e3d1193faa3a8495f109
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596663"
---
# <a name="about-run-with-powershell"></a>关于在 PowerShell 中运行

## <a name="short-description"></a>简短说明
介绍如何使用 "使用 PowerShell 运行" 功能从文件系统驱动器运行脚本。

## <a name="long-description"></a>详细说明

从 Windows PowerShell 3.0 开始，你可以使用 "使用 PowerShell 运行" 功能，通过 Windows 8 和 Windows Server 2012 和 windows 资源管理器中的 windows 资源管理器在 windows 的早期版本中运行脚本。

"使用 PowerShell 运行" 功能旨在运行没有必需参数的脚本，不会将输出返回到命令提示符。

当你使用 "使用 PowerShell 运行" 功能时，PowerShell 控制台窗口仅出现短暂的情况（如果有）。 你无法与它交互。

若要使用 "使用 PowerShell 运行" 功能：

在文件资源管理器 (或 Windows 资源管理器) 中，右键单击脚本文件名，然后选择 "用 PowerShell 运行"。

"使用 PowerShell 运行" 功能将启动具有 "绕过" 执行策略的 PowerShell 会话，运行该脚本并关闭会话。

它运行以下格式的命令：

```
PowerShell.exe -File <FileName> -ExecutionPolicy Bypass
```

"使用 PowerShell 运行" 设置仅对会话 () 在其中运行脚本的 PowerShell 进程的当前实例的绕过执行策略。
此功能不会更改计算机或用户的执行策略。

"使用 PowerShell 运行" 功能仅受 AllSigned 执行策略的影响。 如果 AllSigned 执行策略对计算机或用户有效，则 "通过 PowerShell 运行" 仅运行签名脚本。 任何其他执行策略都不会影响 "使用 PowerShell 运行"。 有关详细信息，请参阅 [about_Execution_Policies](about_Execution_Policies.md)。

疑难解答说明： "用 PowerShell 运行" 命令可能会提示您确认执行策略更改。

## <a name="see-also"></a>另请参阅

[about_Execution_Policies](about_Execution_Policies.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Scripts](about_Scripts.md)

