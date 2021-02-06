---
description: Alias
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_alias_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Alias 提供程序
ms.openlocfilehash: d6bfbaf878a6d971b1e01d963faec8c8ece5d1fc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596854"
---
# <a name="alias-provider"></a>别名提供程序

## <a name="provider-name"></a>提供程序名称
Alias

## <a name="drives"></a>驱动器

`Alias:`

## <a name="capabilities"></a>功能

**ShouldProcess**

## <a name="short-description"></a>简短说明

提供对 PowerShell 别名及其所代表的值的访问权限。

## <a name="detailed-description"></a>详细说明

PowerShell **别名** 提供程序可让你获取、添加、更改、清除和删除 PowerShell 中的别名。

别名是 cmdlet、函数、可执行文件（包括脚本）的替代名称。 PowerShell 包含一组内置别名。 可以将自己的别名添加到当前会话和 PowerShell 配置文件。

**别名** 驱动器是只包含 Alias 对象的平面命名空间。
这些别名没有子项。

**Alias** 提供程序支持以下 cmdlet，本文将对此进行介绍。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

PowerShell 包括一组用于查看和更改别名的 cmdlet。 使用 **别名** cmdlet 时，无需 `Alias:` 在名称中指定驱动器。 本文不介绍如何使用 **别名** cmdlet。

