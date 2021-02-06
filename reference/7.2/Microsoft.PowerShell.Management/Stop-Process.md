---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Process
ms.openlocfilehash: 8c9e520f1f19444fd538fabee99a48ec08c69992
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598479"
---
# Stop-Process

## 摘要
停止一个或多个正在运行的进程。

## SYNTAX

### ID（默认值）

```
Stop-Process [-Id] <Int32[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 名称

```
Stop-Process -Name <String[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Stop-Process [-InputObject] <Process[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**停止进程** cmdlet 停止一个或多个正在运行的进程。
可以通过进程名称或进程 ID 指定进程 (PID) ，或将进程对象传递到 **停止进程**。
**停止-进程** 仅适用于在本地计算机上运行的进程。

在 Windows Vista 和更高版本的 Windows 操作系统上，若要停止不是由当前用户拥有的进程，则必须使用 "以管理员身份运行" 选项启动 PowerShell。
此外，除非指定 *Confirm* 参数，否则不会提示你进行确认。

## 示例

### 示例1：停止进程的所有实例

```
PS C:\> Stop-Process -Name "notepad"
```

此命令停止计算机上 Notepad 进程的所有实例。
记事本的每个实例都在其自己的进程中运行。
它使用 *Name* 参数来指定进程，所有进程都具有相同的名称。
如果要使用 *Id* 参数来停止相同进程，则必须列出每个 Notepad 实例的进程 id。

### 示例2：停止进程的特定实例

```
PS C:\> Stop-Process -Id 3952 -Confirm -PassThru
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "notepad (3952)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):y
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
41       2      996       3212    31            3952 notepad
```

此命令停止 Notepad 进程的特定实例。
它使用进程 ID 3952 来标识该进程。
*Confirm* 参数指示 PowerShell 在停止该进程之前提示您。
由于提示中包含进程名称的 ID，因此这是最佳做法。
*PassThru* 参数将进程对象传递给格式化程序以进行显示。
如果没有此参数，则在 **停止处理** 命令后将不会显示。

### 示例3：停止进程并检测它是否已停止

```
PS C:\> calc
PS C:\> $p = Get-Process -Name "calc"
PS C:\> Stop-Process -InputObject $p
PS C:\> Get-Process | Where-Object {$_.HasExited}
```

这一系列命令将启动和停止 Calc 进程，然后检测已停止的进程。

第一个命令启动一个计算器实例。

第二个命令使用 **获取进程** 获取一个表示 Calc 过程的对象，然后将该对象存储在 $p 的变量中。

第三个命令停止计算进程。
它使用 *InputObject* 参数将对象传递到 **停止进程**。

最后一个命令获取计算机上所有曾经运行但现已停止的进程。
它使用 **获取进程** 获取计算机上的所有进程。
管道运算符 (|) 将结果传递给 Where-Object cmdlet，该 cmdlet 选择 **HasExited** 属性的值 $True 的值。
**HasExited** 只是进程对象的一个属性。
若要查找所有属性，请键入 `Get-Process | Get-Member` 。

### 示例4：停止不是由当前用户拥有的进程

```
PS C:\> Get-Process -Name "lsass" | Stop-Process

Stop-Process : Cannot stop process 'lsass (596)' because of the following error: Access is denied
At line:1 char:34
+ Get-Process -Name "lsass" | Stop-Process <<<<

[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process

Warning!
Are you sure you want to perform this action?
Performing operation 'Stop-Process' on Target 'lsass(596)'
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process -Force
[ADMIN]: PS C:\>
```

这些命令演示了使用 *Force* 停止用户不拥有的进程的效果。

第一个命令使用 **Get 进程** 获取 Lsass 进程。
管道运算符将进程发送到 **停止进程** 以停止进程。
如示例输出中所示，第一个命令失败并出现 "拒绝访问" 消息，因为此进程只能由计算机上的管理员组的成员停止。

使用 "以管理员身份运行" 选项打开 PowerShell 后，命令重复，PowerShell 会提示你进行确认。

第二个命令指定 *强制* 禁止显示提示。
因此进程将在不提示确认的情况下停止。

## PARAMETERS

### -Force

在不提示确认的情况下停止指定的进程。
默认情况下，在停止当前用户不拥有的任何进程之前， **停止进程** 提示进行确认。

若要查找进程的所有者，请使用 `Get-CimInstance` cmdlet 获取表示该进程的 **Win32_Process** 对象，然后使用该对象的 **GetOwner** 方法。

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

### -Id

指定要停止的进程的进程 Id。
若要指定多个 ID，请使用逗号分隔 ID。
若要查找进程的 PID，请键入 `Get-Process`。

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

指定要停止的进程对象。
输入一个包含对象的变量，或键入可获取对象的命令或表达式。

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定要停止的进程的进程名称。
可以键入多个进程名称（以逗号分隔）或使用通配符。

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

返回一个表示进程的对象。
默认情况下，此 cmdlet 将不产生任何输出。

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
此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Diagnostics.Process

可以将进程对象通过管道传递给此 cmdlet。

## 输出

### 无、System.Diagnostics.Process

如果指定 *PassThru* 参数，则此 cmdlet 将返回一个表示已停止进程的 **system.object** 对象。
否则，此 cmdlet 将不生成任何输出。

## 注释

* 还可以通过其内置别名 " **kill** " 和 " **spps**" 来对 **其进行引用**。 有关详细信息，请参阅 about_Aliases。

  你还可以在 Windows PowerShell 中使用 Windows Management Instrumentation (WMI) **Win32_Process** 对象的属性和方法。
有关详细信息，请参阅 `Get-CimInstance` 和 WMI SDK。

* 停止进程时，请注意停止进程可能会停止依赖该进程的进程和服务。
在极端情况下，停止进程可能会使 Windows 停止。

## 相关链接

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)

