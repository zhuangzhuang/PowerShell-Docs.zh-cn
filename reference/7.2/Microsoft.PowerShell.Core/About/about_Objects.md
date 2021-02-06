---
description: 提供有关 PowerShell 中的对象的基本信息。
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_objects?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Objects
ms.openlocfilehash: bfb66e72a74d20379123558b85047097dc801e9d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603606"
---
# <a name="about-objects"></a>关于对象

## <a name="short-description"></a>简短说明
提供有关 PowerShell 中的对象的基本信息。

## <a name="long-description"></a>详细说明

在 PowerShell 中执行的每个操作都在对象的上下文中发生。 当数据从一个命令移到下一个命令时，它将作为一个或多个可识别对象移动。 对象是表示项的数据集合。 对象由三种类型的数据组成：对象类型、对象的方法和属性。

## <a name="types-methods-and-properties"></a>类型、方法和属性

对象类型告诉对象的类型。 例如，表示文件的对象是一个 FileInfo 对象。

对象方法是可对对象执行的操作。
例如，FileInfo 对象具有可用于复制文件的 CopyTo 方法。

对象属性存储有关对象的信息。 例如，FileInfo 对象具有 LastWriteTime 属性，该属性存储最近一次访问该文件的日期和时间。

使用对象时，可以使用命令中的方法和属性来执行操作和管理数据。

## <a name="objects-in-pipelines"></a>管道中的对象

当命令合并到管道中时，它们会将信息互相传递为对象。 第一条命令运行时，它将一个或多个对象向下移动到第二个命令。 第二个命令从第一个命令接收对象，处理对象，然后将新的或已修改的对象传递到管道中的下一个命令。
此过程将一直继续，直到管道中的所有命令都运行为止。

下面的示例演示如何将对象从一个命令传递到下一个命令：

```powershell
Get-ChildItem C: | where { $_.PsIsContainer -eq $false } | Format-List
```

第一个命令 `Get-ChildItem C:` 为文件系统的根目录中的每个项返回一个文件或目录对象。 文件和目录对象通过管道向下传递到第二个命令。

第二个命令 `where { $_.PsIsContainer -eq $false }` 使用所有文件系统对象的 PsIsContainer 属性来仅选择文件，这些文件的 PsIsContainer 属性中的值为 false (\$ false) 。 文件夹是容器，因此，它们的 PsIsContainer 属性中的值为 True (\$ true) 。

第二个命令仅将文件对象传递给第三个命令 `Format-List` ，后者将在列表中显示文件对象。

## <a name="see-also"></a>另请参阅

[about_Methods](about_Methods.md)

[about_Object_Creation](about_Object_Creation.md)

[about_Properties](about_Properties.md)

[about_pipelines](about_Pipelines.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)

