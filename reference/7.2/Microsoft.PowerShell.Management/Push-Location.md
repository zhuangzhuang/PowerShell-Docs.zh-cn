---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/push-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Push-Location
ms.openlocfilehash: eaa7622e29680de4228579f8b77a6c829a586bf8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595634"
---
# Push-Location

## 摘要
将当前位置添加到位置堆栈的顶部。

## SYNTAX

### Path（默认值）

```
Push-Location [[-Path] <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

### LiteralPath

```
Push-Location [-LiteralPath <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## DESCRIPTION

`Push-Location`Cmdlet 将 ( "推送" ) 当前位置添加到位置堆栈上。 如果指定路径，则 `Push-Location` 将当前位置推送到位置堆栈上，然后将当前位置更改为路径指定的位置。 可以使用 `Pop-Location` cmdlet 从位置堆栈中获取位置。

默认情况下，该 `Push-Location` cmdlet 将当前位置推入当前位置堆栈，但你可以使用 **StackName** 参数来指定备用位置堆栈。 如果堆栈不存在，则 `Push-Location` 创建它。

有关位置堆栈的详细信息，请参阅 [注释](#notes)。

## 示例

### 示例 1

此示例将当前位置推入到默认位置堆栈中，然后将位置更改为 `C:\Windows` 。

```
PS C:\> Push-Location C:\Windows
```

### 示例 2

此示例将当前位置推送到 RegFunction 堆栈上，并将当前位置更改为该 `HKLM:\Software\Policies` 位置。

```
PS C:\> Push-Location HKLM:\Software\Policies -StackName RegFunction
```

可以在任何 PowerShell 驱动器中使用 Location cmdlet (New-psdrive) 。

### 示例 3

此命令将当前位置推入到默认堆栈中。 它不会更改位置。

```
PS C:\> Push-Location
```

### 示例 4-创建并使用命名堆栈

这些命令展示了如何创建和使用已命名的位置堆栈。

```
PS C:\> Push-Location ~ -StackName Stack2
PS C:\Users\User01> Pop-Location -StackName Stack2
PS C:\>
```

第一个命令将当前位置推入到名为 Stack2 的新堆栈中，然后将当前位置更改为主目录，该目录在命令中用颚化符符号 (`~`) ，在 FileSystem 提供程序驱动器上使用的是与 `$HOME` 和等效的 `$env:USERPROFILE` 。

如果会话中尚不存在 Stack2，则将 `Push-Location` 创建它。 第二个命令使用 `Pop-Location` cmdlet `C:\` 从 Stack2 堆栈中弹出原始位置 () 。 如果没有 **StackName** 参数，则 `Pop-Location` 将从未命名的默认堆栈中弹出位置。

有关位置堆栈的详细信息，请参阅 [注释](#notes)。

## PARAMETERS

### -LiteralPath

指定新位置的路径。 与 **Path** 参数不同，**LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

将表示位置的对象传递到管道。 默认情况下，此 cmdlet 将不产生任何输出。

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

在此命令将当前位置添加（推入）到堆栈顶部之后，将把你的位置更改到由此路径指定的位置。 输入其提供程序支持此 cmdlet 的任何位置的路径。 允许使用通配符。 参数名为可选项。

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -StackName

指定要将当前位置添加到的位置堆栈。 输入位置堆栈名称。
如果堆栈不存在，则 `Push-Location` 创建它。

如果没有此参数， `Push-Location` 则会将位置添加到当前位置堆栈。 默认情况下，当前位置堆栈是 PowerShell 创建的未命名的默认位置堆栈。
若要使位置堆栈成为当前位置堆栈，请使用 cmdlet 的 **StackName** 参数 `Set-Location` 。 有关位置堆栈的详细信息，请参阅 [注释](#notes)。

> [!NOTE]
> `Push-Location` 无法将某个位置添加到未命名的默认堆栈中，除非该堆栈为当前位置堆栈。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default stack
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

你可以通过管道将包含路径 (但不) 文本路径的字符串传递给 `Push-Location` 。

## 输出

### 无或 System.Management.Automation.PathInfo

当使用 **PassThru** 参数时，将 `Push-Location` 生成表示位置的 **PathInfo** 对象。 否则，此 cmdlet 将不生成任何输出。

## 注释

PowerShell 支持每个进程运行多个运行空间。 每个运行空间都有其自己的 _当前目录_。
这与不相同 `[System.Environment]::CurrentDirectory` 。 调用 .NET Api 或运行本机应用程序时，如果不提供显式目录路径，则可能会出现这种问题。

即使位置 cmdlet 设置了进程范围的当前目录，也不能依赖于该目录，因为另一个运行空间可能会随时更改该目录。 应使用 location cmdlet，以使用当前特定于当前运行空间的工作目录执行基于路径的操作。

堆栈是后进先出的列表，其中只有最近添加的项是可访问的。
采用要使用项的顺序将这些项添加到堆栈，然后采用相反顺序检索这些项以供使用。 PowerShell 使你能够在位置堆栈中存储提供程序位置。

PowerShell 创建一个未命名的默认位置堆栈，你可以创建多个命名的位置堆栈。 如果未指定堆栈名称，PowerShell 将使用当前位置堆栈。 默认情况下，未命名的默认位置为当前位置堆栈，但你可以使用 `Set-Location` cmdlet 来更改当前位置堆栈。

若要管理位置堆栈，请使用 PowerShell 位置 cmdlet，如下所示。

- 若要将位置添加到位置堆栈，请使用 `Push-Location` cmdlet。

- 若要从位置堆栈获取位置，请使用 `Pop-Location` cmdlet。

- 若要显示当前位置堆栈中的位置，请使用 cmdlet 的 **stack** 参数 `Get-Location` 。

- 若要显示命名位置堆栈中的位置，请使用 cmdlet 的 **StackName** 参数 `Get-Location` 。

- 若要创建新的位置堆栈，请使用 cmdlet 的 StackName 参数 `Push-Location` 。 如果指定不存在的堆栈， `Push-Location` 将创建堆栈。

- 若要使位置堆栈成为当前位置堆栈，请使用 cmdlet 的 StackName 参数 `Set-Location` 。

未命名的默认位置堆栈仅在其是当前位置堆栈时处于完全可访问状态。
如果使命名位置堆栈成为当前位置堆栈，则不能再使用 `Push-Location` 或 `Pop-Location` cmdlet 来添加或获取默认堆栈中的项，也不能使用 `Get-Location` cmdlet 来显示未命名堆栈中的位置。 若要使未命名堆栈成为当前堆栈，请使用 cmdlet 的 **StackName** 参数，其 `Set-Location` 值为 `$null` 或空字符串 (`""`) 。

还可以 `Push-Location` 通过其内置别名来引用 `pushd` 。 有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

`Push-Location`Cmdlet 设计用于处理由任何提供程序公开的数据。 若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相关链接

[Get-Location](Get-Location.md)

[Pop-Location](Pop-Location.md)

[Set-Location](Set-Location.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
