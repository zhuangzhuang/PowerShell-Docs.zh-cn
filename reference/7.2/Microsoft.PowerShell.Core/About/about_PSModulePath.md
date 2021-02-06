---
description: PSModulePath 环境变量包含一个文件夹位置列表，将在其中进行搜索以查找模块和资源。
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: ce77005d816f49c0a6353bd7b3e0580293b05d23
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597237"
---
# <a name="about-psmodulepath"></a>关于 PSModulePath

`$env:PSModulePath`环境变量包含一个文件夹位置列表，将在其中进行搜索以查找模块和资源。 PowerShell 会以递归方式在每个文件夹中搜索模块 (`.psd1` 或 `.psm1`) 文件。

默认情况下，分配到的有效位置 `$env:PSModulePath` 为：

- 系统范围的位置：这些文件夹包含 PowerShell 附带的模块。 这些模块存储在文件夹中 `$PSHOME\Modules` 。 这也是安装 Windows 管理模块的位置。

- 用户安装的模块：这些是用户安装的模块。
  `Install-Module` 具有 **作用域** 参数，该参数可用于指定是为当前用户还是为所有用户安装该模块。 有关详细信息，请参阅 [Install-Module](xref:PowerShellGet.Install-Module)。

  - 在 Windows 上，特定于用户的 **CurrentUser** 范围是 `$HOME\Documents\PowerShell\Modules` 文件夹。 **AllUsers** 作用域的位置为 `$env:ProgramFiles\PowerShell\Modules` 。
  - 在非 Windows 系统上，特定于用户的 **CurrentUser** 范围是 `$HOME/.local/share/powershell/Modules` 文件夹。 **AllUsers** 作用域的位置为 `/usr/local/share/powershell/Modules` 。

此外，在其他目录中安装模块的安装程序（如 Program Files 目录）可以将它们的位置附加到的值 `$env:PSModulePath` 。

> [!NOTE]
> 在 Windows 上，用户特定的位置是 `PowerShell\Modules` 位于用户配置文件中的 **Documents** 文件夹中的文件夹。 该位置的特定路径因 Windows 版本而异，无论是否正在使用文件夹重定向。 Microsoft OneDrive 还可以更改 **文档** 文件夹的位置。 可以使用以下命令来验证 **Documents** 文件夹的位置： `[Environment]::GetFolderPath('MyDocuments')` 。

## <a name="modifying-psmodulepath"></a>修改 PSModulePath

若要更改当前会话的默认模块目录，请使用以下命令格式来更改 `PSModulePath` 环境变量的值。

例如，若要将 `C:\Program Files\Fabrikam\Modules` 目录添加到 PSModulePath 环境变量的值，请键入：

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

命令中的分号 (`;`) 将新路径与列表中其前面的路径分隔开。 在非 Windows 平台上，冒号 (`:`) 将环境变量中的路径位置隔开。

若要 `PSModulePath` 在每个会话中更改的值，请将上一个命令添加到 PowerShell 配置文件，或使用 **环境** 类的 **SetEnvironmentVariable** 方法。

下面的命令使用 **GetEnvironmentVariable** 方法来获取的计算机设置 `PSModulePath` ，并使用 **SetEnvironmentVariable** 方法将 `C:\Program Files\Fabrikam\Modules` 路径添加到值中。

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

若要将路径添加到用户设置，请将 "目标" 值更改为 " **用户**"。

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

有关 **system.web** 类的方法的详细信息，请参阅 [环境方法](/dotnet/api/system.environment)。

## <a name="powershell-psmodulepath-construction"></a>PowerShell PSModulePath 构造

`$env:PSModulePath`每次启动 PowerShell 时，都会构造的值。
该值因 PowerShell 版本和启动方式而异。

### <a name="windows-powershell-startup"></a>Windows PowerShell 启动

Windows PowerShell 在启动时使用以下逻辑来构造 `PSModulePath` ：

- 如果 `PSModulePath` 不存在，则将 **CurrentUser**、 **AllUsers** 和 `$PSHOME` 模块路径组合在一起
- 如果 `PSModulePath` 存在，则：
  - 如果 `PSModulePath` 包含 `$PSHOME` 模块路径：
    - 在模块路径之前插入 **AllUsers** 模块路径 `$PSHOME`
  - else:
    - 只需使用 `PSModulePath` 自用户特意删除位置后定义 `$PSHOME` 的

