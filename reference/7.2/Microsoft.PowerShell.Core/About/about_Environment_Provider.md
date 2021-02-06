---
description: 环境
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Environment 提供程序
ms.openlocfilehash: f50558ba23d21b5ca145a06086c1c6d9b1fcd3bf
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597268"
---
# <a name="environment-provider"></a>环境提供程序

## <a name="provider-name"></a>提供程序名称
环境

## <a name="drives"></a>驱动器

`Env:`

## <a name="capabilities"></a>功能

**ShouldProcess**

## <a name="short-description"></a>简短说明

提供对 Windows 环境变量的访问权限。

## <a name="detailed-description"></a>详细说明

PowerShell **环境** 提供程序可让你获取、添加、更改、清除和删除 PowerShell 中的环境变量和值。

**环境** 变量是动态命名的变量，用于描述程序运行的环境。 Windows 和 PowerShell 使用环境变量来存储影响系统和进程执行的持久性信息。 与 PowerShell 变量不同，环境变量不服从范围约束。

**环境** 驱动器是一个平面命名空间，其中包含特定于当前用户的会话的环境变量。 环境变量没有子项。

**环境** 提供程序支持以下 cmdlet，这将在本文中介绍。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a>此提供程序公开的类型

每个环境变量都是 [DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) 类的实例。 变量的名称是字典键。 环境变量的值是字典值。

## <a name="navigating-the-environment-drive"></a>导航环境驱动器

**环境** 提供程序在驱动器中公开其数据存储 `Env:` 。 若要使用环境变量，请将你的位置更改为 `Env:` 驱动器 (`Set-Location Env:`) 或从另一个 PowerShell 驱动器工作。 若要从其他位置引用环境变量，请 `Env:` 在路径中使用驱动器名称。

```powershell
Set-Location Env:
```

若要返回到文件系统驱动器，请键入驱动器名称。 例如，键入：

```powershell
Set-Location C:
```

你还可以从任何其他 PowerShell 驱动器使用该 **环境** 提供程序。 若要从其他位置引用环境变量，请 `Env:` 在路径中使用驱动器名称。

**环境** 提供程序还使用的变量前缀公开环境变量 `$env:` 。  以下命令将查看 **ProgramFiles** 环境变量的内容。 `$env:`可以在任何 PowerShell 驱动器中使用变量前缀。

```
PS C:\> $env:ProgramFiles
C:\Program Files
```

还可以使用变量前缀来更改环境变量的值 `$env:` 。  只要活动有效，所做的任何更改仅适用于当前 PowerShell 会话。

> [!NOTE]
> PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。 命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [设置位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名。 和 `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。

## <a name="getting-environment-variables"></a>获取环境变量

此命令列出当前会话中的所有环境变量。

```powershell
Get-Item -Path Env:
```

可以在任何 PowerShell 驱动器中使用此命令。

环境提供程序没有容器，因此，当与一起使用时，上面的命令具有相同的效果 `Get-ChildItem` 。

```powershell
Get-ChildItem -Path Env:
```

### <a name="get-a-selected-environment-variable"></a>获取选定的环境变量

此命令获取 `WINDIR` 环境变量。

```powershell
Get-ChildItem -Path Env:windir
```

还可以使用变量前缀格式。

```powershell
$env:windir
```

## <a name="create-an-environment-variable"></a>创建环境变量

此命令创建 `USERMODE` 值为 "非管理员" 的环境变量。 `-Path`参数值在驱动器中创建新项 `Env:` 。 仅在当前 PowerShell 会话中可使用新的环境变量，前提是它处于活动状态。

```powershell
PS C:\> New-Item -Path Env: -Name USERMODE -Value Non-Admin
```

## <a name="changing-an-environment-variable"></a>更改环境变量

### <a name="rename-an-environment-variable"></a>重命名环境变量

此命令使用 `Rename-Item` cmdlet 将创建的环境变量的名称更改 `USERMODE` 为 `USERROLE` 。 不要更改系统所使用的环境变量的名称。 尽管这些更改仅影响当前会话，但它们可能会导致系统或程序无法正常运行。

```powershell
Rename-Item -Path Env:USERMODE -NewName USERROLE
```

### <a name="change-an-environment-variable"></a>更改环境变量

此命令使用 `Set-Item` cmdlet 将环境变量的值更改 `USERROLE` 为 "Administrator"。

```powershell
Set-Item -Path Env:USERROLE -Value Administrator
```

## <a name="copy-an-environment-variable"></a>复制环境变量

此命令将环境变量的值复制 `USERROLE` 到 `USERROLE2` 环境变量。

```powershell
Copy-Item -Path Env:USERROLE -Destination Env:USERROLE2
```

## <a name="remove-an-environment-variable"></a>删除环境变量

此命令 `USERROLE2` 从当前会话中删除环境变量。

```powershell
Remove-Item -Path Env:USERROLE2
```

## <a name="remove-an-environment-variable-with-clear-item"></a>删除具有 Clear-Item 的环境变量

此命令 `USERROLE` 通过清除环境变量的值来删除它。

```powershell
Clear-Item -Path Env:USERROLE
```

## <a name="using-the-pipeline"></a>使用管道

提供程序 cmdlet 接受管道输入。 可以通过将提供程序数据从一个 cmdlet 发送到另一个提供程序 cmdlet 来使用管道来简化任务。
若要详细了解如何将管道与提供程序 cmdlet 配合使用，请参阅本文中提供的 cmdlet 参考。

## <a name="getting-help"></a>获取帮助

从 Windows PowerShell 3.0 开始，你可以获取有关提供程序 cmdlet 的自定义帮助主题，它们介绍了这些 cmdlet 在文件系统驱动器中的行为方式。

若要获取针对文件系统驱动器进行自定义的帮助主题，请在文件系统驱动器中运行[get-help](xref:Microsoft.PowerShell.Core.Get-Help)命令，或使用 get-help 的 `-Path` 参数来[](xref:Microsoft.PowerShell.Core.Get-Help)指定文件系统驱动器。

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path env:
```

## <a name="see-also"></a>请参阅

[about_Providers](../About/about_Providers.md)

