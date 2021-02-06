---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/21/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimInstance
ms.openlocfilehash: 0e4a148601f3ef2212f9c97128c54258906106d7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597659"
---
# Get-CimInstance

## 摘要
从 CIM 服务器获取类的 CIM 实例。

## SYNTAX

### ClassNameComputerSet (默认值) 

```
Get-CimInstance [-ClassName] <String> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### ResourceUriSessionSet

```
Get-CimInstance -CimSession <CimSession[]> -ResourceUri <Uri> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### QuerySessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

### ClassNameSessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ClassName] <String> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### CimInstanceSessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### CimInstanceComputerSet

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### ResourceUriComputerSet

```
Get-CimInstance -ResourceUri <Uri> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### QueryComputerSet

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

## DESCRIPTION

`Get-CimInstance`Cmdlet 从 cim 服务器获取类的 cim 实例。 可以为此 cmdlet 指定类名或查询。 此 cmdlet 将返回一个或多个 CIM 实例对象，这些对象表示 CIM 服务器上存在的 CIM 实例的快照。

如果未指定 **InputObject** 参数，该 cmdlet 将采用以下方法之一：

- 如果 **ComputerName** 参数和 **CimSession** 参数均未指定，则此 cmdlet 将在本地 Windows Management Instrumentation (WMI) 使用组件对象模型 (COM) 会话。
- 如果指定 **computername** 参数或 **CimSession** 参数，则此 cmdlet 适用于 **ComputerName** 参数或 **CimSession** 参数指定的 CIM 服务器。

如果指定了 **InputObject** 参数，该 cmdlet 将采用以下方法之一：

- 如果 **ComputerName** 参数和 **CimSession** 参数均未指定，则此 cmdlet 将使用输入对象中的 CIM 会话或计算机名称。
- 如果指定了 **ComputerName** 参数或 **CimSession** 参数，则此 cmdlet 将使用 CimSession 参数值或 **ComputerName** 参数值。

## 示例

### 示例1：获取指定类的 CIM 实例

此示例将检索名为 **Win32_Process** 的类的 CIM 实例。

```powershell
Get-CimInstance -ClassName Win32_Process
```

### 示例2：从 WMI 服务器获取命名空间列表

此示例在 WMI 服务器上的 **根** 命名空间下检索命名空间的列表。

```powershell
Get-CimInstance -Namespace root -ClassName __Namespace
```

### 示例3：获取使用查询筛选的类的实例

此示例使用 **查询** 参数指定的查询，检索以名为 **Win32_Process** 的类的字母 **P** 开头的所有 CIM 实例。

```powershell
Get-CimInstance -Query "SELECT * from Win32_Process WHERE name LIKE 'P%'"
```

### 示例4：获取通过使用类名称和筛选器表达式筛选的类的实例

此示例使用 Filter 参数检索以名为 **Win32_Process** 的类的字母 **P** 开头的所有 CIM 实例。

```powershell
Get-CimInstance -ClassName Win32_Process -Filter "Name like 'P%'"
```

### 示例5：获取仅填充了密钥属性的 CIM 实例

此示例在内存中为名为 **Win32_Process** 的类创建一个名为的新 CIM 实例，该实例具有键属性 `@{ "Handle"=0 }` ，并将其存储在名为的变量中 `$x` 。 变量作为 CIM 实例传递到 `Get-CimInstance` cmdlet 以获取特定的实例。

```powershell
$x = New-CimInstance -ClassName Win32_Process -Namespace root\cimv2 -Property @{ "Handle"=0 } -Key Handle -ClientOnly
Get-CimInstance -CimInstance $x
```

### 示例6：检索并重复使用 CIM 实例

此示例将获取名为 **Win32_Process** 的类的 CIM 实例，并将其存储在变量 `$x` 和中 `$y` 。 然后，将变量设置为 `$x` 仅包含 **Name** 和 **KernelModeTime** 属性的表，并将该表设置为 "自动 **调整大小**"。

```powershell
$x,$y = Get-CimInstance -ClassName Win32_Process
$x | Format-Table -Property Name,KernelModeTime -AutoSize
```

```Output
Name                 KernelModeTime
----                 --------------
System Idle Process 157238797968750
```

### 示例7：从远程计算机获取 CIM 实例

此示例从名为 **Server01** 和 **Server02** 的远程计算机中检索名为 **Win32_ComputerSystem** 的类的 CIM 实例。

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName Server01,Server02
```

### 示例8：仅获取密钥属性，而不是所有属性

此示例仅检索密钥属性，这会减少对象和网络流量的大小。

```powershell
$x = Get-CimInstance -Class Win32_Process -KeyOnly
$x | Invoke-CimMethod -MethodName GetOwner
```

### 示例9：仅获取属性的子集，而不是所有属性

此示例仅检索部分属性，这会减少对象和网络流量的大小。

```powershell
Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x = Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x | Invoke-CimMethod -MethodName GetOwner
```

使用 **属性** 参数检索到的实例可用于执行其他 CIM 操作，例如 `Set-CimInstance` 或 `Invoke-CimMethod` 。

### 示例10：使用 CIM 会话获取 CIM 实例

此示例使用 cmdlet 在名为 **Server01** 和 **Server02** 的计算机上创建 CIM 会话 `New-CimSession` ，并将会话信息存储在名为的变量中 `$s` 。 然后，使用 CimSession 参数将变量的内容传递到 `Get-CimInstance` ， 以获取名为 **WIN32_COMPUTERSYSTEM** 的类的 CIM 实例。

