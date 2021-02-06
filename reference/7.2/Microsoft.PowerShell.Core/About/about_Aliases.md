---
description: 介绍如何在 PowerShell 中使用 cmdlet 和命令的备用名称。
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_aliases?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Aliases
ms.openlocfilehash: e8b93e2b687e779048784c1eedb15fa53972b8b0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598496"
---
# <a name="about-aliases"></a>关于别名

## <a name="short-description"></a>简短说明
介绍如何在 PowerShell 中使用 cmdlet 和命令的备用名称。

## <a name="long-description"></a>详细说明

别名是 cmdlet 或命令元素（例如函数、脚本、文件或可执行文件）的替代名称或昵称。 可以在任何 PowerShell 命令中使用别名，而不是命令名。

若要创建别名，请使用 New-Alias cmdlet。 例如，以下命令为 cmdlet 创建 "气体" 别名 `Get-AuthenticodeSignature` ：

```powershell
New-Alias -Name gas -Value Get-AuthenticodeSignature
```

为 cmdlet 名称创建别名后，可以使用别名，而不是 cmdlet 名称。 例如，若要获取 SqlScript.ps1 文件的 Authenticode 签名，请键入：

```powershell
Get-AuthenticodeSignature SqlScript.ps1
```

或者键入：

```powershell
gas SqlScript.ps1
```

如果创建 "word" 作为 Microsoft Office Word 的别名，则可以键入 "word" 而不是以下内容：

```powershell
"C:\Program Files\Microsoft Office\Office11\Winword.exe"
```

## <a name="built-in-aliases"></a>内置别名

PowerShell 包括一组内置别名，其中包括用于 Set-Location cmdlet 的 "cd" 和 "chdir"，以及 Get-ChildItem cmdlet 的 "ls" 和 "dir"。

若要获取计算机上的所有别名（包括内置的别名），请键入：

```powershell
Get-Alias
```

## <a name="alias-cmdlets"></a>别名 CMDLET

PowerShell 包含以下 cmdlet，这些 cmdlet 设计用于使用别名：

- `Get-Alias` -获取当前会话中的所有别名。
- `New-Alias` -创建新别名。
- `Set-Alias` -创建或更改别名。
- `Export-Alias` -将一个或多个别名导出到文件。
- `Import-Alias` -将别名文件导入 PowerShell。

有关 cmdlet 的详细信息，请键入：

```powershell
Get-Help <cmdlet-Name> -Detailed
```

例如，键入：

```powershell
Get-Help Export-Alias -Detailed
```

## <a name="creating-an-alias"></a>创建别名

若要创建新别名，请使用 New-Alias cmdlet。 例如，若要创建 Get-help 的 "gh" 别名，请键入：

```powershell
New-Alias -Name gh -Value Get-Help
```

您可以使用命令中的别名，就像使用完整的 cmdlet 名称一样，可以将别名用于参数。

例如，若要获取 Get-WmiObject cmdlet 的详细帮助，请键入：

```powershell
Get-Help Get-WmiObject -Detailed
```

或者键入：

```powershell
gh Get-WmiObject -Detailed
```

## <a name="saving-aliases"></a>保存别名

你创建的别名仅保存在当前会话中。 若要在其他会话中使用别名，请将别名添加到 PowerShell 配置文件。 或者使用 Export-Alias cmdlet 将别名保存到文件。

有关详细信息，请键入：

```powershell
Get-Help about_Profiles
```

## <a name="getting-aliases"></a>获取别名

若要获取当前会话中的所有别名（包括内置别名、PowerShell 配置文件中的别名以及在当前会话中创建的别名），请键入：

```powershell
Get-Alias
```

若要获取特定别名，请使用 Get-Alias cmdlet 的 Name 参数。 例如，若要获取以 "p" 开头的别名，请键入：

```powershell
Get-Alias -Name p*
```

若要获取特定项的别名，请使用定义参数。 例如，若要获取 Get-ChildItem cmdlet 类型的别名：

