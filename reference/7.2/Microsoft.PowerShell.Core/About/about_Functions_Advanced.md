---
description: 引入了一种使用脚本创建 cmdlet 的高级功能。
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced
ms.openlocfilehash: a0b8b027c91f2adedfcecd07bfc80392c1b1e071
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597658"
---
# <a name="about-functions-advanced"></a>关于函数高级

## <a name="short-description"></a>简短说明
引入了一种使用脚本创建 cmdlet 的高级功能。

## <a name="long-description"></a>详细说明

Cmdlet 是参与 PowerShell 管道语义的单个命令。 这包括二进制 cmdlet、高级脚本函数、CDXML 和工作流。

利用高级功能，你可以创建以 PowerShell 函数形式编写的 cmdlet。 利用高级功能，无需编写和编译二进制 cmdlet 即可更轻松地创建 cmdlet。 二进制 cmdlet 是用 .NET 语言（如 c #）编写的 .NET 类。

高级函数使用 `CmdletBinding` 特性将它们标识为充当 cmdlet 的函数。 `CmdletBinding`属性类似于编译的 cmdlet 类中使用的 cmdlet 属性，用于将类标识为 cmdlet。 有关此属性的详细信息，请参阅 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)。

下面的示例演示一个函数，该函数接受名称，然后使用提供的名称打印问候语。 另请注意，此函数定义一个名称，该名称包括一个谓词 (发送) 和名词 (问候语) 对，如编译 cmdlet 的动词-名词对。 但是，函数不需要具有动词-名词名称。

```powershell
function Send-Greeting
{
    [CmdletBinding()]
    Param(
        [Parameter(Mandatory=$true)]
        [string] $Name
    )

    Process
    {
        Write-Host ("Hello " + $Name + "!")
    }
}
```

函数的参数是使用参数特性声明的。
此特性可以单独使用，也可以与 Alias 特性或其他一些参数验证特性结合使用。 有关如何声明参数 (包括在运行时) 添加的动态参数的详细信息，请参阅 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。

先前函数的实际工作是在进程块中执行的，该进程块等效于编译的 cmdlet 用来处理传递到 cmdlet 的数据的 ProcessingRecord 方法。 [About_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)主题中介绍了此块以及 Begin 和 End 块。

高级函数与已编译的 cmdlet 在以下方面有所不同：

- 当字符串数组绑定到布尔参数时，高级函数参数绑定不会引发异常。
- ValidateSet 属性和 ValidatePattern 属性不能传递指定的参数。
- 不能在事务中使用高级函数。

## <a name="see-also"></a>另请参阅

[about_Functions](about_Functions.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
