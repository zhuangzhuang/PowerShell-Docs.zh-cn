---
description: 函数
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_function_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Function 提供程序
ms.openlocfilehash: f72ad1e93e65848238afd9feacb38982b4986177
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598282"
---
# <a name="function-provider"></a>函数提供程序

## <a name="provider-name"></a>提供程序名称
函数

## <a name="drives"></a>驱动器

`Function:`

## <a name="capabilities"></a>功能

**ShouldProcess**

## <a name="short-description"></a>简短说明

提供对在 PowerShell 中定义的函数的访问权限。

## <a name="detailed-description"></a>详细说明

PowerShell **函数** 提供程序可让你获取、添加、更改、清除和删除 PowerShell 中的函数和筛选器。

函数是用于执行某项操作的命名的代码块。 在键入函数名称后，将运行该函数中的代码。 筛选器是用于建立操作条件的命名的代码块。 您可以键入筛选器的名称来代替条件，例如在 `Where-Object` 命令中。

**函数** 驱动器是只包含函数和筛选器对象的平面命名空间。 函数和筛选器都没有子项。

**函数** 提供程序支持以下 cmdlet，这将在本文中介绍。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a>此提供程序公开的类型

每个函数都是 [FunctionInfo](/dotnet/api/system.management.automation.functioninfo) 类的实例。 每个筛选器都是 [都是 system.management.automation.filterinfo](/dotnet/api/system.management.automation.filterinfo) 类的实例。

## <a name="navigating-the-function-drive"></a>导航函数驱动器

**函数** 提供程序在驱动器中公开其数据存储区 `Function:` 。 若要使用函数，你可以将你的位置更改为 `Function:` 驱动器 (`Set-Location Function:`) 。 或者，你可以从另一个 PowerShell 驱动器进行工作。 若要从其他位置引用函数，请在路径中使用驱动器名称 (`Function:`) 。

```powershell
Set-Location Function:
```

若要返回到文件系统驱动器，请键入驱动器名称。 例如，键入：

```powershell
Set-Location C:
```

你还可以从任何其他 PowerShell 驱动器使用该 **函数** 提供程序。 若要从其他位置引用函数，请 `Function:` 在路径中使用驱动器名称。

> [!NOTE]
> PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。 命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [设置位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名。 和 `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。

## <a name="getting-functions"></a>获取函数

此命令将获取当前会话中所有函数的列表。 可以在任何 PowerShell 驱动器中使用此命令。

```powershell
Get-ChildItem -Path Function:
```

函数提供程序没有容器，因此，当与一起使用时，上面的命令具有相同的效果 `Get-ChildItem` 。

```powershell
Get-ChildItem -Path Function:
```

可以通过访问 **定义** 属性来检索函数的定义，如下所示。

```powershell
(Get-Item -Path function:more).Definition
```

还可以使用以美元符号 () 前缀的提供程序路径来检索函数的定义 `$` 。

```powershell
$function:more
```

### <a name="getting-selected-functions"></a>正在获取选定函数

此命令获取 `man` 驱动器中的函数 `Function:` 。 它使用 `Get-Item` cmdlet 来获取函数。 管道运算符 (`|` 将结果发送到) `Format-Table` 。 `-Wrap`参数将不适合行的文本定向到下一行。 `-Autosize`参数调整表列的大小以容纳文本。

```powershell
Get-Item -Path man | Format-Table -Wrap -Autosize
```

### <a name="working-with-function-provider-paths"></a>使用函数提供程序路径

这些命令均获取名为的函数 `c:` 。 第一个命令可在任何驱动器中使用。 第二个命令在驱动器中使用 `Function:` 。 由于名称以冒号结束（这是驱动器的语法），因此必须使用驱动器名称来限定路径。 在 `Function:` 驱动器中，可以使用任何一种格式。 在第二个命令中，点 (`.`) 表示当前位置。

```
PS C:\> Get-Item -Path Function:c:
PS Function:\> Get-Item -Path .\c:
```

## <a name="creating-a-function"></a>创建函数

此命令使用 `New-Item` cmdlet 创建名为的函数 `Win32:` 。
大括号中的表达式是以函数名称表示的脚本块。

```powershell
New-Item -Path Function:Win32: -Value {Set-Location C:\Windows\System32}
```

还可以通过在 PowerShell 命令行中键入函数来创建该函数。 例如，tpe `Function:Win32: {Set-Location C:\Windows\System32}` 。 如果在 `Function:` 驱动器中，则可以省略驱动器名称。

## <a name="deleting-a-function"></a>删除函数

此命令 `more:` 从当前会话中删除该函数。

```powershell
Remove-Item Function:more:
```

## <a name="changing-a-function"></a>更改函数

此命令使用 `Set-Item` cmdlet 来更改函数， `prompt` 使其在路径之前显示时间。

```powershell
Set-Item -Path Function:prompt -Value {
  'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '
  }
```

### <a name="rename-a-function"></a>重命名函数

此命令使用 `Rename-Item` cmdlet 将函数的名称更改 `help` 为 `gh` 。

```powershell
Rename-Item -Path Function:help -NewName gh
```

## <a name="copying-a-function"></a>复制函数

此命令将 `prompt` 函数复制到 `oldPrompt` ，从而为与 prompt 函数相关联的脚本块有效地创建一个新名称。
如果计划更改原始 prompt 函数，你可以使用此命令来保存该函数。
新函数的 **Options** 属性的值为 `None` 。 若要更改 **Options** 属性的值，请使用 `Set-Item` 。

```powershell
Copy-Item -Path Function:prompt -Destination Function:oldPrompt
```

## <a name="dynamic-parameters"></a>动态参数

动态参数是 PowerShell 提供程序添加的 cmdlet 参数，只有在启用了提供程序的驱动器中使用 cmdlet 时，这些参数才可用。

### <a name="options-systemmanagementautomationscopeditemoptions"></a>选项 < [ScopedItemOptions] >

确定函数的 **Options** 属性的值。

- `None`：无选项。 `None` 为默认值。
- `Constant`：无法删除该函数，并且无法更改其属性。 `Constant` 仅在创建函数时才可用。
  不能将现有函数的选项更改为 `Constant` 。
- `Private`：该函数仅在当前范围内可见
-  (子范围) 。
- `ReadOnly`：除使用参数外，不能更改函数的属性 `-Force` 。 您可以使用 `Remove-Item` 删除函数。
- `AllScope`：该函数将复制到任何创建的新作用域。

### <a name="cmdlets-supported"></a>支持的 cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)

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
Get-Help Get-ChildItem -Path function:
```

## <a name="see-also"></a>请参阅

[about_Functions](../About/about_Functions.md)

[about_Providers](../About/about_Providers.md)

