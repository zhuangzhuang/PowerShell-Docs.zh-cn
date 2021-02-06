---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: ec6f69d1d4a0b382ceec26b9409d01501edb814f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597062"
---
# Set-Location

## 摘要
将当前工作位置设置为指定的位置。

## SYNTAX

### Path（默认值）

```
Set-Location [[-Path] <String>] [-PassThru] [<CommonParameters>]
```

### LiteralPath

```
Set-Location -LiteralPath <String> [-PassThru] [<CommonParameters>]
```

### 堆栈

```
Set-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## DESCRIPTION

`Set-Location`Cmdlet 将工作位置设置为指定的位置。 该位置可以是目录、子目录、注册表位置或任何提供程序路径。

PowerShell 6.2 添加了对 `-` 和的支持， `+` 作为 **Path** 参数的值。 PowerShell 维护可使用和访问的最后20个位置的历史记录 `-` `+` 。 此列表独立于使用 **StackName** 参数访问的位置堆栈。

## 示例

### 示例1：设置当前位置

```
PS C:\> Set-Location -Path "HKLM:\"
PS HKLM:\>
```

此命令将当前位置设置为驱动器的根目录 `HKLM:` 。

### 示例2：设置当前位置并显示该位置

```
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```Output
Path
----
Env:\

PS Env:\>
```

此命令将当前位置设置为驱动器的根目录 `Env:` 。 它使用 **PassThru** 参数来指示 PowerShell 返回表示位置的 **PathInfo** 对象 `Env:\` 。

### 示例3：将位置设置为 C：驱动器中的当前位置

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

第一个命令将位置设置为 `HKLM:` 注册表提供程序中驱动器的根目录。
第二个命令将位置设置为 `C:` FileSystem 提供程序中驱动器的当前位置。
如果以格式指定驱动器名称时 `<DriveName>:` (没有反斜杠) ，则该 cmdlet 会将该位置设置为 new-psdrive 中的当前位置。
获取 New-psdrive use 命令中的当前位置 `Get-Location -PSDrive <DriveName>` 。

### 示例4：将当前位置设置为命名堆栈

```
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

第一个命令将当前位置添加到路径堆栈。
第二个命令使路径位置堆栈成为当前位置堆栈。
第三个命令显示当前位置堆栈中的位置。

