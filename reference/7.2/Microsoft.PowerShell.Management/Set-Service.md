---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: 0c6cac03f1acbda35069780f0c53eaf6685813ff
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597885"
---
# Set-Service

## 摘要
启动、停止和挂起服务并更改服务的属性。

## SYNTAX

### Name（默认值）

```
Set-Service [-Name] <String> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-Status <String>]
 [-SecurityDescriptorSddl <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Set-Service [-InputObject] <ServiceController> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-SecurityDescriptorSddl <String>]
 [-Status <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Set-Service`Cmdlet 更改服务的属性，如 **状态**、**说明**、 **DisplayName** 和 **StartupType**。 `Set-Service` 可以启动、停止、挂起或暂停服务。 若要标识服务，请输入其服务名称或提交服务对象。 或者，将服务名称或服务对象向下发送到 `Set-Service` 。

## 示例

### 示例1：更改显示名称

在此示例中，将更改服务的显示名称。 若要查看原始显示名称，请使用 `Get-Service` 。

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

`Set-Service` 使用 **name** 参数来指定服务的名称， **LanmanWorkstation**。 **DisplayName** 参数指定新的显示名称 " **LanMan Workstation**"。

### 示例2：更改服务的启动类型

此示例演示如何更改服务的启动类型。

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

`Set-Service` 使用 **name** 参数来指定服务的名称， **位**。 **StartupType** 参数将服务设置为 **自动**。

`Get-Service` 使用 **Name** 参数指定 **BITS** 服务，并沿管道向下发送对象。 `Select-Object` 使用 **属性** 参数显示 **BITS** 服务的状态。

### 示例3：更改服务的描述

此示例更改 BITS 服务的说明并显示结果。

`Get-CimInstance`使用 cmdlet 的原因是它将返回一个包含服务 **说明** 的 **Win32_Service** 对象。

```powershell
Get-CimInstance Win32_Service -Filter 'Name = "BITS"'  | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth. If the service is
              disabled, then any applications that depend on BITS, such as Windows Update or MSN
              Explorer, will be unable to automatically download programs and other information.
```

```powershell
Set-Service -Name BITS -Description "Transfers files in the background using idle network bandwidth."
Get-CimInstance Win32_Service -Filter 'Name = "BITS"' | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth.
```

`Get-CimInstance` 将对象向下发送到管道， `Format-List` 并显示服务的名称和说明。 出于比较目的，将在更新说明之前和之后运行该命令。

`Set-Service` 使用 **Name** 参数指定 **BITS** 服务。 **Description** 参数指定服务说明的更新文本。

### 示例4：启动服务

在此示例中，启动了服务。

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

`Set-Service` 使用 **Name** 参数来指定服务 **WinRM**。 **Status** 参数使用 **运行** 的值来启动服务。 **PassThru** 参数输出显示结果的 **ServiceController** 对象。

### 示例5：挂起服务

此示例使用管道暂停到服务。

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

`Get-Service` 使用 **Name** 参数指定 **计划** 服务，并沿管道向下发送对象。 `Set-Service` 使用 **Status** 参数将服务设置为 "已 **暂停**"。

### 示例6：停止服务

此示例使用变量来停止服务。

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

`Get-Service` 使用 **Name** 参数来指定服务的 **计划**。 对象存储在变量中 `$S` 。 `Set-Service` 使用 **InputObject** 参数，并指定存储的对象 `$S` 。 **Status** 参数将服务设置为 "**已停止**"。

### 示例7：停止远程系统上的服务

