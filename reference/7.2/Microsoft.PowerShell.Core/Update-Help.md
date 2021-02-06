---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/16/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/update-help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Help
ms.openlocfilehash: f4aec907a41378bbf49f744b66c5662aa3404beb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596215"
---
# Update-Help

## 摘要
在计算机上下载和安装最新的帮助文件。

## SYNTAX

### Path（默认值）

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-SourcePath] <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### LiteralPath

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-LiteralPath <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`Update-Help`Cmdlet 可为 PowerShell 模块下载最新的帮助文件，并将其安装在计算机上。 不需要重新启动 PowerShell 即可使更改生效。 可以使用 `Get-Help` cmdlet 立即查看新的帮助文件。

`Update-Help` 检查计算机上的帮助文件的版本。 如果没有模块的帮助文件，或者帮助文件已过时，则会 `Update-Help` 下载最新的帮助文件。 可从 internet 或文件共享下载和安装帮助文件。

如果没有参数，则将为 `Update-Help` 支持可更新帮助的所有已安装模块更新会话中的模块的帮助文件。 包含当前会话中安装但未加载的模块。 PowerShell 模块存储在环境变量中列出的位置 `$env:PSModulePath` 。 有关详细信息，请参阅 [about_Updatable_Help](./About/about_Updatable_Help.md)。

您可以使用 **Module** 参数为特定模块更新帮助文件。 使用 **UICulture** 参数下载多个语言和区域设置的帮助文件。

你还可以 `Update-Help` 在未连接到 internet 的计算机上使用。 首先，使用 `Save-Help` cmdlet 从 internet 下载帮助文件，并将其保存在可由未连接到 internet 的系统访问的共享文件夹中。 然后，使用 **SourcePath** 参数 `Update-Help` 从共享中下载更新的帮助文件，并将其安装在计算机上。

可以通过将 `Update-Help` cmdlet 添加到 PowerShell 配置文件来自动执行帮助更新。 默认情况下， `Update-Help` 每台计算机上每天仅运行一次。 若要重写每天一次的限制，请使用 **Force** 参数。

`Update-Help`Cmdlet 是在 Windows PowerShell 3.0 中引入的。

> [!IMPORTANT]
> `Update-Help` 需要在 PowerShell 6.0 和更低的管理权限。
> PowerShell 6.1 和更高版本将默认 **范围** 设置为 `CurrentUser` 。
> 在 PowerShell 6.1 之前， **作用域** 参数不可用。
>
> 您必须是计算机上 Administrators 组的成员，才能更新 PowerShell Core 模块的帮助文件。
>
> 若要下载或更新 PowerShell 安装目录中的模块的帮助文件 (`$PSHOME\Modules`) （包括 PowerShell Core 模块），请使用 "以 **管理员身份运行** " 选项启动 powershell。
> 例如：`Start-Process pwsh.exe -Verb RunAs`。

## 示例

### 示例1：为所有模块更新帮助文件

`Update-Help`Cmdlet 将为支持可更新帮助的已安装模块更新帮助文件。 用户界面 (UI) 区域性语言是在操作系统中设置的。

```powershell
Update-Help
```

### 示例2：更新指定模块的帮助文件

`Update-Help`Cmdlet 仅更新以 **Microsoft PowerShell** 开头的模块名称的帮助文件。

```powershell
Update-Help -Module Microsoft.PowerShell*
```

### 示例3：更新不同语言的帮助文件

该 `Update-Help` cmdlet 将为所有模块更新日语 (ja-jp) 和英语 (en-us) 帮助文件。

如果某个模块没有为指定的 UI 区域性提供帮助文件，则会为该模块和 UI 区域性显示错误消息。 在此示例中，错误消息指示找不到模块的 **Microsoft PowerShell****帮助文件**。

```powershell
Update-Help -UICulture ja-JP, en-US
```

```Output
Update-Help : Failed to update Help for the module(s) 'Microsoft.PowerShell.Utility' with UI culture(s) {ja-JP}
No UI culture was found that matches the following pattern: ja-JP.
```

### 示例4：从文件共享更新多台计算机上的帮助文件

在此示例中，将从 internet 下载更新的帮助文件，并将其保存在文件共享中。 需要用户凭据才能访问文件共享和安装更新。 使用文件共享时，可以更新防火墙后面或未连接到 internet 的计算机。

```powershell
Save-Help -DestinationPath \\Server01\Share\PSHelp -Credential Domain01\Admin01
Invoke-Command -ComputerName (Get-Content Servers.txt) -ScriptBlock {
     Update-Help -SourcePath \\Server01\Share\PSHelp -Credential Domain01\Admin01
}
```

