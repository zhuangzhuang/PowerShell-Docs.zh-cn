---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Location
ms.openlocfilehash: 57535b4f566a3bdd541d2035b61c8162e15b35f3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598046"
---
# Get-Location

## 摘要
获取有关当前工作位置或某个位置堆栈的信息。

## SYNTAX

### Location（默认值）

```
Get-Location [-PSProvider <String[]>] [-PSDrive <String[]>] [<CommonParameters>]
```

### 堆栈

```
Get-Location [-Stack] [-StackName <String[]>] [<CommonParameters>]
```

## DESCRIPTION

该 `Get-Location` cmdlet 将获取表示当前目录的对象，这与打印工作目录 (pwd) 命令非常类似。

当你在 PowerShell 驱动器间移动时，PowerShell 会保留你在每个驱动器中的位置。 可以使用此 cmdlet 查找每个驱动器中的位置。

可以使用此 cmdlet 在运行时获取当前目录，并将其用于函数和脚本中，如在 PowerShell 提示符下显示当前目录的函数中。

你还可以使用此 cmdlet 显示位置堆栈中的位置。 有关详细信息，请参阅 **Stack** 和 **StackName** 参数的说明和说明。

## 示例

### 示例1：显示当前驱动器位置

此命令显示你在当前 PowerShell 驱动器中的位置。

```powershell
PS C:\Windows> Get-Location
```

```Output
Path
----
C:\Windows
```

例如，如果位于驱动器的目录中 `Windows` `C:` ，则会显示该目录的路径。

### 示例2：显示不同驱动器的当前位置

此示例演示 `Get-Location` 如何使用来显示你在不同 PowerShell 驱动器中的当前位置。 `Set-Location` 用于将位置更改为不同 PSDrives 上的多个不同路径。

```powershell
PS C:\> Set-Location C:\Windows
PS C:\Windows> Set-Location HKLM:\Software\Microsoft
PS HKLM:\Software\Microsoft> Set-Location "HKCU:\Control Panel\Input Method"
PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive C

Path
----
C:\Windows

PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive HKLM

Path
----
HKLM:\Software\Microsoft

PS HKCU:\Control Panel\Input Method> Set-Location C:
PS C:\Windows> Get-Location -PSProvider Registry

Path
----
HKCU:\Control Panel\Input Method
```

### 示例3：使用堆栈获取位置

此示例演示如何使用的 **Stack** 和 **StackName** 参数 `Get-Location` 来列出当前位置堆栈和备用位置堆栈中的位置。

`Push-Location`Cmdlet 用于更改为三个不同的位置。 第三个推送使用不同的堆栈名称。 的 **Stack** 参数 `Get-Location` 显示默认堆栈的内容。 的 **StackName** 参数 `Get-Location` 显示名为的堆栈的内容 `Stack2` 。

```powershell
PS C:\> Push-Location C:\Windows
PS C:\Windows>Push-Location System32
PS C:\Windows\System32>Push-Location WindowsPowerShell -StackName Stack2
C:\Windows\System32\WindowsPowerShell>Get-Location -Stack

Path
----
C:\Windows
C:\

C:\Windows\System32\WindowsPowerShell>Get-Location -StackName Stack2

Path
----
C:\Windows\System32
```

### 示例4：自定义 PowerShell 提示符

此示例演示如何自定义 PowerShell 提示符。

```powershell
PS C:\>
function prompt { 'PowerShell: ' + (Get-Location) + '> '}
PowerShell: C:\>
```

定义提示符的函数包含一个 `Get-Location` 命令，该命令在控制台中出现提示时运行。

默认 PowerShell 提示符的格式由一个名为的特殊函数来定义 `prompt` 。 可以通过创建一个名为的新函数来更改控制台中的提示 `prompt` 。

若要查看当前的 prompt 函数，请键入以下命令： `Get-Content Function:\prompt`

## PARAMETERS

### -PSDrive

获取指定 PowerShell 驱动器中的当前位置。

例如，如果你位于 `Cert:` 驱动器中，则可以使用此参数来查找你在驱动器中的当前位置 `C:` 。

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

获取指定 PowerShell 提供程序支持的驱动器中的当前位置。
如果指定的提供程序支持多个驱动器，则此 cmdlet 将返回最近访问过的驱动器上的位置。

