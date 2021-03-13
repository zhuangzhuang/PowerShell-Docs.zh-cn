---
ms.date: 03/12/2021
ms.topic: reference
title: 修改 PSModulePath 安装路径
description: 修改 PSModulePath 安装路径
ms.openlocfilehash: 1bea1e8ed20f55352cc9b4270e95cf7f0f7e2faa
ms.sourcegitcommit: 2560a122fe3a85ea762c3af6f1cba9e237512b2d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103412874"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>修改 PSModulePath 安装路径

`PSModulePath`环境变量将路径存储到磁盘上安装的模块的位置。 当用户未指定模块的完整路径时，PowerShell 将使用此变量来查找模块。 此变量中的路径按它们出现的顺序进行搜索。

当 PowerShell 启动时， `PSModulePath` 将创建为系统环境变量，其默认值为： `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` Windows 和 `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` Linux 或 Mac 上的，以及 `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` 适用于 windows PowerShell。

> [!NOTE]
> 用户特定的 **CurrentUser** 位置是 `WindowsPowerShell\Modules` 位于用户配置文件的 " **文档** " 位置中的文件夹。 该位置的特定路径因 Windows 版本而异，无论是否正在使用文件夹重定向。 默认情况下，在 Windows 10 上，该位置是 `$HOME\Documents\WindowsPowerShell\Modules` 。

## <a name="to-view-the-psmodulepath-variable"></a>查看 PSModulePath 变量

若要查看变量中指定的路径 `PSModulePath` ，请键入以下命令：

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>向 PSModulePath 变量添加位置

若要向此变量添加路径，请使用以下方法之一：

- 若要添加仅适用于当前会话的临时值，请在命令行中运行以下命令：

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- 若要添加在会话打开时可用的永久值，请将上述命令添加到 PowerShell 配置文件 (`$PROFILE`) >

  有关配置文件的详细信息，请参阅 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)。

- 若要向注册表添加持久性变量，请 `PSModulePath` 在 " **系统属性** " 对话框中使用环境变量编辑器创建一个名为的新用户环境变量。

- 若要通过使用脚本来添加持久性变量，请在[SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable)类上使用 .net[方法。](/dotnet/api/system.environment) 例如，以下脚本将 `C:\Program Files\Fabrikam\Module` 路径添加到 `PSModulePath` 计算机的环境变量值。 若要将路径添加到用户 `PSModulePath` 环境变量，请将 "目标" 设置为 "user"。

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

您还可以 `PSModulePath` 在配置文件中设置这些值 `powershell.config.json` 。 有关详细信息，请参阅 [about_PowerShell_Config](/powershell/module/microsoft.powershell.core/about/about_powershell_config#psmodulepath)。

## <a name="to-remove-locations-from-the-psmodulepath"></a>从 PSModulePath 删除位置

您可以使用类似的方法从变量中移除路径：例如， `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"`
将从当前会话中删除 **c:\ModulePath** 路径。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)

[about_Modules](/powershell/module/microsoft.powershell.core/about/about_modules)
