---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimclass?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimClass
ms.openlocfilehash: 483b4b5b940a9effca99e942b86a967de5d26d68
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595395"
---
# Get-CimClass

## 摘要
获取特定命名空间中的 CIM 类的列表。

## SYNTAX

### ComputerSet (默认值) 

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

### SessionSet

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

## DESCRIPTION

`Get-CimClass`Cmdlet 将检索特定命名空间中的 CIM 类的列表。 如果未提供类名，则该 cmdlet 将返回命名空间中的所有类。 与 CIM 实例不同，CIM 类不包含从中检索它们的 CIM 会话或计算机名称。

## 示例

### 示例1：获取所有类定义

此示例获取命名空间 **root/cimv2** 下的所有类定义。

```powershell
Get-CimClass
```

### 示例2：获取具有特定名称的类

此示例获取名称中包含单词 **disk** 的类。

```powershell
Get-CimClass -ClassName *disk*
```

### 示例3：获取具有特定方法名称的类

此示例获取以名称 **Win32** 开头并且具有以 **Term** 开头的方法名称的类。

```powershell
Get-CimClass -ClassName Win32* -MethodName Term*
```

### 示例4：获取具有特定属性名称的类

此示例获取以名称 **Win32** 开头并具有名为 **Handle** 的属性的类。

```powershell
Get-CimClass -ClassName Win32* -PropertyName Handle
```

### 示例5：获取具有特定限定符名称的类

此示例获取以名称 **Win32** 开头的类，在其名称中包含单词 **Disk** ，并具有指定的限定符 **关联**。

```powershell
Get-CimClass -ClassName Win32*Disk* -QualifierName Association
```

### 示例6：获取特定命名空间中的类定义

此示例从指定的命名空间 **root/standardCimv2** 获取名称中包含单词 **Net** 的类定义。

```powershell
Get-CimClass -Namespace root/standardCimv2 -ClassName *Net*
```

### 示例7：从远程服务器获取类定义

此示例从指定远程服务器 **Server01** 和 **Server02** 中获取名称中包含单词 **disk** 的类定义。

```powershell
Get-CimClass -ClassName *disk* -ComputerName Server01, Server02
```

### 示例8：使用 CIM 会话获取类

```powershell
$s = New-CimSession -ComputerName Server01, Server02
Get-CimClass -ClassName *disk* -CimSession $s
```

此组命令创建一个与多台计算机的会话，并使用 cmdlet 将其存储在变量中 `$s` `New-CimSession` ，然后使用 cmdlet 获取类 `Get-CimClass` 。

## PARAMETERS

### -CimSession

在远程会话中或在远程计算机上运行 cmdlet。 输入计算机名或会话对象，例如 `New-CimSession` 或 cmdlet 的输出 `Get-CimSession` 。 默认为本地计算机上的当前会话。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: SessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

指定要对其执行操作的 CIM 类的名称。 您可以使用 tab 自动补全来浏览类列表，因为 PowerShell 从本地 WMI 服务器获取类的列表以提供类名的列表。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ComputerName

指定要在其上运行 CIM 操作的计算机。 可以指定完全限定的域名 (FQDN) NetBIOS 名称或 IP 地址。

如果指定此参数，则该 cmdlet 将使用 WsMan 协议创建到指定计算机的临时会话。

如果未指定此参数，则该 cmdlet 将使用组件对象模型 (COM) 在本地计算机上执行操作。

如果在同一台计算机上执行多个操作，则使用 CIM 会话可提供更好的性能。

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -方法名称

查找具有与此名称匹配的方法的类。 可以将通配符用于此参数。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Namespace

指定 CIM 操作的命名空间。 默认命名空间为 **root/cimv2**。 您可以使用 tab 自动补全来浏览命名空间列表，因为 PowerShell 从本地 WMI 服务器获取命名空间列表以提供命名空间列表。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

指定 cmdlet 等待计算机响应的时间量。 默认情况下，此参数的值为0，表示该 cmdlet 使用服务器的默认超时值。

如果 **OperationTimeoutSec** 参数设置为小于3分钟的稳定连接重试超时值，则不能恢复最后超过 **OperationTimeoutSec** 参数值的网络故障，因为在客户端重新连接之前，服务器上的操作将超时。

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PropertyName

查找具有与此名称匹配的属性的类。 可以将通配符用于此参数。

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

### -QualifierName

按类级别限定符名称筛选类。 可以将通配符用于此参数。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

此 cmdlet 不接受输入对象。

## 输出

### CimClass。

此 cmdlet 将返回一个 CIM 类对象。

## 注释

## 相关链接

[New-CimSession](New-CimSession.md)

