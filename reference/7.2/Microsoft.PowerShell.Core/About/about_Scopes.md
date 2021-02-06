---
description: 说明 PowerShell 中的作用域的概念，并演示如何设置和更改元素的作用域。
Locale: en-US
ms.date: 11/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_scopes
ms.openlocfilehash: c9439412ab80eee4cedc1265a3927a274547d409
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595418"
---
# <a name="about-scopes"></a>关于范围

## <a name="short-description"></a>简短说明
说明 PowerShell 中的作用域的概念，并演示如何设置和更改元素的作用域。

## <a name="long-description"></a>长说明

PowerShell 通过限制可以读取和更改变量、别名、函数和 PowerShell 驱动器 (PSDrives) ，来保护这些驱动器的访问。 PowerShell 使用范围规则确保你不会无意中更改不应更改的项。

下面是范围的基本规则：

- 范围可以嵌套。 外部作用域称为父作用域。 任何嵌套的作用域都是该父级的子作用域。

- 项目在创建它的作用域和任何子作用域中可见，除非你显式将其设为私有。 可以在一个或多个作用域中放置变量、别名、函数或 PowerShell 驱动器。

- 在范围内创建的项只能在创建它的范围内更改，除非显式指定了不同的范围。

如果在作用域中创建一个项，并且该项与不同范围内的项共享其名称，则原始项可能会隐藏在新项下，但不会被覆盖或更改。

## <a name="powershell-scopes"></a>PowerShell 范围

PowerShell 支持以下作用域：

- 全局： PowerShell 启动或创建新会话或运行空间时生效的作用域。 在全局作用域（例如自动变量和首选项变量）中创建了 PowerShell 启动时出现的变量和函数。 PowerShell 配置文件中的变量、别名和函数也是在全局范围内创建的。 全局范围是会话中的根父范围。

- Local：当前范围。 本地作用域可以是全局作用域或任何其他作用域。

- 脚本：运行脚本文件时创建的作用域。 只有脚本中的命令在脚本作用域中运行。 对于脚本中的命令，脚本范围为本地范围。

