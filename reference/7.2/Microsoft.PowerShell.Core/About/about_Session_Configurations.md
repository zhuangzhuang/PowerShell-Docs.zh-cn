---
description: 介绍会话配置，用于确定可远程连接到计算机的用户以及他们可以运行的命令。
Locale: en-US
ms.date: 12/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configurations
ms.openlocfilehash: 4c6d5494f49bc271a7fe128fbce7b27c9d1f675f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603821"
---
# <a name="about-session-configurations"></a>关于会话配置

## <a name="short-description"></a>简短说明
介绍会话配置，用于确定可远程连接到计算机的用户以及他们可以运行的命令。

## <a name="long-description"></a>详细说明

会话配置（也称为 "终结点"）是本地计算机上的一组设置，用于定义在远程或本地用户连接到本地计算机上的 PowerShell 时所创建的 PowerShell 会话的环境。

计算机管理员可以使用会话配置来保护计算机，并为连接到计算机的用户定义自定义环境。

管理员还可以使用会话配置来确定连接到计算机所需的权限。 默认情况下，只有 Administrators 组的成员才有权使用会话配置进行远程连接，但你可以更改默认设置，以允许所有用户或所选用户远程连接到你的计算机。

从 PowerShell 3.0 开始，你可以使用会话配置文件来定义会话配置的元素。 使用此功能可以轻松地自定义会话，而无需编写代码和发现会话配置的属性。 若要创建会话配置文件，请使用 New-PSSessionConfiguration cmdlet。 有关会话配置文件的详细信息，请参阅 [about_Session_Configuration_Files](about_Session_Configuration_Files.md)。

会话配置是 Web 服务的一项功能，用于管理 (WS-MANAGEMENT) 的 PowerShell 远程处理。 仅当你使用新的-PSSession、Invoke 命令或 Enter-PSSession cmdlet 连接到远程计算机时，才使用它们。

注意：若要管理会话配置，请以 "以管理员身份运行" 选项启动 PowerShell。

关于会话配置

每个 PowerShell 会话都使用会话配置。 这包括你使用 New-PSSession 或 Enter-PSSession cmdlet 创建的持久会话，以及 PowerShell 在你使用使用基于 WS-MANAGEMENT 的远程处理技术（如调用-Command）的 cmdlet 的 ComputerName 参数时创建的临时会话。

管理员可以使用会话配置来保护计算机的资源，并为连接到计算机的用户创建自定义环境。 例如，你可以使用会话配置来限制计算机在会话中接收的对象的大小，定义会话的语言模式，以及指定会话中可用的 cmdlet、提供程序和功能。

通过配置会话配置的安全描述符，你可以确定哪些用户可以使用会话配置来连接到计算机。
用户必须具有会话配置的 "执行" 权限才能在会话中使用该会话配置。 如果用户没有在计算机上使用任何会话配置所需的权限，则该用户无法远程连接到该计算机。

默认情况下，只有计算机的管理员才有权使用默认的会话配置。 但是，可以更改安全描述符，以允许所有人、没有用户或仅选定的用户使用计算机上的会话配置。

内置会话配置

PowerShell 3.0 包括名为 Microsoft PowerShell 和 Microsoft PowerShell 的内置会话配置。 在运行64位版本 Windows 的计算机上，PowerShell 还提供 Microsoft.powershell32，即32位会话配置。

默认情况下，Microsoft PowerShell 会话配置用于会话，即，当创建会话的命令不包含新的 PSSession、ConfigurationName 或 Invoke-Command cmdlet 的参数时。

默认会话配置的安全描述符仅允许本地计算机上 Administrators 组的成员使用这些配置。 因此，只有 Administrators 组的成员才能远程连接到计算机，除非更改默认设置。

您可以使用 $PSSessionConfigurationName 首选项变量来更改默认会话配置。 有关详细信息，请参阅 about_Preference_Variables。

查看本地计算机上的会话配置

若要获取本地计算机上的会话配置，请使用 Get-PSSessionConfiguration cmdlet。

例如，键入：

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property Name, Permission

Name       : microsoft.powershell
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell.workflow
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell32
Permission : BUILTIN\Administrators AccessAllowed
```

会话配置对象在 PowerShell 3.0 中展开，以显示使用会话配置文件配置的会话配置的属性。

例如，若要查看会话配置对象的所有属性，请键入：

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property *
```

你还可以在 PowerShell 中使用 WSMan 提供程序来查看会话配置。 WSMan 提供程序在会话中创建 WSMAN：驱动器。

在 WSMAN：驱动器中，会话配置在 "插件" 节点中。  (所有会话配置都在 "插件" 节点中，但在 "插件" 节点中有一些不是会话配置的项。 ) 

例如，若要查看本地计算机上的会话配置，请键入：

```powershell
PS C:> dir wsman:\localhost\plugin\microsoft*

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

查看远程计算机上的会话配置

若要查看远程计算机上的会话配置，请使用 Connect-WSMan cmdlet 将远程计算机的备注添加到本地计算机上的 WSMAN：驱动器中，然后使用 WSMAN：驱动器查看会话配置。

例如，以下命令将 Server01 远程计算机的节点添加到本地计算机上的 WSMAN：驱动器。

```powershell
PS C:> Connect-WSMan server01.corp.fabrikam.com
```

完成该命令后，可以导航到 Server01 计算机的节点，以查看会话配置。

例如：

```powershell
PS C:> cd wsman:

