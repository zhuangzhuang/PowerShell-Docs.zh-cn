---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionConfigurationFile
ms.openlocfilehash: a41c52bf163aa0a73b54e75b5192389a14da82bb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598875"
---
# New-PSSessionConfigurationFile

## 摘要
创建用于定义会话配置的文件。

## SYNTAX

```
New-PSSessionConfigurationFile [-Path] <String> [-SchemaVersion <Version>] [-Guid <Guid>]
 [-Author <String>] [-Description <String>] [-CompanyName <String>] [-Copyright <String>]
 [-SessionType <SessionType>] [-TranscriptDirectory <String>] [-RunAsVirtualAccount]
 [-RunAsVirtualAccountGroups <String[]>] [-MountUserDrive] [-UserDriveMaximumSize <Int64>]
 [-GroupManagedServiceAccount <String>] [-ScriptsToProcess <String[]>]
 [-RoleDefinitions <IDictionary>] [-RequiredGroups <IDictionary>] [-LanguageMode <PSLanguageMode>]
 [-ExecutionPolicy <ExecutionPolicy>] [-PowerShellVersion <Version>] [-ModulesToImport <Object[]>]
 [-VisibleAliases <String[]>] [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>]
 [-VisibleExternalCommands <String[]>] [-VisibleProviders <String[]>]
 [-AliasDefinitions <IDictionary[]>] [-FunctionDefinitions <IDictionary[]>]
 [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>] [-Full] [<CommonParameters>]
```

## DESCRIPTION

`New-PSSessionConfigurationFile`Cmdlet 将创建一个设置文件，用于定义会话配置，以及使用会话配置创建的会话的环境。
若要在会话配置中使用该文件，请使用或 cmdlet 的 **Path** 参数 `Register-PSSessionConfiguration` `Set-PSSessionConfiguration` 。

创建的会话配置文件 `New-PSSessionConfigurationFile` 是一个可读的文本文件，其中包含会话配置属性和值的哈希表。 文件具有文件 `.pssc` 扩展名。

`New-PSSessionConfigurationFile`除 **Path** 参数外，所有参数都是可选的。
如果省略一个参数，则将注释掉会话配置文件中的相应键，已在参数说明中注明的除外。

会话配置（也称为终结点）是本地计算机上的一组设置，用于定义连接到计算机 (**pssession**) 的 PowerShell 会话的环境。 所有 **pssession** 都使用会话配置。 若要指定特定的会话配置，请使用 cmdlet 的 **ConfigurationName** 参数，该参数可创建一个会话（如 `New-PSSession` cmdlet）。

session configuration file 可以轻松地定义会话配置，无需复杂的脚本或代码程序集。 该文件中的设置与可选的启动脚本和会话配置中的任何程序集一起使用。

有关会话配置和会话配置文件的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md) 和 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。

此 cmdlet 是在 PowerShell 3.0 中引入的。

## 示例

### 示例1：创建和使用 NoLanguage 会话

此示例演示如何创建和使用无语言会话的效果。

步骤包括：

1. 创建新的配置文件。
1. 注册配置。
1. 创建使用该配置的新会话。
1. 在该新会话中运行命令。

