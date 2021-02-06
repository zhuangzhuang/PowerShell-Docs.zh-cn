---
description: 定义脚本块的定义，并说明如何在 PowerShell 编程语言中使用脚本块。
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_blocks?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Blocks
ms.openlocfilehash: 1ba5e92bedc03a2d61d528715ab13c5d96eb3075
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596238"
---
# <a name="about-script-blocks"></a>关于脚本块

## <a name="short-description"></a>简短说明

定义脚本块的定义，并说明如何在 PowerShell 编程语言中使用脚本块。

## <a name="long-description"></a>长说明

在 PowerShell 编程语言中，脚本块是可用作单个单元的语句或表达式的集合。
脚本块可以接受参数并返回值。

从语法上讲，脚本块是括在大括号中的语句列表，如下面的语法所示：

```
{<statement list>}
```

脚本块以单个对象或数组形式返回脚本块中所有命令的输出。

你还可以使用关键字指定返回值 `return` 。 `return`关键字不会影响或禁止从脚本块返回的其他输出。 不过， `return` 关键字退出该脚本块。 有关详细信息，请参阅 [about_Return](about_Return.md)。

与函数一样，脚本块可以包含参数。 使用 Param 关键字分配命名参数，如以下语法所示：

```
{
Param([type]$Parameter1 [,[type]$Parameter2])
<statement list>
}
```

> [!NOTE]
> 在脚本块中，与函数不同，不能在大括号之外指定参数。

与函数一样，脚本块可以包含 `DynamicParam` 、 `Begin` 、 `Process` 和 `End` 关键字。 有关详细信息，请参阅 [about_Functions](about_Functions.md) 和 [about_Functions_Advanced](about_Functions_Advanced.md)。

## <a name="using-script-blocks"></a>使用脚本块

脚本块是 Microsoft .NET 框架类型的实例 `System.Management.Automation.ScriptBlock` 。 命令可以具有脚本块参数值。 例如， `Invoke-Command` cmdlet 具有一个 `ScriptBlock` 采用脚本块值的参数，如以下示例中所示：

```powershell
Invoke-Command -ScriptBlock { Get-Process }
```

```Output
Handles  NPM(K)    PM(K)     WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----     ----- -----   ------     -- -----------
999          28    39100     45020   262    15.88   1844 communicator
721          28    32696     36536   222    20.84   4028 explorer
...
```

`Invoke-Command` 还可以执行具有参数块的脚本块。
使用 **ArgumentList** 参数按位置分配参数。

```powershell
Invoke-Command -ScriptBlock { param($p1, $p2)
"p1: $p1"
"p2: $p2"
} -ArgumentList "First", "Second"
```

```Output
p1: First
p2: Second
```

前面的示例中的脚本块使用 `param` 关键字创建参数 `$p1` 和 `$p2` 。 字符串 "First" 绑定到)  (第一个参数 `$p1` ，而 "Second" 绑定到 (`$p2`) 。

有关 **ArgumentList** 行为的详细信息，请参阅 [about_Splatting](about_Splatting.md#splatting-with-arrays)。

您可以使用变量来存储和执行脚本块。 下面的示例将一个脚本块存储在一个变量中，并将其传递给 `Invoke-Command` 。

```powershell
$a = { Get-Service BITS }
Invoke-Command -ScriptBlock $a
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  BITS               Background Intelligent Transfer Ser...
```

Call 运算符是执行存储在变量中的脚本块的另一种方法。
与一样 `Invoke-Command` ，调用运算符执行子范围中的脚本块。 调用运算符可使你更轻松地将参数用于脚本块。

```powershell
$a ={ param($p1, $p2)
"p1: $p1"
"p2: $p2"
}
&$a -p2 "First" -p1 "Second"
```

```Output
p1: Second
p2: First
```

您可以使用赋值将脚本块中的输出存储在变量中。

```
PS>  $a = { 1 + 1}
PS>  $b = &$a
PS>  $b
2
```

```
PS>  $a = { 1 + 1}
PS>  $b = Invoke-Command $a
PS>  $b
2
```

有关调用运算符的详细信息，请参阅 [about_Operators](about_Operators.md)。

## <a name="using-delay-bind-script-blocks-with-parameters"></a>将延迟绑定脚本块与参数一起使用

一个类型化参数，该参数接受管道输入 (`by Value`) 或 (`by PropertyName`) 允许在参数上使用 **延迟绑定** 脚本块。
在 **延迟绑定** 脚本块中，可以使用管道变量引用对象中的管道 `$_` 。

```powershell
# Renames config.log to old_config.log
dir config.log | Rename-Item -NewName {"old_" + $_.Name}
```

在更复杂的 cmdlet 中，延迟绑定脚本块允许在对象中重复使用一个管道来填充其他参数。

延迟时 **的说明-** 将脚本块绑定为参数：

- 您必须显式指定任何用于 **延迟绑定** 脚本块的参数名称。
- 参数不能是非类型化的，并且参数的类型不能为 `[scriptblock]` 或 `[object]` 。
- 如果在不提供管道输入的情况下使用 **延迟绑定** 脚本块，会收到错误。

  ```powershell
  Rename-Item -NewName {$_.Name + ".old"}
  ```

  ```Output
  Rename-Item : Cannot evaluate parameter 'NewName' because its argument is
  specified as a script block and there is no input. A script block cannot
  be evaluated without input.
  At line:1 char:23
  +  Rename-Item -NewName {$_.Name + ".old"}
  +                       ~~~~~~~~~~~~~~~~~~
      + CategoryInfo          : MetadataError: (:) [Rename-Item],
        ParameterBindingException
      + FullyQualifiedErrorId : ScriptBlockArgumentNoInput,
        Microsoft.PowerShell.Commands.RenameItemCommand
  ```

## <a name="see-also"></a>另请参阅

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Operators](about_Operators.md)

