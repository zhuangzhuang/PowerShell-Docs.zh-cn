---
description: 介绍会话配置文件，这些文件在会话配置中使用 (也称为终结点) ，用于定义使用会话配置的会话的环境。
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configuration_Files
ms.openlocfilehash: 1ed87e95b2ce823b5a887546545e1158630eabfb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597685"
---
# <a name="about-session-configuration-files"></a>关于会话配置文件

## <a name="short-description"></a>简短说明
介绍会话配置文件，这些文件在会话配置中使用 (也称为 "终结点" ) ，用于定义使用会话配置的会话的环境。

## <a name="long-description"></a>详细说明

"会话配置文件" 是文件扩展名为 .pssc 的文本文件，其中包含会话配置属性和值的哈希表。 您可以使用会话配置文件来设置会话配置的属性。 这样做将定义使用该会话配置的任何 PowerShell 会话的环境。

会话配置文件可以轻松地创建自定义会话配置，而无需使用复杂的 c # 程序集或脚本。

"会话配置" 或 "终结点" 是本地计算机设置的集合，用于确定用户可以在计算机上创建会话的情况。用户可以在这些会话中运行的命令;会话是否应作为特权虚拟帐户运行。 有关会话配置的详细信息，请参阅 [about_Session_Configurations](about_Session_Configurations.md)。

Windows PowerShell 2.0 中引入了会话配置，并且会话配置文件是在 Windows PowerShell 3.0 中引入的。 必须使用 Windows PowerShell 3.0 将会话配置文件包含在会话配置中。 但是，Windows PowerShell 2.0 (和更高版本的用户) 受会话配置中的设置影响。

## <a name="creating-custom-sessions"></a>创建自定义会话

通过在会话配置中指定会话属性，可以自定义 PowerShell 会话的许多功能。 您可以通过编写定义自定义运行空间的 c # 程序自定义会话，也可以使用会话配置文件来定义使用会话配置创建的会话的属性。 通常，使用会话配置文件比编写 c # 程序更容易。

你可以使用会话配置文件为高度可信的用户创建诸如功能齐全的会话等项目;锁定的会话，允许访问最少;为特定而设计的会话，仅包含这些任务所需的模块;和会话，无特权用户只能以特权帐户的身份运行特定命令。

除此之外，你还可以管理会话的用户是否可以使用 PowerShell 语言元素（如脚本块）或是否只能运行命令。 你可以管理可在会话中运行的 PowerShell 用户的版本;管理导入到会话中的模块。并管理用户可运行的 cmdlet、函数和别名。 使用 RoleDefinitions 字段时，可以基于组成员身份向用户授予会话中的不同功能。

有关 RoleDefinitions 以及如何定义此值的详细信息，请参阅 New-PSRoleCapabilityFile Cmdlet 的帮助主题。

## <a name="creating-a-session-configuration-file"></a>创建会话配置文件

创建会话配置文件的最简单方法是使用 New-PSSessionConfigurationFile cmdlet。 此 cmdlet 将生成一个使用正确语法和格式的文件，并自动验证许多配置文件属性值。

有关可以在会话配置文件中设置的属性的详细说明，请参阅 New-PSSessionConfigurationFile cmdlet 的帮助主题。

以下命令将创建一个使用默认值的会话配置文件。 生成的配置文件仅使用默认值，因为没有路径参数 (指定包含) 文件路径的其他参数：

```powershell
New-PSSessionConfigurationFile -Path .\Defaults.pssc
```

若要在默认文本编辑器中查看新的配置文件，请使用以下命令：

```powershell
Invoke-Item -Path .\Defaults.pssc
```

若要为用户可运行命令的会话创建会话配置，而不是使用 PowerShell 语言的其他元素，请键入：

```powershell
New-PSSessionConfigurationFile -LanguageMode NoLanguage
-Path .\NoLanguage.pssc
```

在上述命令中，将 LanguageMode 参数设置为 NoLanguage 可防止用户执行编写或运行脚本或使用变量等操作。

若要为用户仅能使用 Get cmdlet 的会话创建会话配置，请键入：

```powershell
New-PSSessionConfigurationFile -VisibleCmdlets Get-*
-Path .\GetSessions.pssc
```

在前面的示例中，将 VisibleCmdlets 参数设置为-* 可将用户限制为名称以字符串值 "Get-" 开头的 cmdlet。

若要为使用特权虚拟帐户（而不是用户凭据）运行的会话创建会话配置，请键入：

```powershell
New-PSSessionConfigurationFile -RunAsVirtualAccount
-Path .\VirtualAccount.pssc
```

若要为会话创建会话配置，其中在角色功能文件中指定了向用户显示的命令，请键入：

```powershell
New-PSSessionConfigurationFile -RoleDefinitions
@{ 'CONTOSO\User' = @{ RoleCapabilities = 'Maintenance' }}
-Path .\Maintenance.pssc
```

### <a name="using-a-session-configuration-file"></a>使用会话配置文件

