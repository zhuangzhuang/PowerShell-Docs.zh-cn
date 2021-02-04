---
external help file: Microsoft.PowerShell.ConsoleHost.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/start-transcript?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transcript
ms.openlocfilehash: 4f90dd8e3080d393e50fb8f48133c74909ec2b80
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860739"
---
# Start-Transcript

## 摘要
创建与文本文件的全部或部分 PowerShell 会话的记录。

## 语法

### ByPath（默认值）

```
Start-Transcript [[-Path] <String>] [-Append] [-Force] [-NoClobber] [-IncludeInvocationHeader] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Start-Transcript [[-LiteralPath] <String>] [-Append] [-Force] [-NoClobber] [-IncludeInvocationHeader] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ByOutputDirectory

```
Start-Transcript [[-OutputDirectory] <String>] [-Append] [-Force] [-NoClobber] [-IncludeInvocationHeader]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 说明

`Start-Transcript`Cmdlet 可在文本文件中创建所有或部分 PowerShell 会话的记录。 该脚本包括用户键入的所有命令和在控制台上显示的所有输出。

从 Windows PowerShell 5.0 开始，在 `Start-Transcript` 所有脚本的生成文件名中包含主机名。 这在集中处理企业的日志记录时尤其有用。
Cmdlet 创建的文件 `Start-Transcript` 在名称中包含随机字符，以防止在两个或多个脚本同时启动时可能覆盖或重复。
这还可以防止未经授权地发现存储在集中文件共享中的脚本。

使用 **Append** 参数时，如果目标文件没有字节顺序标记 (BOM) `Start-Transcript` 默认为 `ASCII` 目标文件中的编码。 此行为可能会导致脚本中的 mulitbyte 字符编码不正确。

## 示例

### 示例 1：在使用默认设置的情况下启动脚本文件

```powershell
Start-Transcript
```

此命令将启动默认文件位置中的脚本。

### 示例 2：在特定位置启动脚本文件

```powershell
Start-Transcript -Path "C:\transcripts\transcript0.txt" -NoClobber
```

此命令启动中文件中的脚本 `Transcript0.txt` `C:\transcripts` 。 因为使用了 NoClobber 参数，所以此命令可防止覆盖任何现有文件。 如果 `Transcript0.txt` 文件已存在，则该命令将失败。

## 参数

### -Append

指示此 cmdlet 将新脚本添加到现有文件末尾。 使用 **Path** 参数指定文件。

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

### -Force

允许 cmdlet 将该脚本追加到现有的只读文件。 在只读文件上使用时，该 cmdlet 会将文件权限更改为读写。 使用此参数时，cmdlet 无法覆盖安全限制。

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

### -IncludeInvocationHeader

指示此 cmdlet 记录命令运行时的时间戳。

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

### -LiteralPath

指定脚本文件的位置。 与 **Path** 参数不同，**LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号通知 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

指示此 cmdlet 不会覆盖现有文件。 默认情况下，如果指定路径中存在脚本文件，则将 `Start-Transcript` 覆盖该文件而不发出警告。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputDirectory

指定要在其中保存脚本的特定路径和文件夹。 PowerShell 会自动分配脚本名称。

```yaml
Type: System.String
Parameter Sets: ByOutputDirectory
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定脚本文件的位置。 输入文件的路径 `.txt` 。 不允许使用通配符。

如果未指定路径，将 `Start-Transcript` 使用全局变量的值中的路径 `$Transcript` 。 如果尚未创建此变量，请将 `Start-Transcript` 这些脚本存储在 `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` 文件中。

如果路径中不存在任何目录，该命令将失败。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: False
Position: 0
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

### 无

不能通过管道将对象传递给此 cmdlet。

## 输出

### System.String

此 cmdlet 将返回一个字符串，包含一条确认消息和输出文件的路径。

## 说明

若要停止脚本，请使用 `Stop-Transcript` cmdlet。

若要记录整个会话，请将 `Start-Transcript` 命令添加到配置文件。 有关详细信息，请参阅 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。

## 相关链接

[Stop-Transcript](Stop-Transcript.md)
