---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-content?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Content
ms.openlocfilehash: 89ac365524658612dd878cf8c2c462a40a278487
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692743"
---
# Clear-Content

## 摘要
删除项的内容，但不删除该项。

## SYNTAX

### Path（默认值）

```
Clear-Content [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

### LiteralPath

```
Clear-Content -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

## DESCRIPTION

`Clear-Content`Cmdlet 删除项的内容（如从文件中删除文本），但不删除该项。
鉴于上述原因，项存在，但没有内容。
与 `Clear-Content` 类似 `Clear-Item` ，但它适用于具有内容的项，而不是具有值的项。

## 示例

### 示例1：删除目录中的所有内容

```powershell
Clear-Content "..\SmpUsers\*\init.txt"
```

此命令删除 SmpUsers 目录的所有子目录内的“init.txt”文件中的所有内容。
不删除这些文件，但它们为空。

### 示例2：删除包含通配符的所有文件的内容

```powershell
Clear-Content -Path "*" -Filter "*.log" -Force
```

此命令删除当前目录中所有扩展名为“.log”的文件（包括具有只读属性的文件）的内容。 路径中的星号 (\*) 表示当前目录中的所有项。 **Force** 参数使该命令对只读文件有效。 使用筛选器将命令限制为具有 .log 文件扩展名的文件，而不是指定 \* 。在路径中，可以更快地执行操作。

### 示例3：清除流中的所有数据

此示例显示了 `Clear-Content` cmdlet 如何从备用数据流中清除内容，同时保持流不变。

第一个命令使用 `Get-Content` cmdlet 来获取 `Zone.Identifier` Copy-Script.ps1 文件中的流内容，该文件已从 Internet 下载。

第二个命令使用 `Clear-Content` cmdlet 清除内容。

第三个命令重复第一个命令。 它将验证内容是否已清除，但流仍保持不变。 如果已删除该流，则该命令将生成错误。

您可以使用类似此方法的方法来清除备用数据流的内容。 但是，若要取消安全检查（该安全检查可阻止从 Internet 下载的文件），则不建议使用此方法。 如果验证下载的文件是安全的，请使用 `Unblock-File` cmdlet。

```
PS C:\> Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

[ZoneTransfer]
ZoneId=3

PS C:\>Clear-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

PS C:\>Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
PS C:\>
```

## PARAMETERS

### -Stream

> [!NOTE]
> 此参数仅在 Windows 上可用。

指定内容的备用数据流。 如果该流不存在，则此 cmdlet 将创建它。 不支持通配符。

**Stream** 是 FileSystem 提供程序添加到的动态参数 `Clear-Content` 。 此参数仅在文件系统驱动器中有效，并将清除文件和目录中的备用数据流的内容。

可以使用 `Clear-Content` cmdlet 更改张瑾雯备用数据流的内容，例如 `Zone.Identifier` 。 但是，若要取消安全检查（该安全检查可阻止从 Internet 下载的文件），则不建议使用此方法。 如果验证下载的文件是安全的，请使用 `Unblock-File` cmdlet。

此参数是在 PowerShell 3.0 中引入的。 从 PowerShell 7.2 开始， `Clear-Content` 可以清除目录以及文件中的备用数据流的内容。

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

### -Credential

> [!NOTE]
> 随 PowerShell 一起安装的任何提供程序都不支持此参数。 若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 Invoke 命令。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exclude

以字符串数组的形式指定此 cmdlet 从内容路径中省略的字符串。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如“*.txt”。 允许使用通配符。

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

### -Filter

以提供程序的格式或语言指定筛选器。 此参数值使 **Path** 参数有效。 筛选器的语法（包括通配符的使用）取决于提供程序。 筛选器比其他参数更有效，因为提供程序是在检索对象时应用筛选器，而不是在检索对象后再对其进行筛选。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

强制运行命令而不要求用户确认。

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

### -Include

以字符串数组的形式指定此 cmdlet 清除的内容。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如“*.txt”。 允许使用通配符。

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

### -LiteralPath

指定要删除其内容的项的路径。 与 **Path** 参数不同，**LiteralPath** 的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。
如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定要删除其内容的项的路径。 允许使用通配符。 此路径必须是指向该项的路径，而不是容器的路径。 例如，必须指定一个或多个文件的路径，而不是目录的路径。 允许使用通配符。 此参数为必需参数，但参数名（“Path”）为可选项。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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
Default value: None
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

### 无

不能通过管道将对象传递给 `Clear-Content` 。

## 输出

### 无

此 cmdlet 不返回任何对象。

## 注释

你可以将 `Clear-Content` 与 PowerShell FileSystem 提供程序和操作内容的其他提供程序一起使用。 若要清除不视为内容的项（例如，由 PowerShell 证书或注册表提供程序管理的项），请使用 `Clear-Item` 。

`Clear-Content`Cmdlet 设计用于处理由任何提供程序公开的数据。
若要列出会话中可用的提供程序，请键入 `Get-PsProvider`。
有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相关链接

[Add-Content](Add-Content.md)

[Get-Content](Get-Content.md)

[Get-Item](Get-Item.md)

[Set-Content](Set-Content.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

