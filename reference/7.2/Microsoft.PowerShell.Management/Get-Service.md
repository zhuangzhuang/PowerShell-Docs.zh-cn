---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: c27dac11cdd8ebbf1705ac3bba0c0aa5147d4fa8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598867"
---
# Get-Service

## 摘要
获取计算机上的服务。

## SYNTAX

### Default（默认值）

```
Get-Service [[-Name] <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### DisplayName

```
Get-Service [-DependentServices] [-RequiredServices] -DisplayName <String[]> [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### InputObject

```
Get-Service [-DependentServices] [-RequiredServices] [-Include <String[]>] [-Exclude <String[]>]
 [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## DESCRIPTION

该 `Get-Service` cmdlet 将获取表示计算机上的服务（包括正在运行和已停止的服务）的对象。 默认情况下，在不带参数的情况下 `Get-Service` 运行时，将返回所有本地计算机的服务。

可以通过指定服务的服务名称或显示名称来指示此 cmdlet 仅获取特定服务，也可以通过管道将服务对象传递给此 cmdlet。

## 示例

### 示例1：获取计算机上的所有服务

此示例将获取计算机上的所有服务。 它的行为如同你键入 `Get-Service *` 的一样。 默认显示将显示每个服务的状态、服务名称和显示名称。

```powershell
Get-Service
```

### 示例2：获取以搜索字符串开头的服务

此示例检索服务名称以 WMI (Windows Management Instrumentation) 开头的服务。

```powershell
Get-Service "wmi*"
```

### 示例3：显示包含搜索字符串的服务

此示例显示显示名称包括 "网络" 的服务。 搜索显示名称会找到与网络相关的服务，即使服务名称不包括 Net （如 xmlprov），网络预配服务也是如此。

```powershell
Get-Service -Displayname "*network*"
```

### 示例4：获取以搜索字符串开头的服务和排除项

此示例仅获取服务名称以 " **win**" 开头的服务（WinRM 服务除外）。

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

### 示例5：显示当前处于活动状态的服务

此示例仅显示状态为 "正在运行" 的服务。

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

`Get-Service` 获取计算机上的所有服务，并沿管道向下发送对象。 `Where-Object`Cmdlet 仅选择 **状态** 属性等于 "正在运行" 的服务。

Status 是服务对象的唯一属性。 若要查看所有属性，请键入 `Get-Service | Get-Member` 。

### 示例6：列出计算机上具有依赖服务的服务

此示例获取具有依赖服务的服务。

```powershell
Get-Service |
  Where-Object {$_.DependentServices} |
    Format-List -Property Name, DependentServices, @{
      Label="NoOfDependentServices"; Expression={$_.dependentservices.count}
    }
```

```Output
Name                  : AudioEndpointBuilder
DependentServices     : {AudioSrv}
NoOfDependentServices : 1

Name                  : Dhcp
DependentServices     : {WinHttpAutoProxySvc}
NoOfDependentServices : 1
...
```

该 `Get-Service` cmdlet 将获取计算机上的所有服务，并沿管道向下发送对象。 `Where-Object`Cmdlet 将选择其 **DependentServices** 属性不为 null 的服务。

结果将通过管道向下发送到 `Format-List` cmdlet。 **Property** 参数显示服务的名称、依赖服务的名称以及显示每个服务的依赖服务数目的计算属性。

### 示例7：按属性值对服务排序

此示例显示，当你按 **状态** 属性的值以升序对服务进行排序时，已停止的服务将显示在运行服务之前。 原因在于， **Status** 的值是一个枚举，其中，已停止的值为1，并且运行的值为4。 有关详细信息，请参阅 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)。

若要首先列出正在运行的服务，请使用 cmdlet 的 **降序** 参数 `Sort-Object` 。

```powershell
Get-Service "s*" | Sort-Object status
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  stisvc             Windows Image Acquisition (WIA)
Stopped  SwPrv              MS Software Shadow Copy Provider
Stopped  SysmonLog          Performance Logs and Alerts
Running  Spooler            Print Spooler
Running  srservice          System Restore Service
Running  SSDPSRV            SSDP Discovery Service
Running  ShellHWDetection   Shell Hardware Detection
Running  Schedule           Task Scheduler
Running  SCardSvr           Smart Card
Running  SamSs              Security Accounts Manager
Running  SharedAccess       Windows Firewall/Internet Connectio...
Running  SENS               System Event Notification
Running  seclogon           Secondary Logon
```

### 示例8：获取服务的依赖服务

此示例获取 WinRM 服务所需的服务。 返回该服务的 **ServicesDependedOn** 属性的值。

```powershell
Get-Service "WinRM" -RequiredServices
```

### 示例9：通过管道运算符获取服务

此示例将获取本地计算机上的 WinRM 服务。 用引号引起来的服务名称字符串向下发送到 `Get-Service` 。

```powershell
"WinRM" | Get-Service
```

## PARAMETERS

### -DependentServices

指示此 cmdlet 仅获取依赖于指定服务的服务。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

指定作为字符串数组，要检索的服务的显示名称。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Exclude

指定为字符串数组、此 cmdlet 从操作中排除的一个或一组服务。
此参数值使 **Name** 参数有效。 输入名称元素或模式，例如 `s*` 。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

指定为字符串数组、此 cmdlet 包含在操作中的一个或一项服务。 此参数值使 **Name** 参数有效。 输入名称元素或模式，例如 `s*` 。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

指定表示要检索的服务的 **ServiceController** 对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。 可以通过管道将服务对象传递给此 cmdlet。

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定要检索的服务的名称。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -RequiredServices

指示此 cmdlet 仅获取此服务所需的服务。 此参数获取服务的 **ServicesDependedOn** 属性的值。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.ServiceProcess.ServiceController、System.String

可以通过管道将服务对象或服务名称传递给此 cmdlet。

## 输出

### System.ServiceProcess.ServiceController

此 cmdlet 将返回表示计算机上的服务的对象。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

从 PowerShell 6.0 开始，将以下属性添加到 **ServiceController** 对象： **UserName**、 **Description**、 **DelayedAutoStart**、 **BinaryPathName** 和 **StartupType** 。

还可以 `Get-Service` 通过其内置别名来引用 `gsv` 。 有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

此 cmdlet 只能在当前用户有权查看服务时显示服务。 如果此 cmdlet 未显示服务，则你可能没有查看它们的权限。

若要在系统中查找每个服务的服务名称和显示名称，请键入 `Get-Service` 。 服务名称显示在 "名称" 列中，显示名称显示在 **DisplayName** 列中。

如果按 **状态** 属性的值按升序排序，停止的服务将显示在运行服务之前。 服务的 **status** 属性是一个枚举值，状态名称表示整数值。 排序顺序取决于整数值，而不是名称。 已停止出现，因为运行，因为停止的值为1，并且运行的值为4。 有关详细信息，请参阅 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)。

## 相关链接

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)