此 `Save-Help` 命令将为支持可更新帮助的所有模块下载最新的帮助文件。
**DestinationPath** 参数将文件保存在 `\\Server01\Share\PSHelp` 文件共享中。 **Credential** 参数指定有权访问该文件共享的用户。

`Invoke-Command`Cmdlet `Update-Help` 在多台计算机上运行远程命令。 **ComputerName** 参数从 **Servers.txt** 文件中获取远程计算机的列表。 **ScriptBlock** 参数运行 `Update-Help` 命令，并使用 **SourcePath** 参数指定包含更新的帮助文件的文件共享。 **Credential** 参数指定可以访问文件共享的用户并运行远程 `Update-Help` 命令。

### 示例5：获取已更新的帮助文件的列表

`Update-Help`Cmdlet 可为指定的模块更新帮助。 Cmdlet 使用 **Verbose** common 参数显示已更新的帮助文件的列表。 您可以使用 **Verbose** 来查看特定模块的所有帮助文件或帮助文件的输出。

如果没有 **详细** 参数， `Update-Help` 则不会显示命令的结果。 **详细** 参数输出用于验证是否已更新帮助文件或安装了最新版本。

```powershell
Update-Help -Module Microsoft.PowerShell.Utility -Verbose
```

### 示例6：查找支持可更新帮助的模块

此示例列出了支持可更新帮助的模块。 该命令使用模块的 **HelpInfoUri** 属性来标识支持可更新帮助的模块。 **HelpInfoUri** 属性包含在运行 cmdlet 时重定向的地址 `Update-Help` 。

```powershell
Get-Module -ListAvailable | Where-Object -Property HelpInfoUri
```

```output
   Directory: C:\program files\powershell\6\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   6.1.0.0    CimCmdlets                          Core      {Get-CimAssociatedInstance... }
Manifest   1.2.2.0    Microsoft.PowerShell.Archive        Desk      {Compress-Archive... }
Manifest   6.1.0.0    Microsoft.PowerShell.Diagnostics    Core      {Get-WinEvent, New-WinEvent}

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, ... }
Script     1.0.0.0    AssignedAccess                      Core,Desk {Clear-AssignedAccess, ... }
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, ... }
```

### 示例7：清点已更新的帮助文件

在此示例中，该脚本将 `Get-UpdateHelpVersion.ps1` 为每个模块的可更新帮助文件及其版本号创建清单。

该脚本通过使用模块的 **HelpInfoUri** 属性来标识支持可更新帮助的模块。 对于支持可更新帮助的模块，该脚本将查找并分析帮助信息文件 ( * helpinfo.xml) 以查找最新的版本号。

该脚本使用 **PSCustomObject** 类和哈希表来创建自定义输出对象。

```powershell
# Get-UpdateHelpVersion.ps1
Param(
    [parameter(Mandatory=$False)]
    [String[]]
    $Module
)
$HelpInfoNamespace = @{helpInfo='http://schemas.microsoft.com/powershell/help/2010/05'}

if ($Module) { $Modules = Get-Module $Module -ListAvailable | where {$_.HelpInfoUri} }
else { $Modules = Get-Module -ListAvailable | where {$_.HelpInfoUri} }

foreach ($mModule in $Modules)
{
    $mDir = $mModule.ModuleBase

    if (Test-Path $mdir\*helpinfo.xml)
    {
        $mName=$mModule.Name
        $mNodes = dir $mdir\*helpinfo.xml -ErrorAction SilentlyContinue |
            Select-Xml -Namespace $HelpInfoNamespace -XPath "//helpInfo:UICulture"
        foreach ($mNode in $mNodes)
        {
            $mCulture=$mNode.Node.UICultureName
            $mVer=$mNode.Node.UICultureVersion

            [PSCustomObject]@{"ModuleName"=$mName; "Culture"=$mCulture; "Version"=$mVer}
        }
    }
}
```

```Output
ModuleName                              Culture                                 Version
----------                              -------                                 -------
ActiveDirectory                         en-US                                   3.0.0.0
ADCSAdministration                      en-US                                   3.0.0.0
ADCSDeployment                          en-US                                   3.0.0.0
ADDSDeployment                          en-US                                   3.0.0.0
ADFS                                    en-US                                   3.0.0.0
```

## PARAMETERS

### -Credential

指定有权访问由 **SourcePath** 指定的文件系统位置的用户的凭据。 仅当命令中使用了 **SourcePath** 或 **LiteralPath** 参数时，此参数才有效。

**Credential** 参数使你可以 `Update-Help` 在远程计算机上运行具有 **SourcePath** 参数的命令。 通过提供显式凭据，你可以在远程计算机上运行该命令并访问第三台计算机上的文件共享，而不会遇到 "拒绝访问" 错误或使用 CredSSP 身份验证委派凭据。

