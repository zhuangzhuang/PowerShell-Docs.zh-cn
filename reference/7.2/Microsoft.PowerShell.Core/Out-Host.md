---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Host
ms.openlocfilehash: 4fefb133416b3db6c19c71a916d73fe00f86f3a4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596833"
---
# Out-Host

## 摘要
将输出发送到命令行。

## SYNTAX

### 全部

```
Out-Host [-Paging] [-InputObject <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

`Out-Host`Cmdlet 将输出发送到 PowerShell 主机以供显示。 该主机在命令行上显示输出。 由于 `Out-Host` 是默认值，因此除非你想要使用其参数，否则无需指定它。

`Out-Host` 将自动追加到每个执行的命令。 它将管道的输出传递给执行命令的主机。 `Out-Host` 忽略 ANSI 转义序列。 转义序列由主机处理。 `Out-Host` 将 ANSI 转义序列传递到主机，而不尝试解释或更改它们。

## 示例

### 示例1：每次显示一页输出

此示例显示系统每次处理一页。

```powershell
Get-Process | Out-Host -Paging
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     30    24.12      36.95      15.86   21004  14 ApplicationFrameHost
     55    24.33      60.48      10.80   12904  14 BCompare
<SPACE> next page; <CR> next line; Q quit
      9     4.71       8.94       0.00   16864  14 explorer
<SPACE> next page; <CR> next line; Q quit
```

`Get-Process` 获取系统进程，并沿管道向下发送对象。 `Out-Host` 使用 **分页** 参数一次显示一页数据。

### 示例2：使用变量作为输入

此示例使用变量中存储的对象作为的输入 `Out-Host` 。

```powershell
$io = Get-History
Out-Host -InputObject $io
```

`Get-History` 获取 PowerShell 会话的历史记录，并将对象存储在 `$io` 变量中。
`Out-Host` 使用 **InputObject** 参数指定 `$io` 变量并显示历史记录。

## PARAMETERS

### -InputObject

指定要写入控制台的对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Paging

指示 `Out-Host` 每次显示一个输出页，并等待用户输入，然后显示剩余页面。 默认情况下，所有输出都显示在单个页面上。 页大小由主机的特征确定。

按 <kbd>空格键</kbd> 显示下一页输出，或按 <kbd>enter</kbd> 键查看下一个输出行。 按 <kbd>Q</kbd> 退出。

**分页** 类似于 " **更多** " 命令。

> [!NOTE]
> PowerShell ISE 主机不支持 **分页** 参数。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以将对象向下发送到 `Out-Host` 。

## 输出

### 无

`Out-Host` 不会生成任何输出。 它将对象发送到主机以便显示。

## 注释

所有 PowerShell 主机均不支持 **分页** 参数。 例如，如果在 PowerShell ISE 中使用 **寻呼** 参数，则会显示以下错误： `out-lineoutput : The method or operation is not implemented.`

包含 **Out** 谓词的 cmdlet `Out-` 不设置对象的格式。 它们呈现对象并将其发送到指定的显示目标。 如果将无格式对象发送到 `Out-` cmdlet，则该 cmdlet 会在呈现该对象之前将其发送到格式设置 cmdlet。

`Out-`Cmdlet 没有用于名称或文件路径的参数。 若要将数据发送到 `Out-` cmdlet，请使用管道将 PowerShell 命令的输出发送到 cmdlet。 或者，可以将数据存储在变量中，并使用 **InputObject** 参数将数据传递给 cmdlet。

`Out-Host` 发送数据，但不生成任何输出对象。 如果将的输出通过管道 `Out-Host` 进行管道 `Get-Member` ，则会 `Get-Member` 报告未指定任何对象。

## 相关链接

[Clear-Host](Clear-Host.md)

[Out-Default](Out-Default.md)

[Out-File](../Microsoft.PowerShell.Utility/Out-File.md)

[Out-Null](Out-Null.md)

[Out-printer](../Microsoft.PowerShell.Utility/Out-Printer.md)

[Out-String](../Microsoft.PowerShell.Utility/Out-String.md)

[Write-Host](../Microsoft.PowerShell.Utility/Write-Host.md)

