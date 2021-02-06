---
description: 介绍更简单、更自然语言的对象集合脚本筛选方式。
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_simplified_syntax?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Simplified_Syntax
ms.openlocfilehash: dbd30d566414f784e7d5eca04af716c2bf1642b9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597467"
---
# <a name="about_simplified_syntax"></a>about_Simplified_Syntax

## <a name="short-description"></a>简短说明
介绍更简单、更自然语言的对象集合脚本筛选方式。

## <a name="long-description"></a>详细说明

Windows PowerShell 3.0 中引入的简化语法使你可以在不使用脚本块的情况下生成某些筛选器命令。 简化的语法更加类似于自然语言，并主要用于通过管道转换为命令的对象集合及其 `Where-Object` 对应的 `ForEach-Object` 别名 `where` 和 `foreach` 。

您可以对集合的成员使用方法 (最常见的是数组) ，而不引用 `$_` 脚本块中的自动变量。

请考虑以下两个调用：

### <a name="standard-syntax"></a>标准语法

```powershell
dir Cert:\LocalMachine\Root | where { $_.FriendlyName -eq 'Verisign' }
dir Cert:\ -Recurse | foreach { $_.GetKeyAlgorithm() }
```

### <a name="simplified-syntax"></a>简化的语法

在简化语法下，处理集合中对象成员的比较运算符被视为参数。 您可以对集合中的对象调用方法，而不引用 `$_` 脚本块中的自动变量。
将以下两个调用与上一示例中的调用进行比较：

```powershell
dir Cert:\LocalMachine\Root | where FriendlyName -eq 'Verisign'
dir Cert:\ -Recurse | foreach GetKeyAlgorithm
```

虽然这两种语法都起作用，但简化的语法返回结果，而不引用 `$_` 脚本块中的自动变量。
方法名称 `GetKeyAlgorithm` 被视为的参数 `ForEach-Object` 。
第二个命令将返回相同的结果，但不会返回错误，因为简化的语法不会尝试返回指定参数不适用于的项的结果。

在此示例中， `Process` 属性 `Description` 作为成员名称参数传递到 `ForEach-Object` 命令。 结果是活动过程的说明。

```powershell
Get-Process | foreach Description
```

在此示例中， `DirectoryInfo` 方法 `GetFiles` 作为命令的成员名称参数传递 `ForEach-Object` 。  
用搜索模式参数调用方法 `.*` 。  
结果为 `FileInfo` 用户主目录中所有 Unix 样式的隐藏文件的记录。 

```powershell
Get-ChildItem /home -Directory | foreach GetFiles .*
```

## <a name="see-also"></a>另请参阅

- [about_Comparison_Operators](about_Comparison_Operators.md)
- [about_Foreach](about_Foreach.md)
- [Where-Object](xref:Microsoft.PowerShell.Core.Where-Object)
- [Foreach-对象](xref:Microsoft.PowerShell.Core.ForEach-Object)

