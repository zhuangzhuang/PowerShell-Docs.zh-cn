---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Error
ms.openlocfilehash: 7e4f4adf60a4f6386c646d92ada0003f239f05f4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603392"
---
# Get-Error

## 摘要

获取并显示当前会话中最近的错误消息。

## SYNTAX

### 最新 (默认值) 

```
Get-Error [[-Newest] <Int32>] [<CommonParameters>]
```

### 错误

```
Get-Error [-InputObject <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

该 `Get-Error` cmdlet 将获取一个 **PSExtendedError** 对象，该对象表示会话中发生的最后一个错误的当前错误详细信息。

您可以使用 `Get-Error` 来显示在当前会话中使用 **最新** 参数发生的指定数量的错误。

该 `Get-Error` cmdlet 还从集合接收错误对象，例如 `$Error` ，用于显示当前会话中的多个错误。

## 示例

### 示例1：获取最新的错误详细信息

在此示例中， `Get-Error` 显示当前会话中发生的最新错误的详细信息。

```powershell
Get-Childitem -path /NoRealDirectory
Get-Error
```

```
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.

Exception             :
    ErrorRecord          :
        Exception             :
            Message : Cannot find path 'C:\NoRealDirectory' because it does not exist.
            HResult : -2146233087
        TargetObject          : C:\NoRealDirectory
        CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [], ParentContainsErrorRecordException
        FullyQualifiedErrorId : PathNotFound
    ItemName             : C:\NoRealDirectory
    SessionStateCategory : Drive
    TargetSite           :
        Name          : GetChildItems
        DeclaringType : System.Management.Automation.SessionStateInternal
        MemberType    : Method
        Module        : System.Management.Automation.dll
    StackTrace           :
   at System.Management.Automation.SessionStateInternal.GetChildItems(String path, Boolean recurse, UInt32 depth,
CmdletProviderContext context)
   at System.Management.Automation.ChildItemCmdletProviderIntrinsics.Get(String path, Boolean recurse, UInt32
depth, CmdletProviderContext context)
   at Microsoft.PowerShell.Commands.GetChildItemCommand.ProcessRecord()
    Message              : Cannot find path 'C:\NoRealDirectory' because it does not exist.
    Source               : System.Management.Automation
    HResult              : -2146233087
TargetObject          : C:\NoRealDirectory
CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [Get-ChildItem], ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
InvocationInfo        :
    MyCommand        : Get-ChildItem
    ScriptLineNumber : 1
    OffsetInLine     : 1
    HistoryId        : 57
    Line             : Get-Childitem -path c:\NoRealDirectory
    PositionMessage  : At line:1 char:1
                       + Get-Childitem -path c:\NoRealDirectory
                       + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    InvocationName   : Get-Childitem
    CommandOrigin    : Internal
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo :
```

### 示例2：获取当前会话中发生的指定数量的错误消息

此示例演示如何将 `Get-Error` 与 **最新** 参数一起使用。 在此示例中， **最新** 返回此会话中发生的3个最新错误的详细信息。

```powershell
Get-Error -Newest 3
```

### 示例3：发送错误集合以接收详细消息

`$Error`自动变量包含当前会话中的错误对象的数组。 可以通过管道将对象数组发送到 `Get-Error` ，以接收详细的错误消息。

在此示例中， `$Error` 将通过管道传递给 `Get-Error` cmdlet。 结果为详细的错误消息列表，类似于示例1的结果。

```powershell
$Error | Get-Error
```

## PARAMETERS

### -Newest

指定当前会话中已发生的错误数。

```yaml
Type: System.Int32
Parameter Sets: Newest
Aliases: Last

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

此参数用于管道输入。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Error
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### PSObject

支持来自任何 **PSObject** 的输入，但结果不同，除非提供了 **ErrorRecord** 或 **Exception** 对象。

## 输出

### ErrorRecord # PSExtendedError。

**PSExtendedError** 对象中的输出。

## 注释

`Get-Error` 接受管道输入。 例如，`$Error | Get-Error`。

## 相关链接

[about_Try_Catch_Finally](../Microsoft.PowerShell.Core/About/about_Try_Catch_Finally.md)
