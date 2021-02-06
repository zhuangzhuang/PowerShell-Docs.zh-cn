---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ChildItem
ms.openlocfilehash: dc47a7bc29d93e1784571f9e6b27dafcb8494bae
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596028"
---
# Get-ChildItem

## 摘要

获取一个或多个指定位置中的项和子项。

## SYNTAX

### Items（默认值）

```
Get-ChildItem [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>]
 [-Recurse] [-Depth <uint32>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>]
 [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### LiteralItems

```
Get-ChildItem [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>]
 [-Exclude <string[]>] [-Recurse] [-Depth <uint32>] [-Force] [-Name]
 [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden]
 [-ReadOnly] [-System] [<CommonParameters>]
```

## DESCRIPTION

`Get-ChildItem`Cmdlet 获取一个或多个指定位置中的项。 如果该项为容器，则此命令将获取容器内的各项（称为子项）。 可以使用 **递归** 参数获取所有子容器中的项，并使用 **Depth** 参数来限制要递归的级别数。

`Get-ChildItem` 不显示空目录。 当 `Get-ChildItem` 命令包含 **深度** 或 **递归** 参数时，输出中不包括空目录。

位置 `Get-ChildItem` 由 PowerShell 提供程序向公开。 位置可以是文件系统目录、注册表配置单元或证书存储区。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 示例

### 示例1：从文件系统目录获取子项目

此示例从文件系统目录中获取子项目。 将显示文件名和子目录的名称。 对于空位置，该命令不会返回任何输出，并返回到 PowerShell 提示符。

`Get-ChildItem`Cmdlet 使用 **Path** 参数来指定目录 `C:\Test` 。
`Get-ChildItem` 显示 PowerShell 控制台中的文件和目录。

```powershell
Get-ChildItem -Path C:\Test
```

```Output
   Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     08:29                Logs
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

默认情况 `Get-ChildItem` 下，会列出模式 (**特性**) 、 **LastWriteTime**、文件大小 (**长度**) 和项的 **名称** 。 **Mode** 属性中的字母可解释如下：

- `l` (链接) 
- `d` (目录) 
- `a` (存档) 
- `r` (只读) 
- `h` (隐藏) 
- `s` (系统) 。

有关模式标志的详细信息，请参阅 [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression)。

### 示例2：获取目录中的子项目名称

此示例仅列出目录中项的名称。

`Get-ChildItem`Cmdlet 使用 **Path** 参数来指定目录 `C:\Test` 。 **Name** 参数仅返回指定路径中的文件名或目录名。

```powershell
Get-ChildItem -Path C:\Test -Name
```

```Output
Logs
anotherfile.txt
Command.txt
CreateTestFile.ps1
ReadOnlyFile.txt
```

### 示例3：获取当前目录和子目录中的子项

此示例显示位于当前目录及其子目录中的 **.txt** 文件。

```powershell
Get-ChildItem -Path C:\Test\*.txt -Recurse -Force
```

```Output
    Directory: C:\Test\Logs\Adirectory

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile4.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile4.txt

    Directory: C:\Test\Logs\Backup

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 ATextFile.txt
-a----        2/12/2019     15:50             20 LogFile3.txt

    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

`Get-ChildItem`Cmdlet 使用 **Path** 参数指定 `C:\Test\*.txt` 。 **Path** 使用 `*`) 通配符 (星号来指定具有文件扩展名的所有文件 `.txt` 。 **递归** 参数会搜索 **Path** 目录的子目录，如 **目录：** 标题中所示。 **Force** 参数显示其模式为 h 的隐藏文件 `hiddenfile.txt` 。 

### 示例4：使用 Include 参数获取子项目

在此示例中， `Get-ChildItem` 使用 **Include** 参数查找 **Path** 参数所指定的目录中的特定项。

```powershell
# When using the -Include parameter, if you don't include an asterisk in the path
# the command returns no output.
Get-ChildItem -Path C:\Test\ -Include *.txt
```

```Output

```

```powershell
Get-ChildItem -Path C:\Test\* -Include *.txt
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

`Get-ChildItem`Cmdlet 使用 **Path** 参数指定目录 **C:\Test**。 **Path** 参数包含一个尾部星号 (`*`) 通配符，以指定目录的内容。
**Include** 参数使用星号 (`*`) 通配符来指定文件扩展名为 **.txt** 的所有文件。