例如，如果你位于 `C:` 驱动器中，则可以使用此参数来查找 PowerShell **注册表** 提供程序的驱动器中的当前位置。

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Stack

指示此 cmdlet 显示添加到当前位置堆栈中的位置。 您可以使用 cmdlet 将位置添加到堆栈 `Push-Location` 中。

若要显示其他位置堆栈中的位置，请使用 **StackName** 参数。 有关位置堆栈的信息，请参阅 [注释](#notes)。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StackName

指定作为字符串数组，即命名的位置堆栈。 输入一个或多个位置堆栈名称。

若要显示当前位置堆栈中的位置，请使用 **stack** 参数。 若要使某个位置堆栈成为当前位置堆栈，请使用 `Set-Location` cmdlet。

此 cmdlet 无法显示未命名的默认堆栈中的位置，除非该堆栈为当前堆栈。

```yaml
Type: System.String[]
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将输入传递给此 cmdlet。

## 输出

### System.Management.Automation.PathInfo 或 System.Management.Automation.PathInfoStack

如果使用 **Stack** 或 **StackName** 参数，则此 cmdlet 将返回 **system.management.automation.pathinfostack** 对象。 否则，它将返回 **PathInfo** 对象。

## 注释

PowerShell 支持每个进程运行多个运行空间。 每个运行空间都有其自己的 _当前目录_。
这与不相同 `[System.Environment]::CurrentDirectory` 。 调用 .NET Api 或运行本机应用程序时，如果不提供显式目录路径，则可能会出现这种问题。
`Get-Location`Cmdlet 返回当前 PowerShell 运行空间的当前目录。

此 cmdlet 用于处理由任何提供程序公开的数据。 若要列出会话中的提供程序，请键入 `Get-PSProvider` 。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

**PSProvider**、 **new-psdrive**、 **Stack** 和 **StackName** 参数的交互方式取决于提供程序。 某些组合将会导致错误，例如，指定驱动器以及没有公开该驱动器的提供程序。 如果未指定参数，则此 cmdlet 将返回包含当前工作位置的提供程序的 **PathInfo** 对象。

堆栈是后进先出的列表，其中只有最近添加的项是可访问的。 采用要使用项的顺序将这些项添加到堆栈，然后采用相反顺序检索这些项以供使用。 PowerShell 使你能够在位置堆栈中存储提供程序位置。 PowerShell 创建一个未命名的默认位置堆栈，你可以创建多个命名的位置堆栈。 如果未指定堆栈名称，PowerShell 将使用当前位置堆栈。 默认情况下，未命名的默认位置为当前位置堆栈，但你可以使用 `Set-Location` cmdlet 来更改当前位置堆栈。

若要管理位置堆栈，请使用 PowerShell `*-Location` cmdlet，如下所示。

- 若要将位置添加到位置堆栈，请使用 `Push-Location` cmdlet。

- 若要从位置堆栈获取位置，请使用 `Pop-Location` cmdlet。

- 若要显示当前位置堆栈中的位置，请使用 cmdlet 的 **stack** 参数 `Get-Location` 。 若要显示命名位置堆栈中的位置，请使用 cmdlet 的 **StackName** 参数 `Get-Location` 。

- 若要创建新的位置堆栈，请使用 cmdlet 的 **StackName** 参数 `Push-Location` 。
  如果指定不存在的堆栈， `Push-Location` 将创建堆栈。

- 若要使位置堆栈成为当前位置堆栈，请使用 cmdlet 的 **StackName** 参数 `Set-Location` 。

未命名的默认位置堆栈仅在其是当前位置堆栈时处于完全可访问状态。
如果使命名位置堆栈成为当前位置堆栈，则不能再使用 `Push-Location` 或 `Pop-Location` cmdlet 来添加或获取默认堆栈中的项，也不能使用此 cmdlet 显示未命名堆栈中的位置。 若要使未命名堆栈成为当前堆栈，请使用 cmdlet 的 **StackName** 参数，其 `Set-Location` 值为 `$null` 或空字符串 (`""`) 。

## 相关链接

[Pop-Location](Pop-Location.md)

[Push-Location](Push-Location.md)

[Set-Location](Set-Location.md)