你可以在创建会话配置时包括会话配置文件，也可以在添加时将文件添加到会话配置中。

若要在创建会话配置时包括会话配置文件，请使用 Register-PSSessionConfiguration cmdlet 的 Path 参数。

例如，以下命令在创建 NoLanguage 会话配置时使用 .pssc 文件。

```powershell
Register-PSSessionConfiguration -Name NoLanguage
-Path .\NoLanguage.pssc
```

启动新的 NoLanguage 会话时，用户将只能访问 PowerShell 命令。

若要将会话配置文件添加到现有会话配置，请使用 Set-PSSessionConfiguration cmdlet 和 Path 参数。 这会影响通过指定的会话配置创建的任何新会话。 请注意，Set-PSSessionConfiguration cmdlet 将更改会话本身，而不会修改会话配置文件。

例如，以下命令将 NoLanguage 文件添加到 LockedDown 会话配置中。

```powershell
Set-PSSessionConfiguration -Name LockedDown
-Path .\NoLanguage.pssc
```

当用户使用 LockedDown 会话配置创建会话时，他们将能够运行 cmdlet，但不能创建或使用变量、分配值或使用其他 PowerShell 语言元素。

以下命令使用 New-PSSession cmdlet 在计算机 Srv01 上创建一个会话，该会话使用 LockedDown 会话配置，并将对象引用保存到 $s 变量中的会话。 会话配置的 ACL (访问控制列表) 确定哪些用户可以使用它来创建会话。

```powershell
$s = New-PSSession -ComputerName Srv01
-ConfigurationName LockedDown
```

由于已将 NoLanguage 约束添加到 LockedDown 会话配置，因此 LockedDown 会话中的用户将只能运行 PowerShell 命令和 cmdlet。 例如，以下两个命令使用 Invoke-Command cmdlet 在 $s 变量中引用的会话中运行命令。 第一个命令将运行 Get-UICulture cmdlet，并且不使用任何变量，因此将成功。 第二个命令获取 $PSUICulture 变量的值失败。

```
Invoke-Command -Session $s {Get-UICulture}
en-US

Invoke-Command -Session $s {$PSUICulture}
The syntax is not supported by this runspace. This might be
because it is in no-language mode.
+ CategoryInfo          : ParserError: ($PSUICulture:String) [],
ParseException
+ FullyQualifiedErrorId : ScriptsNotAllowed
```

## <a name="editing-a-session-configuration-file"></a>编辑会话配置文件

除了将 runasvirtualaccount 设置和 RunAsVirtualAccountGroups 之外的会话配置中的所有设置都可以通过编辑会话配置使用的会话配置文件进行修改。 为此，请首先查找会话配置文件的活动副本。

使用会话配置中的会话配置文件时，PowerShell 会创建会话配置文件的活动副本，并将其存储在 \$ \\ 本地计算机上的 pshome SessionConfig 目录中。

会话配置文件的活动副本的位置存储在会话配置对象的 ConfigFilePath 属性中。

以下命令将获取 NoLanguage 会话配置的会话配置文件的位置。

```powershell
(Get-PSSessionConfiguration -Name NoLanguage).ConfigFilePath
```

该命令返回类似于以下内容的文件路径：

```
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

可以在任何文本编辑器中编辑 .pssc 文件。 文件保存后，任何使用会话配置的新会话都将使用该文件。

如果需要修改将 runasvirtualaccount 设置或 RunAsVirtualAccountGroups 设置，则必须取消注册会话配置，并重新注册包含已编辑值的会话配置文件。

## <a name="testing-a-session-configuration-file"></a>测试会话配置文件

使用 Test-PSSessionConfigurationFile cmdlet 测试手动编辑的会话配置文件。 这一点很重要：如果文件语法和值无效，用户将无法使用会话配置来创建会话。

例如，以下命令测试 NoLanguage 会话配置的活动会话配置文件。

```powershell
Test-PSSessionConfigurationFile -Path C:\WINDOWS\System32\
WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

如果配置文件中的语法和值有效 Test-PSSessionConfigurationFile 返回 True。 如果语法和值无效，则该 cmdlet 将返回 False。

你可以使用 Test-PSSessionConfigurationFile 来测试任何会话配置文件，包括 New-PSSessionConfiguration cmdlet 创建的文件。 有关详细信息，请参阅 Test-PSSessionConfigurationFile cmdlet 的帮助主题。

## <a name="removing-a-session-configuration-file"></a>删除会话配置文件

不能从会话配置中删除会话配置文件。
不过，您可以将该文件替换为使用默认设置的新文件。 这会有效地取消原始配置文件使用的设置。

若要替换会话配置文件，请创建新的会话配置文件，该文件使用默认设置，然后使用 Set-PSSessionConfiguration cmdlet 将自定义会话配置文件替换为新文件。

例如，以下命令将创建一个默认会话配置文件，然后在 NoLanguage 会话配置中替换活动会话配置文件。