PS WSMan:> dir

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01.corp.fabrikam.com                    Container

PS WSMan:> dir server01\plugin\

WSManConfig: Microsoft.WSMan.Management\WSMan::server01.corp.fabrikam.com\Pl
ugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

更改会话配置的安全描述符

在 Windows Server 2012 和更新版本的 Windows Server 中，默认情况下为远程用户启用内置会话配置。 在其他受支持的 Windows 版本中，你必须将会话配置的安全描述符更改为允许远程访问。

若要启用对计算机上的会话配置的远程访问，请使用 Enable-PSRemoting cmdlet。 此 cmdlet 将创建两个会话配置：

- 名称定义为： "PowerShell"。 + "当前 PowerShell 版本"
- 对于任何特定 PowerShell 版本，名称为 "untied"。

另外，默认情况下，只有计算机上 Administrators 组的成员才具有对默认会话配置的 Execute 权限，但你可以更改默认会话配置和你创建的任何会话配置上的安全描述符。

若要授予其他用户远程连接到计算机的权限，请使用 Set-PSSessionConfiguration cmdlet 将这些用户的 "执行" 权限添加到 Microsoft PowerShell 和 Microsoft.powershell32 会话配置的安全描述符中。

例如，下面的命令将打开一个属性页，您可以使用该属性页更改 Microsoft PowerShell 默认会话配置的安全描述符。

```powershell
Set-PSSessionConfiguration -name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

若要拒绝每个人对计算机上所有会话配置的权限，请使用 Disable-PSSessionConfiguration cmdlet。 例如，以下命令禁用计算机上的默认会话配置。

```powershell
PS C:> Disable-PSSessionConfiguration -Name Microsoft.PowerShell
```

若要防止远程用户连接到计算机，但允许本地用户进行连接，请使用 Disable-PSRemoting cmdlet。 Disable-PSRemoting 将 "Network_Deny_All" 条目添加到计算机上的所有会话配置。

```powershell
PS C:> Disable-PSRemoting
```

若要允许远程用户使用计算机上的所有会话配置，请使用 Enable-PSRemoting 或 Enable-PSSessionConfiguration cmdlet。 例如，以下命令启用对内置会话配置的远程访问。

```powershell
PS C:> Enable-PSSessionConfiguration -name Microsoft.Power*
```

若要对会话配置的安全描述符进行其他更改，请使用 Set-PSSessionConfiguration cmdlet。 使用 SecurityDescriptorSDDL 参数提交 SDDL 字符串值。 使用 ShowSecurityDescriptorUI 参数显示可帮助你创建新 SDDL 的 "用户界面" 属性表。

例如：

```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

创建新的会话配置

若要在本地计算机上创建新的会话配置，请使用 Register-PSSessionConfiguration cmdlet。 若要定义新的会话配置，可以使用 c # 程序集、PowerShell 脚本和 Register-PSSessionConfiguration cmdlet 的参数。

例如，以下命令将创建一个与 Microsoft PowerShell 会话配置相同的会话配置，只不过它会将从远程命令收到的数据限制为 20 mb (MB) 。  (默认值为 50 MB) 。

```powershell
Register-PSSessionConfiguration -Name NewConfig `
  -MaximumReceivedDataSizePerCommandMB 20
```

当你创建会话配置时，你可以使用其他会话配置 cmdlet 来管理它，并显示在 WSMAN：驱动器中。

有关详细信息，请参阅 Set-pssessionconfiguration。

删除会话配置

若要从本地计算机中删除会话配置，请使用 Unregister-PSSessionConfiguration cmdlet。 例如，以下命令将从计算机中删除 Newconfig.json 会话配置。

```powershell
PS C:> Unregister-PSSessionConfiguration -Name NewConfig
```

有关详细信息，请参阅 Set-pssessionconfiguration。

还原会话配置

若要还原 (取消注册) 意外删除的默认会话配置，请使用 Enable-PSRemoting cmdlet。

Enable-PSRemoting cmdlet 将重新创建计算机上不存在的所有默认会话配置。 它不会覆盖或更改现有会话配置的属性值。

若要还原默认会话配置的原始属性值，请使用 Unregister-PSSessionConfiguration 删除会话配置，然后使用 Enable-PSRemoting cmdlet 重新创建它。

选择会话配置

若要为会话选择特定的会话配置，请使用新的-PSSession、Enter-PSSession 或 ConfigurationName 参数。

例如，此命令使用 New-PSSession cmdlet 来启动 Server01 计算机上的 PSSession。 该命令使用 ConfigurationName 参数来选择 Server01 计算机上的 WithProfile 配置。

```powershell
PS C:> New-PSSession -ComputerName Server01 -ConfigurationName WithProfile
```

仅当当前用户有权使用 WithProfile 会话配置或可以提供具有所需权限的用户的凭据时，此命令才会成功。

你还可以使用 $PSSessionConfigurationName 首选项变量来更改计算机上的默认会话配置。 有关 $PSSessionConfigurationName 首选项变量的详细信息，请参阅 about_Preference_Variables。

## <a name="keywords"></a>字

about_Endpoints about_SessionConfigurations

## <a name="see-also"></a>另请参阅

[about_Preference_Variables](about_Preference_Variables.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Session_Configuration_Files](about_Session_Configuration_Files.md)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Disable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[Enable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[Get-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[New-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[Register-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[Set-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[Test-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[Unregister-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