```powershell
Get-Alias -Definition Get-ChildItem
```

### <a name="get-alias-output"></a>获取别名输出

Get-Alias 仅返回一种类型的对象，System.management.automation.aliasinfo) 的 System.management.automation.aliasinfo (对象。 不包含连字符的别名名称（如 "cd"）将按以下格式显示：

```powershell
Get-Alias ac
```

```Output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Alias           ac -> Add-Content
```

这样，就可以非常快捷地获取所需的信息。

基于箭头的别名名称格式不适用于含有连字符的别名。 它们可能是 cmdlet 和函数（而不是典型的缩写或昵称）的首选替代名称，并且作者可能不希望它们明显。

## <a name="alternate-names-for-commands-with-parameters"></a>带参数的命令的替换名称

可以为 cmdlet、脚本、函数或可执行文件指定别名。 不能为命令及其参数分配别名。 例如，可以将别名分配给该 `Get-Eventlog` cmdlet，但不能为该命令分配别名 `Get-Eventlog -LogName System` 。

你可以创建包含命令的函数。 若要创建函数，请键入单词 "function"，后跟函数的名称。 键入命令，并将其括在大括号中， ({}) 。

例如，以下命令将创建 syslog 函数。 此函数表示 `Get-Eventlog -LogName System` 命令：

```powershell
function Get-SystemEventlog {Get-Eventlog -LogName System}
Set-Alias -Name syslog -Value Get-SystemEventlog
```

现在可以键入 "syslog" 而不是命令。 而且，你可以为新函数创建别名。

有关函数的详细信息，请键入：

```powershell
Get-Help about_Functions
```

## <a name="alias-objects"></a>别名对象

PowerShell 别名由作为 System.management.automation.aliasinfo 类的实例的对象表示。 有关此类对象的详细信息，请参阅 PowerShell SDK 中的 [System.management.automation.aliasinfo 类][aliasinfo] 。

若要查看 alias 对象的属性和方法，请获取别名。
然后，将它们传递给 Get-Member cmdlet。 例如：

```powershell
Get-Alias | Get-Member
```

若要查看特定别名的属性值（如 `dir` 别名），请获取别名。 然后，通过管道将它传递给 Format-List cmdlet。 例如，以下命令将获取 "dir" 别名。 接下来，该命令通过管道将别名传输到 Format-List cmdlet。 然后，该命令将 Format-List 的属性参数与通配符 (\*) ，以显示该别名的所有属性 `dir` 。 以下命令执行这些任务：

```powershell
Get-Alias -Name dir | Format-List -Property *
```

## <a name="powershell-alias-provider"></a>PowerShell 别名提供程序

PowerShell 包含别名提供程序。 别名提供程序允许你查看 PowerShell 中的别名，就好像它们位于文件系统驱动器上一样。

别名提供程序公开 Alias：驱动器。 若要进入 Alias：驱动器，请键入：

```powershell
Set-Location Alias:
```

若要查看驱动器的内容，请键入：

```powershell
Get-ChildItem
```

若要查看另一 PowerShell 驱动器中的驱动器内容，请以驱动器名称开头。 包括冒号 (： ) 。 例如：

```powershell
Get-ChildItem -Path Alias:
```

若要获取有关特定别名的信息，请键入驱动器名称和别名。 或者，键入名称模式。 例如，若要获取以 "p" 开头的所有别名，请键入：

```powershell
Get-ChildItem -Path Alias:p*
```

有关 PowerShell 别名提供程序的详细信息，请键入：

```powershell
Get-Help Alias
```

## <a name="see-also"></a>另请参阅

- [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias)
- [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [Set-Alias](xref:Microsoft.PowerShell.Utility.Set-Alias)
- [Export-Alias](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [Import-Alias](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)
- [Get-PSDrive](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [about_functions](about_functions.md)
- [about_profiles](about_profiles.md)
- [about_providers](about_providers.md)

<!-- External links -->
[aliasinfo]: /dotnet/api/system.management.automation.aliasinfo