> [!NOTE]
> **私有** 不是范围。 它是一个 [选项](#private-option) ，它更改项的范围之外的项的可见性。

## <a name="parent-and-child-scopes"></a>父范围和子范围

可以通过调用脚本或函数来创建新的子作用域。 调用范围为父范围。 被调用的脚本或函数是子作用域。
您调用的函数或脚本可以调用其他函数，从而创建子范围的层次结构，该层次结构的根作用域是全局作用域。

除非显式将项设置为私有，否则父范围中的项可用于子范围。 但是，在子范围内创建和更改的项不影响父范围，除非你在创建项时显式指定范围。

> [!NOTE]
> 模块中的函数不在调用作用域的子范围中运行。
> 模块具有其自己的会话状态，该状态链接到全局范围。
> 所有模块代码都在具有自身根作用域的特定于模块的范围层次结构中运行。

## <a name="inheritance"></a>继承

子作用域不从父作用域继承变量、别名和函数。 除非项是私有的，否则子范围可以查看父范围中的项。 并且，它可以通过显式指定父范围来更改项，但项不是子范围的一部分。

但是，使用一组项创建子范围。 通常，它包括具有 **AllScope** 选项的所有别名。 本文稍后将对此进行讨论。 它包括具有 **AllScope** 选项的所有变量，以及一些自动变量。

若要查找特定范围中的项，请使用或的作用域参数 `Get-Variable` `Get-Alias` 。

例如，若要获取本地范围内的所有变量，请键入：

```powershell
Get-Variable -Scope local
```

若要获取全局范围内的所有变量，请键入：

```powershell
Get-Variable -Scope global
```

## <a name="scope-modifiers"></a>作用域修饰符

变量、别名或函数名可以包含以下任意一种可选的作用域修饰符：

- `global:` -指定名称存在于 **全局** 范围内。
- `local:` -指定名称存在于 **本地** 作用域中。 当前范围始终是 **本地** 范围。
- `private:` -指定该名称是 **私有** 的，仅对当前作用域可见。
- `script:` -指定名称存在于 **脚本** 作用域中。
  如果没有最近的上级脚本文件，则 **脚本** 范围是最近的上级脚本文件的范围或 **全局**。
- `using:` -用于在通过 cmdlet （如和）运行脚本时访问在其他作用域中定义的变量 `Start-Job` `Invoke-Command` 。
- `workflow:` -指定名称存在于工作流中。 注意： PowerShell Core 不支持工作流。
- `<variable-namespace>` -PowerShell New-psdrive 提供程序创建的修饰符。
  例如：

  |  命名空间  |                    说明                     |
  | ----------- | -------------------------------------------------- |
  | `Alias:`    | 当前作用域中定义的别名               |
  | `Env:`      | 在当前作用域中定义的环境变量 |
  | `Function:` | 当前作用域中定义的函数             |
  | `Variable:` | 当前作用域中定义的变量             |

脚本的默认作用域为脚本范围。 函数和别名的默认作用域为本地作用域，即使它们是在脚本中定义的也是如此。

### <a name="using-scope-modifiers"></a>使用作用域修饰符

若要指定新变量、别名或函数的作用域，请使用作用域修饰符。

变量中的作用域修饰符的语法为：

```
$[<scope-modifier>:]<name> = <value>
```

函数中的作用域修饰符的语法为：

```
function [<scope-modifier>:]<name> {<function-body>}
```

以下不使用范围修饰符的命令将在当前或 **本地** 范围内创建变量：

```powershell
$a = "one"
```

若要在 **全局** 作用域中创建相同的变量，请使用作用域 `global:` 修饰符：

```powershell
$global:a = "one"
```

若要在 **脚本** 作用域中创建相同的变量，请使用 `script:` 作用域修饰符：

```powershell
$script:a = "one"
```

还可以将作用域修饰符用于函数。 以下函数定义将在 **全局** 范围内创建函数：

```powershell
function global:Hello {
  Write-Host "Hello, World"
}
```

你还可以使用作用域修饰符来引用不同范围中的变量。
以下命令 `$test` 首先引用本地作用域中的变量，然后在全局范围内引用：

```powershell
$test
$global:test
```

### <a name="the-using-scope-modifier"></a>`Using:`作用域修饰符

使用是一个特殊的作用域修饰符，用来标识远程命令中的局部变量。 如果不使用修饰符，则 PowerShell 应在远程会话中定义远程命令中的变量。

`Using`PowerShell 3.0 中引入了作用域修饰符。

对于任何执行进程外的脚本或命令，都需要 `Using` 范围修饰符来嵌入调用会话范围内的变量值，以便使会话代码不能访问它们。 `Using`以下上下文支持作用域修饰符：

- 远程执行的命令，已开始 `Invoke-Command` 使用 **ComputerName**、 **HostName**、 **SSHConnection** 或 **Session** 参数 (远程会话) 
- 后台作业， `Start-Job` (进程外会话开始) 
- 通过 `Start-ThreadJob` 或 `ForEach-Object -Parallel` (单独的线程会话启动的线程作业) 

根据上下文，嵌入变量值是调用方的作用域中的数据的独立副本或对其的引用。 在远程和进程外会话中，它们始终是独立的副本。

有关详细信息，请参阅 [about_Remote_Variables](about_Remote_Variables.md)。

在线程会话中，它们是通过引用传递的。 这意味着可以在不同的线程中修改调用范围变量。 安全修改变量需要线程同步。

有关详细信息，请参阅：

- [Start-ThreadJob](xref:ThreadJob.Start-ThreadJob)
- [ForEach-Object](xref:Microsoft.PowerShell.Core.ForEach-Object)

#### <a name="serialization-of-variable-values"></a>变量值的序列化

远程执行的命令和后台作业在进程外运行。
进程外会话使用基于 XML 的序列化和反序列化来使变量的值可在进程边界内使用。 序列化进程将对象转换为包含原始对象属性但不包含其方法的 **PSObject** 。

对于有限类型的类型，请将解除冻结对象反序列化为原始类型。 解除冻结对象是原始对象实例的副本。
它具有类型属性和方法。 对于简单的类型（如 **system.object**），副本是精确的。 对于复杂类型，复制为完善。 例如，解除冻结证书对象不包含私钥。

所有其他类型的实例都是 **PSObject** 实例。 **PSTypeNames** 属性包含以 **反序列化** 的原始类型名称，例如 **Deserialized.System。Data DataTable**

### <a name="the-allscope-option"></a>AllScope 选项

变量和别名有一个 **选项** 属性，该属性的值为 **AllScope**。 具有 **AllScope** 属性的项将成为你创建的任何子范围的一部分，尽管它们不会被父范围继承。

具有 **AllScope** 属性的项在子范围中是可见的，它是该范围的一部分。 对任何范围内的项所做的更改都会影响定义该变量的所有范围。

### <a name="managing-scope"></a>管理作用域

多个 cmdlet 具有 **作用域** 参数，可让你获取或设置 (创建和更改特定作用域中) 项的功能。 使用以下命令查找会话中具有 **作用域** 参数的所有 cmdlet：

```powershell
Get-Help * -Parameter scope
```

若要查找在特定作用域中可见的变量，请使用的 `Scope` 参数 `Get-Variable` 。 可见变量包括全局变量、父作用域中的变量以及当前作用域中的变量。

例如，以下命令将获取在本地作用域中可见的变量：

```powershell
Get-Variable -Scope local
```

若要在特定范围内创建变量，请使用的作用域修饰符或 **作用域** 参数 `Set-Variable` 。 以下命令在全局范围内创建变量：

```powershell
New-Variable -Scope global -Name a -Value "One"
```

你还可以使用、或 cmdlet 的作用域参数 `New-Alias` `Set-Alias` `Get-Alias` 来指定作用域。 以下命令在全局范围内创建一个别名：

```powershell
New-Alias -Scope global -Name np -Value Notepad.exe
```

若要获取特定范围中的函数，请 `Get-Item` 在范围内使用 cmdlet。 `Get-Item`Cmdlet 没有 **Scope** 参数。

> [!NOTE]
> 对于使用 **Scope** 参数的 cmdlet，还可以按编号引用范围。 该数字描述一个作用域相对于另一个作用域的相对位置。 范围0表示当前范围或本地范围。 作用域1指示直接父作用域。 作用域2指示父作用域的父项，依此类推。 如果已创建多个递归作用域，编号范围很有用。

### <a name="using-dot-source-notation-with-scope"></a>在作用域中使用点源表示法

脚本和函数遵循作用域的所有规则。 在特定的范围内创建它们，除非使用 cmdlet 参数或作用域修饰符来更改该作用域，否则它们只会影响该作用域。

但是，您可以使用点源表示法将脚本或函数添加到当前作用域。 然后，当脚本在当前作用域中运行时，该脚本创建的任何函数、别名和变量都在当前作用域中可用。

若要将函数添加到当前作用域，请在函数调用中键入一个句点 (. ) 和该函数的路径和名称之前的空格。

例如，若要在脚本范围中的 C：\Scripts 目录中运行 Sample.ps1 脚本 (脚本) 的默认值，请使用以下命令：

```powershell
c:\scripts\sample.ps1
```

若要在本地作用域中运行 Sample.ps1 脚本，请使用以下命令：

```powershell
. c:\scripts.sample.ps1
```

使用 call 运算符 ( # A0) 运行函数或脚本时，不会将其添加到当前作用域。 下面的示例使用调用运算符：

```powershell
& c:\scripts.sample.ps1
```

可以在 [about_operators](about_operators.md)中详细了解 call 运算符。

Sample.ps1 脚本创建的任何别名、函数或变量在当前作用域中都不可用。

## <a name="restricting-without-scope"></a>不带作用域的限制

一些 PowerShell 概念类似于作用域或与作用域交互。 这些概念可能会与范围或范围的行为混淆。

会话、模块和嵌套的提示是独立的环境，但是它们不是会话中全局作用域的子作用域。

### <a name="sessions"></a>会话

会话是 PowerShell 运行的环境。 在远程计算机上创建会话时，PowerShell 会建立与远程计算机的持久连接。 使用持久性连接可以将会话用于多个相关命令。

由于会话是包含的环境，因此它具有其自己的作用域，但会话不是在其中创建它的会话的子作用域。 该会话从其自己的全局作用域开始。 此作用域独立于会话的全局作用域。 你可以在会话中创建子作用域。 例如，你可以运行一个脚本以在会话中创建子作用域。

### <a name="modules"></a>模块

你可以使用 PowerShell 模块来共享和传递 PowerShell 工具。 模块是一个可包含 cmdlet、脚本、函数、变量、别名和其他有用项的单位。 除非显式定义，否则模块中的项在模块外部不可访问。 因此，可以将该模块添加到会话中，并使用这些公共项，而不必担心其他项可能会覆盖会话中的 cmdlet、脚本、函数和其他项。

默认情况下，模块将加载到当前 _会话状态_ 的顶层，而不是当前 _作用域_。 当前会话状态可以是模块会话状态或全局会话状态。 向会话添加模块不会更改范围。 如果在全局范围内，则将模块加载到全局会话状态。 所有导出都放置在全局表中。
如果从 module1 _中_ 加载 module2，则 module2 将加载到 module1 的会话状态，而不是全局会话状态。 Module2 中的任何导出都置于 module1 会话状态的顶部。 如果使用 `Import-Module -Scope local` ，则会将导出置于当前范围对象而不是顶级。 如果你 _在模块中_ ，并使用 `Import-Module -Scope global` (或 `Import-Module -Global`) 加载另一个模块，则该模块及其导出将加载到全局会话状态，而不是模块的本地会话状态。 此功能设计用于编写操作模块的模块。 **WindowsCompatibility** 模块执行此将代理模块导入全局会话状态。

在会话状态中，模块具有其自己的作用域。 请考虑以下模块 `C:\temp\mod1.psm1` ：

```powershell
$a = "Hello"

function foo {
    "`$a = $a"
    "`$global:a = $global:a"
}
```

现在，我们创建一个全局变量 `$a` ，为其指定一个值，并调用函数 **foo**。

```powershell
$a = "Goodbye"
foo
```

模块 `$a` 在模块范围内声明变量，而函数 **foo** 则在这两个作用域中输出该变量的值。

```Output
$a = Hello
$global:a = Goodbye
```

### <a name="nested-prompts"></a>嵌套提示

嵌套式提示不具有其自己的作用域。 当您输入嵌套提示符时，嵌套提示符将是环境的子集。 但仍在本地范围内。

脚本具有自己的作用域。 如果要调试脚本，并在脚本中找到断点，则输入脚本范围。

### <a name="private-option"></a>Private 选项

别名和变量具有 **选项** 属性，该属性的值可以是 **Private**。 具有 **Private** 选项的项可以在创建它们的范围内查看和更改，但无法在该范围外查看或更改它们。

例如，如果在全局作用域中创建一个具有 private 选项的变量，然后运行脚本，则 `Get-Variable` 该脚本中的命令不显示专用变量。 在此实例中使用全局作用域修饰符不显示私有变量。

可以使用 `New-Variable` 、、和 cmdlet 的选项参数 `Set-Variable` `New-Alias` `Set-Alias` 将选项属性的值设置为私有。

### <a name="visibility"></a>可见性

变量或别名的 " **可见性** " 属性决定了是否可以在创建容器的容器外查看项。 容器可以是模块、脚本或管理单元。 可见性适用于容器的设计方式与 **选项** 属性的 **私有** 值为作用域设计的方式相同。

**Visibility** 属性采用 **公共** 值和 **私有** 值。 只有在创建了私有可见性的项的容器中才能查看和更改这些项。 如果已添加或导入容器，则无法查看或更改具有私有可见性的项。

由于可见性是为容器设计的，因此它在作用域中的工作方式有所不同。

- 如果创建的项在全局范围内具有私有可见性，则无法查看或更改任何范围中的项。
- 如果尝试查看或更改具有私有可见性的变量的值，则 PowerShell 将返回错误消息。

您可以使用 `New-Variable` 和 `Set-Variable` cmdlet 来创建具有私有可见性的变量。

## <a name="examples"></a>示例

### <a name="example-1-change-a-variable-value-only-in-a-script"></a>示例1：仅在脚本中更改变量值

以下命令更改 `$ConfirmPreference` 脚本中变量的值。 此更改不会影响全局范围。

首先，若要 `$ConfirmPreference` 在本地范围中显示变量的值，请使用以下命令：

```
PS>  $ConfirmPreference
High
```

创建包含以下命令的 Scope.ps1 脚本：

```powershell
$ConfirmPreference = "Low"
"The value of `$ConfirmPreference is $ConfirmPreference."
```

运行该脚本。 此脚本将更改变量的值 `$ConfirmPreference` ，然后在脚本作用域中报告其值。 输出应类似于以下输出：

```output
The value of $ConfirmPreference is Low.
```

接下来，测试 `$ConfirmPreference` 当前作用域中的变量的当前值。

```
PS>  $ConfirmPreference
High
```

此示例说明对脚本作用域中变量的值所做的更改不会影响父作用域中的变量值。

### <a name="example-2-view-a-variable-value-in-different-scopes"></a>示例2：查看不同范围中的变量值

您可以使用作用域修饰符来查看本地范围和父范围中的变量的值。

首先， `$test` 在全局范围内定义变量。

```powershell
$test = "Global"
```

接下来，创建一个定义变量的 Sample.ps1 脚本 `$test` 。 在脚本中，使用范围修饰符来引用变量的全局或局部版本 `$test` 。

在 Sample.ps1 中：

```powershell
$test = "Local"
"The local value of `$test is $test."
"The global value of `$test is $global:test."
```

运行 Sample.ps1 时，输出应类似于以下输出：

```output
The local value of $test is Local.
The global value of $test is Global.
```

当脚本完成时，只有的全局值 `$test` 在会话中定义。

```
PS>  $test
Global
```

### <a name="example-3-change-the-value-of-a-variable-in-a-parent-scope"></a>示例3：更改父作用域中的变量的值

除非使用 Private 选项或其他方法保护项，否则可以在父范围中查看和更改变量的值。

首先， `$test` 在全局范围内定义变量。

```powershell
$test = "Global"
```

接下来，创建一个定义变量的 Sample.ps1 脚本 `$test` 。 在脚本中，使用范围修饰符来引用变量的全局或局部版本 `$test` 。

在 Sample.ps1 中：

```powershell
$global:test = "Local"
"The global value of `$test is $global:test."
```

脚本完成后，的全局值 `$test` 将更改。

```
PS>  $test
Local
```

### <a name="example-4-creating-a-private-variable"></a>示例4：创建私有变量

私有变量是具有值为 *private* 的 **选项** 属性的变量。 *私有* 变量由子作用域继承，但只能在创建它们的作用域中查看或更改它们。

下面的命令创建一个 `$ptest` 在本地范围中调用的私有变量。

```powershell
New-Variable -Name ptest -Value 1 -Option private
```

您可以 `$ptest` 在本地范围中显示和更改的值。

```
PS>  $ptest
1

PS>  $ptest = 2
PS>  $ptest
2
```

接下来，创建一个包含以下命令的 Sample.ps1 脚本。 命令尝试显示并更改的值 `$ptest` 。

在 Sample.ps1 中：

```powershell
"The value of `$Ptest is $Ptest."
"The value of `$Ptest is $global:Ptest."
```

`$ptest`变量在脚本作用域中不可见，输出为空。

```powershell
"The value of $Ptest is ."
"The value of $Ptest is ."
```

### <a name="example-5-using-a-local-variable-in-a-remote-command"></a>示例5：使用远程命令中的局部变量

对于在本地会话中创建的远程命令中的变量，请使用 `Using` 作用域修饰符。 PowerShell 假设远程会话中创建了远程命令中的变量。

语法为：

```
$Using:<VariableName>
```

例如，以下命令在 `$Cred` 本地会话中创建一个变量，然后 `$Cred` 在远程命令中使用该变量：

```powershell
$Cred = Get-Credential
Invoke-Command $s {Remove-Item .\Test*.ps1 -Credential $Using:Cred}
```

使用范围是在 PowerShell 3.0 中引入的。 在 PowerShell 2.0 中，若要指示在本地会话中创建了变量，请使用以下命令格式。

```powershell
$Cred = Get-Credential
Invoke-Command $s {
  param($c)
  Remove-Item .\Test*.ps1 -Credential $c
} -ArgumentList $Cred
```

## <a name="see-also"></a>请参阅

[about_Variables](about_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Functions](about_Functions.md)

[about_Script_Blocks](about_Script_Blocks.md)

[Start-ThreadJob](/powershell/module/ThreadJob/Start-ThreadJob)