键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。 如果键入用户名，系统会提示输入密码。

凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指示此 cmdlet 不遵循每日一次的限制，跳过版本检查，并下载超出 1 GB 限制的文件。

如果没有此参数，则 `Update-Help` 每24小时运行一次。 下载内容限制为每个模块 1 GB 的未压缩内容，并且仅当比计算机上的现有文件更新时，才会安装帮助文件。

每日一次限制可以保护托管帮助文件的服务器，并使你能够将 `Update-Help` 命令添加到 PowerShell 配置文件，而不会导致重复连接或下载的资源成本。

若要在没有 **Force** 参数的情况下，为多个 UI 区域性中的模块更新帮助，请将所有 UI 区域性包括在相同的命令中，例如：

`Update-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

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

### -FullyQualifiedModule

指定名称以 **ModuleSpecification** 对象的形式指定的模块。
ModuleSpecification 构造函数的 "备注" 部分中介绍了这些模块 [ (Hashtable) ](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)。

例如， **FullyQualifiedModule** 参数接受以下格式指定的模块名称：

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

或

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.`

**ModuleName** 和 **ModuleVersion** 是必需的，但 **Guid** 是可选的。

不能在与 **Module** 参数相同的命令中指定 **FullyQualifiedModule** 参数。

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

### -LiteralPath

指定更新的帮助文件的文件夹，而不是从 internet 下载。 如果已使用 `Save-Help` cmdlet 将帮助文件下载到目录，请使用此参数或 SourcePath。

你可以通过管道将目录对象（如从 `Get-Item` 或 `Get-ChildItem` cmdlet）通过管道进行管道 `Update-Help` 。

与 **SourcePath** 的值不同， **LiteralPath** 的值严格按照所键入的形式使用。 不会将任何字符解释为通配字符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Module

为指定模块更新帮助。 在以逗号分隔的列表中输入一个或多个模块名称或名称模式，或指定在每行上列出一个模块名称的文件。 允许使用通配符。 可以通过管道将模块从 `Get-Module` cmdlet 布线到 `Update-Help` cmdlet。

你指定的模块必须安装在计算机上，但不必导入到当前会话中。 您可以指定会话中的任何模块或在环境变量中列出的位置中安装的任何模块 `$env:PSModulePath` 。

值为 `*` (所有) 尝试为计算机上安装的所有模块更新帮助。
包括不支持可更新帮助的模块。 当该命令遇到不支持可更新帮助的模块时，此值可能会生成错误。 而是不 `Update-Help` 带参数运行。

Cmdlet 的 **module** 参数 `Update-Help` 不接受模块文件或模块清单文件的完整路径。 若要为不在某个位置的模块更新帮助 `$env:PSModulePath` ，请在运行该命令之前将模块导入到当前会话中 `Update-Help` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Recurse

在指定的目录中执行对帮助文件的递归搜索。 仅当命令使用 **SourcePath** 参数时，此参数才有效。

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

### -Scope

指定更新帮助的系统范围。 在 **AllUsers** 范围更新需要对 Windows 系统具有管理权限。 此 `-Scope` 参数是在 PowerShell Core 版本6.1 中引入的。

**CurrentUser** 是 PowerShell 6.1 和更高版本中帮助文件的默认作用域。 可以指定 **AllUsers** ，为所有用户安装或更新帮助。 `sudo`若要更新所有用户的帮助，需要在 Unix 系统上执行权限。 例如： `sudo pwsh -c Update-Help`

可接受的值如下：

- CurrentUser
- AllUsers

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourcePath

指定一个文件系统文件夹，在该文件夹中 `Update-Help` 获取更新的帮助文件，而不是从 internet 下载它们。 输入文件夹的路径。 不要指定文件名或文件扩展名。 你可以通过管道将一个文件夹（例如，一个 `Get-Item` ）从或 `Get-ChildItem` cmdlet 到 `Update-Help` 。

默认情况下，会 `Update-Help` 从 internet 下载更新的帮助文件。 使用该 `Save-Help` cmdlet 将已更新的帮助文件下载到目录时，请使用 SourcePath。

若要为 **SourcePath** 指定默认值，请参阅 " **组策略**" 和 " **计算机配置**"，并 **设置 update-help 的默认源路径**。 此组策略设置可防止用户使用 `Update-Help` 从 internet 下载帮助文件。
有关详细信息，请参阅 [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md)。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UICulture

