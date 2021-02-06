---
description: 描述使函数的工作方式与已编译的 cmdlet 相同的特性。
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_CmdletBindingAttribute
ms.openlocfilehash: f1463bafc462ae2a266f5b1f6f4d71e3422f5831
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596656"
---
# <a name="about-functions-cmdletbindingattribute"></a>关于函数 CmdletBindingAttribute

## <a name="short-description"></a>简短说明
描述使函数的工作方式与已编译的 cmdlet 相同的特性。

## <a name="long-description"></a>长说明

`CmdletBinding`特性是使它们运行的函数的特性，如用 c # 编写的编译 cmdlet。 它提供对 cmdlet 功能的访问权限。

PowerShell 绑定具有属性的函数的参数， `CmdletBinding` 其方式与绑定编译 cmdlet 的参数的方式相同。 `$PSCmdlet`自动变量可用于具有属性的函数 `CmdletBinding` ，但该变量不可用 `$Args` 。

在具有属性的函数中 `CmdletBinding` ，未知参数和没有匹配位置参数的位置参数会导致参数绑定失败。

> [!NOTE]
> 已编译的 cmdlet 使用所需的 `Cmdlet` 属性，该属性类似于 `CmdletBinding` 本主题中描述的属性。

## <a name="syntax"></a>语法

下面的示例演示了一个函数的格式，该函数指定属性的所有可选参数 `CmdletBinding` 。 此示例的后面是每个参数的简要说明。

```powershell
{
    [CmdletBinding(ConfirmImpact=<String>,
    DefaultParameterSetName=<String>,
    HelpURI=<URI>,
    SupportsPaging=<Boolean>,
    SupportsShouldProcess=<Boolean>,
    PositionalBinding=<Boolean>)]

    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

## <a name="confirmimpact"></a>ConfirmImpact

**ConfirmImpact** 参数指定通过调用 **ShouldProcess** 方法来确认函数的操作的时间。 仅当 **ConfirmImpact** 参数等于或大于首选项变量的值时，对 **ShouldProcess** 方法的调用才会显示确认提示 `$ConfirmPreference` 。  (自变量的默认值为 **Medium**。 ) 仅在指定了 **SupportsShouldProcess** 参数时才指定此参数。

有关确认请求的详细信息，请参阅 [请求确认](/powershell/scripting/developer/cmdlet/requesting-confirmation)。

## <a name="defaultparametersetname"></a>DefaultParameterSetName

**DefaultParameterSetName** 参数指定 PowerShell 在无法确定要使用哪个参数时将尝试使用的参数集的名称。 可以通过使每个参数的唯一参数设置一个必需的参数来避免此问题。

## <a name="helpuri"></a>HelpURI

**HelpURI** 参数指定描述该函数的帮助主题的联机版本的 internet 地址。 **HelpURI** 参数的值必须以 "http" 或 "https" 开头。

**HelpURI** 参数值用于为函数返回的 **CommandInfo** 对象的 **HelpURI** 属性的值 `Get-Command` 。

但是，当在计算机上安装了帮助文件，并且帮助文件的 **RelatedLinks** 部分中第一个链接的值为 uri，或基于注释的帮助中的第一个指令的值为 `.Link` uri 时，帮助文件中的 uri 将用作函数的 **HelpUri** 属性的值。

`Get-Help`当命令中指定的 **联机** 参数时，该 Cmdlet 将使用 **HelpURI** 属性的值查找函数帮助主题的联机版本 `Get-Help` 。

## <a name="supportspaging"></a>SupportsPaging

**SupportsPaging** 参数将 **第一个**、 **Skip** 和 **IncludeTotalCount** 参数添加到函数。 用户可以使用这些参数选择非常大的结果集的输出。 此参数适用于从支持数据选择的大型数据存储（如 SQL 数据库）中返回数据的 cmdlet 和函数。

此参数是在 Windows PowerShell 3.0 中引入的。

- **First**：仅获取前 "n" 个对象。
- **Skip**：忽略第一个 "n" 对象，然后获取剩余的对象。
- **IncludeTotalCount**：报告数据集中的对象数 (整数) 后接对象。 如果 cmdlet 无法确定总计数，它将返回 "未知总数"。

PowerShell 包含 **NewTotalCount**，这是一个帮助器方法，用于获取要返回的总计数值并包含总计值的准确性。

下面的示例函数演示如何向高级函数添加对分页参数的支持。

```powershell
function Get-Numbers {
    [CmdletBinding(SupportsPaging = $true)]
    param()

    $FirstNumber = [Math]::Min($PSCmdlet.PagingParameters.Skip, 100)
    $LastNumber = [Math]::Min($PSCmdlet.PagingParameters.First +
      $FirstNumber - 1, 100)

    if ($PSCmdlet.PagingParameters.IncludeTotalCount) {
        $TotalCountAccuracy = 1.0
        $TotalCount = $PSCmdlet.PagingParameters.NewTotalCount(100,
          $TotalCountAccuracy)
        Write-Output $TotalCount
    }
    $FirstNumber .. $LastNumber | Write-Output
}
```

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

**SupportsShouldProcess** 参数将 **Confirm** 和 **WhatIf** 参数添加到函数。 **Confirm** 参数会提示用户，然后在管道中的每个对象上运行该命令。 **WhatIf** 参数会列出命令所进行的更改，而不是运行命令。

## <a name="positionalbinding"></a>PositionalBinding

**PositionalBinding** 参数确定函数中的参数在默认情况下是否是位置。 默认值是 `$True`。 可以使用值为的 **PositionalBinding** 参数 `$False` 禁用位置绑定。

**PositionalBinding** 参数是在 Windows PowerShell 3.0 中引入的。

如果参数是位置参数，则参数名称是可选的。
根据函数命令中未命名参数值的顺序或位置，PowerShell 将未命名的参数值与函数参数关联。

如果参数不是位置 (它们分别为 "命名" ) ，则在命令中需要参数名称 (或名称) 的缩写或别名。

如果 **PositionalBinding** 为 `$True` ，则默认情况下函数参数是位置。 PowerShell 将位置编号按其在函数中的声明顺序分配给参数。

当 **PositionalBinding** 为时 `$False` ，默认情况下函数参数不是位置。 除非在参数上声明 **参数** 特性的 **Position** 参数，否则在函数中使用参数时，参数名称 (或别名或缩写) 必须包括在内。

**参数** 特性的 **Position** 参数优先于 **PositionalBinding** 默认值。 您可以使用 **position** 参数来指定参数的位置值。 有关 **Position** 参数的详细信息，请参阅 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。

## <a name="notes"></a>说明

高级函数中不支持 **SupportsTransactions** 参数。

## <a name="keywords"></a>关键字

about_Functions_CmdletBinding_Attribute

## <a name="see-also"></a>请参阅

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
