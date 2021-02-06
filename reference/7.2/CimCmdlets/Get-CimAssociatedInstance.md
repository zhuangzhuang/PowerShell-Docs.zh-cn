---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimassociatedinstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimAssociatedInstance
ms.openlocfilehash: e14ba6db4f5e93c6e2c1824ce845f82720616bc5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595643"
---
# Get-CimAssociatedInstance

## 摘要
检索通过关联连接到特定 CIM 实例的 CIM 实例。

## SYNTAX

### ComputerSet (默认值) 

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] [-ComputerName <String[]>] [-KeyOnly] [<CommonParameters>]
```

### SessionSet

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] -CimSession <CimSession[]> [-KeyOnly] [<CommonParameters>]
```

## DESCRIPTION

`Get-CimAssociatedInstance`Cmdlet 通过关联检索连接到特定 cim 实例（称为源实例）的 cim 实例。

在关联中，每个 CIM 实例都有一个已命名的角色，同一 CIM 实例可以参与不同角色的关联。

如果未指定 InputObject 参数，该 cmdlet 将采用以下方法之一：

- 如果 **ComputerName** 参数和 **CimSession** 参数均未指定，则此 cmdlet 将在本地 Windows Management Instrumentation (WMI) 使用组件对象模型 (COM) 会话。
- 如果指定 **computername** 参数或 **CimSession** 参数，则此 cmdlet 适用于 **ComputerName** 参数或 **CimSession** 参数指定的 CIM 服务器。

## 示例

### 示例1：获取特定实例的所有关联实例

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1]
```

这一组命令将检索名为 Win32_LogicalDisk 的类的实例，并使用 cmdlet 将该信息存储在名为的变量中 `$disk` `Get-CimInstance` 。 然后，将变量中的第一个逻辑磁盘实例用作 cmdlet 的输入对象 `Get-CimAssociatedInstance` ，以获取指定的 cim 实例的所有关联 cim 实例。

### 示例2：获取特定类型的所有关联实例

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1] -ResultClass Win32_DiskPartition
```

这一组命令将检索 **Win32_LogicalDisk** 类的所有实例，并将它们存储在一个名为的变量中 `$disk` 。 然后，将变量中的第一个逻辑磁盘实例用作 cmdlet 的输入对象， `Get-CimAssociatedInstance` 以获取通过指定的 association 类 **Win32_DiskPartition** 关联的所有关联的实例。

### 示例3：通过特定类的限定符获取所有关联的实例

```powershell
$s = Get-CimInstance -Query "Select * from Win32_Service where name like 'Winmgmt'"
Get-CimClass -ClassName *Service* -Qualifier "Association"
$c.CimClasName
```

```Output
Win32_LoadOrderGroupServiceDependencies
Win32_DependentService
Win32_SystemServices
Win32_LoadOrderGroupServiceMembers
Win32_ServiceSpecificationService
```

```powershell
Get-CimAssociatedInstance -InputObject $s -Association Win32_DependentService
```

这一组命令将检索依赖于 WMI 服务的服务，并将它们存储在一个名为的变量中 `$s` 。 使用 cmdlet 检索 **Win32_DependentService** 的关联类名称，方法是将 `Get-CimClass` **association** 指定为限定符，然后将 $s 传递到 `Get-CimAssociatedInstance` cmdlet，以获取已检索关联类的所有关联实例。

## PARAMETERS

### -关联

指定关联类的名称。 如果未指定此参数，则该 cmdlet 将返回任何类型的所有现有关联对象。

例如，如果类 A 通过两个关联（AB1 和 AB2）与类 B 关联，则可以使用此参数来指定关联类型（AB1 或 AB2）。

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

### -CimSession

使用指定的 CIM 会话运行该命令。 输入包含 CIM 会话的变量，或输入创建或获取 CIM 会话的命令（如 `New-CimSession` 或） `Get-CimSession` 。 有关详细信息，请参阅 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。

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

### -ComputerName

指定要在其上运行 CIM 操作的计算机的名称。 可以指定完全限定的域名 (FQDN) 或 NetBIOS 名称。

如果指定此参数，则该 cmdlet 将使用 WsMan 协议创建到指定计算机的临时会话。

如果未指定此参数，则该 cmdlet 将使用组件对象模型 (COM) 在本地计算机上执行操作。

如果在同一台计算机上执行多个操作，则使用 CIM 会话进行连接可以提高性能。

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定此 cmdlet 的输入。 可以使用此参数，也可以通过管道传送此 cmdlet 的输入。

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -KeyOnly

返回仅填充了键属性的对象。 这将减少通过网络传输的数据量。

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

### -Namespace

指定 CIM 操作的命名空间。 默认命名空间为 root/cimv2。

> [!NOTE]
> 您可以使用 tab 自动补全来浏览命名空间列表，因为 PowerShell 从本地 WMI 服务器获取命名空间列表以提供命名空间列表。

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

### -ResourceUri

指定资源类或实例 (URI) 的资源统一资源标识符。 URI 用于标识计算机上特定类型的资源，例如磁盘或进程。

URI 由前缀和指向资源的路径组成。 例如：

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

默认情况下，如果不指定此参数，则将使用 DMTF 标准资源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 并向其追加类名称。

**ResourceURI** 只能与使用 wsman 协议创建的 cim 会话一起使用，也可以在指定 **ComputerName** 参数时使用，后者使用 wsman 创建 cim 会话。 如果在不指定 **ComputerName** 参数的情况下指定此参数，或指定使用 DCOM 协议创建的 CIM 会话，则会出现错误，因为 DCOM 协议不支持 **ResourceURI** 参数。

如果同时指定了 **ResourceUri** 参数和 **筛选器** 参数，则忽略 **筛选器** 参数。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResultClassName

指定关联实例的类名称。 CIM 实例可以与一个或多个 CIM 实例相关联。 如果未指定结果类名称，则返回所有关联的 CIM 实例。

默认情况下，此参数的值为 null，并返回所有关联的 CIM 实例。

可以筛选关联结果以匹配特定类名。 筛选将在服务器上进行。 如果未指定此参数，则将 `Get-CIMAssociatedInstance` 返回所有现有关联。 例如，如果类 A 与类 B、C 和 D 相关联，则可以使用此参数将输出限制为 (B、C 或 D) 的特定类型。

```yaml
Type: System.String
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

### 无

此 cmdlet 不接受输入对象。

## 输出

### System.Object

此 cmdlet 将返回一个对象。

## 注释

## 相关链接

[Get-CimClass](get-cimclass.md)

[Get-CimInstance](get-ciminstance.md)

