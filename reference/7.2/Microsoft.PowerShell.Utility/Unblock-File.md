---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 8bbfe761a71b38b541f23730d84eb0023a059318
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597250"
---
# Unblock-File

## 摘要
取消阻止已从 Internet 下载的文件。

## SYNTAX

### ByPath（默认值）

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Unblock-File`Cmdlet 可让你打开从 Internet 下载的文件。 它取消阻止从 Internet 下载的 PowerShell 脚本文件，以便你可以运行这些文件，即使 PowerShell 执行策略是 **RemoteSigned** 也是如此。 默认情况下，将阻止这些文件以保护计算机免受不受信任的文件的威胁。

使用 cmdlet 之前 `Unblock-File` ，请查看该文件及其来源，并验证是否可以安全地打开。

在内部，该 `Unblock-File` cmdlet 将删除该区域。标识符备用数据流，该数据流的值为 "3"，表示它是从 Internet 下载的。

有关 PowerShell 执行策略的详细信息，请参阅 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)。

此 cmdlet 是在 Windows PowerShell 3.0 中引入的。

## 示例

### 示例 1：取消阻止一个文件

此命令将取消阻止 PowerShellTips.chm 文件。

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

### 示例 2：取消阻止多个文件

此命令取消阻止 `C:\Downloads` 目录中其名称包含 "PowerShell" 的所有文件。 在你已验证所有文件都安全之前，不要运行类似此命令的命令。

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

### 示例 3：查找和取消阻止脚本

此命令显示了如何查找和取消阻止 PowerShell 脚本。

第一个命令使用 *get* Cmdlet 的 **Stream** 参数获取带有区域的文件。标识符流。

第二个命令显示在 PowerShell 会话中运行已阻止的脚本时所发生的情况，其中执行策略为 **RemoteSigned**。 RemoteSigned 策略阻止你运行从 Internet 下载的脚本，除非它们已进行数字签名。

第三个命令使用 `Unblock-File` cmdlet 取消阻止脚本，以便它可以在会话中运行。

```
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

## PARAMETERS

### -LiteralPath

指定要取消阻止的文件。 与 **Path** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定要取消阻止的文件。 支持使用通配符。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
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

### System.String

可以通过管道将文件路径传递给 `Unblock-File` 。

## 输出

### 无

此 cmdlet 将不生成任何输出。

## 注释

- PowerShell 7 中增加了对 macOS 的支持。
- 此 `Unblock-File` cmdlet 仅适用于文件系统驱动器。
- `Unblock-File`执行与文件资源管理器的 "**属性**" 对话框中的 "**解除阻止**" 按钮相同的操作。
- 如果在 `Unblock-File` 未被阻止的文件上使用 cmdlet，则该命令对未阻止的文件无效，并且该 cmdlet 不会生成错误。

## 相关链接

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[Get-Item](../Microsoft.PowerShell.Management/Get-Item.md)

[Out-File](Out-File.md)

[FileSystem 提供程序](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)
