---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: 78691b806fe68aaa8d9e502d28e6f3967867f95b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597853"
---
# Get-PSBreakpoint

## 摘要
获取在当前会话中设置的断点。

## SYNTAX

### 脚本 (默认值) 

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### 变量

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### 命令

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### 类型

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### ID

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## DESCRIPTION

**Set-psbreakpoint** cmdlet 获取在当前会话中设置的断点。
可以使用该 cmdlet 参数获取特定断点。

断点是命令或脚本中的一个点，在该点处将暂时停止执行，以便你可以检查指令。
**Set-psbreakpoint** 是为调试 PowerShell 脚本和命令而设计的几个 cmdlet 之一。 有关 PowerShell 调试器的详细信息，请参阅 about_Debuggers。

## 示例

### 示例1：获取所有脚本和函数的所有断点

```
PS C:\> Get-PSBreakpoint
```

此命令获取在当前会话中所有脚本和函数上设置的所有断点。

### 示例2：按 ID 获取断点

```
PS C:\> Get-PSBreakpoint -Id 2
Function   :
IncrementAction     :
Enabled    :
TrueHitCount   : 0
Id         : 2
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

此命令获取断点 ID 为 2 的断点。

### 示例3：通过管道将 ID 发送到 Get-PSBreakpoint

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

这些命令演示如何通过将断点 ID 通过管道传递给 **set-psbreakpoint** 来获取断点。

第一个命令使用 Set-PSBreakpoint cmdlet 在 Sample.ps1 脚本中的 Increment 函数上创建断点。 它将断点对象保存在 $B 变量中。

第二个命令使用点运算符 ( ) 获取 $B 变量中断点对象的 Id 属性。 它使用管道运算符 (|) 将 ID 发送到 **set-psbreakpoint** cmdlet。

因此， **set-psbreakpoint** 将获取具有指定 ID 的断点。

### 示例4：获取指定脚本文件中的断点

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

此命令获取 Sample.ps1 和 SupportScript.ps1 文件中的所有断点。

此命令不会获取可能在会话中的其他脚本或函数上设置的其他断点。

### 示例5：在指定的 cmdlet 中获取断点

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

此命令获取在 Sample.ps1 文件中的 Read-Host 或 Write-Host 命令上设置的所有 Command 断点。

### 示例6：在指定的文件中获取命令断点

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

此命令获取 Sample.ps1 文件中的所有 Command 断点。

### 示例7：按变量获取断点

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

此命令获取在当前会话中的 $Index 和 $Swap 变量上设置的断点。

### 示例8：获取文件中的所有行断点和变量断点

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

此命令获取 Sample.ps1 脚本中的所有行断点和变量断点。

## PARAMETERS

### -Command

指定在指定命令名称上设置的命令断点的数组。
输入命令名称，例如 cmdlet 或函数的名称。

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定此 cmdlet 获取的断点 Id。
将 ID 输入以逗号分隔的列表中。
还可以通过管道将断点 Id 传递给 **set-psbreakpoint**。

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Script

指定包含断点的脚本数组。
输入一个或多个脚本文件的路径 (可选) 和名称。
如果省略路径，则默认位置为当前目录。

```yaml
Type: System.String[]
Parameter Sets: Script, Variable, Command, Type
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Type

指定此 cmdlet 获取的断点类型的数组。
输入一个或多个类型。
此参数的可接受值为：

- 折线图
- 命令
- 变量

还可以通过管道将断点类型传递给 **set-psbreakpoint**。

```yaml
Type: Microsoft.PowerShell.Commands.BreakpointType[]
Parameter Sets: Type
Aliases:
Accepted values: Line, Variable, Command

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Variable

指定在指定变量名称上设置的变量断点数组。
输入不带美元符号的变量名称。

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216) 。

## 输入

### System.object、BreakpointType 的命令

可以通过管道将断点 Id 和断点类型传递给 **set-psbreakpoint**。

## 输出

### System.Management.Automation.Breakpoint

**Set-psbreakpoint** 返回表示会话中的断点的对象。

## 注释

* 可以使用 **set-psbreakpoint** 或其别名 "gbp"。

## 相关链接

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