- [Export-Alias](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [Import-Alias](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias)
- [Set-Alias](xref:Microsoft.PowerShell.Utility.Set-Alias)

## <a name="types-exposed-by-this-provider"></a>此提供程序公开的类型

每个别名都是 [system.management.automation.aliasinfo](/dotnet/api/system.management.automation.aliasinfo) 类的实例。

## <a name="navigating-the-alias-drive"></a>导航别名驱动器

**别名** 提供程序在驱动器中公开其数据存储 `Alias:` 。 若要使用别名，可以使用以下命令将位置更改为 `Alias:` 驱动器：

```powershell
Set-Location Alias:
```

若要返回到文件系统驱动器，请键入驱动器名称。 例如，键入：

```powershell
Set-Location C:
```

还可以从任何其他 PowerShell 驱动器使用别名提供程序。 若要从其他位置引用别名，请 `Alias:` 在路径中使用驱动器名称。

> [!NOTE]
> PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。 命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [设置位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名。 和 `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。

### <a name="displaying-the-contents-of-the-alias-drive"></a>显示别名的内容：驱动器

此命令获取当前位置为驱动器时所有别名的列表 `Alias:` 。 它使用通配符 `*` 来指示当前位置的所有内容。

```powershell
PS Alias:\> Get-Item -Path *
```

在 `Alias:` 驱动器中，表示当前位置的点， `.` 以及 `*` 表示当前位置中所有项的通配符，具有相同的效果。 例如， `Get-Item -Path .` 或 `Get-Item \*` 生成相同的结果。

别名提供程序没有容器，因此，当与一起使用时，上面的命令具有相同的效果 `Get-ChildItem` 。

```powershell
Get-ChildItem -Path Alias:
```

### <a name="get-a-selected-alias"></a>获取所选别名

此命令将获取 `ls` 别名。
由于它包括路径，因此可以在任何 PowerShell 驱动器中使用它。

```powershell
Get-Item -Path Alias:ls
```

如果在 `Alias:` 驱动器中，则可以省略路径中的驱动器名称。

还可以通过在提供程序路径前面加上美元符号 () 来检索别名的定义 `$` 。

```powershell
$Alias:ls
```

### <a name="get-all-aliases-for-a-specific-cmdlet"></a>获取特定 cmdlet 的所有别名

此命令获取与 cmdlet 关联的别名列表 `Get-ChildItem` 。 它使用 **定义** 属性，该属性存储 cmdlet 名称。

```powershell
Get-Item -Path Alias:* | Where-Object {$_.Definition -eq "Get-ChildItem"}
```

## <a name="creating-aliases"></a>创建别名

### <a name="create-an-alias-from-the-alias-drive"></a>从 Alias：驱动器创建别名

此命令 `serv` 为 cmdlet 创建别名 `Get-Service` 。 由于当前位置位于驱动器中，因此 `Alias:` `-Path` 不需要参数。

此命令还使用 `-Options` dynamic 参数在别名上设置 **AllScope** 选项。 `-Options` `New-Item` 仅当位于驱动器中时，此参数才会出现在 cmdlet 中 `Alias:` 。 点 (`.`) 指示当前目录，即别名驱动器。

```
PS Alias:\> New-Item -Path . -Name serv -Value Get-Service -Options "AllScope"
```

### <a name="create-an-alias-with-an-absolute-path"></a>创建具有绝对路径的别名

你可以为可调用命令的任意项创建别名。
此命令为创建 `np` 别名 `Notepad.exe` 。

```powershell
New-Item -Path Alias:np -Value c:\windows\notepad.exe
```

### <a name="create-an-alias-to-a-new-function"></a>为新函数创建别名

你可以为任意函数创建别名。 可使用此功能创建一个包括 cmdlet 及其参数的别名。

第一个命令创建 `CD32` 函数，该函数将当前目录更改为 `System32` 目录。 第二个命令 `go` 为函数创建别名 `CD32` 。

完成该命令后，可以使用 `CD32` 或 `go` 来调用函数。

```powershell
function CD32 {Set-Location -Path c:\windows\system32}
Set-Item -Path Alias:go -Value CD32
```

## <a name="changing-aliases"></a>更改别名

### <a name="change-the-options-of-an-alias"></a>更改别名选项

可以将 `Set-Item` cmdlet 与 `-Options` 动态参数一起使用来更改别名的属性的值 `-Options` 。

此命令设置别名的 **AllScope** 和 **ReadOnly** 选项 `dir` 。 该命令使用 `-Options` cmdlet 的动态参数 `Set-Item` 。 `-Options` `Set-Item` 当你将参数与 **Alias** 或 **Function** 提供程序一起使用时，可在中使用。

```powershell
Set-Item -Path Alias:dir -Options "AllScope,ReadOnly"
```

### <a name="change-an-aliases-referenced-command"></a>更改别名引用命令

此命令使用 `Set-Item` cmdlet 来更改别名， `gp` 使其表示 `Get-Process` cmdlet 而不是 `Get-ItemProperty` cmdlet。
`-Force`参数是必需的，因为别名的 **Options** 属性的值 `gp` 设置为 `ReadOnly` 。 因为该命令是从驱动器内部提交的 `Alias:` ，所以未在路径中指定该驱动器。

```powershell
Set-Item -Path gp -Value Get-Process -Force
```

更改将影响四个用于定义别名和命令之间的关联的属性。 若要查看更改的效果，请键入以下命令：

```powershell
Get-Item -Path gp | Format-List -Property *
```

### <a name="rename-an-alias"></a>重命名别名

此命令使用 `Rename-Item` cmdlet 将 `popd` 别名更改为 `pop` 。

```powershell
Rename-Item -Path Alias:popd -NewName pop
```

## <a name="copying-an-alias"></a>复制别名

此命令复制 `pushd` 别名，以便为 `push` cmdlet 创建新别名 `Push-Location` 。

创建新别名后，其 **Description** 属性的值为 null。
而且，其 **选项** 属性的值为 `None` 。 如果命令是从驱动器内部发出的 `Alias:` ，则可以从参数的值中省略驱动器名称 `-Path` 。

```powershell
Copy-Item -Path Alias:pushd -Destination Alias:push
```

## <a name="deleting-an-alias"></a>删除别名

此命令 `serv` 从当前会话中删除别名。
可以在任何 PowerShell 驱动器中使用此命令。

```powershell
Remove-Item -Path Alias:serv
```

此命令删除以“s”开头的别名。
它不会删除只读别名。

```powershell
Clear-Item -Path Alias:s*
```

### <a name="delete-read-only-aliases"></a>删除只读别名

此命令从当前会话中删除所有别名，但 `Constant` 其 **Options** 属性的值除外。 `-Force`参数允许命令删除其 **Options** 属性值为的别名 `ReadOnly` 。

```powershell
Remove-Item Alias:* -Force
```

## <a name="dynamic-parameters"></a>动态参数

动态参数是 PowerShell 提供程序添加的 cmdlet 参数，只有在启用了提供程序的驱动器中使用 cmdlet 时，这些参数才可用。

### <a name="options-systemmanagementautomationscopeditemoptions"></a>选项 [ScopedItemOptions]

确定别名的 **Options** 属性的值。

- **None**：无选项。 此值为默认值。
- **常量**：无法删除别名，也无法更改其属性。
  **常量** 仅在创建别名时才可用。 不能将现有别名的选项更改为 **常量**。
- **Private**：别名仅在当前作用域（而不是子作用域）中可见。
- **ReadOnly**：除非使用参数，否则无法更改别名的属性 `-Force` 。 您可以使用 `Remove-Item` 来删除别名。
- **AllScope**：将别名复制到任何创建的新作用域。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

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
Get-Help Get-ChildItem -Path alias:
```

## <a name="see-also"></a>请参阅

[about_Aliases](../About/about_Aliases.md)

[about_Providers](../About/about_Providers.md)

