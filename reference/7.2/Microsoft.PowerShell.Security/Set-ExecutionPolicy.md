---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ExecutionPolicy
ms.openlocfilehash: 4c45267113ff7b8a870d5a05bf3e4ab922f7e9c6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595628"
---
# Set-ExecutionPolicy

## 摘要
设置 Windows 计算机的 PowerShell 执行策略。

## SYNTAX

### 全部

```
Set-ExecutionPolicy [-ExecutionPolicy] <ExecutionPolicy> [[-Scope] <ExecutionPolicyScope>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Set-ExecutionPolicy`Cmdlet 更改 Windows 计算机的 PowerShell 执行策略。 有关详细信息，请参阅 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)。

从非 Windows 计算机的 PowerShell 6.0 开始，默认的执行策略是不 **受限制** 的，无法更改。 `Set-ExecutionPolicy`Cmdlet 可用，但 PowerShell 会显示不受支持的控制台消息。

执行策略是 PowerShell 安全策略的一部分。 执行策略确定你是否可以加载配置文件（如 PowerShell 配置文件）或运行脚本。 并且，在运行脚本之前是否必须对其进行数字签名。

此 `Set-ExecutionPolicy` cmdlet 的默认作用域为 **LocalMachine**，这会影响使用该计算机的每个人。 若要更改 **LocalMachine** 的执行策略，请以 **管理员身份运行** 启动 PowerShell。

若要按优先级顺序显示每个作用域的执行策略，请使用 `Get-ExecutionPolicy -List` 。 若要查看 PowerShell 会话的有效执行策略，请使用 `Get-ExecutionPolicy` 不带参数的。

## 示例

### 示例1：设置执行策略

此示例演示如何设置本地计算机的执行策略。

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
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy`Cmdlet 使用 **set-executionpolicy** 参数指定 **RemoteSigned** 策略。 **Scope** 参数指定默认作用域值 " **LocalMachine**"。 若要查看执行策略设置，请将 `Get-ExecutionPolicy` cmdlet 与 **List** 参数一起使用。

### 示例2：设置与组策略冲突的执行策略

此命令尝试将 **LocalMachine** 作用域的执行策略设置为 " **受限**"。
**LocalMachine** 的限制更强，但并不是有效的策略，因为它与组策略冲突。 **受限制** 的策略会写入到 **HKEY_LOCAL_MACHINE** 的注册表配置单元。

```
PS> Set-ExecutionPolicy -ExecutionPolicy Restricted -Scope LocalMachine

Set-ExecutionPolicy : PowerShell updated your local preference successfully, but the setting is
overridden by the Group Policy applied to your system. Due to the override, your shell will retain
its current effective execution policy of "AllSigned". Contact your Group Policy administrator for
more information. At line:1 char:20 + Set-ExecutionPolicy <<<< restricted

PS> Get-ChildItem -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds

Name                    Property
----                    --------
Microsoft.PowerShell    Path            : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
                        ExecutionPolicy : Restricted
ScriptedDiagnostics     ExecutionPolicy : Unrestricted
```

`Set-ExecutionPolicy`Cmdlet 使用 **set-executionpolicy** 参数指定 **受限制** 的策略。 **Scope** 参数指定默认作用域值 " **LocalMachine**"。
`Get-ChildItem`Cmdlet 将 **Path** 参数与 **HKLM** 提供程序一起使用，以指定注册表位置。

### 示例3：将远程计算机上的执行策略应用于本地计算机

此命令获取远程计算机上的执行策略对象并在本地计算机上设置策略。 `Get-ExecutionPolicy` 沿管道向下发送 **Microsoft.PowerShell.ExecutionPolicy** 对象。 `Set-ExecutionPolicy` 接受管道输入，而不需要 **set-executionpolicy** 参数。

```
PS> Invoke-Command -ComputerName Server01 -ScriptBlock { Get-ExecutionPolicy } | Set-ExecutionPolicy
```

`Invoke-Command`Cmdlet 在本地计算机上执行，并将 **ScriptBlock** 发送到远程计算机。 **ComputerName** 参数指定远程计算机 **Server01**。 **ScriptBlock** 参数 `Get-ExecutionPolicy` 在远程计算机上运行。 将 `Get-ExecutionPolicy` 对象向下发送到 `Set-ExecutionPolicy` 。
`Set-ExecutionPolicy` 将执行策略应用于本地计算机的默认作用域 " **LocalMachine**"。

### 示例4：设置执行策略的作用域

此示例演示如何为指定的作用域 " **CurrentUser**" 设置执行策略。 **CurrentUser** 范围仅影响设置此作用域的用户。

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser
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

`Set-ExecutionPolicy` 使用 **set-executionpolicy** 参数指定 **AllSigned** 策略。
**Scope** 参数指定 **CurrentUser**。 若要查看执行策略设置，请将 `Get-ExecutionPolicy` cmdlet 与 **List** 参数一起使用。

用户的有效执行策略将变为 " **AllSigned**"。

### 示例5：删除当前用户的执行策略

此示例演示如何使用 **未定义** 执行策略删除指定作用域的执行策略。

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy` 使用 **set-executionpolicy** 参数指定 **未定义** 的策略。
**Scope** 参数指定 **CurrentUser**。 若要查看执行策略设置，请将 `Get-ExecutionPolicy` cmdlet 与 **List** 参数一起使用。

