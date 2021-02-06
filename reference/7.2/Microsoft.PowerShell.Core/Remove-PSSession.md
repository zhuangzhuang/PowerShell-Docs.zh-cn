---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: cd0e2b62464a4c34278d42b833a669c6c28e377f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598078"
---
# Remove-PSSession

## 摘要
 (Pssession) 关闭一个或多个 PowerShell 会话。

## SYNTAX

### ID（默认值）

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 会话

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ContainerId

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### VMId

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### VMName

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 名称

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 计算机名

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

Pssession **cmdlet 将** 关闭当前会话中 () 的 PowerShell 会话。
它将停止在 **PSSession** 中运行的任何命令、结束 **PSSession**，并释放 **PSSession** 使用的资源。
如果 **PSSession** 连接到远程计算机，则此 cmdlet 还会关闭本地计算机和远程计算机之间的连接。

若要删除 **PSSession**，请输入会话的 Name、ComputerName、ID 或 InstanceID。

如果你已将 PSSession 保存在变量中，则会话对象将保留在该变量中，但 PSSession 的状态为 Closed。

## 示例

### 示例 1：使用 ID 删除会话

```powershell
Remove-PSSession -Id 1, 2
```

此命令将删除具有 ID 1 和 2 的 **PSSession**。

### 示例 2：删除当前会话中的所有会话

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

这些命令将删除当前会话中的所有 **PSSession**。
虽然这三个命令格式看起来不同，但它们具有相同的效果。

### 示例 3：使用名称关闭会话

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

这些命令将关闭连接到名称以 Serv 开头的计算机的 **PSSession**。

### 示例 4：关闭连接到某个端口的会话

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

此命令将关闭连接到端口 90 的 **PSSession**。
你可以使用此命令格式，通过 ComputerName、Name、InstanceID 和 ID 以外的属性标识 **PSSession**。

### 示例 5：基于实例 ID 关闭会话

```powershell
Get-PSSession | Format-Table ComputerName, InstanceID  -AutoSize
```

```Output
ComputerName InstanceId
------------ ----------------
Server01     875d231b-2788-4f36-9f67-2e50d63bb82a
localhost    c065ffa0-02c4-406e-84a3-dacb0d677868
Server02     4699cdbc-61d5-4e0d-b916-84f82ebede1f
Server03     4e5a3245-4c63-43e4-88d0-a7798bfc2414
TX-TEST-01   fc4e9dfa-f246-452d-9fa3-1adbdd64ae85 PS C:\> Remove-PSSession -InstanceID fc4e9dfa-f246-452d-9fa3-1adbdd64ae85
```

这些命令显示了如何基于其实例 ID（或 **RemoteRunspaceID**）关闭 **PSSession**。

第一个命令使用 **Get-PSSession** cmdlet 来获取当前会话中的 **PSSession**。
它使用管道运算符 (|) 将 **PSSession** 发送到 Format-Table cmdlet，后者将在表格中设置其 **ComputerName** 和 **InstanceID** 属性的格式。
*AutoSize* 参数将压缩列以供显示。

从生成的显示内容中，可以标识要关闭的 **PSSession**，并将该 **PSSession** 的 InstanceID 复制和粘贴到第二个命令中。

第二个命令使用 **Remove-PSSession** cmdlet 删除具有指定实例 ID 的 PSSession。

### 示例 6：创建删除当前会话中的所有会话的函数

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

此函数将删除当前会话中的所有 **PSSession**。
将此函数添加到 PowerShell 配置文件后，若要删除所有会话，请键入 `EndPSS` 。

## PARAMETERS

### -ComputerName

指定计算机的名称数组。
此 cmdlet 关闭连接到指定计算机的 **PSSession**。
允许使用通配符。

键入一台或多台远程计算机的 NetBIOS 名称、IP 地址或完全限定的域名。
若要指定本地计算机，请键入该计算机名称、localhost 或句点 (.)。

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ContainerId

指定容器的 Id 的数组。 此 cmdlet 将删除每个指定容器的会话。 使用 `docker ps` 命令获取容器 id 列表。 有关详细信息，请参阅 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 命令的帮助。

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Id

指定会话的 ID 数组。
此 cmdlet 关闭具有指定 ID 的 PSSession。
键入一个或多个 ID（以逗号分隔），或使用范围运算符 (..) 来指定 ID 的范围。

ID 是一个整数，用于在当前会话中唯一标识 **PSSession**。
它比 InstanceId 更容易记住和键入，但它仅在当前会话中是唯一的。
若要查找 **PSSession** 的 ID，请运行不带参数的 Get-PSSession。

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

### -InstanceId

指定实例 ID 的数组。
此 cmdlet 关闭具有指定实例 ID 的 **PSSession**。

实例 ID 是一个 GUID，用于在当前会话中唯一标识 **PSSession**。
即使在一台计算机上运行了多个会话，实例 ID 也是唯一的。

实例 ID 存储在表示 **PSSession** 的对象的 **InstanceID** 属性中。
若要查找当前会话中的 **PSSession** 的 **InstanceID**，请键入 `Get-PSSession | Format-Table Name, ComputerName, InstanceId`。

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定会话的友好名称数组。
此 cmdlet 关闭具有指定友好名称的 **PSSession**。
允许使用通配符。

由于 **PSSession** 的友好名称可能不唯一，因此在使用 Name 参数时，还应考虑在 **Remove-PSSession** 命令中使用 WhatIf 或 Confirm 参数。

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Session

指定要关闭的 **PSSession** 的会话对象。
输入包含 **PSSession** 的变量或用于创建或获取 **PSSession** 的命令，例如 New-PSSession 或 **Get-PSSession** 命令。
你还可以通过管道将一个或多个会话对象传递给 **Remove-PSSession**。

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -VMId

指定虚拟机的 ID 的数组。
此 cmdlet 与每个指定的虚拟机启动交互会话。
若要查看可供你使用的虚拟机，请使用以下命令：

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

指定一个虚拟机的名称数组。
此 cmdlet 与每个指定的虚拟机启动交互会话。
若要查看可供你使用的虚拟机，请使用 **Get-VM** cmdlet。

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
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

### System.Management.Automation.Runspaces.PSSession

可以将会话对象通过管道传递给此 cmdlet。

## 输出

### 无

此 cmdlet 不返回任何对象。

## 注释

* Id 参数是必需的。 若要删除当前会话中的所有 **PSSession**，请键入 `Get-PSSession | Remove-PSSession`。
* **PSSession** 使用与远程计算机的持续性连接。 创建 **PSSession** 以运行共享数据的一系列命令。 要了解详情，请键入 `Get-Help about_PSSessions`。
* **PSSession** 特定于当前会话。 结束某个会话时，将强制关闭你在该会话中创建的 **PSSession**。

## 相关链接

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)

