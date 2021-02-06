---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-acl?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Acl
ms.openlocfilehash: 90155472f8455fc479b0f49122182dcec06f6d93
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595615"
---
# Set-Acl

## 摘要
更改指定项（如文件或注册表项）的安全描述符。

## SYNTAX

### ByPath（默认值）

```
Set-Acl [-Path] <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByInputObject

```
Set-Acl [-InputObject] <PSObject> [-AclObject] <Object> [-Passthru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Set-Acl -LiteralPath <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Set-Acl`Cmdlet 更改指定项（如文件或注册表项）的安全描述符，以与你提供的安全描述符中的值相匹配。

若要使用 `Set-Acl` ，请使用 **Path** 或 **InputObject** 参数来识别要更改其安全描述符的项。 然后，使用 **AclObject** 或 **SecurityDescriptor** 参数来提供具有要应用的值的安全描述符。 `Set-Acl` 应用提供的安全描述符。 它将 **AclObject** 参数的值用作模型，并更改项的安全描述符中的值，以与 **AclObject** 参数中的值相匹配。

## 示例

### 示例1：将安全描述符从一个文件复制到另一个文件

```powershell
$DogACL = Get-Acl -Path "C:\Dog.txt"
Set-Acl -Path "C:\Cat.txt" -AclObject $DogACL
```

这些命令将值从 Dog.txt 文件的安全描述符复制到 Cat.txt 文件的安全描述符。 完成这些命令后，Dog.txt 文件和 Cat.txt 文件的安全描述符将完全相同。

第一个命令使用 `Get-Acl` cmdlet 来获取 Dog.txt 文件的安全描述符。
赋值运算符 (`=`) 将安全描述符存储在 $DogACL 变量的值中。

第二个命令使用将 `Set-Acl` Cat.txt 的 ACL 中的值更改为中的值 `$DogACL` 。

**Path** 参数的值是 Cat.txt 文件的路径。 **AclObject** 参数的值是模型 acl，在此示例中，是在变量中保存的 Dog.txt 的 acl `$DogACL` 。

### 示例2：使用管道运算符传递描述符

```powershell
Get-Acl -Path "C:\Dog.txt" | Set-Acl -Path "C:\Cat.txt"
```

此命令与上一示例中的命令几乎相同，不同之处在于它使用管道运算符 (`|`) 将安全描述符从 `Get-Acl` 命令发送到 `Set-Acl` 命令。

第一个命令使用 `Get-Acl` cmdlet 来获取 Dog.txt 文件的安全描述符。 管道运算符 (`|`) 将表示 Dog.txt 安全描述符的对象传递给 `Set-Acl` cmdlet。

第二个命令使用将 `Set-Acl` Dog.txt 的安全描述符应用到 Cat.txt。
完成该命令后，Dog.txt 和 Cat.txt 文件的 ACL 将完全相同。

### 示例3：将安全描述符应用于多个文件

```powershell
$NewAcl = Get-Acl File0.txt
Get-ChildItem -Path "C:\temp" -Recurse -Include "*.txt" -Force | Set-Acl -AclObject $NewAcl
```

这些命令将 File0.txt 文件中的安全描述符应用于 `C:\Temp` 目录及其所有子目录中的所有文本文件。

第一个命令将获取当前目录中 File0.txt 文件的安全描述符，并使用赋值运算符 () 将 `=` 其存储在 `$NewACL` 变量中。

管道中的第一个命令使用 Get-ChildItem cmdlet 获取目录中的所有文本文件 `C:\Temp` 。 **递归** 参数将该命令扩展到的所有子目录 `C:\temp` 。 **Include** 参数将检索到的文件限制为文件扩展名为的文件 `.txt` 。 **Force** 参数将获取本来会被排除的隐藏文件。  (不能使用 `c:\temp\*.txt` ，因为 **递归** 参数适用于目录而非文件。 ) 

管道运算符 (`|`) 将表示检索到的文件的对象发送到 `Set-Acl` cmdlet，这会将 **AclObject** 参数中的安全描述符应用到管道中的所有文件。

在实践中，最好将 **WhatIf** 参数与 `Set-Acl` 可能影响多个项的所有命令一起使用。 在这种情况下，管道中的第二个命令将为 `Set-Acl -AclObject $NewAcl -WhatIf` 。 此命令将列出会受该命令影响的文件。 查看结果后，可以在不带 **WhatIf** 参数的情况下再次运行该命令。

### 示例4：禁用继承并保留继承的访问规则

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
$isProtected = $true
$preserveInheritance = $true
$NewAcl.SetAccessRuleProtection($isProtected, $preserveInheritance)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

这些命令将禁止从父文件夹进行访问继承，同时仍然保留现有的继承访问规则。

第一个命令使用 `Get-Acl` cmdlet 来获取 Dog.txt 文件的安全描述符。

接下来，创建变量以将继承的访问规则转换为显式访问规则。 若要通过继承保护与此关联的访问规则，请将 `$isProtected` 变量设置为 `$true` 。若要允许继承，请将设置 `$isProtected` 为 `$false` 。 有关详细信息，请参阅 [设置访问规则保护](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)。
`$preserveInheritance`设置为 `$true` 以保留继承的访问规则的变量; 如果为 false，则删除继承的访问规则。 然后，使用 **SetAccessRuleProtection ( # B1** 方法更新访问规则保护。

最后一个命令使用将 `Set-Acl` 的安全描述符应用到 Dog.txt。 命令完成后，从 "宠物" 文件夹继承的 Dog.txt 的 Acl 将直接应用到 Dog.txt，而添加到宠物的新访问策略不会更改对 Dog.txt 的访问权限。

### 示例5：授予管理员对文件的完全控制权限

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
# Set properties
$identity = "BUILTIN\Administrators"
$fileSystemRights = "FullControl"
$type = "Allow"
# Create new rule
$fileSystemAccessRuleArgumentList = $identity, $fileSystemRights, $type
$fileSystemAccessRule = New-Object -TypeName System.Security.AccessControl.FileSystemAccessRule -ArgumentList $fileSystemAccessRuleArgumentList
# Apply new rule
$NewAcl.SetAccessRule($fileSystemAccessRule)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

此命令将授予 **BUILTIN\Administrators** 组对 Dog.txt 文件的完全控制权限。

第一个命令使用 `Get-Acl` cmdlet 来获取 Dog.txt 文件的安全描述符。

创建后一种变量，为 **BUILTIN\Administrators** 组授予对 Dog.txt 文件的完全控制权。 `$identity`设置为[用户帐户](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)名称的变量。 `$fileSystemRights`将变量设置为 FullControl，可以是指定与访问规则关联的操作的类型的[FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights)值之一。 `$type`设置为 "允许" 的变量指定是允许还是拒绝该操作。 `$fileSystemAccessRuleArgumentList`变量是在生成新的 **FileSystemAccessRule** 对象时传递的参数列表。 然后，创建一个新的 **FileSystemAccessRule** 对象，并将 **FileSystemAccessRule** 对象传递到 **SetAccessRule ( # B1** 方法，添加新的访问规则。

最后一个命令使用将 `Set-Acl` 的安全描述符应用到 Dog.txt。 命令完成后， **BUILTIN\Administrators** 组将对 Dog.txt 具有完全控制。

## PARAMETERS

### -AclObject

指定具有所需属性值的 ACL。 `Set-Acl` 更改 **Path** 或 **InputObject** 参数指定的项的 ACL，使其与指定安全对象中的值相匹配。

可以将命令的输出保存 `Get-Acl` 在变量中，然后使用 **AclObject** 参数传递变量，或者键入 `Get-Acl` 命令。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClearCentralAccessPolicy

从指定项中删除中心访问策略。

从 Windows Server 2012 开始，管理员可以使用 Active Directory 和组策略为用户和组设置中心访问策略。 有关详细信息，请参阅 [动态访问控制：方案概述](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview)。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByPath, ByLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exclude

忽略指定项。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如 `*.txt`。 允许使用通配符。

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

### -Include

只更改指定项。 此参数值使 **Path** 参数有效。
请输入路径元素或模式，例如 `*.txt`。 允许使用通配符。

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

### -InputObject

更改指定对象的安全描述符。 请输入包含对象的变量或可获取该对象的命令。

不能通过管道将对象更改为 `Set-Acl` 。 而应该在命令中显式使用 **InputObject** 参数。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

更改指定项的安全描述符。 与 **Path** 不同，**LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包含转义符，请将其括在单引号中 (`'`) 。
单引号指示 PowerShell 不要将任何字符解释为转义序列。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Passthru

返回表示已更改的安全描述符的对象。 默认情况下，此 cmdlet 将不产生任何输出。

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

更改指定项的安全描述符。 输入项的路径，如文件或注册表项的路径。 允许使用通配符。

如果将安全对象传递到 `Set-Acl` (通过使用 **AclObject** 或 **SecurityDescriptor** 参数，或者通过将安全对象从 Get-Acl 传递到 `Set-Acl`) ，并且省略了 **path** 参数 (名称和值) ，则 `Set-Acl` 使用安全对象中包含的路径。

```yaml
Type: System.String[]
Parameter Sets: ByPath
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

### System.Security.AccessControl.ObjectSecurity、System.Security.AccessControl.CommonSecurityDescriptor

你可以通过管道将 ACL 对象或安全描述符发送到 `Set-Acl` 。

## 输出

### System.Security.AccessControl.FileSecurity

默认情况下，不 `Set-Acl` 会生成任何输出。 但是，如果使用 **Passthru** 参数，则它会生成一个安全对象。 安全对象的类型取决于项的类型。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

`Set-Acl`PowerShell 文件系统和注册表提供程序支持 cmdlet。 因此，可以使用它来更改文件、目录和注册表项的安全描述符。

## 相关链接

[Get-Acl](Get-Acl.md)

[FileSystemAccessRule](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)

[ObjectSecurity. SetAccessRuleProtection](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)

[FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights)
