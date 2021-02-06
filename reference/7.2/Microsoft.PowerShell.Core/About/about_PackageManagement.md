---
description: PackageManagement 是软件程序包管理器的聚合器。
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_packagemanagement?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PackageManagement
ms.openlocfilehash: 22f47d01063778fca4f51a534b15d485b3beee28
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596007"
---
# <a name="about-packagemanagement"></a>关于 PackageManagement

## <a name="short-description"></a>简短说明
PackageManagement 是软件程序包管理器的聚合器。

## <a name="long-description"></a>详细说明

PackageManagement 功能是在 Windows PowerShell 5.0 中引入的。

PackageManagement 是软件包管理系统的统一接口;可以运行 PackageManagement cmdlet 来执行软件发现、安装和清单 (SDII) 任务。 无论采用哪种基础安装技术，都可以在 PackageManagement 模块中运行公共 cmdlet，搜索、安装或卸载包;添加、删除和查询包存储库;并在计算机上运行查询以确定安装了哪些软件包。

PackageManagement 支持支持其他软件包管理系统的灵活插件模型。

PackageManagement 模块随 Windows PowerShell 5.0 和更高版本的 PowerShell 一起提供，可用于三个级别的包管理结构：包提供程序、包源和包本身。 让我们定义一些术语：

- 程序包管理器：软件程序包管理系统。 采用 PackageManagement 术语，这是一个程序包提供程序。
- 包提供程序：适用于包管理器的 PackageManagement 术语。 示例可以包括 Windows Installer、Chocolatey 等。
- 包源：配置包提供程序以用作存储库的 URL、本地文件夹或网络共享文件夹。
- 包：包提供程序管理并存储在特定包源中的一段软件。

PackageManagement 模块包含以下 cmdlet。 有关详细信息，请参阅 [PackageManagement](/powershell/module/packagemanagement) 帮助。

- `Get-PackageProvider`：返回连接到 PackageManagement 的包提供程序的列表。
- `Get-PackageSource`：获取为包提供程序注册的包源的列表。
- `Register-PackageSource`：为指定的包提供程序添加包源。
- `Set-PackageSource`：设置现有包源的属性。
- `Unregister-PackageSource`：删除已注册的包源。
- `Get-Package`：返回已安装软件包的列表。
- `Find-Package`：在可用包源中查找软件包。
- `Install-Package`：安装一个或多个软件包。
- `Save-Package`：将包保存到本地计算机，但不安装它们。
- `Uninstall-Package`：卸载一个或多个软件包。

### <a name="package-provider-bootstrapping-and-dynamic-cmdlet-parameters"></a>包提供程序引导和动态 Cmdlet 参数

默认情况下，PackageManagement 附带核心启动提供程序。 你可以通过引导提供程序来安装其他包提供程序，因为你需要它们;也就是说，从 web 服务响应自动安装提供程序的提示。 你可以使用任何 PackageManagement cmdlet 指定包提供程序;如果指定的提供程序不可用，则 PackageManagement 会提示你启动 (或自动安装) 提供程序。 在以下示例中，如果尚未安装 Chocolatey 提供程序，则 PackageManagement 引导会安装该提供程序。

```powershell
Find-Package -Provider Chocolatey <PackageName>
```

如果尚未安装 Chocolatey 提供程序，则在运行上述命令时，系统将提示你安装它。

```powershell
Install-Package <Chocolatey package Name> -ForceBootstrap
```

如果尚未安装 Chocolatey 提供程序，则在运行上述命令时，将安装该提供程序;但由于 ForceBootstrap 参数已添加到命令中，系统不会提示你进行安装。提供程序和包都是自动安装的。

当你尝试安装包时，如果你尚未安装支持的提供程序，并且未将 ForceBootstrap 参数添加到命令中，则 PackageManagement 会提示你安装该提供程序。

在 PackageManagement 命令中指定包提供程序可使动态参数可用于特定于该程序包提供程序。 针对特定的 PackageManagement cmdlet 运行 Get-Help 时，将返回参数集的列表，并将可用包提供程序的动态参数分组到不同的参数集。

有关 PackageManagement 项目的详细信息

有关 PackageManagement open 开发项目的详细信息（包括如何创建 PackageManagement 包提供程序），请参阅 GitHub 上的 PackageManagement 项目 https://oneget.org 。

## <a name="see-also"></a>另请参阅

[Get-PackageProvider](xref:PackageManagement.Get-PackageProvider)

[Get-PackageSource](xref:PackageManagement.Get-PackageSource)

[Register-PackageSource](xref:PackageManagement.Register-PackageSource)

[Set-PackageSource](xref:PackageManagement.Set-PackageSource)

[Unregister-PackageSource](xref:PackageManagement.Unregister-PackageSource)

[Get-Package](xref:PackageManagement.Get-Package)

[Find-Package](xref:PackageManagement.Find-Package)

[Install-Package](xref:PackageManagement.Install-Package)

[Save-Package](xref:PackageManagement.Save-Package)

[Uninstall-Package](xref:PackageManagement.Uninstall-Package)

