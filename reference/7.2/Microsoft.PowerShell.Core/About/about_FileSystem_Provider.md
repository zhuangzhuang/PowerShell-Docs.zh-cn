---
description: FileSystem
Locale: en-US
ms.date: 11/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_filesystem_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: FileSystem 提供程序
ms.openlocfilehash: cfe074475cc1304243dfd4b2245e4eec44c25244
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597455"
---
# <a name="filesystem-provider"></a>FileSystem 提供程序

## <a name="provider-name"></a>提供程序名称

FileSystem

## <a name="drives"></a>驱动器

`C:`, `D:` ...

## <a name="capabilities"></a>功能

**Filter**、 **ShouldProcess**

## <a name="short-description"></a>简短说明

提供对文件和目录的访问权限。

## <a name="detailed-description"></a>详细说明

PowerShell **FileSystem** 提供程序可让你获取、添加、更改、清除和删除 PowerShell 中的文件和目录。

**文件系统** 驱动器是包含计算机上的目录和文件的分层命名空间。 **FileSystem** 驱动器可以是逻辑或物理驱动器、目录或映射的网络共享。

名为的驱动器 `TEMP:` 将映射到用户的临时目录路径。

>[!NOTE]
> TEMP：驱动器中的内容不会由 PowerShell 自动删除，并且由用户或操作系统进行管理。 此功能已从 PowerShell 版本7.0 中的实验功能中移出

