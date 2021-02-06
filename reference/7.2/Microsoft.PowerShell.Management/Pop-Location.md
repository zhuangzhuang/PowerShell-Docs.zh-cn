---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/pop-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Pop-Location
ms.openlocfilehash: 8a44849f27de80ece486b573f1adccafab51972a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596025"
---
# Pop-Location

## 摘要
将当前位置更改为最近推入到堆栈中的位置。

## SYNTAX

```
Pop-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## DESCRIPTION

`Pop-Location`Cmdlet 使用 cmdlet 将当前位置更改为最近推入堆栈的位置 `Push-Location` 。 你可以从默认堆栈或使用命令创建的堆栈中弹出位置 `Push-Location` 。

## 示例

### 示例 1：更改为最近位置

```
PS C:\> Pop-Location
```

此命令将你的位置更改为最近添加到当前堆栈中的位置。

### 示例 2：更改为命名堆栈中的最近位置

```
PS C:\> Pop-Location -StackName "Stack2"
```

此命令将你的位置更改为最近添加到 Stack2 位置堆栈中的位置。

有关位置堆栈的详细信息，请参阅 [注释](#notes)。

### 示例 3：在不同提供程序的位置之间移动

```
PS C:\> pushd HKLM:\Software\Microsoft\PowerShell
PS HKLM:\Software\Microsoft\PowerShell> pushd Cert:\LocalMachine\TrustedPublisher
PS cert:\LocalMachine\TrustedPublisher> popd
PS HKLM:\Software\Microsoft\PowerShell> popd
PS C:\>
```

这些命令使用 `Push-Location` 和 `Pop-Location` cmdlet 在不同 PowerShell 提供程序支持的位置之间移动。 命令使用的 `pushd` 别名 `Push-Location` 和的 `popd` 别名 `Pop-Location` 。

第一个命令将当前文件系统位置推送到堆栈上，并移到 PowerShell 注册表提供程序支持的 HKLM 驱动器。

第二个命令将注册表位置推送到堆栈上，并移到 PowerShell 证书提供程序支持的位置。

最后两个命令将这些位置弹出堆栈。 第一个 `popd` 命令返回到注册表驱动器，第二个命令返回到文件系统驱动器。

## PARAMETERS

### -PassThru

将表示位置的对象传递到管道。 默认情况下，此 cmdlet 将不产生任何输出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StackName

指定弹出位置的位置堆栈。 输入位置堆栈名称。

如果没有此参数，则 `Pop-Location` 从当前位置堆栈中弹出位置。 默认情况下，当前位置堆栈是 PowerShell 创建的未命名的默认位置堆栈。 若要使位置堆栈成为当前位置堆栈，请使用 cmdlet 的 **StackName** 参数 `Set-Location` 。 有关位置堆栈的详细信息，请参阅 [注释](#notes)。

`Pop-Location` 无法从未命名的默认堆栈中弹出位置，除非该堆栈为当前位置堆栈。

```yaml
Type: System.String
Parameter Sets: (All)
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

### 无，System.Management.Automation.PathInfo

如果指定 **PassThru** 参数，则此 cmdlet 生成表示位置的 **System.Management.Automation.PathInfo** 对象。 否则，此 cmdlet 将不生成任何输出。

## 注释

PowerShell 支持每个进程运行多个运行空间。 每个运行空间都有其自己的 _当前目录_。
这与不相同 `[System.Environment]::CurrentDirectory` 。 调用 .NET Api 或运行本机应用程序时，如果不提供显式目录路径，则可能会出现这种问题。

即使位置 cmdlet 设置了进程范围的当前目录，也不能依赖于该目录，因为另一个运行空间可能会随时更改该目录。 应使用 location cmdlet，以使用当前特定于当前运行空间的工作目录执行基于路径的操作。

堆栈是一种后进先出的列表，在其中只能访问最后添加的项。 采用要使用项的顺序将这些项添加到堆栈，然后采用相反顺序检索这些项以供使用。 PowerShell 使你能够在位置堆栈中存储提供程序位置。

PowerShell 创建一个未命名的默认位置堆栈，你可以创建多个命名的位置堆栈。 如果未指定堆栈名称，PowerShell 将使用当前位置堆栈。 默认情况下，未命名的默认位置为当前位置堆栈，但你可以使用 `Set-Location` cmdlet 来更改当前位置堆栈。

若要管理位置堆栈，请使用 PowerShell `*-Location` cmdlet，如下所示：

- 若要将位置添加到位置堆栈，请使用 `Push-Location` cmdlet。

- 若要从位置堆栈获取位置，请使用 `Pop-Location` cmdlet。

- 若要显示当前位置堆栈中的位置，请使用 cmdlet 的 **stack** 参数 `Get-Location` 。

- 若要显示命名位置堆栈中的位置，请使用 cmdlet 的 **StackName** 参数 `Get-Location` 。

- 若要创建新的位置堆栈，请使用 cmdlet 的 **StackName** 参数 `Push-Location` 。 如果指定不存在的堆栈， `Push-Location` 将创建堆栈。

- 若要使位置堆栈成为当前位置堆栈，请使用 cmdlet 的 **StackName** 参数 `Set-Location` 。

未命名的默认位置堆栈仅在其是当前位置堆栈时处于完全可访问状态。
如果使命名位置堆栈成为当前位置堆栈，则不能再使用 `Push-Location` 或 `Pop-Location` cmdlet 来添加或获取默认堆栈中的项，也不能使用 `Get-Location` cmdlet 来显示未命名堆栈中的位置。 若要使未命名堆栈成为当前堆栈，请使用 cmdlet 的 **StackName** 参数，其 `Set-Location` 值为 `$Null` 或空字符串 (`""`) 。

还可以 `Pop-Location` 通过其内置别名来引用 `popd` 。 有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

`Pop-Location` 设计用于处理由任何提供程序公开的数据。 若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相关链接

[Get-Location](Get-Location.md)

[Push-Location](Push-Location.md)

[Set-Location](Set-Location.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
