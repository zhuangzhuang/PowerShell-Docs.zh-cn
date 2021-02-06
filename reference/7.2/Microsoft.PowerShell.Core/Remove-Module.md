---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: 2954bbec68b837a73e5365ab6a1e8ecb501d4898
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595838"
---
# Remove-Module

## 摘要
删除当前会话中的模块。

## SYNTAX

### name

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FullyQualifiedName

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ModuleInfo

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**Remove-Module** cmdlet 将从当前会话中删除模块的成员，如 cmdlet 和函数。

如果模块包含某个程序集 (.dll)，则将删除由该程序集实现的所有成员，但不会卸载该程序集。

此 cmdlet 不会将该模块从计算机中卸载或删除。
它仅影响当前 PowerShell 会话。

## 示例

### 示例 1：删除模块

```powershell
Remove-Module -Name "BitsTransfer"
```

此命令将从当前会话中删除 BitsTransfer 模块。

### 示例 2：删除所有模块

```powershell
Get-Module | Remove-Module
```

此命令将从当前会话中删除所有模块。

### 示例 3：通过使用管道删除模块

```powershell
"FileTransfer", "PSDiagnostics" | Remove-Module -Verbose
```

```Output
VERBOSE: Performing operation "Remove-Module" on Target "filetransfer (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\filetransfer\filetransfer.psd1')".
VERBOSE: Performing operation "Remove-Module" on Target "Microsoft.BackgroundIntelligentTransfer.Management (Path: 'C:\Windows\assembly\GAC_MSIL\Microsoft.BackgroundIntelligentTransfer.Management\1.0.0.0__31bf3856ad364e35\Microsoft.BackgroundIntelligentTransfe
r.Management.dll')".
VERBOSE: Performing operation "Remove-Module" on Target "psdiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\psdiagnostics.psd1')".
VERBOSE: Removing imported function 'Start-Trace'.
VERBOSE: Removing imported function 'Stop-Trace'.
VERBOSE: Removing imported function 'Enable-WSManTrace'.
VERBOSE: Removing imported function 'Disable-WSManTrace'.
VERBOSE: Removing imported function 'Enable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Disable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Set-LogProperties'.
VERBOSE: Removing imported function 'Get-LogProperties'.
VERBOSE: Removing imported function 'Enable-PSTrace'.
VERBOSE: Removing imported function 'Disable-PSTrace'.
VERBOSE: Performing operation "Remove-Module" on Target "PSDiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\PSDiagnostics.psm1')".
```

此命令将从当前会话中删除 BitsTransfer 和 PSDiagnostics 模块。

该命令使用管道运算符 (|) 将模块名称发送到 **Remove-Module**。
它使用 *Verbose* 通用参数来获取有关要删除的成员的详细信息。

Verbose 消息显示所删除的项。
这些消息会有所不同，因为 BitsTransfer 模块包含一个实现其 cmdlet 的程序集，以及一个拥有自己的程序集的嵌套模块。
PSDiagnostics 模块包含用于导出函数的模块脚本文件 (.psm1)。

### 示例 4：通过使用 ModuleInfo 删除模块

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

此命令使用 ModuleInfo 参数删除 BitsTransfer 模块。

## PARAMETERS

### -Force

指示此 cmdlet 将删除只读模块。
默认情况下，**Remove-Module** 只删除读写模块。

**ReadOnly** 和 **ReadWrite** 值存储在模块的 **AccessMode** 属性中。

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

### -FullyQualifiedName

指定要删除的模块的完全限定名称。

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ModuleInfo

指定要删除的模块对象。
输入包含模块对象 (**PSModuleInfo**) 的变量，或输入可获取模块对象的命令，如 Get-Module 命令。
你还可以通过管道将模块对象传递给 **Remove-Module**。

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定要删除的模块的名称。
允许使用通配符。
还可以通过管道将名称字符串传递给 **Remove-Module**。

```yaml
Type: System.String[]
Parameter Sets: name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
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

### System.String, System.Management.Automation.PSModuleInfo

可以通过管道将模块名称和模块对象传递给 **Remove-Module**。

## 输出

### 无

此 cmdlet 将不生成任何输出。

## 注释

删除模块时，将执行的模块上有一个事件。
此事件允许模块响应被删除并执行一些清理，如释放资源。 例如：

$OnRemoveScript = {

  \# 执行清理

  $cachedSessions |Remove-PSSession

}

SessionState. OnRemove + = $OnRemoveScript $ExecutionContext

为了完全保持一致性，响应 PowerShell 进程的关闭可能也很有用：

Register-EngineEvent ( [PsEngineEvent]：：正在退出) -操作 $OnRemoveScript

## 相关链接

[Get-Module](Get-Module.md)

[Import-Module](Import-Module.md)

