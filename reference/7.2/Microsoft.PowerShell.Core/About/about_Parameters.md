---
description: 介绍如何在 PowerShell 中使用命令参数。
Locale: en-US
ms.date: 02/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters
ms.openlocfilehash: c9d7ab62c13a7cafcf93103f9a70f6575d5dd7b8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598707"
---
# <a name="about-parameters"></a>关于参数

## <a name="short-description"></a>简短说明
介绍如何在 PowerShell 中使用命令参数。

## <a name="long-description"></a>长说明

大多数 PowerShell 命令（如 cmdlet、函数和脚本）都依赖于参数，以允许用户选择选项或提供输入。 参数跟在命令名之后，格式如下：

```
-<parameter_name> <parameter_value>
-<parameter_name>:<parameter_value>
```

参数的名称前面带有连字符 ( ) ，这向 PowerShell 发出信号，表示连字符后面的单词是参数名称。 参数名称和值可以用空格或冒号字符分隔。 某些参数不需要或接受参数值。 其他参数需要一个值，但是在命令中不需要参数名称。

参数的类型和这些参数的要求各不相同。 若要查找有关命令的参数的信息，请使用 `Get-Help` cmdlet。 例如，若要查找有关该 cmdlet 的参数的信息 `Get-ChildItem` ，请键入：

```powershell
Get-Help Get-ChildItem
```

若要查找有关脚本的参数的信息，请使用脚本文件的完整路径。 例如：

```powershell
Get-Help $home\Documents\Scripts\Get-Function.ps1
```

`Get-Help`Cmdlet 返回有关命令的各种详细信息，包括说明、命令语法、有关参数的信息，以及演示如何在命令中使用参数的示例。

你还可以使用 cmdlet 的参数参数 `Get-Help` 查找有关特定参数的信息。 或者，可以将 **参数** 参数与通配符 ( ) 值一起使用， `*` 查找有关该命令的所有参数的信息。 例如，以下命令将获取有关该 cmdlet 的所有参数的信息 `Get-Member` ：

```powershell
Get-Help Get-Member -Parameter *
```

### <a name="default-parameter-values"></a>默认参数值

可选参数具有默认值，该值是在命令中未指定参数时使用或假设的值。

例如，许多 cmdlet 的 **ComputerName** 参数的默认值是本地计算机的名称。 因此，在命令中使用本地计算机名称，除非指定 **ComputerName** 参数。

若要查找默认参数值，请参阅 cmdlet 的帮助主题。 参数说明应包含默认值。

还可以为 cmdlet 或高级函数的任何参数设置自定义默认值。 有关设置自定义默认值的信息，请参阅 [about_Parameters_Default_Values](about_Parameters_Default_Values.md)。

### <a name="parameter-attribute-table"></a>参数属性表

当你使用 cmdlet 的 **Full**、 **parameter** 或 **Online** 参数时 `Get-Help` ，将 `Get-Help` 显示一个参数属性表，其中包含有关参数的详细信息。

此信息包括你需要知道使用参数的详细信息。
例如，cmdlet 的帮助主题 `Get-ChildItem` 包含有关其 Path 参数的以下详细信息：

```
-path <string[]>
    Specifies a path of one or more locations. Wildcard characters are
    permitted. The default location is the current directory (.).

Required?                    false
Position?                    0
Default value                Current directory
Accept pipeline input?       true (ByValue, ByPropertyName)
Accept wildcard characters?  true
```

参数信息包括参数语法、参数说明和参数特性。 以下各节介绍参数特性。

#### <a name="parameter-required"></a>必需参数

此设置指示参数是否是必需的，即是否所有使用此 cmdlet 的命令都必须包含此参数。 如果值为 **True** ，并且命令中缺少参数，则 PowerShell 将提示你输入参数的值。

#### <a name="parameter-position"></a>参数位置

如果 `Position` 设置设置为正整数，则不需要参数名称。 这种类型的参数称为位置参数，数值指示参数必须与其他位置参数出现的位置。 命名的参数可以在 cmdlet 名称后的任何位置中列出。 如果包含位置参数的参数名称，则可以在 cmdlet 名称后的任何位置中列出参数。

