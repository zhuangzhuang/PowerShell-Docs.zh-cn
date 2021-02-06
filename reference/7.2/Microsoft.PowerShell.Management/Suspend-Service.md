---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/suspend-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Service
ms.openlocfilehash: 9515f524df38813817b3fefd1437a3e2df296392
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598889"
---
# Suspend-Service

## 摘要
挂起（暂停）一个或多个正在运行的服务。

## SYNTAX

### InputObject（默认值）

```
Suspend-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 默认

```
Suspend-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Suspend-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

该 `Suspend-Service` cmdlet 将为每个指定的服务向 Windows 服务控制器发送一条挂起消息。 挂起时，服务仍在运行，但其操作将停止，直到恢复，如使用 `Resume-Service` cmdlet。 可以通过服务名称或显示名称来指定服务，也可以使用 **InputObject** 参数传递一个服务对象来表示要挂起的服务。

## 示例

### 示例1：挂起服务

```
PS C:\> Suspend-Service -DisplayName "Telnet"
```

此命令挂起本地计算机上的 Telnet 服务 (Tlntsvr)。

### 示例2：显示挂起服务后会发生的情况

```
PS C:\> Suspend-Service -Name lanman* -WhatIf
```

此命令会告诉你挂起服务名称以 lanman 开头的服务后会发生的情况。 若要挂起服务，请在不带 **WhatIf** 参数的情况下重新运行该命令。

### 示例3：获取和暂停服务

```
PS C:\> Get-Service schedule | Suspend-Service
```

此命令使用 `Get-Service` cmdlet 来获取一个对象，该对象表示计算机上的任务计划程序 (计划) 服务。 管道运算符 (`|`) 将结果传递给 `Suspend-Service` ，这会挂起服务。

### 示例4：挂起所有可挂起的服务

```
PS C:\> Get-Service | Where-Object {$_.CanPauseAndContinue -eq "True"} | Suspend-Service -Confirm
```

此命令挂起计算机上所有可挂起的服务。 它使用 `Get-Service` 来获取表示计算机上的服务的对象。 管道运算符将结果传递给 `Where-Object` cmdlet，后者只选择值 `$True` 为的 **CanPauseAndContinue** 属性的服务。 另一个管道运算符将结果传递给 `Suspend-Service` 。 **Confirm** 参数会提示您进行确认，然后再挂起每个服务。

## PARAMETERS

### -DisplayName

指定要挂起的服务的显示名称。 允许使用通配符。

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

指定要从指定服务中省略的服务。 此参数值使 **Name** 参数有效。 请输入名称元素或模式，例如“s*”。 允许使用通配符。

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

指定要挂起的服务。 此参数值使 **Name** 参数有效。 请输入名称元素或模式，例如“s*”。 允许使用通配符。

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

指定表示要挂起的服务的 **ServiceController** 对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

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

指定要挂起的服务的服务名称。 允许使用通配符。

参数名为可选项。 您可以使用 **Name** 或其 **别名，也** 可以省略参数名称。

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

显示运行该 cmdlet 时会发生什么情况。
此 cmdlet 未运行。

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

如果指定 **PassThru** 参数，则此 cmdlet 将生成表示该服务的 **ServiceController** 对象。 否则，此 cmdlet 将不生成任何输出。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

- `Suspend-Service` 仅当当前用户有权执行此操作时，才能控制服务。 如果某个命令不能正常工作，则可能你不具有所需的权限。
- `Suspend-Service` 只能挂起支持被挂起和恢复的服务。 若要确定是否可以挂起特定服务，请将 `Get-Service` cmdlet 与 **CanPauseAndContinue** 属性一起使用。 例如，`Get-Service wmi | Format-List Name, CanPauseAndContinue`。 若要查找计算机上可以挂起的所有服务，请键入 `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}` 。
- 若要查找服务名称并显示系统中的服务名称，请键入 `Get-Service`。
  服务名称显示在 " **名称** " 列中，显示名称显示在 **DisplayName** 列中。

## 相关链接

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Remove-Service](Remove-Service.md)
