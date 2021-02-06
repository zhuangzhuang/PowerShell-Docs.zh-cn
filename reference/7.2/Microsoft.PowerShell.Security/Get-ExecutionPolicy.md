---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExecutionPolicy
ms.openlocfilehash: d6555f1abc824add4613654461106af34045e1a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596627"
---
# Get-ExecutionPolicy

## 摘要
获取当前会话的执行策略。

## SYNTAX

### 全部

```
Get-ExecutionPolicy [[-Scope] <ExecutionPolicyScope>] [-List] [<CommonParameters>]
```

## DESCRIPTION

若要按优先级顺序显示每个作用域的执行策略，请使用 `Get-ExecutionPolicy -List` 。 若要查看 PowerShell 会话的有效执行策略，请使用 `Get-ExecutionPolicy` 不带参数的。

有效的执行策略由通过设置的执行策略确定 `Set-ExecutionPolicy` ，并组策略设置。

有关详细信息，请参阅 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)。

## 示例

### 示例1：获取所有执行策略

此命令按优先级顺序显示每个作用域的执行策略。

```powershell
Get-ExecutionPolicy -List
```

```Output
Scope          ExecutionPolicy
-----          ---------------
MachinePolicy  Undefined
UserPolicy     Undefined
Process        Undefined
CurrentUser    AllSigned
LocalMachine   Undefined
```

`Get-ExecutionPolicy`Cmdlet 使用 **List** 参数显示每个作用域的执行策略。

### 示例2：设置执行策略

此示例演示如何为本地计算机设置执行策略。

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy`Cmdlet 使用 **set-executionpolicy** 参数指定 **RemoteSigned** 策略。 **Scope** 参数指定默认作用域值 " **LocalMachine**"。 若要查看执行策略设置，请将 `Get-ExecutionPolicy` cmdlet 与 **List** 参数一起使用。

### 示例3：获取有效的执行策略

此示例演示如何显示 PowerShell 会话的有效执行策略。

```
PS> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned

PS> Get-ExecutionPolicy

AllSigned
```

`Get-ExecutionPolicy`Cmdlet 使用 **List** 参数显示每个作用域的执行策略。 `Get-ExecutionPolicy`不使用参数运行 cmdlet，以显示有效的执行策略 **AllSigned**。

### 示例4：取消阻止脚本，以便在不更改执行策略的情况下运行该脚本

此示例演示 **RemoteSigned** 执行策略如何阻止你运行未签名的脚本。

最佳做法是读取脚本的代码，并在使用 cmdlet **之前** 验证它是否安全 `Unblock-File` 。 `Unblock-File`Cmdlet 取消阻止脚本，以便它们可以运行，但不会更改执行策略。

```
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

.\Start-ActivityTracker.ps1 : File .\Start-ActivityTracker.ps1 cannot be loaded.
The file .\Start-ActivityTracker.ps1 is not digitally signed.
The script will not execute on the system.
For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess

PS> Unblock-File -Path .\Start-ActivityTracker.ps1

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

Task 1:
```

`Set-ExecutionPolicy`使用 **set-executionpolicy** 参数来指定 **RemoteSigned** 策略。 策略设置为默认作用域 " **LocalMachine**"。

`Get-ExecutionPolicy`Cmdlet 显示 **RemoteSigned** 是当前 PowerShell 会话的有效执行策略。

从当前目录执行 **Start-ActivityTracker.ps1** 脚本。 由于脚本未进行数字签名，因此脚本被 **RemoteSigned** 阻止。

在此示例中，脚本的代码已评审并验证为可安全运行。 `Unblock-File`Cmdlet 使用 **Path** 参数取消阻止脚本。

若要验证是否 `Unblock-File` 未更改执行策略， `Get-ExecutionPolicy` 则会显示有效的执行策略 **RemoteSigned**。

将从当前目录执行 **Start-ActivityTracker.ps1** 的脚本。 脚本开始运行，因为它已被 cmdlet 取消阻止 `Unblock-File` 。

## PARAMETERS

### -List

获取按优先级顺序列出的会话的所有执行策略值。 默认情况下， `Get-ExecutionPolicy` 仅获取有效的执行策略。

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

### -Scope

指定受执行策略影响的作用域。

有效的执行策略由优先级顺序确定，如下所示：

- **MachinePolicy**。 为计算机的所有用户组策略设置。
- **UserPolicy**。 为计算机的当前用户组策略设置。
- **进程**。 仅影响当前 PowerShell 会话。
- **CurrentUser**。 仅影响当前用户。
- **LocalMachine**。 影响计算机的所有用户的默认作用域。

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 0
Default value: Effective execution policy
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

`Get-ExecutionPolicy` 不接受来自管道的输入。

## 输出

### Microsoft.PowerShell.ExecutionPolicy

Cmdlet 始终在 Linux 和 macOS 平台上返回不 **受限制** 。

## 注释

执行策略是 PowerShell 安全策略的一部分。 执行策略确定你是否可以加载配置文件（如 PowerShell 配置文件）或运行脚本。 并且，在运行脚本之前是否必须对其进行数字签名。

## 相关链接

[about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)

[about_Group_Policy_Settings](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)