```powershell
$s = New-CimSession -ComputerName Server01,Server02
Get-CimInstance -ClassName Win32_ComputerSystem -CimSession $s
```

## PARAMETERS

### -CimSession

指定要用于此 cmdlet 的 CIM 会话。 输入包含 CIM 会话的变量，或输入创建或获取 CIM 会话的命令（如 `New-CimSession` 或 `Get-CimSession` cmdlet）。 有关详细信息，请参阅 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

指定要为其检索 CIM 实例的 CIM 类的名称。 您可以使用 tab 自动补全来浏览类列表，因为 PowerShell 从本地 WMI 服务器获取类的列表以提供类名的列表。

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ComputerName

指定要在其上运行 CIM 操作的计算机。 可以指定完全限定的域名 (FQDN) 、NetBIOS 名称或 IP 地址。 如果未指定此参数，则该 cmdlet 将使用组件对象模型 (COM) 在本地计算机上执行操作。

如果指定此参数，则该 cmdlet 将使用 WsMan 协议创建到指定计算机的临时会话。

如果在同一台计算机上执行多个操作，请使用 CIM 会话进行连接以获得更好的性能。

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, CimInstanceComputerSet, ResourceUriComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Filter

指定要用作筛选器的 where 子句。 指定 **WQL** 或 **CQL** 查询语言中的子句。 不要 `WHERE` 在参数的值中包含关键字。

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

指定要用作输入的 CIM 实例对象。

如果已在使用 CIM 实例对象，则可以使用此参数传递 CIM 实例对象，以便从 CIM 服务器获取最新的快照。 将 CIM 实例对象作为输入传递时，将 `Get-CimInstance` 从服务器使用 GET CIM 操作（而不是枚举或查询操作）返回对象。 使用 get CIM 操作比检索所有实例并筛选它们更有效。

如果 CIM 类未实现 get 操作，则指定 **InputObject** 参数将返回错误。

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceSessionSet, CimInstanceComputerSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -KeyOnly

指示只返回填充了键属性的对象。 指定 **KeyOnly** 参数将减少通过网络传输的数据量。

使用 **KeyOnly** 参数可仅返回对象的一小部分，该对象可用于其他操作，例如 `Set-CimInstance` 或 `Get-CimAssociatedInstance` cmdlet。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace

指定 CIM 类的命名空间。

默认命名空间为 **root/cimv2**。 您可以使用 tab 自动补全来浏览命名空间列表，因为 PowerShell 从本地 WMI 服务器获取命名空间列表以提供命名空间列表。

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
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

### -Property

指定要检索的实例属性集。 如果需要减小返回对象的大小（在内存中或网络上），请使用此参数。 返回的对象还包含键属性，即使您未使用 **Property** 参数列出它们也是如此。 类的其他属性存在，但未填充它们。

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases: SelectProperties

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Query

指定要在 CIM 服务器上运行的查询。 如果指定的值包含双引号 `"` 、单引号 `'` 或反斜杠 `\` ，则必须通过在它们前面加上反斜杠字符来对这些字符进行转义。 如果指定的值使用 WQL **LIKE** 运算符，则必须通过将以下字符括在方括号中来对其进行转义 `[]` ：百分比 `%` 、下划线 `_` 或左方括号 `[` 。

不能使用元数据查询来检索类或事件查询的列表。 若要检索类的列表，请使用 `Get-CimClass` cmdlet。 若要检索事件查询，请使用 `Register-CimIndicationEvent` cmdlet。

您可以使用 **QueryDialect** 参数指定查询方言。

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QueryDialect

指定用于查询参数的查询语言。 此参数的可接受值为： **WQL** 或 **CQL**。 默认值为 **WQL**。

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QuerySessionSet, ClassNameSessionSet, QueryComputerSet
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

**ResourceURI** 只能与使用 wsman 协议创建的 cim 会话一起使用，也可以在指定 **ComputerName** 参数时使用，后者使用 wsman 创建 cim 会话。 如果在不指定 **ComputerName** 参数的情况下指定此参数，或指定使用 DCOM 协议创建的 CIM 会话，则将收到错误，因为 DCOM 协议不支持 **ResourceURI** 参数。

如果同时指定了 **ResourceUri** 参数和 **筛选器** 参数，则忽略 **筛选器** 参数。

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet, QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -浅

指示返回类的实例，但不包含任何子类的实例。 默认情况下，该 cmdlet 将返回类及其子类的实例。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
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

### CIM 实例

此 cmdlet 接受使用 InputObject 参数指定的输入对象。

## 输出

### CIM 实例

此 cmdlet 将返回一个或多个 CIM 实例对象，这些对象表示 CIM 服务器上 CIM 实例的快照。

## 注释

## 相关链接

[Format-Table](../microsoft.powershell.utility/format-table.md)

[Get-CimAssociatedInstance](Get-CimAssociatedInstance.md)

[Get-CimClass](Get-CimClass.md)

[Invoke-CimMethod](invoke-cimmethod.md)

[New-CimInstance](New-CimInstance.md)

[Register-CimIndicationEvent](Register-CimIndicationEvent.md)

[Remove-CimInstance](remove-ciminstance.md)

[Set-CimInstance](Set-CimInstance.md)

