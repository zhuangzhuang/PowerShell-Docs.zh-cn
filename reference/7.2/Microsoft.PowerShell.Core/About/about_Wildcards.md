---
description: 介绍如何在 PowerShell 中使用通配符。
Locale: en-US
ms.date: 02/13/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: 40620e54bb889d683192b346f3ba1c139895e4d0
ms.sourcegitcommit: 9777152e026c47ba8d319593051416054cb62246
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/16/2021
ms.locfileid: "100529968"
---
# <a name="about-wildcards"></a>关于通配符

## <a name="short-description"></a>简短说明

介绍如何在 PowerShell 中使用通配符。

## <a name="long-description"></a>详细说明

通配符表示一个或多个字符。 您可以使用它们在命令中创建 word 模式。 通配符表达式与 `-like` 运算符或任何接受通配符的参数一起使用。

例如，若要匹配 `C:\Techdocs` 目录中具有文件扩展名的所有文件 `.ppt` ，请键入：

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

在这种情况下，星号 (`*`) 通配符表示在文件扩展名之前出现的任何字符 `.ppt` 。

通配符表达式比正则表达式简单。 有关详细信息，请参阅 [about_Regular_Expressions](./about_Regular_Expressions.md)。

PowerShell 支持以下通配符：

|通配符|描述               |示例 |匹配        |无匹配项|
|--------|--------------------------|--------|-------------|--------|
|\*      |匹配零个或多个字符 | 的\*  | aA、ag、Apple | 香蕉 |
|?       |匹配该位置中的一个字符 | ？ n | ，在中，在 | 为名 |
|\[ \]   |匹配一系列字符 | \[a-l \] ook | 书籍，库，查找 | 需要 |
|\[ \]   |匹配特定字符 | \[bc \] ook | 书籍，库 | 自已 |

可以在同一单词模式中包含多个通配符字符。 例如，若要查找名称以字母 **a** 到 **l** 开头的文本文件，请键入：

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

许多 cmdlet 接受参数值中的通配符。 每个 cmdlet 的帮助主题描述了哪些参数接受通配符。 对于接受通配符的参数，其使用不区分大小写。

可以在命令和脚本块中使用通配符，例如，创建表示属性值的单词模式。 例如，以下命令将获取 **ServiceType** 属性值包括 **Interactive** 的服务。

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

在下面的示例中， `If` 语句包含使用通配符查找属性值的条件。 如果还原点的 **描述** 包含 **PowerShell**，则该命令会将还原点的 **CreationTime** 属性的值添加到日志文件。

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a>另请参阅

[about_Language_Keywords](about_Language_Keywords.md)

[about_If](about_If.md)

[about_Script_Blocks](about_Script_Blocks.md)