指定 `Update-Help` 使用来获取更新的帮助文件的 UI 区域性值。 输入一个或多个语言代码，例如 **es**、包含区域性对象的变量或用于获取区域性对象的命令，如 `Get-Culture` 或 `Get-UICulture` 命令。 不允许使用通配符，并且你不能提交部分语言代码，例如 **de**。

默认情况下， `Update-Help` 将在为操作系统设置的 UI 区域性中获取帮助文件。 如果指定 **UICulture** 参数，则 `Update-Help` 仅为指定的 UI 区域性查找帮助。

> [!NOTE]
> Ubuntu 18.04 将默认区域设置更改为 `C.UTF.8` ，这是无法识别的 UI 区域性。 `Update-Help` 如果将此参数与支持的区域设置（如）一起使用，则会以静默方式下载帮助 `en-US` 。 这可能发生在使用不受支持的值的任何平台上。

仅当模块为指定的 UI 区域性提供帮助文件时，使用 **UICulture** 参数的命令才会成功。 如果命令由于指定的 UI 区域性不受支持而失败，将显示一条错误消息。

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredentials

指示 `Update-Help` 使用当前用户的凭据运行命令，包括 internet 下载。 默认情况下，在没有显式凭据的情况下运行该命令。

仅当 web 下载使用 NT LAN Manager (NTLM) 、协商或基于 Kerberos 的身份验证时，此参数才有效。

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

显示运行该 cmdlet 时会发生什么情况。 cmdlet 未运行。

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

### System.IO.DirectoryInfo

你可以通过管道将目录路径传递给 `Update-Help` 。

### System.Management.Automation.PSModuleInfo

可以通过管道将模块对象从 `Get-Module` cmdlet 传递给 `Update-Help` 。

## 输出

### 无

`Update-Help` 不会生成任何输出。

## 注释

若要更新 PowerShell 核心模块的帮助，其中包含与 PowerShell 一起安装的命令或目录中的任何模块 `$PSHOME\Modules` ，请以 **管理员身份运行** 选项来启动 powershell。

只有计算机上 Administrators 组的成员才能为 PowerShell 核心模块、与 PowerShell 一起安装的命令和文件夹中的模块更新帮助 `$PSHOME\Modules` 。 如果你没有更新帮助文件的权限，你可以在线阅读帮助文件。 例如，`Get-Help Update-Help -Online`。

模块是可更新帮助的最小单位。 不能为特定 cmdlet 更新帮助。 若要查找包含特定 cmdlet 的模块，请使用该 cmdlet 的 **ModuleName** 属性 `Get-Command` ，例如 `(Get-Command Update-Help).ModuleName` 。

由于帮助文件安装在模块目录中，因此 `Update-Help` cmdlet 只能为计算机上安装的模块安装更新的帮助文件。 但是，该 `Save-Help` cmdlet 可以为未安装在计算机上的模块保存帮助。

如果找 `Update-Help` 不到模块的更新帮助文件，或者找不到指定语言的更新帮助，它将以无提示方式继续，而不显示错误消息。 若要查看状态和进度的详细信息，请使用 **Verbose** 参数。

`Update-Help`Cmdlet 是在 Windows PowerShell 3.0 中引入的。 它在早期版本的 PowerShell 中不起作用。 在同时具有 Windows PowerShell 2.0 和 Windows PowerShell 3.0 的计算机上，使用 `Update-Help` Windows powershell 3.0 会话中的 cmdlet 来下载和更新帮助文件。 Windows PowerShell 2.0 和 Windows PowerShell 3.0 都提供帮助文件。

`Update-Help`和 `Save-Help` cmdlet 使用以下端口下载帮助文件：针对 HTTP 使用端口80，为 HTTPS 使用端口443。

`Update-Help` 支持所有模块和 PowerShell Core 管理单元。它不支持任何其他管理单元。

若要为环境变量中未列出的位置的模块更新帮助 `$env:PSModulePath` ，请将模块导入到当前会话中，然后运行 `Update-Help` 命令。 `Update-Help`不带参数运行，或使用 **module** 参数来指定模块名称。 和 cmdlet 的 **module** 参数 `Update-Help` `Save-Help` 不接受模块文件或模块清单文件的完整路径。

所有模块都支持可更新帮助。 有关在创作的模块中支持可更新帮助的说明，请参阅 [支持可更新帮助](/powershell/scripting/developer/module/supporting-updatable-help)。

`Update-Help` `Save-Help` (Windows PE) Windows 预安装环境上不支持和 cmdlet。

## 相关链接

[Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)

[Get-Help](Get-Help.md)

[Get-Module](Get-Module.md)

[Get-UICulture](../Microsoft.PowerShell.Utility/Get-UICulture.md)

[Start-Job](Start-Job.md)

[Save-Help](Save-Help.md)
