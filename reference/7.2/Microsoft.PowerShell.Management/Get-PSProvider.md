---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: 20820d2d194f41d43048c9617b63b9acb3fbb4f8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598879"
---
# Get-PSProvider

## 摘要
获取有关指定 PowerShell 提供程序的信息。

## SYNTAX

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Get-PSProvider`Cmdlet 将获取当前会话中的 PowerShell 提供程序。
可以获取会话中的特定驱动器或所有驱动器。

PowerShell 提供程序使你可以访问各种数据存储，就好像它们是文件系统驱动器一样。
有关 PowerShell 提供程序的信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 示例

### 示例1：显示所有可用提供程序的列表

```powershell
Get-PSProvider
```

此命令显示所有可用 PowerShell 提供程序的列表。

### 示例2：显示以指定字母开头的所有 PowerShell 提供程序的列表

```powershell
Get-PSProvider f*, r* | Format-List
```

此命令显示其名称以字母 "f" 或 "r" 开头的所有 PowerShell 提供程序的列表。

### 示例3：查找将提供程序添加到会话的管理单元或模块

```powershell
Get-PSProvider | Format-Table name, module, pssnapin -auto
```

```Output
Name        Module       PSSnapIn
----        ------       --------
Test        TestModule
WSMan                    Microsoft.WSMan.Management
Alias                    Microsoft.PowerShell.Core
Environment              Microsoft.PowerShell.Core
FileSystem               Microsoft.PowerShell.Core
Function                 Microsoft.PowerShell.Core
Registry                 Microsoft.PowerShell.Core
Variable                 Microsoft.PowerShell.Core
Certificate              Microsoft.PowerShell.Security
```

```powershell
Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}
```

```Output
Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

这些命令将查找向会话添加提供程序的 PowerShell 管理单元或模块。
所有 PowerShell 元素（包括提供程序）均源自管理单元或模块。

这些命令使用返回的 **ProviderInfo** 对象的 Add-pssnapin 和 Module 属性 `Get-PSProvider` 。
这些属性的值包含添加提供程序的管理单元或模块的名称。

第一个命令获取会话中的所有提供程序，并将它们的格式设置为表，其中显示其 Name、Module 和 PSSnapin 属性的值。

第二个命令使用 `Where-Object` cmdlet 来获取来自 **Microsoft. Security** 管理单元的提供程序。

### 示例4：解析文件系统提供程序的 Home 属性的路径

```powershell
C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

```powershell
PS C:\> (get-psprovider FileSystem).home
```

```Output
C:\Users\User01
```

此示例显示波形符 (~) 表示 FileSystem 提供程序的 **Home** 属性的值。
**Home** 属性值是可选的，但对于 **FileSystem** 提供程序，其定义为 `$env:homedrive\$env:homepath` 或 `$home` 。

## PARAMETERS

### -PSProvider

指定此 cmdlet 从中获取信息的 PowerShell 提供程序的名称。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### String[]

可以通过管道将一个或多个提供程序名称字符串传递给此 cmdlet。

## 输出

### System.web. ProviderInfo

此 cmdlet 返回表示会话中 PowerShell 提供程序的对象。

## 注释

## 相关链接