`*-Location`除非在命令中指定了其他位置堆栈，否则 cmdlet 将使用当前位置堆栈。 有关位置堆栈的信息，请参阅 [注释](#notes)。

### 示例5：使用或导航位置历史记录 `+``-`

```
PS C:\> Set-Location -Path $env:SystemRoot
PS C:\Windows> Set-Location -Path Cert:\
PS Cert:\> Set-Location -Path HKLM:\
PS HKLM:\>

# Navigate back through the history using "-"
PS HKLM:\> Set-Location -Path -
PS Cert:\> Set-Location -Path -
PS C:\Windows>

# Navigate using the Set-Location alias "cd" and the implicit positional Path parameter
PS C:\Windows> cd -
PS C:\> cd +
PS C:\Windows> cd +
PS Cert:\>
```

使用别名， `cd -` 或 `cd +` 在终端中导航到位置历史记录是一种简单的方法。 有关导航的详细信息 `-` / `+` ，请参阅 **Path** 参数。

## PARAMETERS

### -LiteralPath

指定位置的路径。 **LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配字符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

返回表示位置的 **PathInfo** 对象。 默认情况下，此 cmdlet 将不产生任何输出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定新工作位置的路径。 如果未提供路径，则 `Set-Location` 默认为当前用户的主目录。 使用通配符时，该 cmdlet 将选择与通配符模式匹配的第一个路径。

PowerShell 会保留你已设置的最近20个位置的历史记录。 如果 **Path** 参数值为 `-` 字符，则新的工作位置将是历史记录中的上一个工作位置 (如果它存在) 。 同样，如果值为 `+` 字符，则新的工作位置将是历史记录中的下一个工作位置 (如果它存在) 。 这类似于使用 `Pop-Location` 和， `Push-Location` 只不过历史记录是一个列表，而不是一个堆栈，并且是隐式跟踪的，而不是手动控制的。 目前没有办法查看历史记录列表。

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -StackName

指定此 cmdlet 生成当前位置堆栈的现有位置堆栈名称。 输入位置堆栈名称。 若要指明未命名的默认位置堆栈，请键入 `$null` 或 () 的空字符串 `""` 。

`*-Location`Cmdlet 将作用于当前堆栈，除非使用 **StackName** 参数指定其他堆栈。 有关位置堆栈的详细信息，请参阅 [注释](#notes)。

```yaml
Type: System.String
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

### System.String

可以通过管道将包含路径（但不是文本路径）的字符串传递给此 cmdlet。

## 输出

### 无、System.Management.Automation.PathInfo、System.Management.Automation.PathInfoStack

除非指定 **PassThru** 参数，否则此 cmdlet 不会生成任何输出。 结合使用 **PassThru** 和 **Path** 或 **LiteralPath** 将生成一个表示新位置的 **PathInfo** 对象。 结合使用 **PassThru** 和 **StackName** 将生成表示新堆栈上下文的 **system.management.automation.pathinfostack** 对象。

## 注释

PowerShell 支持每个进程运行多个运行空间。 每个运行空间都有其自己的 _当前目录_。
这与不相同 `[System.Environment]::CurrentDirectory` 。 调用 .NET Api 或运行本机应用程序时，如果不提供显式目录路径，则可能会出现这种问题。

即使位置 cmdlet 设置了进程范围的当前目录，也不能依赖于该目录，因为另一个运行空间可能会随时更改该目录。 应使用 location cmdlet，以使用当前特定于当前运行空间的工作目录执行基于路径的操作。

`Set-Location`Cmdlet 设计用于处理由任何提供程序公开的数据。 若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md)。

堆栈是一种后进先出的列表，在其中只能访问最后添加的项。 采用要使用项的顺序将这些项添加到堆栈，然后采用相反顺序检索这些项以供使用。 PowerShell 使你能够在位置堆栈中存储提供程序位置。 PowerShell 创建一个未命名的默认位置堆栈。 可以创建多个命名的位置堆栈。 如果未指定堆栈名称，PowerShell 将使用当前位置堆栈。 默认情况下，未命名的默认位置为当前位置堆栈，但你可以使用 `Set-Location` cmdlet 来更改当前位置堆栈。

若要管理位置堆栈，请使用 `*-Location` cmdlet，如下所示：

- 若要将位置添加到位置堆栈，请使用 `Push-Location` cmdlet。

- 若要从位置堆栈获取位置，请使用 `Pop-Location` cmdlet。

- 若要显示当前位置堆栈中的位置，请使用 cmdlet 的 **stack** 参数 `Get-Location` 。 若要显示命名位置堆栈中的位置，请使用的 **StackName** 参数 `Get-Location` 。

- 若要创建新的位置堆栈，请使用的 **StackName** 参数 `Push-Location` 。 如果指定不存在的堆栈， `Push-Location` 将创建堆栈。

- 若要使某个位置堆栈成为当前位置堆栈，请使用的 **StackName** 参数 `Set-Location` 。

未命名的默认位置堆栈仅在其是当前位置堆栈时处于完全可访问状态。
如果使命名位置堆栈成为当前位置堆栈，则不能再使用 `Push-Location` 或 `Pop-Location` cmdlet 来添加或获取默认堆栈中的项，也不能使用 `Get-Location` cmdlet 来显示未命名堆栈中的位置。 若要使未命名堆栈成为当前堆栈，请使用 cmdlet 的 **StackName** 参数，其 `Set-Location` 值为 `$null` 或空字符串 (`""`) 。

## 相关链接

[Get-Location](Get-Location.md)

[Pop-Location](Pop-Location.md)

[Push-Location](Push-Location.md)

