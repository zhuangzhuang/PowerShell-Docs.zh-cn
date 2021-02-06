---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: 0216c7fae722121ead1c8e9ba122fbc3f1713725
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598696"
---
# Stop-Service

## 摘要
停止一个或多个正在运行的服务。

## SYNTAX

### InputObject（默认值）

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 默认

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DisplayName

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Stop-Service`Cmdlet 为每个指定的服务向 Windows 服务控制器发送一条停止消息。 你可以通过服务名称或显示名称来指定服务，也可以使用 **InputObject** 参数传递表示要停止的服务的服务对象。

## 示例

### 示例1：停止本地计算机上的服务

```
PS C:\> Stop-Service -Name "sysmonlog"
```

此命令停止本地计算机上的性能日志和警报 (SysmonLog) 服务。

### 示例2：使用显示名称停止服务

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

此命令停止本地计算机上的 Telnet 服务。 该命令使用 `Get-Service` 来获取表示 Telnet 服务的对象。 管道运算符 (将 `|` 对象) 管道传输到 `Stop-Service` 停止服务的对象。

### 示例3：停止具有依赖服务的服务

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

此示例在本地计算机上停止 IISAdmin 服务。 由于停止此服务还会停止依赖于 IISAdmin 服务的服务，因此最好 `Stop-Service` 在列出依赖于 IISAdmin 服务的服务的命令之前。

第一个命令列出依赖于 IISAdmin 的服务。 它使用 `Get-Service` 获取表示 IISAdmin 服务的对象。 管道运算符 (`|`) 将结果传递给 `Format-List` cmdlet。 该命令使用的 **属性** 参数 `Format-List` 来仅列出该服务的 **Name** 和 **DependentServices** 属性。

第二个命令停止 IISAdmin 服务。 需要使用 **Force** 参数来停止具有依赖服务的服务。 该命令使用 **Confirm** 参数在停止每个服务之前请求用户确认。

## PARAMETERS

### -DisplayName

指定要停止的服务的显示名称。
允许使用通配符。

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

指定此 cmdlet 省略的服务。 此参数值使 **Name** 参数有效。 输入名称元素或模式，例如 "s *"。 允许使用通配符。

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

### -Force

强制 cmdlet 停止服务（即使该服务有依赖服务）。

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

### -Include

指定此 cmdlet 停止的服务。 此参数值使 **Name** 参数有效。 输入名称元素或模式，例如 "s *"。 允许使用通配符。

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

指定表示要停止的服务的 **ServiceController** 对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定要停止的服务的服务名称。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -NoWait

指示此 cmdlet 使用 "无等待" 选项。

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

### -PassThru

返回一个表示服务的对象。 默认情况下，此 cmdlet 将不产生任何输出。

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

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.ServiceProcess.ServiceController、System.String

可以通过管道将服务对象或包含服务名称的字符串传递给此 cmdlet。

## 输出

### 无、System.ServiceProcess.ServiceController

如果使用 **PassThru** 参数，则此 cmdlet 将生成表示服务的 **ServiceController** 对象。 否则，此 cmdlet 将不生成任何输出。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

还可以 `Stop-Service` 通过其内置别名 **spsv** 来引用。 有关详细信息，请参阅 about_Aliases。

`Stop-Service` 仅当当前用户有权执行此操作时，才能控制服务。 如果某个命令不能正常工作，则可能你不具有所需的权限。

若要查找服务名称并显示系统中的服务名称，请键入 `Get-Service`。 服务名称显示在 " **名称** " 列中，显示名称显示在 **DisplayName** 列中。

## 相关链接

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)