```powershell
New-PSSessionConfigurationFile -Path .\Default.pssc
Set-PSSessionConfiguration -Name NoLanguage
-Path .\Default.pssc
```

完成这些命令后，NoLanguage 会话配置将 (为所有通过该会话配置创建的会话) 默认设置提供完全语言支持。

查看会话配置的属性使用会话配置文件表示会话配置的会话配置对象具有其他属性，使发现和分析会话配置变得更加容易。  (请注意，下面所示的类型名称包含格式化的视图定义。 ) 可以通过运行 Get-PSSessionConfiguration cmdlet 并将返回的数据通过管道传递给 Get-Member cmdlet 来查看属性：

```powershell
Get-PSSessionConfiguration NoLanguage | Get-Member
```

```output
TypeName: Microsoft.PowerShell.Commands.PSSessionConfigurationCommands
#PSSessionConfiguration

Name                          MemberType     Definition
----                          ----------     ----------
Equals                        Method         bool Equals(System.O...
GetHashCode                   Method         int GetHashCode()
GetType                       Method         type GetType()
ToString                      Method         string ToString()
Architecture                  NoteProperty   System.String Archit...
Author                        NoteProperty   System.String Author...
AutoRestart                   NoteProperty   System.String AutoRe...
Capability                    NoteProperty   System.Object[] Capa...
CompanyName                   NoteProperty   System.String Compan...
configfilepath                NoteProperty   System.String config...
Copyright                     NoteProperty   System.String Copyri...
Enabled                       NoteProperty   System.String Enable...
ExactMatch                    NoteProperty   System.String ExactM...
ExecutionPolicy               NoteProperty   System.String Execut...
Filename                      NoteProperty   System.String Filena...
GUID                          NoteProperty   System.String GUID=0...
ProcessIdleTimeoutSec         NoteProperty   System.String Proces...
IdleTimeoutms                 NoteProperty   System.String IdleTi...
lang                          NoteProperty   System.String lang=e...
LanguageMode                  NoteProperty   System.String Langua...
MaxConcurrentCommandsPerShell NoteProperty   System.String MaxCon...
MaxConcurrentUsers            NoteProperty   System.String MaxCon...
MaxIdleTimeoutms              NoteProperty   System.String MaxIdl...
MaxMemoryPerShellMB           NoteProperty   System.String MaxMem...
MaxProcessesPerShell          NoteProperty   System.String MaxPro...
MaxShells                     NoteProperty   System.String MaxShells
MaxShellsPerUser              NoteProperty   System.String MaxShe...
Name                          NoteProperty   System.String Name=N...
PSVersion                     NoteProperty   System.String PSVersion
ResourceUri                   NoteProperty   System.String Resour...
RunAsPassword                 NoteProperty   System.String RunAsP...
RunAsUser                     NoteProperty   System.String RunAsUser
SchemaVersion                 NoteProperty   System.String Schema...
SDKVersion                    NoteProperty   System.String SDKVer...
OutputBufferingMode           NoteProperty   System.String Output...
SessionType                   NoteProperty   System.String Sessio...
UseSharedProcess              NoteProperty   System.String UseSha...
SupportsOptions               NoteProperty   System.String Suppor...
xmlns                         NoteProperty   System.String xmlns=...
XmlRenderingType              NoteProperty   System.String XmlRen...
Permission                    ScriptProperty System.Object Permis...
```

通过这些属性可以轻松地搜索特定的会话配置。
例如，你可以使用 Set-executionpolicy 属性来查找使用 RemoteSigned 执行策略支持会话的会话配置。
请注意，由于 Set-executionpolicy 属性仅存在于使用会话配置文件的会话上，因此该命令可能不会返回所有合格的会话配置。

```powershell
Get-PSSessionConfiguration |
where {$_.ExecutionPolicy -eq "RemoteSigned"}
```

以下命令获取 RunAsUser 为 Exchange 管理员的会话配置。

```powershell
 Get-PSSessionConfiguration |
where {$_.RunAsUser -eq "Exchange01\Admin01"}
```

若要查看与配置关联的角色定义的相关信息，请使用 Get-PSSessionCapability cmdlet。 此 cmdlet 可用于确定特定用户在特定终结点中可用的命令和环境。

## <a name="notes"></a>注释

会话配置还支持称为 "空" 会话的会话类型。 空会话类型使你能够使用选定的命令创建自定义会话。 如果不将模块、函数或脚本添加到空会话中，则该会话将限于表达式，并且可能不是任何实际使用。 SessionType 属性告诉你是否正在使用空会话。

## <a name="see-also"></a>另请参阅

[about_Session_Configurations](about_Session_Configurations.md)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Disable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[Enable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[Get-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[New-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[Register-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[Set-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[Test-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[Unregister-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

[Get-PSSessionCapability](xref:Microsoft.PowerShell.Core.Get-PSSessionCapability)

[New-PSRoleCapabilityFile](xref:Microsoft.PowerShell.Core.New-PSRoleCapabilityFile)

