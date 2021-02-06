---
description: 描述如何从 PowerShell 中的工作位置访问项。
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_locations?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Locations
ms.openlocfilehash: 4876abe3c651ad2279b85355f2e5e029203b6d4e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595806"
---
# <a name="about_locations"></a>about_Locations

## <a name="short-description"></a>简短说明
描述如何从 PowerShell 中的工作位置访问项。

## <a name="long-description"></a>详细说明

当前工作位置是命令点的默认位置。
换句话说，如果不提供受命令影响的项或位置的显式路径，则这是 PowerShell 使用的位置。 在大多数情况下，当前工作位置是通过 PowerShell FileSystem 提供程序访问的驱动器，在某些情况下是该驱动器上的目录。
例如，你可以将当前工作位置设置为以下位置：

```powershell
C:\Program Files\Windows PowerShell
```

因此，除非显式提供另一个路径，否则将从该位置处理所有命令。

即使驱动器不是当前驱动器，PowerShell 也会保留每个驱动器的当前工作位置。 这允许你通过只引用另一个位置的驱动器来访问当前工作位置的项。
例如，假设您的当前工作位置是 C： \\ Windows。 现在，假设你使用以下命令将当前工作位置更改为 HKLM：驱动器：

```powershell
Set-Location HKLM:
```

尽管当前位置现在是注册表驱动器，但仍可以 \\ 使用 c：驱动器仅访问 c： Windows 目录中的项，如以下示例中所示：

```powershell
Get-ChildItem C:
```

PowerShell 会记住，当前该驱动器的工作位置是 Windows 目录，因此它将从该目录中检索项。 如果你运行以下命令，结果将相同：

```powershell
Get-ChildItem C:\Windows
```

在 PowerShell 中，可以使用 Get-Location 命令来确定当前工作位置，并且可以使用 Set-Location 命令设置当前工作位置。 例如，以下命令将当前工作位置设置为 C：驱动器的 Windows 目录：

```powershell
Set-Location c:\windows
```

设置当前工作位置之后，你仍可以通过在命令中包含驱动器名称 (后跟冒号) 来访问其他驱动器中的项，如以下示例中所示：

```powershell
Get-ChildItem HKLM:\software
```

示例命令将检索注册表中 HKEY 本地计算机 hive 的软件容器中的项列表。

PowerShell 还允许使用特殊字符表示当前工作位置及其父位置。 若要表示当前工作位置，请使用单个句点。 若要表示当前工作位置的父级，请使用两个句点。 例如，下面指定了当前工作位置中的系统子目录：

```powershell
Get-ChildItem .\system
```

如果当前工作位置为 C： \\ windows，则此命令将返回 c： windows 系统中所有项的 \\ 列表 \\ 。 但是，如果使用两个句点，则使用当前工作目录的父目录，如下面的示例中所示：

```powershell
Get-ChildItem ..\"program files"
```

在这种情况下，PowerShell 将两个句点视为 C：驱动器，因此该命令检索 C： Program Files 目录中的所有项 \\ 。

以斜杠开头的路径标识来自当前驱动器的根目录的路径。 例如，如果当前工作位置是 C： \\ Program Files \\ PowerShell，则驱动器的根目录为 c。因此，以下命令列出了 C： Windows 目录中的所有项 \\ ：

```powershell
Get-ChildItem \windows
```

如果在提供容器或项的名称时未指定以驱动器名称、斜杠或句点开头的路径，则假定容器或项位于当前工作位置。 例如，如果您的当前工作位置是 C： \\ windows，则以下命令将返回 c： \\ windows 系统目录中的所有项 \\ ：

```powershell
Get-ChildItem system
```

如果指定文件名而不是目录名称，则 PowerShell 将返回有关该文件的详细信息， (假设该文件位于当前工作位置) 。

## <a name="see-also"></a>另请参阅

[Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)

[about_Providers](about_Providers.md)

[about_Path_Syntax](about_Path_Syntax.md)

