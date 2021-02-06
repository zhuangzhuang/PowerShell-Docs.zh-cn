---
description: 变量
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Variable 提供程序
ms.openlocfilehash: f93e58c24fdfc085983459d214db931274e164e2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598672"
---
# <a name="variable-provider"></a>变量提供程序

## <a name="provider-name"></a>提供程序名称
变量

## <a name="drives"></a>驱动器

`Variable:`

## <a name="capabilities"></a>功能

**ShouldProcess**

## <a name="short-description"></a>简短说明

提供对 PowerShell 变量及其值的访问权限。

## <a name="detailed-description"></a>详细说明

PowerShell **变量** 提供程序可让你获取、添加、更改、清除和删除当前控制台中的 PowerShell 变量。

PowerShell **变量** 提供程序支持 powershell 创建的变量，包括自动变量、首选项变量以及你创建的变量。

**变量** 驱动器是仅包含变量对象的平面命名空间。 这些变量没有子项。

**变量** 提供程序支持以下 cmdlet，这将在本文中介绍。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

PowerShell 还包括一组专门用于查看和更改变量的 cmdlet。 使用 **可变** cmdlet 时，无需 `Variable:` 在名称中指定驱动器。 本文不介绍如何使用 **可变** cmdlet。

- [Get-Variable](xref:Microsoft.PowerShell.Utility.Get-Variable)
- [New-Variable](xref:Microsoft.PowerShell.Utility.New-Variable)
- [Set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable)
- [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable)
- [Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable)

> [!NOTE]
> 你还可以使用 PowerShell 表达式分析器来创建、查看和更改变量的值，而无需使用 cmdlet。 直接使用变量时，请使用美元符号 (`$`) 将该名称标识为变量，并将赋值运算符 (`=`) 以建立和更改其值。 例如， `$p = Get-Process` 创建 `p` 变量，并将命令的结果存储 `Get-Process` 在该变量中。

## <a name="types-exposed-by-this-provider"></a>此提供程序公开的类型

变量可以是多种不同类型中的一种。 大多数变量都是类的实例 `PSVariable` 。 下面列出了其他变量及其类型。

- `?`变量是类的实例 `QuestionMarkVariable` 。
- `null`变量是类的实例 `NullVariable` 。
- 最大计数变量是类的实例 `SessionStateCapacityVariable` 。
- `LocalVariable` 实例包含有关当前执行的信息，例如：
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## <a name="navigating-the-variable-drives"></a>导航可变驱动器

**变量** 提供程序在驱动器中公开其数据存储 `Variable:` 。 若要使用变量，可以将位置更改为 `Variable:` 驱动器 (`Set-Location Variable:`) ，也可以从任何其他 PowerShell 驱动器进行操作。 若要从其他位置引用变量，请在路径中使用驱动器名称 (`Variable:`) 。

```powershell
Set-Location Variable:
```

若要返回到文件系统驱动器，请键入驱动器名称。 例如，键入：

```powershell
Set-Location C:
```

还可以从任何其他 PowerShell 驱动器使用 **变量** 提供程序。 若要从其他位置引用变量，请 `Variable:` 在路径中使用驱动器名称。

> [!NOTE]
> PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。 命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [设置位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名。 和 `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。

## <a name="displaying-the-value-of-variables"></a>显示变量的值

### <a name="get-all-variables-in-the-current-session"></a>获取当前会话中的所有变量

此命令将获取当前会话中所有变量及其值的列表。 可以在任何 PowerShell 驱动器中使用此命令。

```powershell
Get-ChildItem -Path Variable:
```

### <a name="get-a-variable-using-its-provider-path"></a>使用其提供程序路径获取变量

此命令使用其提供程序路径检索变量值，其提供程序路径以美元符号 () 为前缀 `$` 。 这与用美元符号 () 的变量名的前缀相同 `$` 。

```powershell
$variable:home
```

### <a name="get-variables-using-wildcards"></a>使用通配符获取变量

此命令将获取名称以“max”开头的变量。 可以在任何 PowerShell 驱动器中使用此命令。

```powershell
Get-ChildItem -Path Variable:max*
```

### <a name="get-the-value-of-the--variable"></a>获取的值？ 可变

此命令使用 `-LiteralPath` [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) 的参数获取 `?` 驱动器中的变量的值 `Variable:` 。 `?`是路径中的通配符，但不 `Get-ChildItem` 尝试解析参数值中的任何通配符 `-LiteralPath` 。

```powershell
Get-ChildItem -Literalpath ?
```

### <a name="get-readonly-and-constant-variables"></a>获取 ReadOnly 和常量变量

此命令将获取 `ReadOnly` `Constant` 其 **Options** 属性的值为或的变量。

```powershell
Get-ChildItem -Path Variable: | Where-Object {
   $_.options -Match "Constant" `
   -or $_.options -Match "ReadOnly"
 } | Format-List -Property name, value, options
```

## <a name="creating-variables"></a>创建变量

### <a name="create-a-new-variable"></a>创建新变量

此命令创建 `services` 变量，并将命令的结果存储 `Get-Service` 在该变量中。 由于当前位置位于驱动器中，因此 `Variable:` 参数的值 `-Path` 是一个点 (`.`) ，表示当前位置。

命令两边的括号 `Get-Service` 可确保在创建变量之前执行该命令。 如果没有圆括号，则新变量的值将为“Get-Service”字符串。

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### <a name="create-a-variable-using-an-absolute-path"></a>使用绝对路径创建变量

此命令创建 `services` 变量，并将命令的结果存储 `Get-Service` 在该变量中。

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 若要创建不含值的变量，请省略赋值运算符。

## <a name="changing-variables"></a>更改变量

### <a name="rename-a-variable"></a>重命名变量

此命令使用 `Rename-Item` cmdlet 将变量的名称更改 `a` 为 `processes` 。

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### <a name="change-the-value-of-a-variable"></a>更改变量的值

此命令使用 `Set-Item` cmdlet 将该变量的值更改 `ErrorActionPreference` 为 "Stop"。

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## <a name="copy-a-variable"></a>复制变量

此命令使用 `Copy-Item` cmdlet 将 `processes` 变量复制到 `old_processes` 。 这将创建一个名为的新变量，该变量 `old_processes` 的值与变量的值相同 `processes` 。

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## <a name="delete-a-variable"></a>删除变量

此命令 `serv` 从当前会话中删除变量。 可以在任何 PowerShell 驱动器中使用此命令。

```powershell
Remove-Variable -Path Variable:serv
```

### <a name="delete-variables-using-the--force-parameter"></a>使用-Force 参数删除变量

此命令从当前会话中删除所有变量，但其 **Options** 属性值为的变量除外 `Constant` 。 如果没有 `-Force` 参数，则该命令不会删除其 **Options** 属性值为的变量 `ReadOnly` 。

```powershell
Remove-Item Variable:* -Force
```

## <a name="setting-the-value-of-a-variable-to-null"></a>将变量的值设置为 NULL

此命令使用 `Clear-Item` cmdlet 将该变量的值更改 `processes` 为 NULL。

```powershell
Clear-Item -Path Variable:processes
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
Get-Help Get-ChildItem -Path variable:
```

## <a name="see-also"></a>请参阅

[about_Variables](../About/about_Variables.md)

[about_Automatic_Variables](../About/about_Automatic_Variables.md)

[about_Providers](../About/about_Providers.md)