此示例将停止远程计算机上的服务。
有关详细信息，请参阅 [调用-命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。

```powershell
$Cred = Get-Credential
$S = Get-Service -Name Schedule
Invoke-Command -ComputerName server01.contoso.com -Credential $Cred -ScriptBlock {
  Set-Service -InputObject $S -Status Stopped
}
```

`Get-Credential` 提示输入用户名和密码，并将凭据存储在变量中 `$Cred` 。 `Get-Service` 使用 **Name** 参数来指定 **计划** 服务。 对象存储在变量中 `$S` 。

`Invoke-Command` 使用 **ComputerName** 参数来指定远程计算机。 **Credential** 参数使用 `$Cred` 变量登录到计算机。 **ScriptBlock** 调用 `Set-Service` 。 **InputObject** 参数指定存储的服务对象 `$S` 。 **Status** 参数将服务设置为 "**已停止**"。

### 示例8：更改服务的凭据

此示例更改用于管理服务的凭据。

```powershell
$credential = Get-Credential
Set-Service -Name Schedule -Credential $credential
```

`Get-Credential` 提示输入用户名和密码，并将凭据存储在变量中 `$credential` 。 `Set-Service` 使用 **Name** 参数来指定 **计划** 服务。 **Credential** 参数使用 `$credential` 变量并更新 **计划** 服务。

### 示例9：更改服务的 SecurityDescriptor

此示例将更改服务的 **SecurityDescriptor**。

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
Set-Service -Name "BITS" -SecurityDescriptorSddl $SDDL
```

**SecurityDescriptor** 存储在 `$SDDL` 变量中。 `Set-Service` 使用 **Name** 参数指定 **BITS** 服务。 **SecurityDescriptorSddl** 参数用于 `$SDDL` 更改 **BITS** 服务的 **SecurityDescriptor** 。

## PARAMETERS

### -Confirm

在运行之前提示你进行确认 `Set-Service` 。

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

### -Credential

将服务使用的帐户指定为 [服务登录帐户](/windows/desktop/ad/about-service-logon-accounts)。

键入用户名（如 **User01** 或 **Domain01\User01**）或输入 PSCredential 对象，例如由 Cmdlet 生成的一个 **PSCredential** 对象 `Get-Credential` 。 键入用户名时，此 cmdlet 会提示输入密码。

凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

此参数是在 PowerShell 6.0 中引入的。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

指定服务的新说明。

服务说明出现在 **"计算机管理，服务**" 中。 **说明** 不是 `Get-Service` **ServiceController** 对象的属性。 若要查看服务说明，请使用 `Get-CimInstance` ，它将返回表示服务的 **Win32_Service** 对象。

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

### -DisplayName

指定服务的新显示名称。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: DN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指定服务的停止模式。 仅当使用时，此参数才有效 `-Status Stopped` 。 如果启用，则在 `Set-Service` 目标服务停止之前停止从属服务。 默认情况下，当其他正在运行的服务依赖于目标服务时，将引发异常。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定表示要更改的服务的 **ServiceController** 对象。 输入包含该对象的变量，或键入获取该对象的命令或表达式（如 `Get-Service` 命令）。 您可以使用管道将服务对象发送到 `Set-Service` 。

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定要更改的服务的服务名称。 不允许使用通配符。 您可以使用管道将服务名称发送到 `Set-Service` 。

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PassThru

返回表示已更改的服务的 **ServiceController** 对象。 默认情况下， `Set-Service` 不会生成任何输出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -StartupType

指定服务的启动模式。

此参数可接受的值如下所示：

- **自动** -服务已启动或由操作系统在系统启动时启动。
  如果一个自动启动的服务依赖于手动启动的服务，则该手动启动的服务也会在系统启动时自动启动。
- **AutomaticDelayedStart** -系统启动后立即启动。
- **已禁用** -服务已禁用，无法由用户或应用程序启动。
- **InvalidValue** -不起作用。 Cmdlet 不会返回错误，但不会更改服务的 StartupType。
- **手动** -服务仅通过用户、使用服务控制管理器或应用程序手动启动。

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases: StartMode, SM, ST, StartType
Accepted values: Automatic, AutomaticDelayedStart, Disabled, InvalidValue, Manual

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Status

指定服务的状态。

此参数可接受的值如下所示：

- 已 **暂停**。 挂起服务。
- **正在运行**。 启动服务。
- **已停止**。 停止服务。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Paused, Running, Stopped

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecurityDescriptorSddl

以 **Sddl** 格式指定服务的 **SecurityDescriptor** 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sd

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

显示运行时将发生 `Set-Service` 的情况。 cmdlet 未运行。

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

您可以使用管道将服务对象或包含服务名称的字符串发送到 `Set-Service` 。

## 输出

### System.ServiceProcess.ServiceController

默认情况下， `Set-Service` 不返回任何对象。 使用 **PassThru** 参数输出 **ServiceController** 对象。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

`Set-Service` 需要提升的权限。 使用 "以 **管理员身份运行** " 选项。

`Set-Service` 仅当当前用户有权管理服务时，才能控制服务。 如果某个命令不能正常工作，则可能没有所需的权限。

若要查找服务的服务名称或显示名称，请使用 `Get-Service` 。 服务名称在 " **名称** " 列中，显示名称显示在 **DisplayName** 列中。

## 相关链接

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)
