---
description: 介绍 PowerShell 提供程序如何提供对在命令行中无法轻松访问的数据和组件的访问。 数据以类似于文件系统驱动器的一致格式显示。
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: 6073ef13a6d0a02cded69073d7ffaef903a807ea
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596012"
---
# <a name="about-providers"></a>关于提供程序

## <a name="short-description"></a>简短说明
介绍 PowerShell 提供程序如何提供对在命令行中无法轻松访问的数据和组件的访问。
数据以类似于文件系统驱动器的一致格式显示。

## <a name="long-description"></a>长说明

PowerShell 提供程序是 .NET 程序，可提供对专用数据存储区的访问权限，便于查看和管理。 数据显示在驱动器中，你可以访问路径中的数据，就像在硬盘驱动器上访问数据一样。 你可以使用提供程序支持的任何内置 cmdlet 来管理提供程序驱动器中的数据。 而且，你可以使用专为数据设计的自定义 cmdlet。

提供程序还可以向内置 cmdlet 添加动态参数。 仅当你将 cmdlet 与提供程序数据结合使用时，这些参数才可用。

## <a name="built-in-providers"></a>内置提供程序

PowerShell 包含一组内置提供程序，可用于访问不同类型的数据存储区。

| 提供程序   |   驱动器 ()   |OutputType                                                    |
|----------- |------------ |--------------------------------------------------------------|
|Alias       |Alias:       |System.Management.Automation.AliasInfo                        |
|证书 |Cert:        |Microsoft.powershell.commands.x509storelocation。               |
|            |             |System.Security.Cryptography.X509Certificates.X509Certificate2|
|环境 |Env:         |DictionaryEntry                            |
|FileSystem  |C： ( * )        |System.IO.FileInfo                                            |
|            |             |System.IO.DirectoryInfo                                       |
|函数    |函数：    |System.web. FunctionInfo                     |
|注册表    |HKLM： HKCU：  |。 RegistryKey                                   |
|变量    |Variable:    |System.Management.Automation.PSVariable                       |
|WSMan       |WSMan：       |WSManConfigContainerElement。        |

 ( * ) 文件系统驱动器在每个系统上各不相同。

您还可以创建自己的 PowerShell 提供程序，并可以安装其他人开发的提供程序。 若要列出会话中可用的提供程序，请键入：

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a>安装和删除提供程序

提供程序通常通过 PowerShell 模块进行安装。 导入模块会将提供程序加载到会话中。 无法卸载内置提供程序。 你可以卸载其他模块加载的提供程序。

可以使用 cmdlet 从当前会话中卸载提供程序 `Remove-Module` 。 此 cmdlet 不会卸载提供程序，但它会使提供程序在会话中不可用。

你还可以使用 `Remove-PSDrive` cmdlet 从当前会话中删除任何驱动器。 驱动器上的这些数据不受影响，但该驱动器在该会话中不再可用。

## <a name="viewing-providers"></a>查看提供程序

若要查看计算机上的 PowerShell 提供程序，请键入：

```powershell
Get-PSProvider
```

输出会列出内置提供程序以及添加到会话中的提供程序。

## <a name="the-provider-cmdlets"></a>提供程序 cmdlet

以下 cmdlet 设计用于处理由任何提供程序公开的数据。 您可以使用相同的 cmdlet 来管理提供程序公开的不同类型的数据。 了解管理一个提供程序的数据后，可以对任何提供程序的数据使用相同的过程。

例如，cmdlet 会 `New-Item` 创建一个新项。 在 `C:` **FileSystem** 提供程序支持的驱动器中，可以使用 `New-Item` 来创建新的文件或文件夹。 在 **注册表** 提供程序支持的驱动器中，可以使用 `New-Item` 来创建新的注册表项。 在 `Alias:` 驱动器中，可以使用 `New-Item` 创建新别名。

有关以下任何 cmdlet 的详细信息，请键入：

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a>Get-childitem cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a>内容 Cmdlet

- [Add-Content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Clear-Content](xref:Microsoft.PowerShell.Management.Clear-Content)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a>项 Cmdlet

- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Rename-Item](xref:Microsoft.PowerShell.Management.Rename-Item)
- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a>Set-itemproperty cmdlet

- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Copy-ItemProperty](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Move-ItemProperty](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Rename-ItemProperty](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a>位置 cmdlet

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Pop-Location](xref:Microsoft.PowerShell.Management.Pop-Location)
- [Push-Location](xref:Microsoft.PowerShell.Management.Push-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a>路径 cmdlet

- [Join-Path](xref:Microsoft.PowerShell.Management.Join-Path)
- [Convert-Path](xref:Microsoft.PowerShell.Management.Convert-Path)
- [Split-Path](xref:Microsoft.PowerShell.Management.Split-Path)
- [Resolve-Path](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [Test-Path](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a>New-psdrive cmdlet

- [Get-PSDrive](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [New-PSDrive](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [Remove-PSDrive](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a>PSProvider Cmdlet

- [Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a>查看提供程序数据

提供程序的主要优点是，它以一种熟悉且一致的方式公开其数据。 数据显示模型是文件系统驱动器。

提供程序允许您查看、导航和更改数据存储中的项，就好像它们是文件系统中的数据一样。 数据存储区由它所支持的驱动器的名称访问。

此驱动器在 cmdlet 的默认显示中列出 `Get-PSProvider` ，但你可以使用 cmdlet 获取有关提供程序驱动器的信息 `Get-PSDrive` 。 例如，若要获取 Function：驱动器的所有属性，请键入：

```powershell
Get-PSDrive Function | Format-List *
```

与在文件系统驱动器上一样，你可以在提供程序驱动器中查看和移动数据。

若要查看提供程序驱动器的内容，请使用 Get-Item 或 Get-ChildItem cmdlet。 键入驱动器名称后跟一个冒号 (： ) 。 例如，若要查看 Alias：驱动器的内容，请键入：

```powershell
Get-Item alias:
```

可以通过在路径中包括驱动器名称，从另一个驱动器查看和管理任何驱动器中的数据。 例如，若要查看其他驱动器中的 HKLM：驱动器中的 HKLM\Software 注册表项，请键入：

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

若要打开驱动器，请使用 Set-Location cmdlet。 指定驱动器路径时，请记住冒号。 例如，若要将你的位置更改为 Cert：驱动器的根目录，请键入：

```powershell
Set-Location cert:
```

然后，若要查看 Cert：驱动器的内容，请键入：

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a>通过分层数据移动

与硬盘驱动器一样，你可以通过提供商驱动器进行移动。
如果数据排列在项中项的层次结构中，请使用反斜杠 (`\`) 来指示子项。 使用以下格式：

```
drive:\location\child-location\...
```

例如，若要将你的位置更改为 HKLM\Software 注册表项，请键入 Set-Location 命令，例如：

```powershell
Set-Location HKLM:\SOFTWARE\
```

如果完全限定名称中的任何元素包含空格，则必须将名称用双引号引起来 (`"`) 。 下面的示例显示了包含空格的完全限定路径。

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

还可以对位置使用相对引用。 一个点 (`.`) 表示当前位置。 例如，如果你在 `HKLM:\Software\Microsoft` 注册表项中，并且想要列出注册表项中的注册表子项 `HKLM:\Software\Microsoft\PowerShell` ，请键入以下命令：

```powershell
Get-ChildItem .\PowerShell
```

另外，双点 (`..`) 是指直接位于当前位置上方的目录或容器。 您可以使用双点 (`..`) 在提供程序层次结构中导航。

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a>提供商主页

提供程序还具有 **主** 位置。  此位置由提供程序所支持的全部共享 `PSDrives` 。 可以通过查看提供程序的 **Home** 属性来检索它。

```powershell
Get-PSProvider | Format-Table Name, Home
```

```Output
Name        Home
----        ----
Registry
Alias
Environment
FileSystem  C:\Users\username
Function
Variable
Certificate
```

**FileSystem** 提供程序是唯一具有 **Home** 默认值的提供程序。 它的值与相同 `$Home` 。 有关详细信息，请参阅 [about_Automatic_Variables](about_Automatic_Variables.md)。

你可以使用其属性为当前会话设置提供程序的 **主** 目录。

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

`~`字符可用于表示提供程序的主目录。
如果提供程序没有设置 **主** 位置，则会出现错误。

```powershell
Cert:\> Set-Location ~
```

```Output
Set-Location : Home location for this provider isn't set. To set the home
location, call "(get-psprovider 'Certificate').Home = 'path'".
At line:1 char:1
+ Set-Location ~
+ ~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Set-Location],
                              PSInvalidOperationException
...
```

## <a name="finding-dynamic-parameters"></a>查找动态参数

动态参数是由提供程序添加到 cmdlet 的 cmdlet 参数。 这些参数仅在 cmdlet 与添加它们的提供程序一起使用时才可用。

例如， `Cert:` 驱动器将 **CodeSigningCert** 参数添加到 `Get-Item` 和 `Get-ChildItem` cmdlet。 仅当在驱动器中使用或时，才可以使用此参数 `Get-Item` `Get-ChildItem` `Cert:` 。

有关提供程序支持的动态参数的列表，请参阅提供程序的帮助文件。 类型：

```
Get-Help <provider-name>
```

例如：

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a>了解提供程序

尽管所有提供程序数据都显示在驱动器中，并且你使用相同的方法在这些数据中移动，但相似性却停止了。 提供程序公开的数据存储可能与 Active Directory 位置和 Microsoft Exchange Server 邮箱不同。

有关各个 PowerShell 提供程序的信息，请键入：

```
Get-Help <ProviderName>
```

例如：

```powershell
Get-Help registry
```

有关提供程序的帮助主题的列表，请键入：

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a>请参阅

[about_Locations](about_Locations.md)

[about_Path_Syntax](about_Path_Syntax.md)

