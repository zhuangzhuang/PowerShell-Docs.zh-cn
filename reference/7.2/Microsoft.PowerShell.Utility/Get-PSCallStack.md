---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-pscallstack?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSCallStack
ms.openlocfilehash: 607e3999a1dbe9a4f22a751f11ac93ee3f9d9409
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596411"
---
# Get-PSCallStack

## 摘要
显示当前的调用堆栈。

## SYNTAX

```
Get-PSCallStack [<CommonParameters>]
```

## DESCRIPTION

**Get-pscallstack** cmdlet 显示当前的调用堆栈。

尽管它旨在用于 PowerShell 调试器，但你可以使用此 cmdlet 在调试器外的脚本或函数中显示调用堆栈。

若要在调试器中运行 **get-pscallstack** 命令，请键入 `k` 或 `Get-PSCallStack` 。

## 示例

### 示例1：获取函数的调用堆栈

```
PS C:\> function my-alias {
$p = $args[0]
Get-Alias | where {$_.definition -like "*$p"} | format-table definition, name -auto
}
PS C:\ps-test> Set-PSBreakpoint -Command my-alias
Command    : my-alias
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : prompt PS C:\> my-alias Get-Content

Entering debug mode. Use h or ? for help.
Hit Command breakpoint on 'prompt:my-alias'
my-alias get-content
[DBG]: PS C:\ps-test> s
$p = $args[0]
DEBUG: Stepped to ':    $p = $args[0]    '
[DBG]: PS C:\ps-test> s
get-alias | Where {$_.Definition -like "*$p*"} | format-table Definition,
[DBG]: PS C:\ps-test>get-pscallstack

Name        CommandLineParameters         UnboundArguments              Location
----        ---------------------         ----------------              --------
prompt      {}                            {}                            prompt
my-alias    {}                            {get-content}                 prompt
prompt      {}                            {}                            prompt PS C:\> [DBG]: PS C:\ps-test> o
Definition  Name
----------  ----
Get-Content gc
Get-Content cat
Get-Content type
```

此命令使用 **get-pscallstack** cmdlet 来显示别名的调用堆栈，这是一个获取 cmdlet 名称的别名的简单函数。

第一个命令在 PowerShell 提示符下进入函数。
第二个命令使用 Set-PSBreakpoint cmdlet 在 My-Alias 函数上设置断点。
第三个命令使用 My-Alias 函数在 Get-Content cmdlet 的当前会话中获取所有别名。

调试器在函数调用时中断。
两个连续的 step-into (s) 命令开始逐行执行该函数。
然后，使用 **get-pscallstack** 命令来检索调用堆栈。

最后的命令是 Step-Out 命令 (o)，它退出调试器并继续执行该脚本直到完成。

## PARAMETERS

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将对象传递给此 cmdlet。

## 输出

### System.web. CallStackFrame

**Get-pscallstack** 返回一个对象，该对象表示调用堆栈中的项。

## 注释

## 相关链接

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Format-Table](Format-Table.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

