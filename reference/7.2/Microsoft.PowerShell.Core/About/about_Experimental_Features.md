---
description: PowerShell 中的实验性功能支持提供了一种机制，可便于实验性功能与 PowerShell 或 PowerShell 模块中的现有稳定功能共存。
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 关于实验性功能
ms.openlocfilehash: 82f5ef9838fcbb98e71e362ad00b1ec68f9a9f67
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598283"
---
# <a name="experimental-features"></a>实验性功能

PowerShell 中的实验性功能支持提供了一种机制，可便于实验性功能与 PowerShell 或 PowerShell 模块中的现有稳定功能共存。

实验性功能是指设计尚未最终确定的功能。 此类功能可供用户进行测试和提供反馈。 一旦实验性功能最终确定下来，设计变更就变成了中断性变更。 实验性功能不适合在生产环境中使用，因为允许变更成为中断性变更。

默认情况下，实验功能处于禁用状态，需要由系统的用户或管理员显式启用。

启用的实验性功能列在 " `powershell.config.json` `$PSHOME` 适用于所有用户的文件" 或特定用户的用户特定的配置文件中。

> [!NOTE]
> 用户配置文件中启用的实验性功能优先于系统配置文件中列出的实验性功能。

## <a name="the-experimental-attribute"></a>实验特性

使用 `Experimental` 属性将一些代码声明为实验性。

使用以下语法声明一个 `Experimental` 属性，该属性提供实验功能的名称和启用实验功能时要执行的操作：

```csharp
[Experimental(NameOfExperimentalFeature, ExperimentAction)]
```

对于模块， `NameOfExperimentalFeature` 必须遵循的形式 `<modulename>.<experimentname>` 。 `ExperimentAction`必须指定参数，并且唯一有效值为：

- `Show` 表示在启用功能的情况下显示此试验性功能
- `Hide` 如果启用了该功能，则表示隐藏此试验性功能

### <a name="declaring-experimental-features-in-modules-written-in-c"></a>在用 C 语言编写的模块中声明实验性功能\#

要使用实验功能标志的模块作者可以通过使用属性将 cmdlet 声明为试验性 `Experimental` 。

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }
```

### <a name="declaring-experimental-features-in-modules-written-in-powershell"></a>在用 PowerShell 编写的模块中声明实验性功能

使用 PowerShell 编写的模块还可以使用 `Experimental` 属性声明实验性 cmdlet：

```powershell
function Enable-SSHRemoting {
    [Experimental("MyRemoting.PSSSHRemoting", "Show")]
    [CmdletBinding()]
    param()
    ...
}
```

### <a name="mutually-exclusive-experimental-features"></a>相互排斥的实验性功能

在某些情况下，实验功能不能与现有功能或其他实验功能并存。

例如，可以有一个可替代现有 cmdlet 的试验性 cmdlet。 这两个版本不能并行共存。 `ExperimentAction.Hide`设置允许一次只启用这两个 cmdlet 之一。

在此示例中，我们将创建一个新的实验性 `Invoke-WebRequest` cmdlet。
`InvokeWebRequestCommand` 包含非试验性实现。
`InvokeWebRequestCommandV2` 包含 cmdlet 的实验版本。

使用 `ExperimentAction.Hide` 将只允许一次启用这两项功能之一：

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }

[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Hide)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommand : WebCmdletBase { ... }
```

`MyWebCmdlets.PSWebCmdletV2`启用实验功能后，将 `InvokeWebRequestCommand` 隐藏现有实现，并提供的 `InvokeWebRequestCommandV2` 实现 `Invoke-WebRequest` 。

这样，用户就可以试用新的 cmdlet 并提供反馈，并在需要时恢复到非实验版本。

### <a name="experimental-parameters-in-cmdlets"></a>Cmdlet 中的实验参数

`Experimental`特性还可以应用于单个参数。 这允许您为现有 cmdlet （而不是全新的 cmdlet）创建实验参数集。

下面是 c # 中的一个示例：

```csharp
[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Show)]
[Parameter(ParameterSet = "NewCompilation")]
public CompilationParameters CompileParameters { ... }

[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Hide)]
[Parameter()]
public CodeDom CodeDom { ... }
```

下面是 PowerShell 脚本中的其他示例：

```powershell
param(
    [Experimental("MyModule.PSNewFeature", "Show")]
    [string] $NewName,

    [Experimental("MyModule.PSNewFeature", "Hide")]
    [string] $OldName
)
```

## <a name="checking-if-an-experimental-feature-is-enabled"></a>检查试验性功能是否已启用

在代码中，需要检查是否已启用实验功能，然后再采取适当的措施。 您可以使用类的静态方法来确定是否启用了实验功能 `IsEnabled()` `System.Management.Automation.ExperimentalFeature` 。

下面是 c # 中的一个示例：

```csharp
if (ExperimentalFeature.IsEnabled("MyModule.MyExperimentalFeature"))
{
   // code specific to the experimental feature
}
```

下面是 PowerShell 脚本中的一个示例：

```powershell
if ([ExperimentalFeature]::IsEnabled("MyModule.MyExperimentalFeature"))
{
  # code specific to the experimental feature
}
```

## <a name="see-also"></a>请参阅

[Enable-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Enable-ExperimentalFeature)

[Disable-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Disable-ExperimentalFeature)

[Get-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Get-ExperimentalFeature)

