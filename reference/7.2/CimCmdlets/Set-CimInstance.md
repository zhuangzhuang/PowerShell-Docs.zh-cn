---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/set-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-CimInstance
ms.openlocfilehash: 041ef2d5b5541c250b98003099fe58018df155c2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595606"
---
# Set-CimInstance

## 摘要
通过调用 CIM 类的 ModifyInstance 方法，修改 CIM 服务器上的 CIM 实例。

## SYNTAX

### CimInstanceComputerSet (默认值) 

```
Set-CimInstance [-ComputerName <String[]>] [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimInstanceSessionSet

```
Set-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### QuerySessionSet

```
Set-CimInstance -CimSession <CimSession[]> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### QueryComputerSet

```
Set-CimInstance [-ComputerName <String[]>] [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

此 cmdlet 修改 CIM 服务器上的 CIM 实例。

如果未指定 **InputObject** 参数，该 cmdlet 将采用以下方法之一：

- 如果 **ComputerName** 参数和 **CimSession** 参数均未指定，则此 cmdlet 将在本地 Windows Management Instrumentation (WMI) 使用组件对象模型 (COM) 会话。
- 如果指定 **computername** 参数或 **CimSession** 参数，则此 cmdlet 适用于 **ComputerName** 参数或 **CimSession** 参数指定的 CIM 服务器。

如果指定了 **InputObject** 参数，该 cmdlet 将采用以下方法之一：

- 如果 **ComputerName** 参数和 **CimSession** 参数均未指定，则此 cmdlet 将使用输入对象中的 CIM 会话或计算机名称。
- 如果指定了 **ComputerName** 参数或 **CimSession** 参数，则此 cmdlet 将使用 **CimSession** 参数值或 **ComputerName** 参数值。 这并不是很常见。

## 示例

### 示例1：设置 CIM 实例

此示例使用 **Query** 参数将 **VariableValue** 属性的值设置为 **abcd** 。 您可以 (WQL) 查询中修改匹配 Windows Management Instrumentation 查询语言的实例。

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"}
```

### 示例2：使用管道设置 CIM 实例属性

此示例使用 cmdlet 检索由 **查询** 参数筛选的 CIM 实例对象 `Get-CimInstance` 。 `Set-CimInstance`Cmdlet 将 **VariableValue** 属性的值修改为 **abcd**。

```powershell
Get-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' |
  Set-CimInstance -Property @{VariableValue="abcd"}
```

### 示例3：使用输入对象设置 CIM 实例属性

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where Name="testvar"'
Set-CimInstance -InputObject $x -Property @{VariableValue="somevalue"} -PassThru
```

此示例使用在中将查询参数筛选的 CIM 实例对象检索到变量 `$x` `Get-CimInstance` ，然后将该变量的内容传递给 `Set-CimInstance` cmdlet。 `Set-CimInstance` 然后将 **VariableValue** 属性修改为 **somevalue**。 由于使用的是 **Passthru** 参数，此示例将返回一个已修改的 CIM 实例对象。

### 示例4：设置 CIM 实例属性

此示例使用 cmdlet 将 **查询** 参数中指定的 CIM 实例对象检索到变量中 `$x` `Get-CimInstance` ，并更改要更改的对象的 **VariableValue** 属性值。 然后，使用 cmdlet 保存 CIM 实例对象 `Set-CimInstance` 。
由于使用的是 **Passthru** 参数，此示例将返回一个已修改的 CIM 实例对象。

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where name="testvar"'
$x.VariableValue = "Change"
Set-CimInstance -CimInstance $x -PassThru
```

### 示例5：显示要使用 WhatIf 修改的 CIM 实例列表

此示例使用通用参数 **WhatIf** 来指定不应完成修改，但仅输出在完成后会发生的情况。

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -WhatIf
```

### 示例6：在用户确认后设置 CIM 实例

此示例使用 common 参数 **Confirm** 来指定仅应在用户确认后进行修改。

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -Confirm
```

### 示例7：设置创建的 CIM 实例

此示例使用 cmdlet 创建具有指定属性的 CIM 实例 `New-CimInstance` ，并将其内容检索到变量中 `$x` 。 然后，将变量传递给 `Set-CimInstance` cmdlet，这会将 **VariableValue** 属性的值修改为 **somevalue**。
由于使用的是 **Passthru** 参数，此示例将返回一个已修改的 CIM 实例对象。

```powershell
$x = New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";UserName="domain\user"} -Keys Name,UserName -ClientOnly
Set-CimInstance -CimInstance $x -Property @{VariableValue="somevalue"} -PassThru
```

## PARAMETERS

### -CimSession

在远程计算机上运行 cmdlet。 输入计算机名或会话对象，例如 `New-CimSession` 或 cmdlet 的输出 `Get-CimSession` 。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimInstanceSessionSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName

指定要在其上运行 CIM 操作的计算机的名称。 可以指定完全限定的域名 (FQDN) 或 NetBIOS 名称。

如果未指定此参数，则该 cmdlet 将使用组件对象模型 (COM) 在本地计算机上执行操作。

如果指定此参数，则该 cmdlet 将使用 WsMan 协议创建到指定计算机的临时会话。

如果在同一台计算机上执行多个操作，则使用 CIM 会话进行连接可以提高性能。

```yaml
Type: System.String[]
Parameter Sets: CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要用作输入的 CIM 实例对象。

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Namespace

指定 CIM 操作的命名空间。 默认命名空间为 root/cimv2。 您可以使用 tab 自动补全来浏览命名空间列表，因为 PowerShell 从本地 WMI 服务器获取命名空间列表以提供命名空间列表。

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
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
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

返回一个代表你所处理的项目的对象。 默认情况下，此 cmdlet 将不产生任何输出。

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

### -Property

使用) 的名称-值对将 CIM 实例的属性指定为哈希表 (。 仅更改使用此参数指定的属性。 CIM 实例的其他属性不会更改。

```yaml
Type: System.Collections.IDictionary
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet, QuerySessionSet, QueryComputerSet
Aliases: Arguments

Required: True (QuerySessionSet, QueryComputerSet), False (CimInstanceComputerSet, CimInstanceSessionSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Query

指定要在 CIM 服务器上运行的查询，以检索要在其上运行 cmdlet 的 CIM 实例。 您可以使用 QueryDialect 参数指定查询方言。

如果指定的值包含双引号 (`"`) 、单引号 (`'`) 或反斜杠 (`\`) ，则必须使用反斜杠 () 字符作为前缀，来对这些字符进行转义 `\` 。 如果指定的值使用 WQL **LIKE** 运算符，则必须通过将以下字符括在方括号中来对其进行转义 (`[]`) ：百分比 (`%`) 、下划线 (`_`) 或左方括号 (`[`) 。

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QueryDialect

指定用于查询参数的查询语言。 此参数的可接受值为： **WQL** 或 **CQL**。 默认值为 **WQL**。

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

指定资源类或实例 (URI) 的资源统一资源标识符。 URI 用于标识计算机上特定类型的资源，例如磁盘或进程。

URI 由前缀和指向资源的路径组成。 例如：

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

默认情况下，如果不指定此参数，则将使用 DMTF 标准资源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 并向其追加类名称。

ResourceURI 只能与使用 WSMan 协议创建的 CIM 会话一起使用，也可以在指定 ComputerName 参数时使用，后者使用 WSMan 创建 CIM 会话。 如果在不指定 ComputerName 参数的情况下指定此参数，或指定使用 DCOM 协议创建的 CIM 会话，则将收到错误，因为 DCOM 协议不支持 ResourceURI 参数。

如果同时指定了 **ResourceUri** 参数和 **筛选器** 参数，则忽略 **筛选器** 参数。

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

提示你在运行 cmdlet 之前进行确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。 此 cmdlet 未运行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### Microsoft.Management.Infrastructure.CimInstance

## 输出

### Microsoft.Management.Infrastructure.CimInstance

当指定 **Passthru** 参数时，此 cmdlet 将返回已修改的 CIM 实例对象。

## 注释

## 相关链接

[Get-CimInstance](get-ciminstance.md)

[New-CimInstance](New-CimInstance.md)

[Remove-CimInstance](remove-ciminstance.md)

