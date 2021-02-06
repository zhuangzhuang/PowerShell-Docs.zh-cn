---
description: 介绍 PowerShell 7 的 Windows PowerShell 兼容性功能。
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_Compatibility
ms.openlocfilehash: 3a7605765da8c17bad2d98a1d3fc3f7cc96f57b8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598690"
---
# <a name="about-windows-powershell-compatibility"></a>关于 Windows PowerShell 兼容性

## <a name="short-description"></a>简短说明

介绍 PowerShell 7 的 Windows PowerShell 兼容性功能。

## <a name="long-description"></a>详细说明

除非模块清单指示模块与 PowerShell Core 兼容，否则，将 `%windir%\system32\WindowsPowerShell\v1.0\Modules` 通过 Windows Powershell 兼容性功能在后台 Windows powershell 5.1 进程中加载文件夹中的模块。

### <a name="using-the-compatibility-feature"></a>使用兼容性功能

使用 Windows PowerShell 兼容性功能导入第一个模块时，PowerShell 会创建一个名为的远程会话， `WinPSCompatSession` 该会话在后台 Windows PowerShell 5.1 进程中运行。 此过程是在兼容性功能导入第一个模块时创建的。  (使用 `Remove-Module`) 或 PowerShell 进程退出时，将关闭上一个此类模块。

`WinPSCompatSession`通过隐式远程处理使用加载到会话中的模块，并将其反射到当前的 PowerShell 会话中。 这与用于 PowerShell 作业的传输方法相同。

当模块导入到会话中时 `WinPSCompatSession` ，隐式远程处理会在用户的目录中生成一个代理模块 `$env:Temp` ，并将此代理模块导入到当前的 PowerShell 会话中。 这允许 PowerShell 检测使用 Windows PowerShell 兼容性功能加载的模块。

创建会话后，可以将其用于在反序列化的对象上无法正常工作的操作。 整个管道在 Windows PowerShell 中执行，只返回最终结果。 例如：

```powershell
$s = Get-PSSession -Name WinPSCompatSession
Invoke-Command -Session $s -ScriptBlock {
  "Running in Windows PowerShell version $($PSVersionTable.PSVersion)"
}
```

可以通过两种方法调用兼容性功能：

- 使用 **UseWindowsPowerShell** 参数通过导入模块显式

   ```powershell
   Import-Module -Name ScheduledTasks -UseWindowsPowerShell
   ```

- 通过命令发现以模块名称、路径或自动加载的方式隐式导入 Windows PowerShell 模块。

   ```powershell
   Import-Module -Name ServerManager
   Get-AppLockerPolicy -Local
   ```

   如果尚未加载，则在运行时会加载 AppLocker 模块  `Get-AppLockerPolicy` 。

Windows PowerShell 兼容性会阻止加载 `WindowsPowerShellCompatibilityModuleDenyList` PowerShell 配置文件中的设置中列出的模块。

此设置的默认值为：

```json
"WindowsPowerShellCompatibilityModuleDenyList":  [
   "PSScheduledJob","BestPractices","UpdateServices"
]
```

### <a name="managing-implicit-module-loading"></a>管理隐式模块加载

若要禁用 Windows PowerShell 兼容功能的隐式导入行为，请使用 `DisableImplicitWinCompat` PowerShell 配置文件中的设置。 此设置可以添加到 `powershell.config.json` 文件中。 有关详细信息，请参阅 [about_powershell_config](about_powershell_config.md)。

此示例演示如何创建一个配置文件，该文件禁用 Windows PowerShell 兼容性的隐式模块加载功能。

```powershell
$ConfigPath = "$PSHOME\DisableWinCompat.powershell.config.json"
$ConfigJSON = ConvertTo-Json -InputObject @{
  "DisableImplicitWinCompat" = $true
  "Microsoft.PowerShell:ExecutionPolicy" = "RemoteSigned"
}
$ConfigJSON | Out-File -Force $ConfigPath
pwsh -settingsFile $ConfigPath
```

有关模块兼容性的最新信息，请参阅 [PowerShell 7 模块兼容性](https://aka.ms/PSModuleCompat) 列表。

### <a name="managing-cmdlet-clobbering"></a>管理 cmdlet clobbering

Windows PowerShell 兼容性功能使用隐式远程处理在兼容模式下加载模块。 结果就是，模块导出的命令优先于当前 PowerShell 7 会话中名称相同的命令。 PowerShell 7.0.0 版包含 PowerShell 随附的核心模块。

在 PowerShell 7.1 中，此行为已更改，因此不 clobbered 以下核心 PowerShell 模块：

- ConsoleHost
- Microsoft.PowerShell.Diagnostics
- Microsoft.PowerShell.Host
- Microsoft.PowerShell.Management
- Microsoft.PowerShell.Security
- Microsoft.PowerShell.Utility
- Microsoft.WSMan.Management

PowerShell 7.1 还添加了列出不应在兼容模式下 clobbered 的其他模块的功能。

你可以将 `WindowsPowerShellCompatibilityNoClobberModuleList` 设置添加到 PowerShell 配置文件。 此设置的值是以逗号分隔的模块名称列表。 此设置的默认值为：

```json
"WindowsPowerShellCompatibilityNoClobberModuleList": [ ]
```

## <a name="limitations"></a>限制

Windows PowerShell 兼容性功能：

1. 仅在 Windows 计算机上以本地方式运行
1. 要求 Windows PowerShell 5。1
1. 对序列化 cmdlet 参数和返回值进行操作，而不是对活动对象进行操作
1. 导入到 Windows PowerShell 远程处理会话的所有模块共享同一运行空间。

## <a name="keywords"></a>关键字

about_Windows_PowerShell_Compatibility

## <a name="see-also"></a>请参阅

[about_Modules](about_Modules.md)

[Import-Module](xref:Microsoft.PowerShell.Core.Import-Module)

