---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 5f2752f53fb5f74b6436548c3bd4fa731d2b02d5
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879229"
---
# Get-Command

## 摘要
获取所有命令。

## SYNTAX

### CmdletSet (默认值) 

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
 [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
 [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### AllCommandSet

```
Get-Command [[-Name] <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-CommandType <CommandTypes>] [-TotalCount <Int32>]
 [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [-UseFuzzyMatching]
 [-UseAbbreviationExpansion] [<CommonParameters>]
```

## DESCRIPTION

该 `Get-Command` cmdlet 将获取安装在计算机上的所有命令，包括 cmdlet、别名、函数、筛选器、脚本和应用程序。 `Get-Command` 从 PowerShell 模块中获取命令，以及从其他会话导入的命令。 若要仅获取已导入到当前会话中的命令，请使用 **ListImported** 参数。

如果没有参数，则将 `Get-Command` 获取计算机上安装的所有 cmdlet、函数和别名。 `Get-Command *` 获取所有类型的命令，包括 Path 环境变量中的所有非 PowerShell 文件 (`$env:Path`) ，它将在应用程序命令类型中列出。

`Get-Command` 如果使用命令的确切名称（不包含通配符），则会自动导入包含命令的模块，以便你可以立即使用命令。 若要启用、禁用和配置模块的自动导入，请使用 `$PSModuleAutoLoadingPreference` 首选项变量。 有关详细信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。

`Get-Command` 直接从命令代码获取其数据，这不同于 `Get-Help` ，它从帮助主题中获取其信息。

从 Windows PowerShell 5.0 开始， `Get-Command` 默认情况下，cmdlet 的结果显示 **版本** 列。 新 **版本** 属性已添加到 **CommandInfo** 类。

## 示例

### 示例1：获取 cmdlet、函数和别名

此命令将获取安装在计算机上的 PowerShell cmdlet、函数和别名。

```powershell
Get-Command
```

### 示例2：获取当前会话中的命令

此命令使用 **ListImported** 参数来仅获取当前会话中的命令。

```powershell
Get-Command -ListImported
```

### 示例3：获取 cmdlet 并按顺序显示

此命令将获取所有的 cmdlet、通过 cmdlet 名称中的名词按字母顺序对其进行排序，然后将其显示在基于名词的组中。 此显示内容可帮助你在任务中查找 cmdlet。

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### 示例4：获取模块中的命令

此命令使用 **Module** 参数来获取 Microsoft. Security 和 Microsoft. Utility 模块中的命令。

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### 示例5：获取有关 cmdlet 的信息

此命令获取有关 cmdlet 的信息 `Get-AppLockerPolicy` 。 它还会导入 **AppLocker** 模块，该模块可将 **AppLocker** 模块中的所有命令添加到当前会话中。

```powershell
Get-Command Get-AppLockerPolicy
```

自动导入模块后，效果与使用 Import-Module cmdlet 相同。
该模块可以添加命令、类型和格式设置文件，并在会话中运行脚本。 若要启用、禁用和配置自动导入模块，请使用 `$PSModuleAutoLoadingPreference` 首选项变量。 有关详细信息，请参阅 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

### 示例6：获取 cmdlet 的语法

当在 Cert：  `Get-ChildItem` 驱动器中使用 cmdlet 时，此命令将使用 ArgumentList 和句法参数获取该 cmdlet 的语法。 Cert：驱动器是证书提供程序添加到会话中的 PowerShell 驱动器。

```powershell
Get-Command  -Name Get-Childitem -Args Cert: -Syntax
```

当你将输出中显示的语法与省略 **Args** (**ArgumentList**) 参数时显示的语法进行比较时，你会看到 **证书提供程序** 将动态参数 **CodeSigningCert** 添加到 `Get-ChildItem` cmdlet。

有关证书提供程序的详细信息，请参阅 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)。

### 示例7：获取动态参数

该示例中的命令使用 `Get-DynamicParameters` 函数获取证书提供程序在证书 `Get-ChildItem` ：驱动器中使用时添加到 cmdlet 的动态参数。

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command -Name $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

`Get-DynamicParameters`此示例中的函数获取 cmdlet 的动态参数。 这是上一示例中所用方法的替代方法。 可以通过另一个 cmdlet 或提供程序将 Dynamic 参数添加到 cmdlet。

### 示例8：获取所有类型的所有命令

此命令将获取本地计算机上所有类型的所有命令，包括 **Path** 环境变量路径中的可执行文件 (`$env:path`) 。

```powershell
Get-Command *
```

它将为每个文件返回一个 **ApplicationInfo** 对象 (System.Management.Automation.ApplicationInfo)，而不是 **FileInfo** 对象 (System.IO.FileInfo)。

### 示例9：使用参数名称和类型获取 cmdlet

此命令将获取其名称包含 authentication 且类型为 **system.management.automation.runspaces.authenticationmechanism** 的参数的 cmdlet。

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

可以使用类似此命令的命令查找允许你指定用于对用户进行身份验证的方法的 cmdlet。

即使采用 **AuthenticationMechanism** 值的参数和采用 **AuthenticationLevel** 参数的参数具有类似名称，**ParameterType** 参数也可区分它们。

### 示例10：获取别名

此示例演示如何使用 `Get-Command` 带有别名的 cmdlet。

```powershell
Get-Command -Name dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

虽然它通常用于 cmdlet 和函数，但 `Get-Command` 也可获取脚本、函数、别名和可执行文件。

命令的输出将显示别名的 **Name** 属性值的特殊视图。 该视图将显示别名以及完整的命令名称。

### 示例11：从别名获取语法

此示例演示如何获取语法以及别名的标准名称。

该命令的输出显示带有标准名称的标记别名，后跟语法。

```powershell
Get-Command -Name dir -Syntax
```

```Output
dir (alias) -> Get-ChildItem

dir [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]

dir [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### 示例12：获取记事本命令的所有实例

此示例使用 cmdlet 的 **all** 参数 `Get-Command` `Notepad` 在本地计算机上显示该命令的所有实例。

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

当会话中的多个命令具有相同名称时，**All** 参数非常有用。

从 Windows PowerShell 3.0 开始，默认情况下，当会话中包含具有相同名称的多个命令时， `Get-Command` 仅获取键入命令名称时运行的命令。 对于 **all** 参数， `Get-Command` 获取具有指定名称的所有命令，并按执行优先级顺序返回它们。 若要运行除列表中第一个命令以外的某个命令，请键入该命令的完全限定的路径。

有关命令优先级的详细信息，请参阅 [about_Command_Precedence](About/about_Command_Precedence.md)。

### 示例13：获取包含 cmdlet 的模块的名称

此命令获取该 cmdlet 所源自的模块的名称 `Get-Date` 。
该命令使用所有命令的 **ModuleName** 属性。

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

此命令格式适用于 PowerShell 模块中的命令，即使未将它们导入到会话中也是如此。

### 示例14：获取具有输出类型的 cmdlet 和函数

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

此命令将获取具有输出类型及其返回的对象类型的 cmdlet 和函数。

该命令的第一部分将获取所有 cmdlet。 管道运算符 (`|`) 将 cmdlet 发送到 `Where-Object` cmdlet，该 cmdlet 只选择在其中填充 **OutputType** 属性的 cmdlet。 另一个管道运算符将选定的 cmdlet 对象发送到 `Format-List` cmdlet，该 cmdlet 将在列表中显示每个 cmdlet 的名称和输出类型。

仅当 cmdlet 代码为 cmdlet 定义了 **OutputType** 属性时，**CommandInfo** 对象的 **OutputType** 属性的值才为非 null。

### 示例15：获取采用特定对象类型作为输入的 cmdlet

```powershell
Get-Command -ParameterType (((Get-NetAdapter)[0]).PSTypeNames)
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Disable-NetAdapter                                 NetAdapter
Function        Enable-NetAdapter                                  NetAdapter
Function        Rename-NetAdapter                                  NetAdapter
Function        Restart-NetAdapter                                 NetAdapter
Function        Set-NetAdapter                                     NetAdapter
```

此命令可查找将网络适配器对象用作输入的 cmdlet。 可以使用此命令格式查找接受任何命令返回的对象类型的 cmdlet。

该命令使用所有对象的 **PSTypeNames** 内部属性，它将获取用于描述该对象的类型。 若要获取网络适配器的 **PSTypeNames** 属性，而不是网络适配器集合的 **PSTypeNames** 属性，该命令将使用数组表示法来获取该 cmdlet 返回的第一个网络适配器。

### 示例16：使用模糊匹配获取命令

在此示例中，该命令的名称特意将错误键入为 "commnd"。
通过使用 `-UseFuzzyMatching` 开关，cmdlet 确定最佳匹配项 `Get-Command` 后跟系统上具有类似匹配项的其他本机命令。

```powershell
Get-Command get-commnd -UseFuzzyMatching
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Command                                        6.2.0.0    Microsoft.PowerShell.Core
Application     getconf                                            0.0.0.0    /usr/bin/getconf
Application     command                                            0.0.0.0    /usr/bin/command
```

## PARAMETERS

### -All

指示此 cmdlet 获取所有命令，包括具有相同名称的相同类型的命令。 默认情况下， `Get-Command` 仅获取键入命令名称时运行的命令。

有关当多个命令具有相同名称时 PowerShell 用于选择要运行的命令的方法的详细信息，请参阅 [about_Command_Precedence](About/about_Command_Precedence.md)。
有关由于名称冲突而默认情况下不会运行的模块限定命令名称和运行命令的信息，请参阅 [about_Modules](About/about_Modules.md)。

已在 Windows PowerShell 3.0 中引入了此参数。

在 Windows PowerShell 2.0 中， `Get-Command` 默认情况下获取所有命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ArgumentList

指定参数数组。 此 cmdlet 将获取有关 cmdlet 或函数的信息，与指定参数一起使用时， ( "arguments" ) 。 **ArgumentList** 的别名是 **Args**。

若要检测仅当使用某些其他参数时才可用的动态参数，请将 **ArgumentList** 的值设置为触发动态参数的参数。

若要检测提供程序添加到 cmdlet 的动态参数，请将 **ArgumentList** 参数的值设置为提供程序驱动器中的路径，例如 WSMan：、HKLM：或 Cert：。 如果命令是 PowerShell 提供程序 cmdlet，请在每个命令中仅输入一个路径。 提供程序 cmdlet 只为第一个路径返回值为 **ArgumentList** 的动态参数。 有关提供程序 cmdlet 的信息，请参阅 [about_Providers](About/about_Providers.md)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandType

指定此 cmdlet 获取的命令类型。 输入一个或多个命令类型。 使用 **CommandType** 或其别名 **Type**。 默认情况下，将 `Get-Command` 获取所有 cmdlet、函数和别名。

此参数的可接受值为：

- A. 获取所有 PowerShell 命令的别名。 有关详细信息，请参阅 [about_Aliases](About/about_Aliases.md)。
- 全部。 获取所有命令类型。 此参数值等效于 `Get-Command *` 。
- 应用程序。 获取 **Path** 环境变量中列出的路径中的非 PowerShell 文件 ($env:p a) ，包括 .txt、.exe 和 .dll 文件。 有关 **Path** 环境变量的详细信息，请参阅 about_Environment_Variables。
- Cmdlet. 获取所有 cmdlet。
- ExternalScript. 获取在 **Path** 环境变量 ($env:path) 中列出的路径中的所有 .ps1 文件。
- Filter 和 Function。 获取所有 PowerShell 高级和简单函数和筛选器。
- 脚本。 获取所有脚本块。 若要)  ( ps1 文件获取 PowerShell 脚本，请使用 ExternalScript 值。

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: AllCommandSet
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FullyQualifiedModule

指定以 **ModuleSpecification** 对象的形式指定的模块，在 ModuleSpecification 构造函数的 " **备注** " 部分中介绍 [ (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)。
例如， **FullyQualifiedModule** 参数接受以下格式之一指定的模块名称：

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**ModuleName** 和 **ModuleVersion** 是必需的，但 **Guid** 是可选的。

不能在与 **Module** 参数相同的命令中指定 **FullyQualifiedModule** 参数。 这两个参数是互斥的。

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ListImported

指示此 cmdlet 仅获取当前会话中的命令。

从 PowerShell 3.0 开始，默认情况下， `Get-Command` 会获取所有已安装的命令，包括但不限于当前会话中的命令。 在 PowerShell 2.0 中，它只获取当前会话中的命令。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Module

指定模块的数组。 此 cmdlet 将获取来自指定模块的命令。
输入模块或模块对象的名称。

此参数采用字符串值，但此参数的值还可以是 **PSModuleInfo** 对象，例如 `Get-Module` 和 `Import-PSSession` cmdlet 返回的对象。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Name

指定一个名称数组。 此 cmdlet 仅获取具有指定名称的命令。 输入一个名称或名称模式。 允许使用通配符。

若要获取具有相同名称的命令，请使用 **All** 参数。 如果两个命令具有相同的名称，则默认情况下，将 `Get-Command` 获取键入命令名称时运行的命令。

```yaml
Type: System.String[]
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -名词

指定一个命令名词的数组。 此 cmdlet 将获取包含具有指定名词的名称的命令，其中包括 cmdlet、函数和别名。 输入一个或多个名词或名词模式。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ParameterName

指定参数名称的数组。 此 cmdlet 将获取会话中具有指定参数的命令。 输入参数名称或参数别名。 支持使用通配符。

**ParameterName** 和 **ParameterType** 参数仅搜索当前会话中的命令。

已在 Windows PowerShell 3.0 中引入了此参数。

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

### -ParameterType

指定参数名称的数组。 此 cmdlet 将获取会话中具有指定类型的参数的命令。 输入参数类型的全名或部分名称。 支持使用通配符。

**ParameterName** 和 **ParameterType** 参数仅搜索当前会话中的命令。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.PSTypeName[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowCommandInfo

指示此 cmdlet 显示命令信息。

此参数是在 Windows PowerShell 5.0 中引入的。

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

### -语法

指示此 cmdlet 仅获取有关该命令的下列指定数据：

- 别名. 获取标准名称和语法。
- Cmdlet. 获取语法。
- 函数和筛选器。 获取函数定义。
- 脚本和应用程序或文件。 获取路径和文件名。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -TotalCount

指定要获取的命令数。 可以使用此参数来限制命令的输出。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseAbbreviationExpansion

指示使用命令中的匹配字符在命令中查找大写字符。 例如， `i-psdf` 将匹配， `Import-PowerShellDataFile` 因为要查找的每个字符都匹配结果中的大写字符。 当使用这种类型的匹配时，任何通配符将导致不匹配。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseFuzzyMatching

指示在查找命令时使用模糊匹配算法。 输出的顺序是从最接近的匹配到最小的可能匹配。 不应将通配符与模糊匹配一起使用，因为它会尝试匹配可能包含这些通配符字符的命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verb

指定命令谓词的数组。 此 cmdlet 将获取包含包含指定谓词的名称的命令，其中包括 cmdlet、函数和别名。 输入一个或多个谓词或谓词模式。 允许使用通配符。

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](About/about_CommonParameters.md)。

## 输入

### System.String

可以通过管道将命令名称传递给此 cmdlet。

## 输出

### System.web. CommandInfo

此 cmdlet 返回派生自 **CommandInfo** 类的对象。 返回的对象类型取决于获取的命令类型 `Get-Command` 。

### System.Management.Automation.AliasInfo

表示别名。

### System.web. ApplicationInfo

表示应用程序和文件。

### System.web. CmdletInfo

表示 cmdlet。

### System.web. FunctionInfo

表示函数和筛选器。

## 注释

* 当具有相同名称的多个命令可用于会话时，将返回在 `Get-Command` 键入命令名称时运行的命令。 若要获取具有相同名称的命令（按运行顺序列出），请使用 **All** 参数。 有关详细信息，请参阅 [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)。
* 自动导入模块后，效果与使用 `Import-Module` cmdlet 相同。 该模块可以添加命令、类型和格式设置文件，并在会话中运行脚本。
  若要启用、禁用和配置自动导入模块，请使用 `$PSModuleAutoLoadingPreference` 首选项变量。 有关详细信息，请参阅 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

## 相关链接

[Export-PSSession](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[Get-Help](Get-Help.md)

[Get-Member](../Microsoft.PowerShell.Utility/Get-Member.md)

[Get-PSDrive](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[Import-PSSession](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[about_Command_Precedence](About/about_Command_Precedence.md)