仅当用户范围不存在时， **CurrentUser** 模块路径才带有前缀 `$env:PSModulePath` 。 否则，将 `$env:PSModulePath` 按定义使用用户作用域。

### <a name="powershell-core-6-startup"></a>PowerShell Core 6 启动

如果 PowerShell Core 6 `$env:PSModulePath` 检测到它是从 PowerShell 启动的，则不使用的内容。 它将覆盖它：

- **CurrentUser** 模块路径 + **AllUsers** 模块路径 + `$PSHOME` 模块路径 + Windows PowerShell `$PSHOME` 模块路径。

### <a name="powershell-7-startup"></a>PowerShell 7 启动

在 Windows 中，对于大多数环境变量，如果存在用户范围的变量，新进程将仅使用该值，即使存在同名的计算机范围的变量。

在 PowerShell 7 中， `PSModulePath` 的处理方式类似于 `Path` Windows 上环境变量的处理方式。 在 Windows 上，的 `Path` 处理方式与其他环境变量不同。 当进程启动时，Windows 会将用户范围 `Path` 与计算机范围合并 `Path` 。

- 检索用户范围 `PSModulePath`
- 与处理继承的 `PSModulePath` 环境变量比较
  - 如果相同：
    - 在 `PSModulePath` `Path` 环境变量的语义后面追加 AllUsers 到末尾
    - Windows `System32` 路径来自定义的计算机 `PSModulePath` ，因此无需显式添加
  - 如果不同，则视为用户显式修改了它，并且不追加 **AllUsers**`PSModulePath`
- 按顺序为 PS7 用户、系统和 `$PSHOME` 路径提供前缀
  - 如果 `powershell.config.json` 包含用户范围的 `PSModulePath` ，请使用它，而不是用户的默认值
  - 如果 `powershell.config.json` 包含系统范围 `PSModulePath` ，请使用此值，而不使用系统的默认值

Unix 系统没有隔离用户和系统环境变量。
`PSModulePath` 是继承的，如果尚未定义 PS7 特定路径，则会将其作为前缀。

### <a name="starting-windows-powershell-from-powershell-7"></a>从 PowerShell 7 启动 Windows PowerShell

对于此讨论， _Windows PowerShell_ 既表示 `powershell.exe` 又是 `powershell_ise.exe` 。

将的值 `$env:PSModulePath` 复制到， `WinPSModulePath` 并进行以下修改：

- 删除用户模块路径 PS7
- 删除系统模块路径 PS7
- 删除模块路径中的 PS7 `$PSHOME`

删除 PS7 路径，以便不会在 Windows PowerShell 中加载 PS7 模块。 `WinPSModulePath`启动 Windows PowerShell 时使用该值。

### <a name="starting-powershell-7-from-windows-powershell"></a>从 Windows PowerShell 启动 PowerShell 7

PowerShell 7 启动将按原样继续，并添加 Windows PowerShell 添加的继承路径。 由于 PS7 特定的路径带有前缀，因此不存在功能问题。

### <a name="starting-powershell-6-from-powershell-7"></a>从 PowerShell 7 启动 PowerShell 6

PowerShell Core 6 将覆盖 `$env:PSModulePath` 。 未进行任何更改。

### <a name="starting-powershell-7-from-powershell-6"></a>从 PowerShell 6 启动 PowerShell 7

PowerShell 7 启动将按原样继续，并添加 PowerShell Core 6 添加的继承路径。 由于 PS7 特定的路径带有前缀，因此不存在功能问题。

## <a name="module-search-behavior"></a>模块搜索行为

PowerShell 会以递归方式搜索 **PSModulePath** 中的每个文件夹 (`.psd1` 或 `.psm1`) 文件。 此搜索模式允许在不同的文件夹中安装相同模块的多个版本。 例如：

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules\PowerShellGet

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----           8/14/2020  5:56 PM                1.0.0.1
d----           9/13/2019  3:53 PM                2.1.2
```

默认情况下，当找到多个版本时，PowerShell 将加载模块的最高版本号。 若要加载特定版本，请使用 `Import-Module` With **FullyQualifiedName** 参数。 有关详细信息，请参阅 [import-module](xref:Microsoft.PowerShell.Core.Import-Module)。

## <a name="see-also"></a>请参阅

- [about_Modules](about_Modules.md)
- [环境方法](/dotnet/api/system.environment)
