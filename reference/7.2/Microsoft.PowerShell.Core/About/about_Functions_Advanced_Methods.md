---
description: 描述指定属性的函数如何 `CmdletBinding` 使用可用于已编译 cmdlet 的方法和属性。
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Methods
ms.openlocfilehash: 13a9d7258f1a52d5fcbb2d8c55b91c8d6454452d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596858"
---
# <a name="about-functions-advanced-methods"></a>关于函数的高级方法

## <a name="short-description"></a>简短说明

描述指定属性的函数如何 `CmdletBinding` 使用可用于已编译 cmdlet 的方法和属性。

## <a name="long-description"></a>长说明

指定特性的函数 `CmdletBinding` 可以通过变量访问多种方法和属性 `$PSCmdlet` 。 这些方法包括以下方法：

- 已编译的 cmdlet 用于完成其工作的输入处理方法。
- `ShouldProcess`用于在 `ShouldContinue` 执行操作之前获取用户反馈的和方法。
- `ThrowTerminatingError`用于生成错误记录的方法。
- `Write`返回不同输出类型的几种方法。

**PSCmdlet** 类的所有方法和属性都可用于高级函数。 有关详细信息，请参阅 [PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)。

有关属性的详细信息 `CmdletBinding` ，请参阅 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)。
有关 **CmdletBindingAttribute** 类的详细，请参阅 [CmdletBindingAttribute](/dotnet/api/system.management.automation.cmdletbindingattribute)。

### <a name="input-processing-methods"></a>输入处理方法

本节中所述的方法称为输入处理方法。 对于函数，这三种方法由函数的 `Begin` 、 `Process` 和 `End` 块表示。 不需要在函数中使用这些块中的任何一个。

> [!NOTE]
> 这些块还可用于不使用属性的函数 `CmdletBinding` 。

#### <a name="begin"></a>开始

此块用于为函数提供可选的一次性预处理。
PowerShell 运行时对管道中的每个函数实例使用一次此块中的代码。

#### <a name="process"></a>过程

此块用于为函数提供按记录处理。 您可以使用 `Process` 块，而无需定义其他块。 `Process`块执行的次数取决于使用函数的方式和函数接收的输入。

自动变量 `$_` 或 `$PSItem` 包含管道中用于块的当前对象 `Process` 。 `$input`自动变量包含一个仅可用于函数和脚本块的枚举器。
有关详细信息，请参阅 [about_Automatic_Variables](about_Automatic_Variables.md)。

- 在管道的开头或外部调用函数时，将执行此 `Process` 块一次。
- 在管道中， `Process` 块针对每个到达函数的输入对象执行一次。
- 如果到达函数的管道输入为空，则 `Process` **不会** 执行块。
  - `Begin`和 `End` 块仍在执行。

> [!IMPORTANT]
> 如果将某个函数参数设置为接受管道输入，但 `Process` 未定义块，记录记录处理将失败。 在这种情况下，无论输入如何，函数都将只执行一次。

#### <a name="end"></a>结束

此块用于为函数提供可选的一次性后续处理。

下面的示例演示了一个函数的轮廓，该函数包含 `Begin` 一个用于一次性预处理的块、一个 `Process` 用于处理多个记录的块和 `End` 一个用于处理一次性后处理的块。