当使用 **Include** 参数时， **Path** 参数需要一个尾部星号 (`*`) 通配符，以指定目录的内容。 例如，`-Path C:\Test\*`。

- 如果将 **递归** 参数添加到命令中，则 `*` **Path** 参数中) 的尾随星号 (是可选的。 **递归** 参数从 **路径** 目录及其子目录中获取项。 例如，`-Path C:\Test\ -Recurse -Include *.txt`
- 如果 `*` **Path** 参数中未包含尾随星号 () ，则该命令不会返回任何输出并返回到 PowerShell 提示符。 例如，`-Path C:\Test\`。

### 示例5：使用 Exclude 参数获取子项目

该示例的输出显示目录 **C:\Test\Logs** 的内容。 输出是对使用 **Exclude** 和 **递归** 参数的其他命令的引用。

```powershell
Get-ChildItem -Path C:\Test\Logs
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Adirectory
d-----        2/15/2019     08:28                AnEmptyDirectory
d-----        2/15/2019     13:21                Backup
-a----        2/12/2019     16:16             20 Afile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

```powershell
Get-ChildItem -Path C:\Test\Logs\* -Exclude A*
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Backup
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

`Get-ChildItem`Cmdlet 使用 **Path** 参数来指定目录 `C:\Test\Logs` 。
**Exclude** 参数使用星号 (`*`) 通配符来指定以或开头的任何文件或目录， 从输出中排除。

使用 **Exclude** 参数时， `*` **Path** 参数中)  (后缀星号是可选的。 例如，`-Path C:\Test\Logs` 或 `-Path C:\Test\Logs\*`。

- 如果 `*` **path** 参数中未包含尾随星号 () ，则显示 **path** 参数的内容。 例外情况是与 **Exclude** 参数的值匹配的文件名或子目录名称。
- 如果 `*` **path** 参数中包含尾随星号 () ，则命令 recurses 到 **path** 参数的子目录中。 例外情况是与 **Exclude** 参数的值匹配的文件名或子目录名称。
- 如果将 **递归** 参数添加到命令中，则无论 **Path** 参数是否包含尾随星号 () ，递归输出都是相同的 `*` 。

### 示例6：从注册表配置单元获取注册表项

此示例从获取中的所有注册表项 `HKEY_LOCAL_MACHINE\HARDWARE` 。

`Get-ChildItem` 使用 **Path** 参数指定注册表项 `HKLM:\HARDWARE` 。 配置单元的路径和顶级注册表项显示在 PowerShell 控制台中。

有关详细信息，请参阅 [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)。

```powershell
Get-ChildItem -Path HKLM:\HARDWARE
```

```Output
    Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name             Property
----             --------
ACPI
DESCRIPTION
DEVICEMAP
RESOURCEMAP
UEFI
```

```powershell
Get-ChildItem -Path HKLM:\HARDWARE -Exclude D*
```

```Output
   Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name                           Property
----                           --------
ACPI
RESOURCEMAP
```

第一个命令显示注册表项的内容 `HKLM:\HARDWARE` 。 **Exclude** 参数指示 `Get-ChildItem` 不返回以开头的任何子项 `D*` 。 目前， **Exclude** 参数仅适用于子项，而不是项属性。

### 示例7：获取具有代码签名颁发机构的所有证书

此示例获取 PowerShell **Cert：** 驱动器中具有代码签名颁发机构的每个证书。

`Get-ChildItem`Cmdlet 使用 **Path** 参数指定 **Cert：** provider。 **递归** 参数搜索 **路径** 及其子目录指定的目录。 **CodeSigningCert** 参数仅获取具有代码签名颁发机构的证书。

```powershell
Get-ChildItem -Path Cert:\* -Recurse -CodeSigningCert
```

有关证书提供程序和 Cert：驱动器的详细信息，请参阅 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)。

### 示例8：使用 Depth 参数获取项

此示例显示目录及其子目录中的项。 **Depth** 参数确定要包括在递归中的子目录级别数。 空目录将从输出中排除。

```powershell
Get-ChildItem -Path C:\Parent -Depth 2
```

```Output
    Directory: C:\Parent

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level1
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level2
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1\SubDir_Level2

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:22                SubDir_Level3
-a----        2/13/2019     08:55             26 file.txt
```

`Get-ChildItem`Cmdlet 使用 **Path** 参数指定 **C:\Parent**。 **Depth** 参数指定两个递归级别。 `Get-ChildItem` 显示 **Path** 参数所指定的目录的内容和两个子目录级别。

### 示例9：获取硬链接信息

在 PowerShell 6.2 中，添加了一个替代视图来获取硬链接信息。

```powershell
Get-ChildItem -Path C:\PathContainingHardLink | Format-Table -View childrenWithHardLink
```

### 示例9：非 Windows 操作系统的输出

在 Unix 系统上的 PowerShell 7.1 中， `Get-ChildItem` 提供类似于 unix 的输出：

```powershell
PS> Get-ChildItem /etc/r*
```

```Output
    Directory: /etc

UnixMode   User Group    LastWriteTime Size Name
--------   ---- -----    ------------- ---- ----
drwxr-xr-x root wheel  9/30/2019 19:19  128 racoon
-rw-r--r-- root wheel  9/26/2019 18:20 1560 rc.common
-rw-r--r-- root wheel  7/31/2017 17:30 1560 rc.common~previous
-rw-r--r-- root wheel  9/27/2019 20:34 5264 rc.netboot
lrwxr-xr-x root wheel  11/8/2019 15:35   22 resolv.conf -> /private/var/run/resolv.conf
-rw-r--r-- root wheel 10/23/2019 17:41    0 rmtab
-rw-r--r-- root wheel 10/23/2019 17:41 1735 rpc
-rw-r--r-- root wheel  7/25/2017 18:37 1735 rpc~previous
-rw-r--r-- root wheel 10/23/2019 18:42  891 rtadvd.conf
-rw-r--r-- root wheel  8/24/2017 21:54  891 rtadvd.conf~previous
```

现在作为输出的一部分的新属性包括：

- **UnixMode** 是 Unix 系统上表示的文件权限
- **用户** 是文件所有者
- **组** 是组的所有者
- **Size** 是在 Unix 系统上表示的文件或目录的大小

> [!NOTE]
> 此功能已从实验迁移到 PowerShell 7.1 中的主流。

## 参数

### -Attributes

获取具有指定属性的文件和文件夹。 此参数支持所有属性，并且允许你指定复杂的属性组合。

例如，若要获取加密或压缩的非系统文件（而不是目录），请键入：

`Get-ChildItem -Attributes !Directory+!System+Encrypted, !Directory+!System+Compressed`

若要查找具有常用属性的文件和文件夹，请使用 **attributes** 参数。 或参数 **目录**、 **文件**、 **隐藏**、 **只读** 和 **系统**。

Properties **参数支持** 以下属性：

- **存档**
- **Compressed**
- **设备**
- **Directory**
- **已加密**
- **Hidden**
- **IntegrityStream**
- **正常**
- **NoScrubData**
- **NotContentIndexed**
- **断开**
- **ReadOnly**
- **ReparsePoint**
- **SparseFile**
- **系统**
- **临时**

有关这些属性的说明，请参阅 [FileAttributes 枚举](/dotnet/api/system.io.fileattributes)。

若要合并属性，请使用以下运算符：

- `!` (未) 
- `+` (和) 
- `,` (或) 

运算符与其属性之间不要使用空格。 逗号后接受空格。

对于常用属性，请使用以下缩写：

- `D` (目录) 
- `H` (隐藏) 
- `R` (只读) 
- `S` (系统) 

```yaml
Type: System.Management.Automation.FlagsExpression`1[System.IO.FileAttributes]
Parameter Sets: (All)
Aliases:
Accepted values: Archive, Compressed, Device, Directory, Encrypted, Hidden, IntegrityStream, Normal, NoScrubData, NotContentIndexed, Offline, ReadOnly, ReparsePoint, SparseFile, System, Temporary

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Depth

此参数是在 PowerShell 5.0 中添加的，使你可以控制递归的深度。 默认情况下， `Get-ChildItem` 显示父目录的内容。 **深度** 参数确定递归中包含的子目录级别数，并显示内容。

例如， `Depth 2` 包括 **Path** 参数的目录、第一级子目录和二级子目录。 默认情况下，输出中包含目录名称和文件名。

> [!NOTE]
> 在从 PowerShell 或 **cmd.exe** 的 Windows 计算机上，可以使用 **tree.com** 命令显示目录结构的图形视图。

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Directory

若要获取目录列表，请使用 **directory** 参数或具有 **Directory** 属性的 **Attributes** 参数。 可以将 **递归** 参数与 **Directory** 一起使用。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ad, d

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exclude

指定为字符串数组，此 cmdlet 从操作中排除的属性或属性。
此参数值使 **Path** 参数有效。 输入路径元素或模式，例如 `*.txt` 或 `A*` 。 可接受通配符。

`*` **Path** 参数中)  (后缀星号是可选的。 例如，`-Path C:\Test\Logs` 或 `-Path C:\Test\Logs\*`。 如果包含尾随星号 (`*`) ，则命令 recurses 到 **Path** 参数的子目录中。 如果没有星号 (`*`) ，则显示 **Path** 参数的内容。 示例5和备注部分中提供了更多详细信息。

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

### -File

若要获取文件列表，请使用 **File** 参数。 可以将 **递归** 参数用于 **File**。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: af

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

指定用于限定 **路径** 参数的筛选器。 [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一安装的支持筛选器的 PowerShell 提供程序。 筛选器比其他参数更有效。 当 cmdlet 获取对象时，提供程序将应用筛选器，而不是在检索对象后再对其进行筛选。 筛选器字符串将传递给 .NET API 以枚举文件。 API 仅支持 `*` 和 `?` 通配符。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -FollowSymlink

默认情况下，该 `Get-ChildItem` cmdlet 显示在递归期间找到的目录的符号链接，但不会对其进行递归。 使用 **FollowSymlink** 参数可搜索以这些符号链接为目标的目录。 **FollowSymlink** 是动态参数，仅 **FileSystem** 提供程序支持。

此参数是在 PowerShell 6.0 中引入的。

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

允许 cmdlet 获取用户不能访问的项，如隐藏文件或系统文件。 **Force** 参数不会覆盖安全限制。 实现提供程序之间的差异。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

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

### -Hidden

若要仅获取隐藏项，请使用 **hidden 参数或** 具有 **Hidden** 属性的 **Attributes** 参数。 默认情况下， `Get-ChildItem` 不会显示隐藏项。 使用 **Force** 参数可获取隐藏项。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ah, h

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Include

指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如 `"*.txt"`。 允许使用通配符。 仅当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。

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
Parameter Sets: LiteralItems
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

仅获取位置中的项的名称。 输出是一个字符串对象，可将其向下发送到其他命令。 允许使用通配符。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

指定一个或多个位置的路径。 可以使用通配符。 默认位置为当前目录 (`.`) 。

```yaml
Type: System.String[]
Parameter Sets: Items
Aliases:

Required: False
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -ReadOnly

若要仅获取只读项，请使用 **readonly** 参数或 **Attributes** 参数 **readonly** 属性。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ar

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Recurse

获取指定位置及其所有子项中的项。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: s

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -System

仅获取系统文件和目录。 若要仅获取系统文件和文件夹，请使用 **system** 参数或 **Attributes** 参数 **系统** 属性。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: as

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String

可以通过管道将包含路径的字符串传递给 `Get-ChildItem` 。

## 输出

### System.Object

返回的对象类型由 `Get-ChildItem` 提供程序驱动器路径中的对象确定。

### System.String

如果使用 **Name** 参数，则 `Get-ChildItem` 以字符串形式返回对象名称。

## 注释

- `Get-ChildItem` 可以使用任何内置的别名、、和来运行 `ls` `dir` `gci` 。 有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。
- `Get-ChildItem` 默认情况下不会获取隐藏项。 若要获取隐藏项，请使用 **Force** 参数。
- `Get-ChildItem`Cmdlet 设计用于处理由任何提供程序公开的数据。 若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。
  有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相关链接

[about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-Alias](../Microsoft.PowerShell.Utility/Get-Alias.md)

[Get-Item](Get-Item.md)

[Get-Location](Get-Location.md)

[Get-Process](Get-Process.md)

[Get-PSProvider](Get-PSProvider.md)

[Split-Path](Split-Path.md)

