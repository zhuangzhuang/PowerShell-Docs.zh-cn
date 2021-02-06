---
description: 描述 PowerShell 中的完整和相对路径名称格式。
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_path_syntax?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Path_Syntax
ms.openlocfilehash: 9a95865d67dc15bf79762987622b702b14faf6c6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596447"
---
# <a name="about-path-syntax"></a>关于路径语法

## <a name="short-description"></a>简短说明
描述 PowerShell 中的完整和相对路径名称格式。

## <a name="long-description"></a>详细说明

可通过 PowerShell 提供程序访问的数据存储区中的所有项都可以通过其路径名称进行唯一标识。 路径名称是项名称、项所在的容器和子容器以及用于访问这些容器的 PowerShell 驱动器的组合。

在 PowerShell 中，路径名分为以下两种类型之一：完全限定的名称和相对路径。 完全限定的路径名称包含构成路径的所有元素。 以下语法显示了完全限定的路径名称中的元素：

```powershell
[<provider>::]<drive>:[\<container>[\<subcontainer>...]]\<item>
```

\<provider\>占位符指的是用于访问数据存储区的 PowerShell 提供程序。 例如，FileSystem 提供程序允许你访问计算机上的文件和目录。 语法的此元素是可选的，并且永远不需要，因为驱动器名称在所有提供程序中都是唯一的。

\<drive\>占位符指特定 powershell 提供程序支持的 powershell 驱动器。 对于 FileSystem 提供程序，PowerShell 驱动器将映射到在系统上配置的 Windows 驱动器。 例如，如果你的系统包含 A：驱动器和 C：驱动器，则 FileSystem 提供程序会在 PowerShell 中创建相同的驱动器。

指定驱动器后，必须指定包含项的任何容器和子容器。 容器必须按照其在数据存储中的存在的层次结构顺序来指定。 换句话说，您必须从父容器开始，然后是该父容器中的子容器，依此类推。 此外，每个容器前面必须加上一个反斜杠。  (请注意，PowerShell 允许使用正斜杠与其他 PowerShells 的兼容性 ) 

指定容器和子容器后，必须提供前面带有反斜杠的项目名称。 例如，C： Windows System32 目录中 Shell.dll 文件的完全限定路径名称 \\ \\ 如下：

```powershell
C:\Windows\System32\Shell.dll
```

在这种情况下，访问容器所使用的驱动器是 C：驱动器，顶级容器是 Windows，subcontainer 是位于 Windows 容器) 内的 System32 (，该项是 Shell.dll 的。

在某些情况下，不需要指定完全限定的路径名称，而是可以使用相对路径名称。 相对路径名称基于当前工作位置。 PowerShell 允许您根据项相对于当前工作位置的位置来标识项。 您可以通过使用特殊字符来指定相对路径名称。 下表对其中每个字符进行了说明，并提供了相对路径名称和完全限定的路径名称的示例。 表中的示例基于要设置为 C:\windows。的当前工作目录。

|符号|说明               |相对路径    |完整路径          |
|------|--------------------------|-----------------|-------------------|
|.     |当前位置          |.\\主板        |c： \\ Windows \\ 系统|
|..    |当前位置的父级|..\\程序文件|c： \\ Program 文件  |
|\     |当前的驱动器根     |\\程序文件  |c： \\ Program 文件  |
|      |location                  |                 |                   |
|内容|无特殊字符     |系统           |c： \\ Windows \\ 系统|

在命令中使用路径名时，输入该名称的方式与使用完全限定的路径名称或相对路径名称的方式相同。 例如，假设当前工作目录为 C:\windows。 以下 Get-ChildItem 命令将检索 C:\Techdocs 目录中的所有项：

```powershell
Get-ChildItem \techdocs
```

反斜杠指示应该使用当前工作位置的驱动器根目录。 由于工作目录为 C： \\ Windows，因此驱动器根为 c：驱动器。 由于 techdocs 目录位于根位置，因此只需指定反斜杠。

可以使用以下命令获得相同的结果：

```powershell
Get-ChildItem c:\techdocs
```

无论是使用完全限定的路径名称还是相对路径名称，路径名都非常重要，因为它会查找项，但它也是唯一标识项，即使该项与其他容器中的另一项共享同一名称也是如此。

例如，假设您有两个分别名为 Results.txt 的文件。
第一个文件位于名为 C： Techdocs Jan 的目录中 \\ \\ ，第二个文件位于名为 c： Techdocs 的目录中 \\ \\ 。第一个文件 (C： \\ Techdocs \\ JanResults.txt) 的路径名称 \\ ，第二个文件的路径名称 (c： \\ Techdocs \\ 2 月 \\Results.txt) 使你可以清楚地区分这两个文件。

## <a name="see-also"></a>另请参阅

[about_Locations](about_Locations.md)