```powershell
Function Test-ScriptCmdlet
{
[CmdletBinding(SupportsShouldProcess=$True)]
    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

> [!NOTE]
> 使用 `Begin` 或 `End` 块需要定义所有三个块。 使用全部三个块时，所有 PowerShell 代码必须位于一个块内。

### <a name="confirmation-methods"></a>确认方法

#### <a name="shouldprocess"></a>ShouldProcess

在函数执行将更改系统的操作之前，调用此方法来请求用户确认。 函数可根据方法返回的布尔值继续。 只能从函数块内调用此方法 `Process{}` 。 `CmdletBinding`特性还必须声明函数支持 `ShouldProcess` (，如前面的示例) 中所示。

有关此方法的详细信息，请参阅 [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess)。

有关如何请求确认的详细信息，请参阅 [请求确认](/powershell/scripting/developer/cmdlet/requesting-confirmation)。

#### <a name="shouldcontinue"></a>ShouldContinue

调用此方法以请求另一条确认消息。 当方法返回时，应调用此 `ShouldProcess` 方法 `$true` 。 有关此方法的详细信息，请参阅 [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue)。

### <a name="error-methods"></a>错误方法

当发生错误时，函数可以调用两种不同的方法。 当发生非终止错误时，函数应调用 `WriteError` 方法，方法部分对此进行了说明 `Write` 。 当发生终止错误并且函数无法继续时，它应调用 `ThrowTerminatingError` 方法。 你还可以使用 `Throw` 语句来终止错误，并使用 [写错误](xref:Microsoft.PowerShell.Utility.Write-Error) cmdlet 来实现非终止错误。

有关详细信息，请参阅 [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror)。

### <a name="write-methods"></a>写入方法

函数可以调用以下方法来返回不同类型的输出。
请注意，并非所有输出都转到管道中的下一个命令。 你还可以使用各种 `Write` cmdlet，例如 `Write-Error` 。

#### <a name="writecommanddetail"></a>WriteCommandDetail

有关方法的信息 `WriteCommandDetails` ，请参阅 [WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail)。

#### <a name="writedebug"></a>WriteDebug

若要提供可用于排查函数问题的信息，请使函数调用 `WriteDebug` 方法。 `WriteDebug`方法向用户显示调试消息。 有关详细信息，请参阅 [WriteDebug](/dotnet/api/system.management.automation.cmdlet.writedebug)。

#### <a name="writeerror"></a>WriteError

当发生非终止错误并且函数旨在继续处理记录时，函数应调用此方法。 有关详细信息，请参阅 [WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror)。

> [!NOTE]
> 如果发生终止错误，则函数应调用 [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) 方法。

#### <a name="writeobject"></a>WriteObject

`WriteObject`方法允许函数将对象发送到管道中的下一个命令。 在大多数情况下， `WriteObject` 是在函数返回数据时要使用的方法。 有关详细信息，请参阅 [PSCmdlet. WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject)。

#### <a name="writeprogress"></a>WriteProgress

对于包含需要很长时间才能完成的操作的函数，此方法允许函数调用方法以 `WriteProgress` 显示进度信息。 例如，可以显示已完成的百分比。
有关详细信息，请参阅 [PSCmdlet. WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress)。

#### <a name="writeverbose"></a>WriteVerbose

若要提供有关函数正在执行的操作的详细信息，请将函数调用 `WriteVerbose` 为向用户显示详细消息。 默认情况下，不显示详细消息。 有关详细信息，请参阅 [PSCmdlet. WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose)。

#### <a name="writewarning"></a>WriteWarning

若要提供有关可能会导致意外结果的情况的信息，请使函数调用 WriteWarning 方法来向用户显示警告消息。 默认情况下，会显示警告消息。 有关详细信息，请参阅 [PSCmdlet. WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning)。

> [!NOTE]
> 还可以通过配置 `$WarningPreference` 变量或使用 `Verbose` 和 `Debug` 命令行选项来显示警告消息。 有关变量的详细信息 `$WarningPreference` ，请参阅 [about_Preference_Variables](about_Preference_Variables.md)。

### <a name="other-methods-and-properties"></a>其他方法和属性

有关可以通过变量访问的其他方法和属性的信息 `$PSCmdlet` ，请参阅 [PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)。

例如， [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) 属性允许您查看正在使用的参数集。 参数集允许您创建一个函数，该函数根据运行函数时指定的参数执行不同的任务。

## <a name="see-also"></a>请参阅

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Preference_Variables](about_Preference_Variables.md)

