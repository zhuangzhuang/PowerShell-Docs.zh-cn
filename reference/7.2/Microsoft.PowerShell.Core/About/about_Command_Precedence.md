---
description: 描述 PowerShell 如何确定要运行哪个命令。
Locale: en-US
ms.date: 02/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_precedence?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Precedence
ms.openlocfilehash: 8b8a27a47c454b59b5dd4bb2d6e8a8cc3cec78c8
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196240"
---
# <a name="about-command-precedence"></a>关于命令优先级

## <a name="short-description"></a>简短说明
描述 PowerShell 如何确定要运行哪个命令。

## <a name="long-description"></a>长说明

命令优先级说明了当会话包含多个具有相同名称的命令时，PowerShell 如何确定要运行哪个命令。 可以隐藏或替换会话中的命令，这些命令具有相同的名称。 本文介绍如何运行隐藏的命令以及如何避免命令名称冲突。

## <a name="command-precedence"></a>命令优先级

当 PowerShell 会话包含多个具有相同名称的命令时，PowerShell 会使用以下规则确定要运行的命令。

如果指定一个命令的路径，则 PowerShell 会在路径指定的位置运行该命令。

例如，以下命令在 "C： TechDocs" 目录中运行 FindDocs.ps1 脚本 \\ ：

```
C:\TechDocs\FindDocs.ps1
```

