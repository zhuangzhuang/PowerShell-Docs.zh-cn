---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Service
ms.openlocfilehash: b1df4490da501111ccb44dea2645a333fdf5c27e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603407"
---
# Start-Service

## 摘要
启动一个或多个已停止的服务。

## SYNTAX

### InputObject（默认值）

```
Start-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 默认

```
Start-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Start-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Start-Service`Cmdlet 为每个指定的服务向 Windows 服务控制器发送一条启动消息。 如果服务已在运行，则无错误忽略该消息。 可以通过服务名称或显示名称指定服务，也可使用 InputObject 参数提供一个服务对象，表示要启动的服务。

## 示例

### 示例 1：通过使用服务名称启动服务

此示例启动本地计算机上的 EventLog 服务。 **Name** 参数通过服务名称来标识服务。

```powershell
Start-Service -Name "eventlog"
```

### 示例 2：在不启动服务的情况下显示信息

此示例显示了启动显示名称中包含 "remote" 的服务后会发生的情况。

```powershell
Start-Service -DisplayName *remote* -WhatIf
```

**DisplayName** 参数通过显示名称而不是服务名称来标识服务。 **WhatIf** 参数会使 cmdlet 显示运行命令时所发生的情况，但不会发生更改。

### 示例 3：启动服务，并将操作记录到文本文件中

此示例启动计算机上的 Windows Management Instrumentation (WMI) 服务，并将操作的记录添加到 services.txt 文件中。

```powershell
$s = Get-Service wmi
Start-Service -InputObject $s -PassThru | Format-List >> services.txt
```

首先，我们使用 `Get-Service` 来获取表示 WMI 服务的对象，并将其存储在 `$s` 变量中。 接下来，我们启动该服务。 如果没有 **PassThru** 参数，则不 `Start-Service` 会创建任何输出。 管道运算符 (|) 将对象输出传递 `Start-Service` 给 cmdlet， `Format-List` 以将对象的格式设置为其属性列表。 追加重定向运算符 (将 \> \> 输出重定向到 services.txt 文件) 。 将输出添加到现有文件的末尾。

### 示例 4：启动禁用的服务

此示例演示如何在 **禁用** 服务的启动类型时启动服务。

```
PS> Start-Service tlntsvr
Start-Service : Service 'Telnet (TlntSvr)' cannot be started due to the following error: Cannot start service TlntSvr on computer '.'.
At line:1 char:14
+ Start-Service  <<<< tlntsvr

PS> Get-CimInstance win32_service | Where-Object Name -eq "tlntsvr"
ExitCode  : 0
Name      : TlntSvr
ProcessId : 0
StartMode : Disabled
State     : Stopped
Status    : OK

PS> Set-Service tlntsvr -StartupType manual
PS> Start-Service tlntsvr
```

第一次尝试启动 Telnet 服务 (tlntsvr) 失败。 该 `Get-CimInstance` 命令显示 Tlntsvr 服务的 **StartMode** 属性已 **禁用**。 `Set-Service`Cmdlet 将启动类型更改为 "**手动**"。 现在，我们可以重新提交 `Start-Service` 命令。 这次，该命令执行成功。 若要验证命令是否成功，请运行 `Get-Service` 。

## PARAMETERS

### -DisplayName

指定要启动的服务的显示名称。 允许使用通配符。

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

指定此 cmdlet 省略的服务。 此参数值使 **Name** 参数有效。 输入名称元素或模式，例如 `s*` 。 允许使用通配符。

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

指定此 cmdlet 启动的服务。 此参数值使 **Name** 参数有效。 输入名称元素或模式，例如 `s*` 。 允许使用通配符。

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

指定表示要启动的服务的 **ServiceController** 对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

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

指定要启动的服务的服务名称。

参数名为可选项。 您可以使用 **Name** 或其 **别名，也** 可以省略参数名称。

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

可以通过管道将对象（该对象表示包含服务名称的服务或字符串）传递给此 cmdlet。

## 输出

### 无、System.ServiceProcess.ServiceController

如果指定 PassThru，此 cmdlet 会生成表示服务的 **System.ServiceProcess.ServiceController** 对象。 否则，此 cmdlet 将不生成任何输出。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

- 还可以 `Start-Service` 通过其内置别名来引用 `sasv` 。 有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。
- `Start-Service` 只有在当前用户有权执行此操作的情况下，才能控制服务。 如果某个命令不能正常工作，则可能你不具有所需的权限。
- 若要查找服务名称并显示系统中的服务名称，请键入 `Get-Service`。
  服务名称显示在 " **名称** " 列中，显示名称显示在 **DisplayName** 列中。
- 只能启动启动类型为 "手动"、"自动" 或 "自动" (延迟启动) 的服务。 无法启动启动类型为 Disabled 的服务。 如果 `Start-Service` 命令失败，并出现消息 `Cannot start service \<service-name\> on computer` ，请使用 `Get-CimInstance` 查找服务的启动类型，如果需要，请使用 `Set-Service` cmdlet 更改服务的启动类型。
- 某些服务在没有工作时将自动停止，例如性能日志和警报 (SysmonLog) 服务。 当 PowerShell 启动一项几乎立即停止的服务时，它会显示以下消息： `Service \<display-name\> start failed.`

## 相关链接

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)
