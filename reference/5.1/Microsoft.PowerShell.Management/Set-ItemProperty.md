---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ItemProperty
ms.openlocfilehash: cbd1229721650823d9780517934c40a2287f4227
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692669"
---
# Set-ItemProperty

## 摘要
创建或更改某一项的属性值。

## SYNTAX

### propertyValuePathSet（默认值）

```
Set-ItemProperty [-Path] <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### propertyPSObjectPathSet

```
Set-ItemProperty [-Path] <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### propertyValueLiteralPathSet

```
Set-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### propertyPSObjectLiteralPathSet

```
Set-ItemProperty -LiteralPath <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## DESCRIPTION

`Set-ItemProperty`Cmdlet 更改指定项的属性的值。 可以使用该 cmdlet 设定或更改项的属性。 例如，可以使用 `Set-ItemProperty` 将文件对象的 **IsReadOnly** 属性的值设置为 `$True` 。

你还可以使用 `Set-ItemProperty` 来创建和更改注册表值和数据。
例如，可以向注册表项中添加新的注册表条目以及设定或更改该条目的值。

## 示例

### 示例1：设置文件的属性

此命令将 "final.doc" 文件的 " **IsReadOnly** " 属性的值设置为 "true"。 它使用 **路径** 指定文件的名称，使用 **name** 指定属性的名称，并使用 **Value** 参数指定新值。

文件是 **FileInfo** 对象，而 **IsReadOnly** 只是它的一个属性。
若要查看所有属性，请键入 `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType Property` 。

`$true`自动变量表示值 "TRUE"。
有关详细信息，请参阅 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

```powershell
Set-ItemProperty -Path C:\GroupFiles\final.doc -Name IsReadOnly -Value $true
```

### 示例2：创建注册表项和值

此示例演示如何使用 `Set-ItemProperty` 来创建新的注册表项，并为该项分配值。 它在 "HKLM\Software" 键中的 "ContosoCompany" 键内创建 "NoOfEmployees" 条目，并将其值设置为823。

因为注册表项被视为注册表项的属性（这些项是项），您可以使用这些项 `Set-ItemProperty` 创建注册表项，并建立和更改它们的值。

第一个命令创建注册表项。
它使用 **path** 来指定驱动器的路径 `HKLM:` 和 "Software\MyCompany" 项。
该命令使用 **name** 来指定输入值的名称和 **值** 。

第二个命令使用 `Get-ItemProperty` cmdlet 查看新的注册表项。 如果使用 `Get-Item` 或 `Get-ChildItem` cmdlet，则这些项将不会显示，因为它们是键的属性，而不是项或子项的属性。

第三个命令将 **NoOfEmployees** 条目的值更改为824。

你还可以使用 `New-ItemProperty` cmdlet 来创建注册表项及其值，并使用 `Set-ItemProperty` 来更改值。

有关驱动器的详细信息 `HKLM:` ，请键入 `Get-Help Get-PSDrive` 。
有关如何使用 PowerShell 管理注册表的详细信息，请键入 `Get-Help Registry` 。

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 823
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 823

```

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 824
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 824
```

### 示例3：使用管道修改项

这些命令演示如何使用管道运算符 () 将 `|` 项发送到 `Set-ItemProperty` 。

该命令的第一部分使用 `Get-ChildItem` 来获取表示 "Weekly.txt" 文件的对象。
该命令使用管道运算符将文件对象发送到 `Set-ItemProperty` 。
该 `Set-ItemProperty` 命令使用 **Name** 和 **Value** 参数来指定属性及其新值。

此命令等效于使用 **InputObject** 参数指定获取的对象 `Get-ChildItem` 。

```powershell
Get-ChildItem weekly.txt | Set-ItemProperty -Name IsReadOnly -Value $True
```

## PARAMETERS

### -Credential

指定有权执行此操作的用户帐户。
默认为当前用户。

键入用户名，如“User01”或“Domain01\User01”；或输入 **PSCredential** 对象，如 `Get-Credential` cmdlet 生成的一个 PSCredential 对象。
如果键入用户名，则将提示你输入密码。

> [!NOTE]
> 随 PowerShell 一起安装的任何提供程序都不支持此参数。
> 若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。

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

指定 cmdlet 不起作用的那些项，并包括所有其他项。
此参数值使 **Path** 参数有效。
请输入路径元素或模式，例如“*.txt”。
允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

以提供程序的格式或语言指定筛选器。
此参数值使 **Path** 参数有效。

筛选器的语法（包括通配符字符的使用），具体取决于提供程序。
筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。

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

强制 cmdlet 设置用户不能访问的项的属性。
不同提供程序有不同的实现。
有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

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

仅指定 cmdlet 操作的那些项，排除所有其他项。
此参数值使 **Path** 参数有效。
请输入路径元素或模式，例如“*.txt”。
允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定具有此 cmdlet 更改的属性的对象。
请输入包含对象的变量或可获取该对象的命令。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: propertyPSObjectPathSet, propertyPSObjectLiteralPathSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定项属性的路径。
与 **Path** 参数不同，**LiteralPath** 的值严格按照所键入的形式使用。
不会将任何字符解释为通配符。
如果路径包括转义符，请将其括在单引号中。
单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String[]
Parameter Sets: propertyValueLiteralPathSet, propertyPSObjectLiteralPathSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定属性的名称。

```yaml
Type: System.String
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

返回一个表示项属性的对象。
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

### -Path

指定包含要修改的属性的项的路径。

```yaml
Type: System.String[]
Parameter Sets: propertyValuePathSet, propertyPSObjectPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Type

**类型** 是注册表提供程序添加到 cmdlet 的动态参数 `Set-ItemProperty` 。
此参数仅适用于注册表驱动器。

指定此 cmdlet 添加的属性类型。
此参数的可接受值为：

- **String**：指定以 null 结尾的字符串。 等效于 **REG_SZ**。
- **ExpandString**：指定一个以 null 结尾的字符串，该字符串包含对在检索值时扩展的环境变量的未展开引用。 等效于 **REG_EXPAND_SZ**。
- **Binary**：指定任意格式的二进制数据。 等效于 **REG_BINARY**。
- **DWord**：指定32位二进制数。 等效于 **REG_DWORD**。
- **多字符串**：指定以 null 结尾的字符串的数组，该数组以两个 null 字符结尾。
  等效于 **REG_MULTI_SZ**。
- **Qword**：指定64位二进制数。 等效于 **REG_QWORD**。
- **未知**：指示不受支持的注册表数据类型，如 **REG_RESOURCE_LIST**。

```yaml
Type: RegistryValueKind
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseTransaction

在活动事务中使用该命令。
仅当正在执行事务时，此参数才有效。
有关详细信息，请参阅 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

指定属性的值。

```yaml
Type: Object
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

提示你在运行 cmdlet 之前进行确认。

```yaml
Type: SwitchParameter
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
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.Management.Automation.PSObject

可以通过管道将对象传递给此 cmdlet。

## 输出

### PSCustomObject （无）

如果指定 **PassThru** 参数，则此 cmdlet 将生成一个 **PSCustomObject** 对象，该对象表示已更改的项及其新的属性值。 否则，此 cmdlet 将不生成任何输出。

## 注释

`Set-ItemProperty` 设计用于处理由任何提供程序公开的数据。 若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相关链接

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-ItemProperty](Rename-ItemProperty.md)