作为一项安全功能，PowerShell 不会运行本机) 命令（包括 PowerShell 脚本） (可执行文件，除非该命令位于 Path 环境变量中列出的路径中，否则， `$env:path` 除非指定了脚本文件的路径。

若要运行位于当前目录中的脚本，请指定完整路径，或键入一个 `.\` 表示当前目录的点。

例如，若要在当前目录中运行 FindDocs.ps1 文件，请键入：

```
.\FindDocs.ps1
```

### <a name="using-wildcards-in-execution"></a>在执行中使用通配符

可以在命令执行中使用通配符。 使用通配符 *也称为组合。*

PowerShell 在文本匹配之前执行具有通配符匹配项的文件。

例如，请考虑具有以下文件的目录：

```
Get-ChildItem C:\temp\test


    Directory: C:\temp\test


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        5/20/2019   2:29 PM             28 a.ps1
-a----        5/20/2019   2:29 PM             28 [a1].ps1
```

这两个脚本文件具有相同的内容： `$MyInvocation.MyCommand.Path` 。
此命令显示所调用的脚本的名称。

当你运行时 `[a1].ps1` ，将执行该文件， `a.ps1` 即使该文件 `[a1].ps1` 是文字匹配。

```powershell
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\a.ps1
```

现在，让我们删除该 `a.ps1` 文件并再次尝试运行它。

```powershell
Remove-Item C:\temp\test\a.ps1
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\[a1].ps1
```

你可以从运行此时间的输出中看到， `[a1].ps1` 因为文本匹配是该通配符模式的唯一文件匹配。

有关 PowerShell 如何使用通配符的详细信息，请参阅 [about_Wildcards](about_Wildcards.md)。

> [!NOTE]
> 若要将搜索范围限制为相对路径，必须在脚本名称前面加上 `.\` 路径。 这会将命令搜索限制为相对路径中的文件。 如果没有此前缀，其他 PowerShell 语法可能会发生冲突，并且很少保证会找到该文件。

如果未指定路径，则在为当前会话中加载的所有项运行命令时，PowerShell 将使用以下优先顺序：

  1. Alias
  2. 函数
  3. Cmdlet
  4. 外部可执行文件 (程序和非 PowerShell 脚本) 

因此，如果键入 "help"，PowerShell 将首先查找名为的别名，然后查找名为的 `help` 函数 `Help` ，最后查找名为的 cmdlet `Help` 。 它会运行它找到的第一 `help` 项。

例如，如果你的会话包含一个 cmdlet 和一个函数，并且在 `Get-Map` 你键入时， `Get-Map` PowerShell 将运行该函数。

> [!NOTE]
> 这仅适用于已加载的命令。 如果有一个 `build` 可执行文件和一个 `build` 名称为的函数的别名， `Invoke-Build` 而该模块未加载到当前会话中，则 PowerShell 将改为运行该 `build` 可执行文件。 如果在这种情况下找到外部可执行文件，则它不会自动加载模块。 仅当找不到外部可执行文件时，才会调用具有给定名称的别名、函数或 cmdlet，从而触发其模块的自动加载。

如果会话包含具有相同名称的相同类型的项，则 PowerShell 将运行较新的项。

例如，如果从模块导入另一个 `Get-Date` cmdlet，则在键入时 `Get-Date` ，PowerShell 将在本机上运行导入的版本。

## <a name="hidden-and-replaced-items"></a>隐藏和替换项

由于这些规则，项可以被具有相同名称的项替换或隐藏。

如果仍可以访问原始项，例如通过使用模块或管理单元名称来限定项名称，则项为 "隐藏" 或 "隐藏"。

例如，如果导入的函数与会话中的 cmdlet 具有相同的名称，则该 cmdlet 将隐藏 (但不替换) ，因为它是从管理单元或模块导入的。

如果您无法再访问原始项，则会 "替换" 或 "覆盖" 项。

例如，如果导入的变量与会话中的变量同名，则原始变量将被替换，并且不再可访问。
不能使用模块名称限定变量。

此外，如果在命令行中键入函数，然后导入具有相同名称的函数，则原始函数会被替换并且不再可访问。

### <a name="finding-hidden-commands"></a>查找隐藏的命令

[Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) Cmdlet 的 **all** 参数将获取具有指定名称的所有命令，即使它们已隐藏或已被替换。 从 PowerShell 3.0 开始，默认情况下， `Get-Command` 仅获取键入命令名称时运行的命令。

在下面的示例中，该会话包括一个 `Get-Date` 函数和一个 [获取日期](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet。

以下命令将获取 `Get-Date` 键入时运行的命令 `Get-Date` 。

```powershell
Get-Command Get-Date
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
```

以下命令使用 **all** 参数获取所有 `Get-Date` 命令。

```powershell
Get-Command Get-Date -All
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
Cmdlet          Get-Date                  Microsoft.PowerShell.Utility
```

### <a name="running-hidden-commands"></a>运行隐藏的命令

可以通过指定项属性来运行特定命令，将命令与其他可能具有相同名称的命令区分开来。 您可以使用此方法来运行任何命令，但它对于运行隐藏命令特别有用。

#### <a name="qualified-names"></a>限定名称

使用 cmdlet 的模块限定名称，可运行由具有相同名称的项隐藏的命令。 例如，你可以 `Get-Date` 通过使用其模块名称 " **Microsoft PowerShell**" 来对其进行限定来运行 cmdlet。

编写要分发的脚本时，请使用此首选方法。 您无法预测运行脚本的会话中可能出现哪些命令。

```powershell
New-Alias -Name "Get-Date" -Value "Get-ChildItem"
Microsoft.PowerShell.Utility\Get-Date
```

```output
Tuesday, September 4, 2018 8:17:25 AM
```

若要运行 `New-Map` 模块添加的命令 `MapFunctions` ，请使用其模块限定名称：

```powershell
MapFunctions\New-Map
```

若要查找从其导入命令的模块，请使用命令的 **ModuleName** 属性。

```
(Get-Command <command-name>).ModuleName
```

例如，若要查找 cmdlet 的源 `Get-Date` ，请键入：

```powershell
(Get-Command Get-Date).ModuleName
```

```output
Microsoft.PowerShell.Utility
```

> [!NOTE]
> 不能限定变量或别名。

#### <a name="call-operator"></a>Call 运算符

你还可以使用 `Call` 运算符 `&` 来运行隐藏的命令，方法是将其与 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) (别名为 "Dir" ) `Get-Command` 或 [get-help](xref:Microsoft.PowerShell.Core.Get-Module)。

调用运算符在子范围内执行字符串和脚本块。 有关详细信息，请参阅 [about_Operators](about_Operators.md)。

例如，如果你有一个名为的函数， `Map` 该函数被名为的别名隐藏 `Map` ，请使用以下命令运行该函数。

```powershell
&(Get-Command -Name Map -CommandType Function)
```

or

```powershell
&(dir Function:\map)
```

你还可以将隐藏命令保存在变量中，以使其更易于运行。

例如，下面的命令将函数保存 `Map` 在变量中 `$myMap` ，然后使用 `Call` 运算符来运行该函数。

```powershell
$myMap = (Get-Command -Name map -CommandType function)
&($myMap)
```

### <a name="replaced-items"></a>替换项

"替换" 项是你不能再访问的项。 可以通过从模块或管理单元中导入具有相同名称的项来替换项。

例如，如果在 `Get-Map` 会话中键入函数，并导入名为的函数 `Get-Map` ，则该函数将替换原始函数。 你无法在当前会话中检索它。

变量和别名不能隐藏，因为不能使用调用运算符或限定名来运行它们。 从模块或管理单元中导入变量和别名时，它们会将会话中的变量替换为同一名称。

### <a name="avoiding-name-conflicts"></a>避免名称冲突

管理命令名称冲突的最佳方式是阻止这些冲突。 为命令命名时，使用唯一的名称。 例如，将首字母缩写或公司名称缩写添加到命令中的名词。

此外，当你将命令从 PowerShell 模块或其他会话导入到会话时，请使用 `Prefix` [import-module](xref:Microsoft.PowerShell.Core.Import-Module) 的参数或

[Import-module](xref:Microsoft.PowerShell.Utility.Import-PSSession) cmdlet 将前缀添加到命令名称中的名词。

例如，以下命令可避免与 `Get-Date` `Set-Date` 导入模块时 PowerShell 附带的和 cmdlet 发生冲突 `DateFunctions` 。

```powershell
Import-Module -Name DateFunctions -Prefix ZZ
```

有关详细信息，请参阅 `Import-Module` 和 `Import-PSSession` 下面的。

## <a name="see-also"></a>另请参阅

- [about_Path_Syntax](about_Path_Syntax.md)
- [about_Aliases](about_Aliases.md)
- [about_Functions](about_Functions.md)
- [Alias-Provider](../../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)
- [Function-Provider](../../Microsoft.PowerShell.Core/About/about_Function_Provider.md)
- [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)
- [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module)
- [Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)