若要运行此示例中的命令，请使用 "以管理员身份运行" 选项启动 PowerShell。 运行 cmdlet 需要此选项 `Register-PSSessionConfiguration` 。

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode NoLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name NoLanguage -Force
$NoLanguageSession = New-PSSession -ComputerName Srv01 -ConfigurationName NoLanguage
Invoke-Command -Session $NoLanguageSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
The syntax is not supported by this runspace. This might be because it is in no-language mode.
    + CategoryInfo          : ParserError: (if ((Get-Date) ...') {'Before'}  :String) [], ParseException
    + FullyQualifiedErrorId : ScriptsNotAllowed
    + PSComputerName        : localhost
```

在此示例中， `Invoke-Command` 失败的原因是 **LanguageMode** 设置为 **NoLanguage**。

### 示例2：创建和使用 RestrictedLanguage 会话

此示例演示如何创建和使用无语言会话的效果。

步骤包括：

1. 创建新的配置文件。
1. 注册配置。
1. 创建使用该配置的新会话。
1. 在该新会话中运行命令。

若要运行此示例中的命令，请使用 "以管理员身份运行" 选项启动 PowerShell。 运行 cmdlet 需要此选项 `Register-PSSessionConfiguration` 。

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode RestrictedLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name RestrictedLanguage -Force
$RestrictedSession = New-PSSession -ComputerName Srv01 -ConfigurationName RestrictedLanguage
Invoke-Command -Session $RestrictedSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
Before
```

在此示例中，将 `Invoke-Command` 成功，因为 **LanguageMode** 设置为 **RestrictedLanguage**。

### 示例3：更改会话配置文件

此示例演示如何更改在名为 "ITTasks" 的现有会话中使用的会话配置文件。 以前，这些会话仅具有核心模块和内部 **ITTasks** 模块。 管理员想要将 **PSScheduledJob** 模块添加到使用 ITTasks 会话配置创建的会话中。

```powershell
New-PSSessionConfigurationFile -Path .\New-ITTasks.pssc -ModulesToImport Microsoft*, ITTasks, PSScheduledJob
Set-PSSessionConfiguration -Name ITTasks -Path .\New-ITTasks.pssc
```

`New-PSSessionConfigurationFile`Cmdlet 来创建导入所需模块的会话配置文件。 `Set-PSSessionConfiguration`Cmdlet 用新的配置文件替换当前的配置文件。 这一新配置仅影响在更改后创建的新会话。
现有 "ITTasks" 会话不受影响。

### 示例4：编辑会话配置文件

此示例显示了如何通过编辑配置文件的主动会话配置副本来更改会话配置。 若要修改配置文件的会话配置副本，您必须对该文件具有完全控制访问权限。 这可能需要更改对文件的权限。

在此方案中，我们想要 `Select-String` 通过编辑活动配置文件来添加 cmdlet 的新别名。

下面的示例代码执行以下步骤来进行此更改：

1. 获取 ITConfig 会话的配置文件路径。
1. 用户使用 **Notepad.exe** 编辑配置文件以更改 **AliasDefinitions** 值，如下所示： `AliasDefinitions = @(@{Name='slst';Value='Select-String'})` 。
1. 测试更新的配置文件。

```powershell
$ITConfig = Get-PSSessionConfiguration -Name ITConfig
notepad.exe $ITConfig.ConfigFilePath
Test-PSSessionConfigurationFile -Path $ITConfig.ConfigFilePath
```

```Output
True
```

结合使用 **Verbose** 参数 `Test-PSSessionConfigurationFile` 来显示检测到的任何错误。 `$True`如果文件中未检测到任何错误，则该 cmdlet 将返回。

### 示例5：创建示例配置文件

此示例显示了一个 `New-PSSessionConfigurationFile` 使用所有 cmdlet 参数的命令。
包含此示例以显示每个参数对应的正确输入格式。

生成的 SampleFile.pssc 将显示在输出中。

```powershell
$configSettings = @{
    Path = '.\SampleFile.pssc'
    SchemaVersion = '1.0.0.0'
    Author = 'User01'
    Copyright = '(c) Fabrikam Corporation. All rights reserved.'
    CompanyName = 'Fabrikam Corporation'
    Description = 'This is a sample file.'
    ExecutionPolicy = 'AllSigned'
    PowerShellVersion = '3.0'
    LanguageMode = 'FullLanguage'
    SessionType = 'Default'
    EnvironmentVariables = @{TESTSHARE='\\Test2\Test'}
    ModulesToImport = @{ModuleName='PSScheduledJob'; ModuleVersion='1.0.0.0'; GUID='50cdb55f-5ab7-489f-9e94-4ec21ff51e59'},'PSDiagnostics'
    AssembliesToLoad = 'System.Web.Services','FSharp.Compiler.CodeDom.dll'
    TypesToProcess = 'Types1.ps1xml','Types2.ps1xml'
    FormatsToProcess = 'CustomFormats.ps1xml'
    ScriptsToProcess = 'Get-Inputs.ps1'
    AliasDefinitions = @{Name='hlp';Value='Get-Help';Description='Gets help.';Options='AllScope'},
        @{Name='Update';Value='Update-Help';Description='Updates help';Options='ReadOnly'}
    FunctionDefinitions = @{Name='Get-Function';ScriptBlock={Get-Command -CommandType Function};Options='ReadOnly'}
    VariableDefinitions = @{Name='WarningPreference';Value='SilentlyContinue'}
    VisibleAliases = 'c*','g*','i*','s*'
    VisibleCmdlets = 'Get*'
    VisibleFunctions = 'Get*'
    VisibleProviders = 'FileSystem','Function','Variable'
    RunAsVirtualAccount = $true
    RunAsVirtualAccountGroups = 'Backup Operators'
}
New-PSSessionConfigurationFile @configSettings
Get-Content SampleFile.pssc
```

```Output
@{

# Version number of the schema used for this document
SchemaVersion = '1.0.0.0'

# ID used to uniquely identify this document
GUID = '1caeff7f-27ca-4360-97cf-37846f594235'

# Author of this document
Author = 'User01'

# Description of the functionality provided by these settings
Description = 'This is a sample file.'

# Company associated with this document
CompanyName = 'Fabrikam Corporation'

# Copyright statement for this document
Copyright = '(c) Fabrikam Corporation. All rights reserved.'

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'Default'

# Directory to place session transcripts for this session configuration
# TranscriptDirectory = 'C:\Transcripts\'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
RunAsVirtualAccountGroups = 'Backup Operators'

# Scripts to run when applied to a session
ScriptsToProcess = 'Get-Inputs.ps1'

# User roles (security groups), and the role capabilities that should be applied to them when applied to a session
# RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\SqlManaged' = @{ RoleCapabilityFiles = 'C:\RoleCapability\SqlManaged.psrc' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }

# Language mode to apply when applied to a session. Can be 'NoLanguage' (recommended), 'RestrictedLanguage', 'ConstrainedLanguage', or 'FullLanguage'
LanguageMode = 'FullLanguage'

# Execution policy to apply when applied to a session
ExecutionPolicy = 'AllSigned'

# Version of the PowerShell engine to use when applied to a session
PowerShellVersion = '3.0'

# Modules to import when applied to a session
ModulesToImport = @{
    'GUID' = '50cdb55f-5ab7-489f-9e94-4ec21ff51e59'
    'ModuleName' = 'PSScheduledJob'
    'ModuleVersion' = '1.0.0.0' }, 'PSDiagnostics'

# Aliases to make visible when applied to a session
VisibleAliases = 'c*', 'g*', 'i*', 's*'

# Cmdlets to make visible when applied to a session
VisibleCmdlets = 'Get*'

# Functions to make visible when applied to a session
VisibleFunctions = 'Get*'

# Providers to make visible when applied to a session
VisibleProviders = 'FileSystem', 'Function', 'Variable'

# Aliases to be defined when applied to a session
AliasDefinitions = @{
    'Description' = 'Gets help.'
    'Name' = 'hlp'
    'Options' = 'AllScope'
    'Value' = 'Get-Help' }, @{
    'Description' = 'Updates help'
    'Name' = 'Update'
    'Options' = 'ReadOnly'
    'Value' = 'Update-Help' }

# Functions to define when applied to a session
FunctionDefinitions = @{
    'Name' = 'Get-Function'
    'Options' = 'ReadOnly'
    'ScriptBlock' = {Get-Command -CommandType Function} }

# Variables to define when applied to a session
VariableDefinitions = @{
    'Name' = 'WarningPreference'
    'Value' = 'SilentlyContinue' }

# Environment variables to define when applied to a session
EnvironmentVariables = @{
    'TESTSHARE' = '\\Test2\Test' }

# Type files (.ps1xml) to load when applied to a session
TypesToProcess = 'Types1.ps1xml', 'Types2.ps1xml'

# Format files (.ps1xml) to load when applied to a session
FormatsToProcess = 'CustomFormats.ps1xml'

# Assemblies to load when applied to a session
AssembliesToLoad = 'System.Web.Services', 'FSharp.Compiler.CodeDom.dll'

}
```

## PARAMETERS

### -AliasDefinitions

将指定的别名添加到使用该会话配置的会话中。 输入一个包含以下键的哈希表：

- 名称-别名的名称。 此键是必需的。
- Value-别名表示的命令。 此键是必需的。
- 说明-描述别名的文本字符串。 此键是可选的。
- 选项-别名选项。 此键是可选的。 默认值为 " **无**"。 此参数的可接受值为： None、ReadOnly、常量、Private 或 AllScope。

例如： `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssembliesToLoad

指定要加载到使用该会话配置的会话中的程序集。

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

### -作者

指定会话配置或配置文件的作者。 默认为当前用户。 此参数的值在会话配置文件中可见，但是它不是会话配置对象的属性。

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

### -公司名称

指定创建了会话配置或配置文件的公司。 默认值是“未知”。 此参数的值在会话配置文件中可见，但是它不是会话配置对象的属性。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Unknown
Accept pipeline input: False
Accept wildcard characters: False
```

### -版权所有

指定会话配置文件的版权。 此参数的值在会话配置文件中可见，但是它不是会话配置对象的属性。

如果省略此参数，则 `New-PSSessionConfigurationFile` 使用 **Author** 参数的值生成版权声明。

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

### -Description

指定会话配置或会话配置文件的描述。 此参数的值在会话配置文件中可见，但是它不是会话配置对象的属性。

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

### -EnvironmentVariables

将环境变量添加到会话中。 输入一个哈希表，其中的键是环境变量名称，而值是环境变量值。

例如： `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExecutionPolicy

指定使用该会话配置的会话的执行策略。 如果省略此参数，则会 **限制** 会话配置文件中 **set-executionpolicy** 键的值。 有关 PowerShell 中的执行策略的信息，请参阅 [about_Execution_Policies](about/about_Execution_Policies.md)。

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: Unrestricted, RemoteSigned, AllSigned, Restricted, Default, Bypass, Undefined

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

指定在使用该会话配置的会话中运行的格式设置文件 (.ps1xml)。
此参数的值必须是格式设置文件的完整或绝对路径。

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

### -Full

指示此操作包括会话配置文件中所有可能的配置属性。

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

### -FunctionDefinitions

将指定函数添加到使用该会话配置的会话中。 输入一个包含以下键的哈希表：

- 名称-函数的名称。 此键是必需的。
- ScriptBlock 函数体。 输入一个脚本块。 此键是必需的。
- Options-函数选项。 此键是可选的。 默认值为 " **无**"。 此参数的可接受值为： None、ReadOnly、常量、Private 或 AllScope。

例如： `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Msds-groupmanagedserviceaccount

将使用此会话配置的会话配置为在指定的组托管服务帐户的上下文中运行。 注册此会话配置的计算机必须有权请求 gMSA 密码才能成功创建会话。 此字段不能与 **将 runasvirtualaccount 设置** 参数一起使用。

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

### -Guid

为会话配置文件指定唯一标识符。 如果省略此参数，则 `New-PSSessionConfigurationFile` 将为文件生成 GUID。 若要在 PowerShell 中创建新的 GUID，请键入 `New-Guid` 。

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LanguageMode

确定在使用此会话配置的会话中允许使用 PowerShell 语言的哪些元素。 可以使用此参数来限制特定用户可以在计算机上运行的命令。

此参数的可接受值为：

- FullLanguage-允许所有语言元素。
- ConstrainedLanguage-不允许包含要计算的脚本的命令。 ConstrainedLanguage 模式限制用户对 Microsoft .NET Framework 类型、对象或方法的访问权限。
- NoLanguage-用户可以运行 cmdlet 和函数，但是不允许使用任何语言元素，如脚本块、变量或运算符。
- RestrictedLanguage-用户可以运行 cmdlet 和函数，但不允许使用除以下允许变量以外的脚本块或变量： `$PSCulture` 、、、 `$PSUICulture` `$True` `$False` 和 `$Null` 。 用户可以只使用基本比较运算符， (`-eq` ， `-gt` `-lt`) 。 不允许使用赋值语句、属性引用和方法调用。

**LanguageMode** 参数的默认值取决于 **SessionType** 参数的值。

- 空-NoLanguage
- RestrictedRemoteServer-NoLanguage
- 默认值-FullLanguage

```yaml
Type: System.Management.Automation.PSLanguageMode
Parameter Sets: (All)
Aliases:
Accepted values: FullLanguage, RestrictedLanguage, NoLanguage, ConstrainedLanguage

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

指定自动导入使用该会话配置的会话的模块和管理单元。

默认情况下，只会将 **Microsoft. Core** 管理单元导入远程会话，但除非排除 cmdlet，否则用户可以使用 `Import-Module` 和 `Add-PSSnapin` cmdlet 将模块和管理单元添加到会话中。

此参数的值中的每个模块或管理单元都可以由字符串表示或以哈希表的形式表示。 模块字符串只包含模块或管理单元的名称。 模块哈希表可以包含 **ModuleName**、 **ModuleVersion** 和 **GUID** 键。 仅 **ModuleName** 键是必需的。

例如，下面的值由字符串和哈希表组成。 字符串和哈希表的任何组合（采用任何顺序）都是有效的。

`'TroubleshootingPack', @{ModuleName='PSDiagnostics'; ModuleVersion='1.0.0.0';GUID='c61d6278-02a3-4618-ae37-a524d40a7f44'}`

Cmdlet 的 **ModulesToImport** 参数的值 `Register-PSSessionConfiguration` 优先于会话配置文件中的 **ModulesToImport** 键的值。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MountUserDrive

配置使用此会话配置公开 New-psdrive 的会话 `User:` 。 用户驱动器对于每个连接用户都是唯一的，并允许用户在不公开文件系统提供程序的情况上向/从 PowerShell 终结点复制数据。 用户驱动器根在下创建 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\` 。 对于连接到终结点的每位用户，将创建一个具有 `$env:USERDOMAIN_$env:USERNAME` 名称的文件夹。

用户驱动器中的内容跨用户会话保持不变，不会自动删除。 默认情况下，用户只能在用户驱动器中存储最多50MB 数据。 可以通过 **UserDriveMaximumSize** 参数自定义此参数。

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

指定会话配置文件的路径和文件名。 文件必须具有 `.pssc` 文件扩展名。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellVersion

指定使用会话配置的会话中的 PowerShell 引擎版本。 此参数可接受的值为：2.0 和3.0。 如果省略此参数，则会在会话中注释掉 **PowerShellVersion** 键，并在会话中运行最新版本的 PowerShell。

Cmdlet 的 **PSVersion** 参数的值 `Register-PSSessionConfiguration` 优先于会话配置文件中的 **PowerShellVersion** 键的值。

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredGroups

指定连接到使用此会话配置的会话的用户的条件性访问规则。

输入一个哈希表以使用每个哈希表、' 和 ' 或 ' 或 ' 仅使用1个密钥来编写规则列表，并将值设置为安全组名称或附加哈希表的数组。

要求将用户连接到单个组成员的示例： `@{ And = 'MyRequiredGroup' }`

要求用户属于组 A 或同时属于组 B 和 C 的示例，用于访问终结点： `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RoleDefinitions

指定安全组之间的映射 (或用户) 和角色功能。 在创建会话时，将向用户授予对其组成员资格适用的所有角色功能的访问权限。

输入一个哈希表，其中的键是安全组的名称，值是包含应对安全组可用的角色功能列表的哈希表。

例如： `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -将 runasvirtualaccount 设置

使用此会话配置配置要作为计算机 (虚拟) 管理员帐户运行的会话。 此字段不能与 **msds-groupmanagedserviceaccount** 参数一起使用。

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

### -RunAsVirtualAccountGroups

指定在使用会话配置的会话作为虚拟帐户运行时要与虚拟帐户关联的安全组。 如果省略，则虚拟帐户属于域控制器上的域管理员和所有其他计算机上的管理员。

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

### -SchemaVersion

指定会话配置文件架构的版本。 默认值为“1.0.0.0”。

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptsToProcess

将指定脚本添加到使用该会话配置的会话中。 请输入脚本的路径和文件名。 此参数的值必须为脚本文件名的完整或绝对路径。

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

### -SessionType

指定通过使用该会话配置创建的会话的类型。 默认值为 Default。 此参数的可接受值为：

- 空-默认情况下，不向会话添加任何模块。 使用此 cmdlet 的参数将模块、函数、脚本和其他功能添加到会话。 此选项可用于通过添加所选命令创建自定义会话。 如果没有将命令添加到空会话中，则该会话将限于表达式，并且可能不可用。
- 默认-将 Microsoft. Core 模块添加到会话中。 此模块包括 `Import-Module` cmdlet，用户可以使用该 cmdlet 导入其他模块，除非显式禁止此 cmdlet。
- RestrictedRemoteServer. 仅包括以下代理函数： `Exit-PSSession` 、 `Get-Command` 、 `Get-FormatData` 、、、 `Get-Help` `Measure-Object` `Out-Default` 和 `Select-Object` 。
  使用此 cmdlet 的参数将模块、函数、脚本和其他功能添加到会话。

```yaml
Type: System.Management.Automation.Remoting.SessionType
Parameter Sets: (All)
Aliases:
Accepted values: Empty, RestrictedRemoteServer, Default

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TranscriptDirectory

指定要为使用此会话配置的会话放置会话脚本的目录。

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

### -TypesToProcess

将指定的 `.ps1xml` 类型文件添加到使用会话配置的会话中。 输入类型文件名。 此参数的值必须为类型文件名的完整或绝对路径。

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

### -UserDriveMaximumSize

指定在使用此会话配置的会话中公开的用户驱动器的最大大小。
如果省略，则每个驱动器根的默认大小 `User:` 为50MB。

应将此参数与 **MountUserDrive** 一起使用。

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VariableDefinitions

将指定变量添加到使用该会话配置的会话中。 输入一个包含以下键的哈希表：

- 名称-变量的名称。 此键是必需的。
- 值-变量值。 此键是必需的。
- 选项-变量选项。 此键是可选的。 默认值为 " **无**"。 此参数的可接受值为： None、ReadOnly、常量、Private 或 AllScope。

例如： `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleAliases

将会话中的别名限制为在此参数的值中指定的别名以及在 **AliasDefinition** 参数中定义的任何别名。 支持使用通配符。 默认情况下，PowerShell 引擎定义的所有别名和模块导出的所有别名都在会话中可见。

例如： `VisibleAliases='gcm', 'gp'`

当会话配置文件中包含任何 **可见** 参数时，PowerShell 会从会话中删除该 `Import-Module` cmdlet 及其 ipmo 别名。

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

### -VisibleCmdlets

将会话中的 cmdlet 限制为在此参数的值中指定的 cmdlet。 支持通配符和模块限定名称。

默认情况下，会话中的模块导出的所有 cmdlet 都在该会话中可见。 使用 **SessionType** 和 **ModulesToImport** 参数来确定哪些模块和管理单元已导入到会话中。 如果 **ModulesToImport** 中没有任何模块公开 cmdlet，则相应的模块将尝试加载。

当会话配置文件中包含任何 **可见** 参数时，PowerShell 会从会话中删除该 `Import-Module` cmdlet 及其 ipmo 别名。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleExternalCommands

将可以在会话中执行的外部二进制文件、脚本和命令限制为在此参数的值中指定的文件。 支持使用通配符。

默认情况下，会话中不显示任何外部命令。

如果会话配置文件中包含任何 **可见** 参数，则 PowerShell 会 `Import-Module` 从会话中删除该 cmdlet 及其 ipmo 别名。

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

### -VisibleFunctions

将会话中的函数限制为在此参数的值中指定的函数以及在 **FunctionDefinition** 参数中定义的任何函数。 支持使用通配符。

默认情况下，会话中的模块导出的所有函数都在该会话中可见。 使用 **SessionType** 和 **ModulesToImport** 参数来确定哪些模块和管理单元已导入到会话中。

当会话配置文件中包含任何 **可见** 参数时，PowerShell 会从会话中删除该 `Import-Module` cmdlet 及其 ipmo 别名。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleProviders

将会话中的 PowerShell 提供程序限制为在此参数的值中指定的提供程序。
支持使用通配符。

默认情况下，会话中的模块导出的所有提供程序都在该会话中可见。 使用 **SessionType** 和 **ModulesToImport** 参数确定导入到会话中的模块。

当会话配置文件中包含任何 **可见** 参数时，PowerShell 将从会话中删除该 `Import-Module` cmdlet 及其 `ipmo` 别名。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将任何对象传递给此 cmdlet。

## 输出

### 无

此 cmdlet 将不生成任何输出。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

- 诸如 **VisibleCmdlets** 和 **VisibleProviders** 的参数不会将项导入到会话中。 而会从导入到会话中的项中进行选择。 例如，如果 **VisibleProviders** 参数的值是证书提供程序，但 **ModulesToImport** 参数未指定包含证书提供程序的 **模块，** 则该证书提供程序在会话中不可见。
- `New-PSSessionConfigurationFile` 创建会话配置文件 **，该文件在 path 参数中** 指定的路径中具有 .pssc 文件扩展名。 使用会话配置文件创建会话配置时，该 `Register-PSSessionConfiguration` cmdlet 会复制配置文件，并将该文件的活动副本保存在目录的 **SessionConfig** 子目录中 `$PSHOME` 。

  会话配置的 **ConfigFilePath** 属性包含活动会话配置文件的完全限定路径。 你可以随时 `$PSHOME` 使用任意文本编辑器修改该目录中的活动配置文件。 所做的更改会影响使用该会话配置的所有新会话，但不会影响现有会话。

  使用已编辑的会话配置文件之前，请使用 `Test-PSSessionConfigurationFile` cmdlet 验证配置文件项是否有效。

## 相关链接

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供程序](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