### 示例6：设置当前 PowerShell 会话的执行策略

**进程** 范围仅影响当前 PowerShell 会话。 执行策略保存在环境变量中 `$env:PSExecutionPolicyPreference` ，并在会话关闭时删除。

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope Process
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       AllSigned
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy`使用 **set-executionpolicy** 参数来指定 **AllSigned** 策略。 **Scope** 参数指定值 **进程**。 若要查看执行策略设置，请将 `Get-ExecutionPolicy` cmdlet 与 **List** 参数一起使用。

### 示例7：取消阻止脚本，以便在不更改执行策略的情况下运行该脚本

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

### -ExecutionPolicy

指定执行策略。 如果没有组策略，并且每个作用域的执行策略设置为 " **未定义**"，则 " **受限制** " 将成为所有用户的有效策略。

可接受的执行策略值如下所示：

- **AllSigned**。 要求所有脚本和配置文件都由受信任的发布者签名，包括在本地计算机上编写的脚本。
- **绕过**。 不阻止任何操作，并且没有任何警告或提示。
- **Default**。 设置默认的执行策略。 **适用于 windows** 客户端或 windows 服务器的 **RemoteSigned** 。
- **RemoteSigned**。 要求从 Internet 下载的所有脚本和配置文件都由受信任的发布者进行签名。 Windows server 计算机的默认执行策略。
- **限制**。 不加载配置文件或运行脚本。 默认的执行策略 Windows 客户端计算机。
- **未定义**。 未为该作用域设置执行策略。 从非组策略设置的作用域中删除已分配的执行策略。 如果所有作用域中的执行策略均未 **定义**，则会 **限制** 有效的执行策略。
- **无限制**。 从 PowerShell 6.0 开始，这是非 Windows 计算机的默认执行策略，无法更改。 加载所有配置文件并运行所有脚本。 如果运行从 internet 下载的未签名脚本，则会在运行之前提示你提供权限。

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: AllSigned, Bypass, Default, RemoteSigned, Restricted, Undefined, Unrestricted

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Force

抑制所有确认提示。 请谨慎使用此参数，以避免意外结果。

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

### -Scope

指定受执行策略影响的作用域。 默认作用域为 **LocalMachine**。

有效的执行策略由优先级顺序确定，如下所示：

- **MachinePolicy**。 为计算机的所有用户组策略设置。
- **UserPolicy**。 为计算机的当前用户组策略设置。
- **进程**。 仅影响当前 PowerShell 会话。
- **CurrentUser**。 仅影响当前用户。
- **LocalMachine**。 影响计算机的所有用户的默认作用域。

**进程** 范围仅影响当前 PowerShell 会话。 执行策略保存在环境变量中 `$env:PSExecutionPolicyPreference` ，而不是保存在注册表中。 关闭 PowerShell 会话后，会删除变量和值。

**CurrentUser** 作用域的执行策略将写入到 **HKEY_LOCAL_USER** 的注册表配置单元中。

**LocalMachine** 作用域的执行策略将写入到 **HKEY_LOCAL_MACHINE** 的注册表配置单元中。

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 1
Default value: LocalMachine
Accept pipeline input: True (ByPropertyName)
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

### Microsoft.PowerShell.ExecutionPolicy、System.String

可以通过管道将执行策略对象或包含执行策略名称的字符串传递给 `Set-ExecutionPolicy` 。

## 输出

### 无

`Set-ExecutionPolicy` 不返回任何输出。

## 注释

`Set-ExecutionPolicy` 不会更改 **MachinePolicy** 和 **UserPolicy** 作用域，因为它们由组策略设置。

`Set-ExecutionPolicy` 不会重写组策略，即使用户首选项比策略更严格。

如果为计算机或用户启用了组策略 **打开脚本执行** ，则将保存用户首选项，但这不是有效的。 PowerShell 会显示一条消息，说明冲突。

## 相关链接

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Group_Policy_Settings](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Unblock-File](../Microsoft.PowerShell.Utility/Unblock-File.md)