例如， `Get-ChildItem` cmdlet 具有 Path 和 Exclude 参数。 `Position`**路径** 的设置为 **0**，这意味着它是一个位置参数。 `Position`**排除** 的设置 **命名** 为。

这意味着该 **路径** 不需要参数名，但其参数值必须是命令中的第一个或唯一一个未命名的参数值。
但是，因为 Exclude 参数是命名参数，你可以将其放在命令中的任意位置。

由于 `Position` 这两个参数的设置，你可以使用以下任一命令：

```powershell
Get-ChildItem -Path c:\techdocs -Exclude *.ppt
Get-ChildItem c:\techdocs -Exclude *.ppt
Get-ChildItem -Exclude *.ppt -Path c:\techdocs
Get-ChildItem -Exclude *.ppt c:\techdocs
```

如果要包含另一个位置参数而不包括参数名称，则该参数必须按设置指定的顺序放置 `Position` 。

#### <a name="parameter-type"></a>参数类型

此设置指定参数值的 Microsoft .NET 框架类型。 例如，如果类型为 **Int32**，则参数值必须是整数。 如果类型为 string，则参数值必须为字符串。 如果字符串包含空格，则必须用引号将该值引起来，或者必须在空格前面加上转义符 ( ") 。

#### <a name="default-value"></a>默认值

如果未提供其他值，则此设置将指定参数将假设的值。 例如，Path 参数的默认值通常为当前目录。 必需的参数决不会有默认值。
对于许多可选参数，没有默认值，因为如果不使用参数，则该参数不起作用。

#### <a name="accepts-multiple-values"></a>接受多个值

此设置指示参数是否接受多个参数值。
当参数接受多个值时，可以在命令中键入以逗号分隔的列表作为参数的值，或将逗号分隔的列表保存 (数组中的数组) ，然后将该变量指定为参数值。

例如，cmdlet 的 ServiceName 参数 `Get-Service` 接受多个值。 以下命令都是有效的：

```powershell
Get-Service -servicename winrm, netlogon
```

```powershell
$s = "winrm", "netlogon"
Get-Service -servicename $s
```

#### <a name="accepts-pipeline-input"></a>接受管道输入

此设置指示是否可以使用管道运算符 ( ) 将 `|` 值发送到参数。

```
Value                    Description
-----                    -----------
False                    Indicates that you cannot pipe a value to the
                         parameter.

True (by Value)          Indicates that you can pipe any value to the
                         parameter, just so the value has the .NET
                         Framework type specified for the parameter or the
                         value can be converted to the specified .NET
                         Framework type.
```

当参数为 "True (值) " 时，PowerShell 会尝试将任何管道值与该参数相关联，然后再尝试其他方法来解释该命令。

```
True (by Property Name)  Indicates that you can pipe a value to the
                         parameter, but the .NET Framework type of the
                         parameter must include a property with the same
                         name as the parameter.
```

例如，仅当值具有一个名为 **name** 的属性时，才能通过管道将值传递给 **name** 参数。

> [!NOTE]
> 一个类型化参数，该参数接受管道输入 (`by Value`) 或 (`by PropertyName`) 允许在参数上使用 **延迟绑定** 脚本块。
>
> **延迟绑定** 脚本块在 **ParameterBinding** 期间自动运行。 结果绑定到参数。 延迟绑定对于定义为类型或的参数 **不** 起作用 `ScriptBlock` ，不 `System.Object` 调用脚本块。 
>
> 你可以在此处了解 about_Script_Blocks 的 **延迟绑定** 脚本块 [。](about_Script_Blocks.md)

#### <a name="accepts-wildcard-characters"></a>接受通配符

此设置指示参数的值是否可以包含通配符，使参数值可以与目标容器中的多个现有项匹配。

#### <a name="common-parameters"></a>通用参数

常见参数是可与任何 cmdlet 一起使用的参数。 有关常见参数的详细信息，请参阅 [about_CommonParameters](about_CommonParameters.md)。

## <a name="see-also"></a>请参阅

[about_Command_syntax](about_Command_syntax.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Parameters_Default_Values](about_Parameters_Default_Values.md)

[about_pipelines](about_Pipelines.md)

[about_Wildcards](about_Wildcards.md)