**FileSystem** 提供程序支持以下 cmdlet，本文将对此进行介绍。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Get-Acl](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-Acl](xref:Microsoft.PowerShell.Security.Set-Acl)
- [Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a>此提供程序公开的类型

文件是 [FileInfo](/dotnet/api/system.io.fileinfo) 类的实例。 目录是 [DirectoryInfo](/dotnet/api/system.io.directoryinfo) 类的实例。

## <a name="navigating-the-filesystem-drives"></a>导航 FileSystem 驱动器

**FileSystem** 提供程序通过将计算机上的所有逻辑驱动器映射为 PowerShell 驱动器来公开其数据存储。 若要使用 **FileSystem** 驱动器，可使用驱动器名称后跟冒号 () ，将位置更改为驱动器 `:` 。

```powershell
Set-Location C:
```

你还可以从任何其他 PowerShell 驱动器使用 **FileSystem** 提供程序。 若要从其他位置引用文件或目录，请 `C:` 在路径中使用驱动器名称 (， `D:` ) 。

> [!NOTE]
> PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。 命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [设置位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名。 和 `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。

## <a name="getting-files-and-directories"></a>获取文件和目录

`Get-ChildItem`Cmdlet 将返回当前位置中的所有文件和目录。 您可以指定不同的路径进行搜索，并使用内置参数来筛选和控制递归深度。

```powershell
Get-ChildItem
```

若要详细了解 cmdlet 的用法，请参阅 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)。

## <a name="copying-files-and-directories"></a>复制文件和目录

`Copy-Item`Cmdlet 将文件和目录复制到指定的位置。
参数可用于筛选和递归，类似于 `Get-ChildItem` 。

以下命令将 "C：\temp" 路径下的所有文件和目录复制 \" 到文件夹 "C:\Windows\Temp"。

```powershell
Copy-Item -Path C:\temp\* -Destination C:\Windows\Temp -Recurse -File
```

`Copy-Item` 覆盖目标目录中的文件，而不提示确认。

此命令将 `a.txt` 目录中的文件复制 `C:\a` 到 `C:\a\bb` 目录。

```powershell
Copy-Item -Path C:\a\a.txt -Destination C:\a\bb\a.txt
```

将目录中的所有目录和文件复制 `C:\a` 到 `C:\c` 目录。 如果要复制的所有目录已存在于目标目录中，则除非指定 Force 参数，否则此命令将会失败。

```powershell
Copy-Item -Path C:\a\* -Destination C:\c -Recurse
```

有关详细信息，请参阅 [复制项](xref:Microsoft.PowerShell.Management.Copy-Item)。

## <a name="moving-files-and-directories"></a>移动文件和目录

此命令将 `c.txt` 目录中的文件移动 `C:\a` 到 `C:\a\aa` 目录：

```powershell
Move-Item -Path C:\a\c.txt -Destination C:\a\aa
```

该命令将不会自动覆盖现有的同名文件。 若要强制该 cmdlet 覆盖现有文件，请指定 Force 参数。

无法移动当前所在的目录。 当你使用在 `Move-Item` 当前位置移动目录时，你会看到此错误。

```
C:\temp> Move-Item -Path C:\temp\ -Destination C:\Windows\Temp

Move-Item : Cannot move item because the item at 'C:\temp\' is in use.
At line:1 char:1
+ Move-Item C:\temp\ C:\temp2\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Move-Item], PSInvalidOperationException
    + FullyQualifiedErrorId : InvalidOperation,Microsoft.PowerShell.Commands.MoveItemCommand
```

## <a name="managing-file-content"></a>管理文件内容

### <a name="get-the-content-of-a-file"></a>获取文件内容

此命令将获取 "Test.txt" 文件的内容，并将其显示在控制台中。

```powershell
Get-Content -Path Test.txt
```

你可以通过管道将文件内容传递给其他 cmdlet。 例如，下面的命令读取文件的内容 `Test.txt` ，然后将其作为输入提供给 [convertto-html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdlet：

```powershell
Get-Content -Path Test.txt | ConvertTo-Html
```

还可以通过在其提供程序路径前面加上美元符号 () 来检索文件的内容 `$` 。 由于变量命名限制，路径必须括在大括号中。 有关详细信息，请参阅 [about_Variables](about_Variables.md)。

```powershell
${C:\Windows\System32\Drivers\etc\hosts}
```

### <a name="add-content-to-a-file"></a>向文件添加内容

此命令将 "test content" 字符串追加到 `Test.txt` 文件中：

```powershell
Add-Content -Path test.txt -Value "test content"
```

`Test.txt`不会删除文件中的现有内容。

### <a name="replace-the-content-of-a-file"></a>替换文件的内容

此命令将文件的内容替换 `Test.txt` 为 "测试内容" 字符串：

```powershell
Set-Content -Path test.txt -Value "test content"
```

它将覆盖的内容 `Test.txt` 。 在创建文件时，可以使用 [新项](xref:Microsoft.PowerShell.Management.New-Item)Cmdlet 的 **Value** 参数将内容添加到文件。

### <a name="loop-through-the-contents-of-a-file"></a>遍历文件的内容

默认情况下，该 `Get-Content` cmdlet 使用行尾字符作为分隔符，因此它将以字符串集合的形式获取文件，每行都作为文件中的一个字符串。

可以使用 `-Delimiter` 参数来指定备用分隔符。 如果将该分隔符设置为表示一个部分的结尾或下一部分开头的字符，则可以将该文件拆分为多个逻辑部分。

第一个命令获取 `Employees.txt` 文件并将其拆分为多个部分，其中每个部分均以单词 "End Of Employee Record" 结尾，并将其保存在 `$e` 变量中。

第二个命令使用数组表示法来获取中的集合中的第一项 `$e` 。 它使用的索引为0，因为 PowerShell 数组是从零开始的。

有关 cmdlet 的详细信息 `Get-Content` ，请参阅 [获取内容](xref:Microsoft.PowerShell.Management.Get-Content)的帮助主题。

有关数组的详细信息，请参阅 [about_Arrays](../About/about_Arrays.md)。

```powershell
$e = Get-Content c:\test\employees.txt -Delimited "End Of Employee Record"
$e[0]
```

## <a name="managing-security-descriptors"></a>管理安全描述符

### <a name="view-the-acl-for-a-file"></a>查看文件的 ACL

此命令返回 [accesscontrol-namespace. FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) 对象：

```powershell
Get-Acl -Path test.txt | Format-List -Property *
```

有关此对象的详细信息，请通过管道将命令传递给 [Get Member](xref:Microsoft.PowerShell.Utility.Get-Member) cmdlet。 或者，请参阅 [FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) 类。

### <a name="modify-the-acl-for-a-file"></a>修改文件的 ACL

### <a name="create-and-set-an-acl-for-a-file"></a>创建和设置文件的 ACL

## <a name="creating-files-and-directories"></a>创建文件和目录

### <a name="create-a-directory"></a>创建目录

此命令 `logfiles` 在驱动器上创建目录 `C` ：

```powershell
New-Item -Path c:\ -Name logfiles -Type directory
```

PowerShell 还包括一个 `mkdir` 函数 (别名 `md`) ，该函数使用 [新项](xref:Microsoft.PowerShell.Management.New-Item) cmdlet 来创建新的目录。

### <a name="create-a-file"></a>创建文件

此命令 `log2.txt` 在目录中创建文件 `C:\logfiles` ，然后将 "test log" 字符串添加到该文件中：

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file
```

### <a name="create-a-file-with-content"></a>创建具有内容的文件

在目录中创建一个名为的文件 `log2.txt` `C:\logfiles` ，并将字符串 "test log" 添加到该文件。

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file -Value "test log"
```

## <a name="renaming-files-and-directories"></a>重命名文件和目录

### <a name="rename-a-file"></a>重命名文件

此命令将 `a.txt` 目录中的文件重命名 `C:\a` 为 `b.txt` ：

```powershell
Rename-Item -Path c:\a\a.txt -NewName b.txt
```

### <a name="rename-a-directory"></a>重命名目录

此命令将目录重命名 `C:\a\cc` 为 `C:\a\dd` ：

```powershell
Rename-Item -Path c:\a\cc -NewName dd
```

## <a name="deleting-files-and-directories"></a>删除文件和目录

### <a name="delete-a-file"></a>删除文件

此命令删除 `Test.txt` 当前目录中的文件：

```powershell
Remove-Item -Path test.txt
```

### <a name="delete-files-using-wildcards"></a>使用通配符删除文件

此命令删除当前目录中文件扩展名为的所有文件 `.xml` ：

```powershell
Remove-Item -Path *.xml
```

## <a name="starting-a-program-by-invoking-an-associated-file"></a>通过调用关联文件启动程序

### <a name="invoke-a-file"></a>调用文件

第一个命令使用 [get-help](xref:Microsoft.PowerShell.Management.Get-Service) cmdlet 来获取有关本地服务的信息。

它通过管道将信息传递给 [导出 Csv](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdlet，然后将该信息存储在 `Services.csv` 文件中。

第二个命令使用 [调用项](xref:Microsoft.PowerShell.Management.Invoke-Item) `services.csv` 在与扩展关联的程序中打开文件 `.csv` ：

```powershell
Get-Service | Export-Csv -Path services.csv
Invoke-Item -Path services.csv
```

## <a name="getting-files-and-folders-with-specified-attributes"></a>获取具有指定属性的文件和文件夹

### <a name="get-system-files"></a>获取系统文件

此命令将获取当前目录及其子目录中的系统文件。

它使用 `-File` 参数仅获取 (不是目录) 的文件，并使用 `-System` 参数仅获取具有 "system" 属性的项。

它使用 `-Recurse` 参数获取当前目录和所有子目录中的项。

```powershell
Get-ChildItem -File -System -Recurse
```

### <a name="get-hidden-files"></a>获取隐藏文件

此命令将获取当前目录中的所有文件，其中包括隐藏文件。

它使用具有两个值的 **属性** 参数， `!Directory+Hidden` 这些值可获取隐藏的文件，并 `!Directory` 可获取所有其他文件。

```powershell
Get-ChildItem -Attributes !Directory,!Directory+Hidden
```

`dir -att !d,!d+h` 等效于此命令。

### <a name="get-compressed-and-encrypted-files"></a>获取压缩和加密的文件

此命令将获取当前目录中已压缩或加密的文件。

它使用 `-Attributes` 具有两个值的参数 `Compressed` 和 `Encrypted` 。 值用逗号分隔， `,` 表示 "OR" 运算符。

```powershell
Get-ChildItem -Attributes Compressed,Encrypted
```

## <a name="dynamic-parameters"></a>动态参数

动态参数是 PowerShell 提供程序添加的 cmdlet 参数，只有在启用了提供程序的驱动器中使用 cmdlet 时，这些参数才可用。

### <a name="encoding-microsoftpowershellcommandsfilesystemcmdletproviderencoding"></a>Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\>

指定文件编码。 默认值为 ASCII。

- **Ascii**：使用 ascii (7 位) 字符集的编码。
- **BigEndianUnicode**：使用大字节序字节顺序对 utf-16 格式进行编码。
- **String**：对字符串使用编码类型。
- **Unicode**：使用小 endian 字节顺序对 utf-16 格式进行编码。
- **UTF7**：用 Utf-7 格式编码。
- **UTF8**：以 utf-8 格式进行编码。
- **UTF8BOM**：采用 Utf-8 格式编码 (BOM) 
- **UF8NOBOM**：用无字节顺序标记的 Utf-8 格式编码 (BOM) 
- **UTF32**：以32格式编码。
- **默认**：在默认的安装代码页中进行编码。
- **OEM**：对 MS-DOS 和控制台程序使用默认编码。
- **未知**：编码类型未知或无效。 数据可作为二进制处理。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Add-Content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="delimiter-systemstring"></a>Delimiter \<System.String\>

指定 [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) 用于在读取文件时将该文件划分为对象的分隔符。

默认值为 `\n` 行尾字符。

读取文本文件时， [获取内容](xref:Microsoft.PowerShell.Management.Get-Content) 将返回 string 对象的集合，其中每个对象都以分隔符字符结尾。

输入文件中不存在的分隔符， [获取内容](xref:Microsoft.PowerShell.Management.Get-Content) 将整个文件作为单个未分隔的对象返回。

你可以使用此参数将大文件拆分为较小的文件，方法是指定文件分隔符（例如“End of Example”）作为分隔符。 分隔符将被保留（不会被丢弃），并且成为每个文件部分中的最后一项。

> [!NOTE]
> 目前，当参数的值 `-Delimiter` 为空字符串时， [get-help](xref:Microsoft.PowerShell.Management.Get-Content) 不会返回任何内容。
> 这是一个已知问题。 若要强制执行 [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) 以将整个文件作为单个的未分隔字符串返回，请输入文件中不存在的值。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="wait-systemmanagementautomationswitchparameter"></a>Wait \<System.Management.Automation.SwitchParameter\>

等待要追加到文件的内容。 如果已追加内容，则返回追加的内容。 如果已更改内容，则返回整个文件。

在等待过程中，[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) 将每秒检查一次文件，直到你中断该操作（例如通过按 CTRL+C）。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="attributes-flagsexpression"></a>Attributes \<FlagsExpression\>

获取具有指定属性的文件和文件夹。 此参数支持所有属性，并且允许你指定复杂的属性组合。

此 `-Attributes` 参数是在 Windows PowerShell 3.0 中引入的。

`-Attributes`参数支持以下属性：

- **存档**
- **Compressed**
- **设备**
- **Directory**
- **已加密**
- **Hidden**
- **正常**
- **NotContentIndexed**
- **断开**
- **ReadOnly**
- **ReparsePoint**
- **SparseFile**
- **系统**
- **临时**

有关这些属性的说明，请参阅 [FileAttributes](/dotnet/api/system.io.fileattributes) 枚举。

使用以下运算符合并属性。

- `!` -NOT
- `+` -和
- `,` -或

运算符与其属性之间不允许有空格。 但是，在逗号之前允许有空格。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="directory-systemmanagementautomationswitchparameter"></a>Directory \<System.Management.Automation.SwitchParameter\>

获取目录（文件夹）。

此 `-Directory` 参数是在 Windows PowerShell 3.0 中引入的。

若要仅获取目录，请使用 `-Directory` 参数并省略 `-File` 参数。 若要排除目录，请使用 `-File` 参数并省略 `-Directory` 参数，或使用 `-Attributes` 参数。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="file-systemmanagementautomationswitchparameter"></a>File \<System.Management.Automation.SwitchParameter\>

获取文件。

此 `-File` 参数是在 Windows PowerShell 3.0 中引入的。

若要仅获取文件，请使用 `-File` 参数并省略 `-Directory` 参数。 若要排除文件，请使用 `-Directory` 参数并省略 `-File` 参数，或使用 `-Attributes` 参数。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="hidden-systemmanagementautomationswitchparameter"></a>Hidden \<System.Management.Automation.SwitchParameter\>

仅获取隐藏的文件和目录（文件夹）。 默认情况下， [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) 仅获取非隐藏项。

此 `-Hidden` 参数是在 Windows PowerShell 3.0 中引入的。

若要仅获取隐藏项，请使用 `-Hidden` 参数、其 `h` 或 `ah` 别名或参数的 **隐藏** 值 `-Attributes` 。 若要排除隐藏项，请省略 `-Hidden` 参数或使用 `-Attributes` 参数。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="readonly-systemmanagementautomationswitchparameter"></a>ReadOnly \<System.Management.Automation.SwitchParameter\>

仅获取只读文件和目录（文件夹）。

此 `-ReadOnly` 参数是在 Windows PowerShell 3.0 中引入的。

若要仅获取只读项，请使用 `-ReadOnly` 参数、其 `ar` 别名或参数的 **ReadOnly** 值 `-Attributes` 。 若要排除只读项，请使用 `-Attributes` 参数。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="system-systemmanagementautomationswitchparameter"></a>System \<System.Management.Automation.SwitchParameter\>

仅获取系统文件和目录（文件夹）。

此 `-System` 参数是在 Windows PowerShell 3.0 中引入的。

若要仅获取系统文件和文件夹，请使用参数 `-System` 、其 `as` 别名或参数的 **系统** 值 `-Attributes` 。 若要排除系统文件和文件夹，请使用 `-Attributes` 参数。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="newerthan-systemdatetime"></a>NewerThan \<System.DateTime\>

`$True`当文件的 `LastWriteTime` 值大于指定的日期时返回。 否则，它将返回 `$False`。

输入日期 [时间](/dotnet/api/system.datetime) 对象（例如 [获取 Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet 返回的对象），或者输入一个可转换为 [DateTime](/dotnet/api/system.datetime) 对象的字符串（例如） `"August 10, 2011 2:00 PM"` 。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Test-Path](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="olderthan-systemdatetime"></a>OlderThan \<System.DateTime\>

`$True`当文件的 `LastWriteTime` 值小于指定日期时返回。 否则，它将返回 `$False`。

输入日期 [时间](/dotnet/api/system.datetime) 对象（例如 [获取 Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet 返回的对象），或者输入一个可转换为 [DateTime](/dotnet/api/system.datetime) 对象的字符串（例如） `"August 10, 2011 2:00 PM"` 。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Test-Path](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="stream-systemstring"></a>Stream \<System.String\>

管理备用数据流。 输入流名称。 仅允许在文件系统驱动器中 [获取项](xref:Microsoft.PowerShell.Management.Get-Item) 和 [删除项](xref:Microsoft.PowerShell.Management.Remove-Item) 命令的通配符。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Add-Content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Clear-Content](xref:Microsoft.PowerShell.Management.Clear-Content)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="raw-switchparameter"></a>Raw \<SwitchParameter\>

忽略换行符。 返回作为单个项的内容。

#### <a name="cmdlets-supported"></a>支持的 cmdlet

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="itemtype-string"></a>ItemType \<String\>

此参数允许你指定要创建的项目的 tye `New-Item`

此参数的可用值取决于当前使用的提供程序。

在 `FileSystem` 驱动器中，允许使用以下值：

- 文件
- Directory
- SymbolicLink
- 交接点
- 硬

### <a name="cmdlets-supported"></a>支持的 cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a>使用管道

提供程序 cmdlet 接受管道输入。 可以通过将提供程序数据从一个 cmdlet 发送到另一个提供程序 cmdlet 来使用管道来简化任务。
若要详细了解如何将管道与提供程序 cmdlet 配合使用，请参阅本文中提供的 cmdlet 参考。

## <a name="getting-help"></a>获取帮助

从 Windows PowerShell 3.0 开始，你可以获取有关提供程序 cmdlet 的自定义帮助主题，它们介绍了这些 cmdlet 在文件系统驱动器中的行为方式。

若要获取针对文件系统驱动器进行自定义的帮助主题，请在文件系统驱动器中运行[get-help](xref:Microsoft.PowerShell.Core.Get-Help)命令，或使用 get-help 的 `-Path` 参数来[](xref:Microsoft.PowerShell.Core.Get-Help)指定文件系统驱动器。

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path c:
```

## <a name="see-also"></a>请参阅

[about_Providers](../About/about_Providers.md)
