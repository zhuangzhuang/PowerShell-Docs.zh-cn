---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 67d9f351b8ef4936dcb4e9cff6583da0f464bc12
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2020
ms.locfileid: "99596225"
---
# Get-Item

## 摘要
获取位于指定位置的项。

## SYNTAX

### Path（默认值）

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### LiteralPath

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Get-Item`Cmdlet 将获取位于指定位置的项。 除非使用通配符 (`*`) 请求该项的所有内容，否则它不会获取位于该位置的项的内容。

PowerShell 提供程序使用此 cmdlet 在不同类型的数据存储中导航。

## 示例

### 示例1：获取当前目录

此示例获取当前目录。 点 ( ".") 表示当前位置 (的项，而不) 内容。

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### 示例2：获取当前目录中的所有项

此示例将获取当前目录中的所有项。 通配符 (`*`) 表示当前项的所有内容。

```powershell
Get-Item *
```

```output
Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006   9:29 AM            Logs
d----         7/26/2006   9:26 AM            Recs
-a---         7/26/2006   9:28 AM         80 date.csv
-a---         7/26/2006  10:01 AM         30 filenoext
-a---         7/26/2006   9:30 AM      11472 process.doc
-a---         7/14/2006  10:47 AM         30 test.txt
```

### 示例3：获取驱动器的当前目录

此示例获取驱动器的当前目录 `C:` 。 检索到的对象仅表示目录，而不表示其内容。

```powershell
Get-Item C:\
```

### 示例4：获取指定驱动器中的项

此示例获取驱动器中的项 `C:` 。 通配符 (`*`) 表示容器中的所有项，而不仅仅是容器。

```powershell
Get-Item C:\*
```

在 PowerShell 中，使用单个星号 (`*`) 来获取内容，而不是使用传统的 `*.*` 。 格式按原义解释，因此 `*.*` 不会检索不带句点的目录或文件名。

### 示例5：获取指定目录中的属性

此示例获取目录的 **LastAccessTime** 属性 `C:\Windows` 。 **LastAccessTime** 只是文件系统目录的一个属性。 若要查看目录的所有属性，请键入 `(Get-Item <directory-name>) | Get-Member` 。

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### 示例6：显示注册表项的内容

此示例显示了 **Microsoft PowerShell** 注册表项的内容。 可以将此 cmdlet 与 PowerShell 注册表提供程序结合使用来获取注册表项和子项，但必须使用 `Get-ItemProperty` cmdlet 来获取注册表值和数据。

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### 示例7：获取目录中具有排除项的项

此示例获取 Windows 目录中名称中包含点 () 的项 `.` ，但不以开头 `w*` 。此示例仅在以下情况下有效：该路径包括 () 的通配符 `*` ，以指定项的内容。

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### 示例8：获取硬链接信息

在 PowerShell 6.2 中，添加了一个替代视图来获取硬链接信息。 若要获取硬链接信息，请通过管道将输出传递给 `Format-Table -View childrenWithHardlink`

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### 示例9：非 Windows 操作系统的输出

在 Unix 系统上的 PowerShell 7.1 中， `Get-Item` cmdlet 提供类似于 unix 的输出：

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

现在作为输出的一部分的新属性包括：

- **UnixMode** 是 Unix 系统上表示的文件权限
- **用户** 是文件所有者
- **组** 是组的所有者
- **Size** 是在 Unix 系统上表示的文件或目录的大小

> [!NOTE]
> 此功能已从实验迁移到 PowerShell 7.1 中的主流。

## PARAMETERS

### -Stream

> [!NOTE]
> 此参数仅在 Windows 上可用。

从文件中获取指定的备用数据流。 输入流名称。 支持通配符。 若要获取所有流，请使用星号 (`*`) 。 此参数在目录中有效，但请注意，默认情况下目录不具有数据流。

此参数是在 PowerShell 3.0 中引入的。  从 PowerShell 7.2 开始， `Get-Item` 可以从目录和文件获取备用数据流。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No alternate file streams
Accept pipeline input: False
Accept wildcard characters: True
```

### -Credential

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

指定为字符串数组，此 cmdlet 在操作中排除的项。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如 `*.txt`。 允许使用通配符。 仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。

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

指定用于限定 **路径** 参数的筛选器。 [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一安装的支持筛选器的 PowerShell 提供程序。 筛选器比其他参数更有效。 当 cmdlet 获取对象时，提供程序将应用筛选器，而不是在检索对象后再对其进行筛选。 筛选器字符串将传递给 .NET API 以枚举文件。 API 仅支持 `*` 和 `?` 通配符。

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

指示此 cmdlet 将获取不能访问的项，如隐藏项。
不同提供程序有不同的实现。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。 即使使用 **Force** 参数，该 cmdlet 也无法覆盖安全限制。

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

指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如 `*.txt`。 允许使用通配符。 仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。

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

指定一个或多个位置的路径。 **LiteralPath** 的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

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

指定项的路径。 此 cmdlet 获取位于指定位置的项。 允许使用通配符。 此参数是必需的，但参数名称 **路径** 是可选的。

使用点)  (`.` 指定当前位置。 使用通配符 (`*`) 来指定当前位置中的所有项。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将包含路径的字符串传递给此 cmdlet。

## 输出

### System.Object

此 cmdlet 将返回它所获取的对象。 类型由路径中的对象的类型确定。

## 注释

此 cmdlet 不具有 **递归** 参数，因为它只获取项，而不获取其内容。
若要以递归方式获取项的内容，请使用 `Get-ChildItem` 。

若要在注册表中导航，请使用此 cmdlet 获取注册表项，并使用 `Get-ItemProperty` 来获取注册表值和数据。 注册表值被视为注册表项的属性。

此 cmdlet 用于处理由任何提供程序公开的数据。 若要列出会话中可用的提供程序，请键入 `Get-PsProvider`。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相关链接

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Get-PSProvider](Get-PSProvider.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

